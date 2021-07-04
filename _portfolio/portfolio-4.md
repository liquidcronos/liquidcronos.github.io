---
title: "Measurment of the relative groundspeed of a SUAV using monocular camera and sonar sensor"
excerpt: "<br/><img src='https://user-images.githubusercontent.com/22688144/124380804-230f4680-dcbf-11eb-8c95-10bbb67b3d52.png' width='500'>"
collection: portfolio
---


## Goal
An estimate of a SUAVs (Small Unmanned Aerial Vehicle) velocity is paramount for precise maneuvering, however, IMU-based measurements lead to drift, and differentiation of GPS data is not only inaccurate but also numerically unstable.

For this reason, the GOAl of this project was to measure a SUAVs velocity using a monocular camera (that most SUAVS already possess) as well as a sonar sensor.

##Problems/Complications
There are several algorithms capable of estimating the velocity of a camera relative to a static plane.
However, in the real world, there are some complications which are illustrated in the picture below.
![TD4sijIg](https://user-images.githubusercontent.com/22688144/124380565-9912ae00-dcbd-11eb-9575-3cf124d80c5b.jpeg)

Not only is a typically structured environment made up of several planes at different heights (pictured in blue, yellow, orange, and red) it also features multiple moving objects such as cars or pedestrians (also pictured red).
Another much more subtle problem is presented by reflections (pictured in purple).



## Contribution

I not only implemented an optical-flow-based algorithm to estimate the velocity of an SUAV relative to the ground.
The problem above was addressed by developing several measures which compare the movement of features in the images with the current velocity estimate of the SUAV.
An extensive error calculation was performed to quantify the covariance of this new method.

To test the results I build a new Hexacopter using custom 3d printed undercarriage to house additional electronics.

![SUAV](https://raw.githubusercontent.com/liquidcronos/optical-stabilisation/master/pictures/aufbau.png)

## Results

The extensive error calculation showed that optical flow algorithms necessarily produce a constant bias that has yet to be addressed in the literature as of the time of this project.
Its effect can be seen down below, where the estimated velocity is ploted as a function of the error in the feature position.
The true velocity of the SUAV in this case is always [1,1,1] m/s!

![scWcx34w](https://user-images.githubusercontent.com/22688144/124380733-94022e80-dcbe-11eb-9b9d-83eb3e4d95e2.png)



The experimental results show that the algorithm is indeed able to filter out moving objects, as well as ground planes at differing heights, better than current algorithms at the time.

However, these results were only verified inside a simulation and recorded traffic videos.
This is because due to timing constraints no sufficient experimental validation could be conducted (though the first experiments looked promising)

For more information about the project visit [this repo](https://github.com/liquidcronos/optical-stabilisation/wiki)
