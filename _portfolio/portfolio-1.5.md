
---
title: "Decentralized Gait Generator"
excerpt: "<br/><img src='https://user-images.githubusercontent.com/22688144/124396303-fd0e9400-dd08-11eb-9b4a-ee071a588fc5.png' width='500'>"
collection: portfolio
---

## Goal
The goal of this project was the design and implementation of a simple decentralized gait generator in which each leg has its own independent controller.
Each controller is also only able to utilize the force sensor of the other legs.


## Problem/Complication
Since typical model predictive control approaches do not work when working with multiple independent systems, this required a complete rethinking of walking robot control

A further complication is, that one first has to investigate how a three-legged system can even walk, meaning what kind of gaits are even possible.


## Contribution

I first specified the possible walking gaits of a three-legged system.
Using a self-developed *switching diagram*  it was analyzed which gaits are easiest to decentralize.
These switching diagrams pictured below, show the required hybrid switches for a given gait.

![walking_patterns](https://user-images.githubusercontent.com/22688144/124395132-ac943800-dd02-11eb-8fdd-d6bfdc0593bb.png)

Additional information about the different gaits can be found [here](https://triped-robot.github.io/docs/walking/).

Using the gained intuition a hybrid controller for each leg was developed.
It is made up of three individual controllers, controlling the leg while on the ground, in the air, and lastly choosing when to switch between the two.

![tri_ctr](https://user-images.githubusercontent.com/22688144/124395109-8d95a600-dd02-11eb-9f73-16630dcec764.png)


To judge the stability of the system the controllers model the system as a mixture of three linearized [inverted pendulums](https://en.wikipedia.org/wiki/Inverted_pendulum).
converting this *pendulum mixture model* into [barycentric coordinates](https://en.wikipedia.org/wiki/Barycentric_coordinate_system) yields a formulation in which the available information for each leg can be easily expressed



## Result

The new controller results in stable movement, as can be seen down below.
![decent_walking](https://user-images.githubusercontent.com/22688144/124389188-574a2d80-dce6-11eb-8980-1a6f0fd0f7c6.gif)

Note that the perfectly synchronous moving of the chassis is due to the self-synchronization of the weight redistribution controller which can be seen here:

![decent_synchro](https://user-images.githubusercontent.com/22688144/124389703-98434180-dce8-11eb-8d53-e0efcf5749a6.gif)

Since the controller also makes no assumptions about the position and number of different legs it can also be used to control this *QuadPed*:

![ezgif-4-2e85bb39e4d8](https://user-images.githubusercontent.com/22688144/124395237-40fe9a80-dd03-11eb-9790-f824ed9d2a00.gif)


Ultimately however the system is still rather slow and reacts poorly to outside disturbances.
To mitigate this, the weight redistribution will in the future be replaced with a game-theoretic controller using what I call a *Talker Listener Game*.
This however is still part of my active research.

Additionally, the controller has yet to be tested on the actual TriPed.



