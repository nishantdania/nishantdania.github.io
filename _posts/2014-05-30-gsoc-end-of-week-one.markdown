---
layout: post
title:  "GSOC 2014 - End of Week 1"
date:   2014-05-30 10:00:00
categories: gsoc update
---

<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/commit1-1.png">
</div><span>The Panda Dance.<br>Models were added and positioned using the Pyqt GUI.</span></div>

Since my last post, I have added a lot of functionality to my 3d-auv-simulator. The first thing I did was to organise my code a bit, make it more object oriented. This took some time since till now I was working directly through my main function. I broke the code into several modules namely guiManager, pandaManager, eventManager and inputManager. Here is a brief overview of what all these do:<br>
<div class="block">
<em>guiManager:</em> Controls the layout of the PyQt interface. Also handles the thread running the PyQt GUI.<br>
<em>pandaManager:</em> Controls the Panda3D thread and the scenegraph used by panda3d to hande all the pbjects in the scene.<br>
<em>eventManager:</em> Controls the flow of data from GUI thread to the Panda3D thread. This is the middleware which helps in the communication between the two modules.<br>
<em>inputManager:</em> Controls the keyboard input.<br>
</div>

The next thing I added was a bunch of options to my GUI. This begins the development of what I call the 'environment builder'. The work of this is to provide a GUI to change the scene in Panda3d. I added options like adding new models and changing the position, orientation and size of the models. Placing the models is now a piece of cake using this GUI.

<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/commit1-2.png">
</div><span>Models can now be placed precisely where required in the scene using the GUI.</span></div>

With all these functions in place, I added a few keyboard inputs, one of which is the 'Out Of Body Experience' aka 'oobe'. Using this function, Panda3d allows us to view the scene from any angle using our mouse. This helps to see the environment from different perspectives without handling any additional camera. Below is the screenshot of the 'oobe' mode in use.

<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/commit1-3.png">
</div><span>Top view of the scene viewed using oobe.</span></div>

This marks the end of the first week of the GSOC program. Till now I am happy to see the application turning out well. I plan to add a lot of features in the next week.

As I mentioned in my previous post, I have added all the code till now to the project's google code repo.
The code resides in the simulator folder <a target = "_blanck" href="https://code.google.com/p/3d-auv-simulator/source/browse/">here</a>.

<em>What's next:</em><br>
Add a World Map which shows the objects of interest in the scene.<br>
Add a mouse handler to easily select and modify the objects using the mouse.<br>
Add collision to the models.<br>
Add a save state option.