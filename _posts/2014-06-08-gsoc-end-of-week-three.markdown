---
layout: post
title:  "GSOC 2014 - Week 3: The World Map"
date:   2014-06-08 10:00:00
categories: gsoc update
---

Week 3 ends giving life to the World Map.

<div class="block"><span>What is the World Map ?</span>
<br>
The World Map would allow the user to edit and view the whole scene from a bird's eye view. This was achieved by rendering the top view of the scene in a small display region around the corner of the window. 
</div>
<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/wm1.png">
</div><span>The small area in the right hand corner defines the world map region. The green box around the panda suggests that it is selected.</span></div>

One of the main challenges that I faced in reaching this milestone was the selection of objects using the mouse. Also differentiating the clicks done in the main window from those done in the world map area was a time consuming task. I followed the most popular technique of creating virtual rays from the camera to the mouse pointer and finding its collisions with the objects.

Creating the green box around the selected object was a challenge too. Thankfully, Panda3d gave an option to compute the bounds of the models. Using this option and tweaking with the SceneGraph in Panda3d, I was finally able to put a box outside the selected object.

I also added keyboard controls for the camera attached to the world map. This allow to change the view of the world map without affecting the main scene.

I'm glad that the first version of the World Map and the mouse handler are finally complete. Now I will think of some additional features to add to the World Map and make the simulator more easy to use(user experience is all that matters). 

<em>What's next:</em><br>
Interfacing ROS with the simulator.

