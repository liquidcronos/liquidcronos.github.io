---
title: "TriPed Robot"
excerpt: "<br/><img src='https://triped-robot.github.io/triped_web_banner.png' width='500'>"
collection: portfolio
---

## Goal
The TriPed is a new robot at the [Aries Lab](https://www.lorenzomasia.com/lab-and-people). It was build according to our specifications at the University of Stuttgart.
The Final Aim of this robot is to study cooperation between machines and humans or machines and machines. 
But before this is possible the robot needs to be actuated. For this purpose, a hardware and software architecture was developed and is currently being implemented.


## Problem/Complication

The system was delivered without any embedded hardware, which meant that suitable embedded controllers had to be chosen, all sensors had to be wired up, and communication interfaces had to be written.

The lower level control of the system is complicated by the complicated mechanical design of the robot, which is further explored [here](https://triped-robot.github.io/docs/kinematics/).
This makes traditional inverse dynamic approaches in real-time next to impossible.



## Contribution
As project lead and main engineer, I am involved in every aspect of the TriPeds development.
This includes everything from PCB design, embedded control, to high-level gait generation.

Initially, I headed a team of 3 research assistants as well as coordinating with our lab engineer.
For this purpose, I developed a system architecture encompassing feedback controllers, software, and embedded hardware.

![decentralised_controller](https://raw.githubusercontent.com/TriPed-Robot/TriPed-Robot.github.io/master/images/full_control_network.png)

More information about the software architecture can be found [here](https://triped-robot.github.io/docs/software_arch/)


I additionally combined the embedded interfaces provided by the rest of the team into simple  PID position controllers for each joint, dealing with the mutual exclusion and other parallel computing-related problems.
The documentation of the resulting package can be found [here](https://triped-robot.github.io/joint_level_control/html/index.html)



To help mitigate the effect of the complicated closed kinematic chain of the legs, I developed a new closing equation that models the influence of a coupling rod as forcing the output lever of the swing motors onto the surface of a sphere

![geometric_closing_equation](https://user-images.githubusercontent.com/22688144/124389180-4dc0c580-dce6-11eb-8566-3a15b9a866e1.png)

Since much of the initial sensor/actuator integration is now finished I continue developing and implementing the higher functionality mostly by myself supported by only a few students whose theses I supervise.


## Result
The project is still ongoing, for more information visit [this site](https://triped-robot.github.io/)

## What I learned
This project has certainly opened my eyes to the intricacies of controller design when dealing with physical system constraints such as BUS communication limitations,  gear backlash, or even communication breakdown-based bugs.

However, the biggest learning experience for me was how to break down a project into work packages so that cross-team dependencies are minimized and how to supervise development to ensure that the objectives of each work package are met.
