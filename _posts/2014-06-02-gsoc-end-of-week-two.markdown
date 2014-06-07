---
layout: post
title:  "GSOC 2014 - Week 2: Saving and Loading Scenes"
date:   2014-06-02 10:00:00
categories: gsoc update
---

An option common to almost all the softwares is the Save and Load file option. Though this was a bit lower in the priority list of my work, but after getting bored of the tedious work of creating scenes to test my code everytime I made a change to it, I decided to add this option. To save a file, I decided to go with creating a .xml file which contained all the variables of the states of the models like position and scale.<br>
The reason I chose an xml format was because the heirarchy of objects can be saved in a proper manner in an xml file.<br>
The Load Scene option is able to read and parse these saved xml files, now allowing me to sit back and letting this load option to create a test scene for me. 
<div class="block"><div class="big clearfix"><img src="{{ site.url }}/assets/saveScene1.png">
</div><span>Save Scene Option</span></div>

<em>What's next:</em><br>
The World Map<br>
