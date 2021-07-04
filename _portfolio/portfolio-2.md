---
title: "RoGaTa Engine"
excerpt: " <br/><img src='https://raw.githubusercontent.com/liquidcronos/liquidcronos.github.io/master/images/rogata_banner.png' width='500'>"
collection: portfolio
---

## Goal
When developing robotics programs inside a simulation, one has the benefit of having perfect information about every aspect of the robot and its environment.

This does not only help with debugging but also with training machine learning agents.

The goal of this project was to bridge this gap between a simulation and real life, by monitoring an area in the real world and providing the same functionality a simulation would provide.




## Problem/Complication
To provide the same functionality as a simulation, real-life objects have to be recognized as  *game objects* which can then be interacted with.

For ease of use, the setup of these objects has to be straightforward and fast.

## Solution
![how_it_works](https://rogata-engine.readthedocs.io/en/latest/_images/setup.png)
To solve this problem, I used a camera above the game area and specified game objects using color.

This allows easy setup of objects by simply painting their border in a specified color.
To be able to reuse the same color and specify more complicated objects with holes, aruco markers can be used to uniquely ID the border of an object. 
The object tracking is done using OpenCV

The whole system is then packaged into a ROS node which offers a [service server](http://wiki.ros.org/Services) which allows other ROS nodes to interact with the game world.

## Result
The resulting Game engine allows  for automatic tracking of moving objects and basic functionality such as:

* get the state of any desired game object 
* calculate the line of sight between robots without on-board cameras 
* check if a robot has entered a specified area 
* simulate laser scanner readings with virtual walls

The full documentation can be found on [https://rogata-engine.readthedocs.io/](https://rogata-engine.readthedocs.io/en/latest/what_is_rogata.html) 

## What I learned 
This was the first project which was designed to be used by people outside of my lab, which is why I concerned myself a lot with auto-generating and hosting documentation as well as streamlining the package installation.
