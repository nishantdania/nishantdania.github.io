---
layout: post
title:  "GSOC 2014 - Week 6: Procedurally Generated a Pool and Adding an Underwater Shader"
date:   2014-06-30 10:00:00
categories: gsoc update
---

<div class="block"><span>Procedurally Generating the Pool</span></div>
This was the easy part. I used the same grid that I had created and added texture coords to every vertex. I added UV map coordinates to every vertex. I made the walls of the pool using this technique. Similarly I added a water plane to the pool. This is how it looked so far:

<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/poolWire.png">
</div><span>The wireframe render of the procedurally generated pool. The front two faces can't be seen due to backface culling.</span></div> 

So far, so good.

<div class="block"><span>Adding the Underwater Shader</span></div>

I also wrote an exponential fog shader. This was required to simulate the decrease in visibility in underwater scenes. A few lines of fragment shader gave me the required effect. The other way to simulate underwater effect was to generate particles which can't be rendered at a decent FPS. So I had to stick to this fake fog shader. 

<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/pool1.png">
</div><span>Pool rendered with the underwater fog effect. The texture on the pool's walls is feebly visible through water. This visibility increases as we move closer to the pool. The upper lighter part is a separate water shader.</span></div> 

Going deep down underwater:
<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/pool2.png">
</div><span>The texture on the walls gets clearer as we move closer. The underwater shader at effect.</span></div> 

Can't leave the Panda alone:
<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/pool3.png">
</div><span>The Panda Bath. A blue tint is added to the models that are underwater.</span></div> 

Another reason why I chose not to use particles for an underwater scene was the fact that it would have messed up the selecting objects feature. Since selecting the objects depends upon the rays sent from the camera to the object, the particles in between would have hindered the path. Without those particles, everything is as smooth as required.

<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/pool4.png">
</div><span>Selecting the Panda</span></div> 

There are still a lot of things that I will add to this underwater scene in later days including a reflection shader and an environment map. 
For now, I am happy to see this beta version of the scene come up in time.

<em>What's next:</em><br>
Animating the water texture.<br>
Adding some controls for the pool to the GUI.<br>
