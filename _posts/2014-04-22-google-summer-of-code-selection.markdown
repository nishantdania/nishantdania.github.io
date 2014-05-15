---
layout: post
title:  "Google Summer of Code 2014 Selection!"
date:   2014-04-22 00:23:05
categories: gsoc update
---

<div class="img clearfix"><img src="{{ site.url }}/assets/gsoc-logo.jpg">
</div>

One long month of wait, and finally the result is out. My proposal got selected for GSOC 2014 under BumbleBee AUV.

<div class="block"><span>What does all this mean?</span><br>
	Google Summer of Code is a program in which Google invites open source organisations to get their code written by people interested in open source(like me). And Google pays for this.
</div>

The people at BBAUV, my organisation, have built an underwater autonomous vehicle. Now everytime they change their code running behind the AUV, they have to put the AUV in water and run the tests. To avoid this, they decided to make a simulator for underwater robots. I sent my proposal of how I wanted the simulator to be and how I would like to achieve the required result. 

<div class="block"><span>Here's a brief version of my proposal</span><br><br>
	<span>Organization:</span><br>BumbleBee Autonomous Underwater Vehicle (BBAUV)<br><br>
<span>Short description:</span><br> In essence, my project aims at building a GUI based simulator that would simulate underwater conditions with obstacles and enable navigation of the robot with motor controls, camera input and sensor input. It would help the user to build models, setup an environment, connect to ROS nodes, plan missions and would also provide presets for all the basic conditions that an AUV can face underwater. The whole software would be fully documented unlike the current simulators.<br><br>

<span>Proposed Features:</span><br>

The simulator would be divided into following modules:<br><br>

Model Builder and Viewer: This would allow the user to create URDF files using a GUI interface. It would allow the user to add external model parts in the form of DAE/OSG files and view the model in a Model Viewer window.<br>
Environment Builder and Viewer: This allows the user to specify the position of the models in by varying the parameters in a GUI interface. The user would also be able to view the environment by going to a View Environment Window which would allow him to see the environment visually as he creates it.<br>
Presets Manager: The user would be able to load from a range of different environments, models, some basic OpenCV algorithms and sensor implementations which he can start using directly in the simulator. It would also allow the user to create custom presets and save them for future use.<br>
Mission Planner and Trajectory Maker: This interface would allow the user to place various predefined or user defined obstacle in an environment. The interface would then find the optimized algorithm to solve the path which the AUV would follow in the simulation.<br>
Parameter Window: This window would contain an organized list of all the environment parameters (like wind speed and water depth), dynamics parameters (collision and inertia of the AUV), sensors parameters (like the range of a SONAR sensor) and control parameters (like PID control parameters).<br>
Camera Navigator: This allows the user to control the camera of the simulator. It would allow him to specify various objects to which the camera would be attached to. It would also give him a better control over the environment camera by providing views from different directions (top/bottom/right/left).<br><br>

<span>Optional Features:</span><br>

Control Graphs Window: This would allow the user to view the graphs of the motion related to the control algorithm of the AUV.<br>
ROS Nodes Manager: It shows all the topics being published and subscribed and the data being exchanged through these topics. This would allow the simulator to integrate with the ROS features like view topics command, thus reducing the need to use command line.<br>
</div>

Now that the proposal has been selected, I am dying to start working on the biggest project that I have ever taken up till now. I hope to complete this as soon as I can. All the code related to the project would be uploaded on my [Github repository][Github-rp]. <br>Feel free to contribute to this project.

[Github-rp]: https://www.github.com/nishantdania


