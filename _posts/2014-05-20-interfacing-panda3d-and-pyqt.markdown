---
layout: post
title:  "Interfacing Panda3d and PyQt4"
date:   2014-05-20 11:20:00
categories: gsoc update
---

<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/panda-qt-1.png">
</div><span>A Panda3d window and a PyQt window running simultaneously. The Open Files Dialog was created from a File menu in PyQt interface.</span></div>

This is a long post and is intended for those who are facing problems in interfacing Panda3d and PyQt4. Hope this post clears some doubts.<br><br>
I wanted to make a GUI in PyQt4 for my 3d-auv-simulator(this is what I named my GSOC project). So I started with the basic code found at the [zetcode site][Zetcode]. Alone, PyQt ran very smoothly. But as soon as I added Panda3d's <code>run()</code> method in my code, everything seemed to go haywire. The PyQt window started crashing and the Panda3D window started hanging.<br><br>
What I realised late from all this was the fact that Panda3d's <code>run()</code> method has its own event loop. In fact, it is the main loop running behind Panda3d. PyQt also has its own event loop. This was the reason why my code was crashing initially since a single program can have only one event loop.<br><br>
<div class="block">
To deal with this situation, any one of the following solutions can be used:<br>
1. Use Panda3d's Direct GUI module instead of PyQt4. (But I like Qt more than any other GuI interface)<br>
2. Use multithreading to separate the two event loops. (This is what I chose to do)<br>
3. Use Tasks in Panda3d as an alternative to multithreading. (I haven't explored this yet)<br>
</div>

Panda3d is built in C++. So its site says that its better to use this: <br>

{% highlight python %}
from direct.stdpy import threading
{% endhighlight %}
instead of this:<br>
{% highlight python %}
import threading
{% endhighlight %}

<code>threading</code> is the python's library to deal with threads. I wrote my code using this library. Other options are to use <code>QThread</code> library of PyQt4. Below are the 3 classes that I created. Run the <code>main-test.py</code> to see everything working.<br>
<div class="block">qtThread.py : Deals with setting up the qt interface.</div>
{% highlight python %}
from PyQt4 import QtGui, QtCore
import sys

class qtThread(QtGui.QMainWindow):
    def __init__(self, parent=None):

        super(qtThread, self).__init__(parent)
        
        self.setWindowTitle('3D AUV Simulator')
        self.resize(500, 500)

        #  exit action
        exitAction = QtGui.QAction(QtGui.QIcon.fromTheme('exit'), '&Exit', self)
        exitAction.setShortcut('Ctrl+Q')
        exitAction.setStatusTip('Exit Application')
        exitAction.triggered.connect(QtCore.QCoreApplication.instance().quit)

        # open action
        openFile = QtGui.QAction(QtGui.QIcon.fromTheme('open'), '&Open', self)
        openFile.setShortcut('Ctrl+O')
        openFile.setStatusTip('Open new file')
        openFile.triggered.connect(self.showDialog)

        # status bar
        self.statusBar().showMessage('Ready')

        # button
        qbtn = QtGui.QPushButton('Quit', self)
        qbtn.clicked.connect(QtCore.QCoreApplication.instance().quit)
        qbtn.resize(qbtn.sizeHint())
        qbtn.move(5, 350)

        # menubar
        menubar = self.menuBar()
        fileMenu = menubar.addMenu('&File')
        fileMenu.addAction(openFile)
        fileMenu.addAction(exitAction)

        # toolbar
        self.toolbar = self.addToolBar('Exit')
        self.toolbar.addAction(exitAction)

        # center the window
        self.center()

    # to center the window
    def center(self):
    	qr = self.frameGeometry()
    	cp = QtGui.QDesktopWidget().availableGeometry().center()
    	qr.moveCenter(cp)
    	self.move(qr.topLeft())

    #  to open the Open file dialog
    def showDialog(self):
    	fname = QtGui.QFileDialog.getOpenFileName(self, 'Open File', '/home')
    	f = open(fname, 'r')

    	with f:
    		data = f.read()
    		self.textEdit.setText(data)
		
{% endhighlight %}

<br>
<div class="block">pandaThread.py : Deals with setting up Panda3d's environment.</div>
{% highlight python %}
from direct.showbase.ShowBase import ShowBase
from pandac.PandaModules import WindowProperties
from pandac.PandaModules import loadPrcFileData
import sys

# loadPrcFileData("", "undecorated 1")
loadPrcFileData("","window-title 3D AUV Simulator")

class pandaThread(ShowBase):
    def __init__(self):

        ShowBase.__init__(self)

        base.useDrive()

        wp = WindowProperties.getDefault()
        wp.setOrigin(0,0)
        base.win.requestProperties(wp)

        self.dummyNode = render.attachNewNode("Dummy Node Name")
        self.environ = self.loader.loadModel("models/environment")
        self.environ.reparentTo(self.dummyNode)
        self.environ.setScale(0.25,0.25,0.25)
        self.environ.setPos(-8,42,0)
        base.camLens.setFov(100)
        self.accept("a", self.pressedA)

    def pressedA(self):
        print "a pressed, panda window is in focus"

{% endhighlight %}
<br>
<div class="block">main-test.py : This is where the two threads are created. Note that the Panda3d's thread is not created separately. It is run in the main thread itself.</div>
{% highlight python %}
from pandaThread import pandaThread
from direct.stdpy import threading
from qtThread import qtThread,QtGui, QtCore
import sys

class GuiThread(threading.Thread):
    def __init__(self):
        threading.Thread.__init__(self)
    
    def run(self):
        app = QtGui.QApplication(sys.argv)
        qt = qtThread()
        qt.show()
        print "Running"
        app.exec_()

# GUI thread
gui = GuiThread()
gui.start()

# Panda Thread with main loop
panda = pandaThread()
panda.run()

{% endhighlight %}

Using the code above, I am able to separately operate both the event loops. I'll try doing the same with Panda3d's Tasks if it is possible.
<br><br>
<em>Whats next:</em><br> 
Communication between Panda3d and the Qt interface. This is needed to control the scene in Panda3d using the GUI.<br>

I have set up a Google Code page for this 3d-auv-simulator. I'll update the Wiki of the project with the details of all the code and would post the link here on my blog soon.


[Zetcode]: http://zetcode.com/gui/pyqt4/

