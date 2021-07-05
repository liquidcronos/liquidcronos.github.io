---
title: "TriPed Simulation"
excerpt: "<br/><img src='https://raw.githubusercontent.com/TriPed-Robot/TriPed-Robot.github.io/master/images/sim_full_parts.png' width='500'>"
collection: portfolio
---

![TriPed_sim](https://raw.githubusercontent.com/TriPed-Robot/TriPed-Robot.github.io/master/images/sim_full_parts.png)

## Goal
To accelerate the development of the [TriPed project](https://triped-robot.github.io/), it was necessary to parallelize the development of the different layers of the control architectures.

This necessitated the development of a  simulation that could not only provide interfaces at different abstraction levels.

Specifically it the ability to not only provide sensor information and allow joint level control but also to directly measure and set the desired foot position.




## Problem/Complication
There were a multitude of problems and considerations when designing the simulation.
One of which being that the full kinematic calculation was rather slow.
This is because each calculation requires the solving of a complicated closure equation (discussed [here](https://triped-robot.github.io/docs/kinematics/)).

While a more streamlined and faster calculation was being workded on that meant that walking experiments where much slower than real time, hampering the development of gait generators.




## Contribution
The simulation was a joint effort between me and Max Goebels who laid the foundation of this simulation in his bachelor thesis which was supervised by me.

Since then then I have fixed mistakes relating to sensor output conventions, and streamlined the simulation, improving its performance by over a factor of 100, while retaining the same accuracy.
This was done by not only optimising the choice of solver but also using relaxation techniquies to circumvent complicated algebraic constraints.
 At the same time suitable initial conditions for the solver where choosen to prevent the system from oscillating between the multiple solutions of the inverse kinematics:
![mult_inv_kin](https://raw.githubusercontent.com/TriPed-Robot/TriPed-Robot.github.io/master/images/triped_2_bar_sec.png)

In addition, I implemented a second simplified simulation, which abstracts the mechanical subsystem requiring the solving of a closure equation using a single joint.
Here once again the solution space had to be constrained to make the simplified simulation congruent with the full simulation.
![redundant](https://user-images.githubusercontent.com/22688144/124382964-52778080-dcca-11eb-9b61-8f7750666b82.png)

Additionally, I restructured the simulation with the help of Max Goebels into a library witch which abrtirary  leg models and configurations could be tested.

## Result
The final Simulation was open sourced including several example scenarions that showcase the capabilities TriPed.
It can be found [here](https://triped-robot.github.io/docs/matlab_getting_started/). 

![triped_orientation](https://raw.githubusercontent.com/TriPed-Robot/TriPed-Robot.github.io/master/images/orienation_example.gif)

## What I learned
On the theoretical side, the project taught me mutch about optimizing computational models to increase performance. 
Such as the importance of choosing the right solver for the right problem as well as methods to circumvent model redundancy and undesirable multiple solutions.

On a practical side, i learned alot about the ins and outs  of what simulink does behind the scenes, and how a Git based workflow can be used with Matlab in general.
