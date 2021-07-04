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
The lower level control of the system is complicated by the complicated mechanical design of the robot, which is further explored [here](https://triped-robot.github.io/docs/kinematics/).
This makes traditional inverse dynamic approaches in real-time next to impossible.

This is compounded by the fact that, by design, each leg has its own independent controller that needs to cooperate with the rest.

This requires a complete rethinking of traditional walking controllers since the typical model predictive control approaches do not work when working with multiple independent systems.


## Contribution
As project lead and main engineer, I am involved in every aspect of the TriPeds development.
This includes everything from PCB design, embedded control, to high-level gait generation.

Initially, I headed a team of 3 research assistants as well as coordinating with our lab engineer.
For this purpose, I developed a system architecture encompassing feedback controllers, software, and embedded hardware.

To help mitigate the effect of the complicated closed kinematic chain of the legs, I developed a new closing equation that models the influence of a coupling rod as forcing the output lever of the swing motors onto the surface of a sphere

![geometric_closing_equation](https://user-images.githubusercontent.com/22688144/124389180-4dc0c580-dce6-11eb-8566-3a15b9a866e1.png)


I additionally developed a decentralized gait generator in which each leg uses only local sensor information and has no knowledge of the whole system model.

![decent_walking](https://user-images.githubusercontent.com/22688144/124389188-574a2d80-dce6-11eb-8980-1a6f0fd0f7c6.gif)
Note that while this seems similar to the centralized walking agent provided [here](https://triped-robot.github.io/docs/matlab_getting_started/) it truly is decentralized and is self-synchronizing, which can be seen if each controller is started at a different time
![decent_synchro](https://user-images.githubusercontent.com/22688144/124389703-98434180-dce8-11eb-8d53-e0efcf5749a6.gif)


Since much of the initial sensor/actuator integration is finished I continue developing and implementing this higher-level functionality by myself.


## Result
The project is still ongoing, for more information visit [this site](https://triped-robot.github.io/)
