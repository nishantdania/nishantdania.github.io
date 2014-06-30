---
layout: post
title:  "GSOC 2014 - Week 4: OpenGL Grid Using Shaders"
date:   2014-06-15 10:00:00
categories: gsoc update
---

Finally I have started creating the underwater effect for my project. Rendering water is one of the most challenging aspects of the simulator I am working on. The reason being the fact that this is my first time creating something with shaders. Before creating something in Panda3d, I decided to work directly in OpenGL and GLSL shader language to know a bit more about how the graphics pipeline works.<br>

Jerry Tessendorf, the name that the whole internet shouts out when it comes to water simulation, particularly ocean water simulation. Tessendorf's 2005 paper titled "Simulating Ocean Water" gives a detailed analysis of
the behaviour of water waves. Though I wanted to work on using his technique, I had to restrict myself to simpler approaches like heightfiled water simulation for my simulator since Tessendorf's method requires a lot of computational power and realtime results are sometimes not achieved.<br>

Coming back to the track, the first thing I needed for my water was a simple plane made up of a grid of triangles. I wrote two simple loops in OpenGL to create such a plane and passed the vertices to the vertex shader.
Below is the screenshot of the grid that I created. 

<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/grid1.png">
</div><span>The plane is made up of 64*64 vertices rendered using gl_Triangles.</span></div> 

To reduce the amount of vertices, I later used indexed vertices approach for creating the grid. 
I then applied some simple trigonometric equations to the vertex shader for animating the grid. This is what I would be doing later for creating the water plane. Also, the fragment shader changes the grid's color while its animating. Below is a screenshot of the animation.

<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/grid2.png">
</div><span>The vertex shader in action.</span></div></div>

After having spent an entire week learning about shaders, I finally feel that shaders are a bit less intimidating than I had thought. Still there is a lot to learn before I can have even the simplest water rendered on my screen. 

I have added this project's code to my <a href="https://github.com/nishantdania/OpenGL-Grid" target="_blanck">Github repo here</a>. 

<em>What's next:</em><br>
Add an option to position objects relative to other objects.<br>
Creating a pool to contain the water and moving on to Panda3d.
