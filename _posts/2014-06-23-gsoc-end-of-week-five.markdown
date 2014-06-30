---
layout: post
title:  "GSOC 2014 - Week 5: Shaders in Panda3d"
date:   2014-06-23 10:00:00
categories: gsoc update
---

This is just a small update on the work done in the past week.

As asked by my mentor Lynnette Ng, I have added the option to place the objects relative to each other rather than relative to the environment's frame. 

Apart from adding this option to the simulator, I tried adding the <a href="https://github.com/nishantdania/OpenGL-Grid" target = "_blanck">Grid</a> that I created earlier to Panda3d. The only difference that I made in the code was using Nvidia's Cg shader language instead of GLSL since Panda3d supports Cg more than GLSL. I also added a fake volumetric fog to simulate underwater scene. Though Panda3d's default fog feature is very comfortable to use, it is not that customizable. I am planning to remove this default fog soon and add a custom Cg shader in its place.

I also read a lot about UV mapping using shaders. Turns out it is one of the most used features in Cg shaders. TEXCOORD is the best way to do what gl_FragCoord does in GLSL. I am still experimenting my way through shaders and the advantages it offers over the fixed pipeline structure.

Still a long way to go ! 

<em>What's next:</em><br>
Procedurally generate a pool and add water to it.
