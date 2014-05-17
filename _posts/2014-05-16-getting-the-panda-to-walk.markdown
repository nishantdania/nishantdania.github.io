---
layout: post
title:  "Getting the Panda to Walk"
date:   2014-05-16 08:10:00
categories: gsoc update
---

<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/panda-1.png">
</div><span>The Panda Walk</span></div>

Panda3D, Ogre3D, Blender Python API...Of all these options to choose from as my 3D rendering engine, I chose Panda3D.<br><br>
Panda3D offered python as the development language and I prefer python over any language like C/C++ where I am always caught up by the pointers and vectors. Blender Python API might be a better option for water simulations. But I'm keeping myself to Panda3D for now. The site of Panda3D says "Just Works, Right out of the Box", and literally I had to just download it and install it on my Ubuntu 13.04 to run the very first programs. If you are on other Linux distros, you should try and find the prebuilt packages on Panda3D site or just google for them before you start compiling the Panda3D source yourself. I tried compiling it on my machine but ran into several errors, mainly with Bullet Physics Engine, GLES2 and ARTollkit. Fortunately I found a prebuilt version for Ubuntu 13.04 on the first google link --> I'm Feeling Lucky.<br><br>
In no time, I was playing with the Panda model which comes along. <br>

<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/panda-2.png">
</div><span>The Panda Ride</span></div>

[Here][here] is the prebuild version of Panda3D 1.8.1 for Ubuntu Raring Ringtail.
[here]: https://docs.google.com/file/d/0B5KBmyjlQESwRWotclpiV1pha2c/edit

<em>Whats next:</em><br> 
A PyQt4 based GUI for the model and environment builder.<br>

<em>The Biggie:</em><br>
Shader to simulate caustic effects in water. I still am trying to find the best way to do this. Maybe I'll add some Godrays too when I'm finished with the caustics.


