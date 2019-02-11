---
layout: post
title: Basic knowledge about quadcopter (part 2)
description: "This part will talk about basic knowledge that I accumulated to prepar for building my own quadcopter"
tags: [Drone]
categories: [Project]
image:
    feature: drone_project_2.jpg
---

As [part 1](http://cuongtv.com/project/Drone-Project-Part-1/) introduced about
necessary components to build a quadcopter. Today, I will talk about basic knowledge
that I accumulated on the internet.

## Orientation - Angles
<figure class="center">
	<img src="/images/drone_project/orientation.jpg" alt="">
	<figcaption>Orientation</figcaption>
</figure>


The quadcopter orientation can be defined by three angles: Pitch, Roll, and Yaw.
These angles determine orientation and therefore the direction the quadcopter will take. Basically, changing the pitch will make the quadcopter go forward/backward,
the roll bends to the left/right and the yaw will make it rotate around its vertical axis. And final parameter you need to control attitude of quadcopter is throttle that will spin your all brushless motors up.

I will use these axes as reference:
<figure class="half center">
	<img src="/images/drone_project/reference.gif" alt="">
</figure>

<!-- more -->

## Quadcopter motion

There are 2 kinds of quadcopter configuration: + and X with  clockwise rotation
and  counter-clockwise rotation propeller.

<figure class="center">
	<img src="/images/drone_project/configuration.jpg" alt="">
</figure>

I am using quad X configuration.

Most commercially available quadcopters work in one of two possible modes:

* Aerobatic Mode: This mode allows you to perform spins and flips on the quadcopter.
* Attitude/ Stable Mode: This is the preferred mode for beginners and this is the mode my quadcopter will run in. In this mode data from accelerometer and gyroscope is combined to caculate the quadcopter angle, no spins or flips will
be performed.

Quadcopter motion in different axis:

<figure class="center">
	<img src="/images/drone_project/motion.JPG" alt="">
</figure>


* Throttle control: Quadcopter moves up when you increase speed all motors.
Moving down when you decrease all motors.
* Pitch control: Quadcopter moves forward when you increase 2 front motors and decrease 2 back motors. Revert with the quadcopter moves backward.
* Roll control: Quadcopter bend left when you increase speed 2 right motors and decrease speed 2 left motors. Vice versa for bending right
* Yaw control: Quadcopter rotates left when you increase speed front right motor and back left and rest motors are decreased. Quadcopter rotates right when you speed up front left motor and back right motor and rest motors are at normal speed.

## Quadcopter Flowchart
This is a flowchart for quadcopter programing that I will follow this reference:
<figure class="center">
	<img src="/images/drone_project/flowchart.jpg" alt="">
</figure>

### 1. PWM Decoder Driver:
In order to interpret commands from a standard RC Transmitter/Receiver, it needs
PWM decoder from each channel of transmitter to control speed of 4 motors and flight modes.

### 2. Command Translator:
Depending on the flight mode, the PWM values give by the transmitter are interpreted differently. The command Translator determines which mode the quadcopter is flying in and translates commands accordingly.

### 3. Sensor Fusion:
Actually, in BNO055 there is a 32-bit ARM Cortex M0+ microcontroller running Bosch Sensortec sensor fusion software, that means you don't need to implement a fusion part. However, the problem here is that price of BNO055 is expensive (around 17$) then maybe I will change another one that is cheaper (MPU-6000). For fusion algorithms, there are [Extended Kalman Filter](https://en.wikipedia.org/wiki/Extended_Kalman_filter) (EKF) and [Complementary Filter](http://robottini.altervista.org/tag/complementary-filter)
to implement, for instance. The reasons for implementing fusion algorithm are:

* Accelerometer - Good for long duration (in short time it has many noise)
* Gyroscope - Good for short duration (in long time it will be drift)

Therefore, fusion algorithm will combine accelerometer and gyroscope to solve their weakness.

### 4. Proportional-Integral-Derivative (PID) Stabilization:
PID controller is used to determine the fastest way to make the desired quadcopter's flying become reality from transmitter commands and value of sensor fusion. PID controller is very efficient for control of a system in which an accurate physical model is unknown. Using calculus to determine error slopes and areas, PID compensates for environmental noise and disturbances while overcoming steady state error and oscillations.

### 5. PWM Encoder Driver:
Once everything has been computed, the PWM Encoder takes the control values and generates a pulse width modulated (PWM) output for each motor.
