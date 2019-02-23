---
layout: post
title: Drone Project Introduction (part 1)
description: "Drones have huge potential for industrial and military applications as well. They can enable access to potentially hazardous locations remotely and remove the need to put personnel in a dangerous situation. Quadcopters can be incredibly agile giving them the ability to navigate within relatively confined spaces and perform complex tasks. "
tags: [Drone]
categories: [Project]
image:
    feature: drone_project.jpg
---

When I was an undergraduate student, I saw my seniors played and tried to make something flied.
At that time, I don't know what it is and how it could fly. And they just said to me that I called something is Drone.
With propellers, motors, MCU, controller, gyro & accelerometer, they said in detailed, of course, at 2nd-year I can not understand
anything about these components or devices. Just something can fly. It has been making me curious and excited. Until now, I have a chance to
build it for my own.

There are a lot of drone projects with open source even open hardware for users. However, this project I hope I can build a quadcopter by my self. Additionally, this project is relative with my master thesis that I am researching about using a ring gesture control device to control drone.

I will update process in this blog.\.

<!-- more -->

## Quadcopter parts

Here is my list I have chosen for building a quadcopter:

<figure>
	<img src="/images/drone_project/drone_components.JPG" alt="">
</figure>

### Frame + Motors + ESC (Kits)

<figure>
	<img src="/images/drone_project/F450-Kit.jpg" alt="">
</figure>


I chose to use is F450 DJI kit with:

* Frame (282g)
* Flame wheel integrated PCB wiring
* 2312E 960KV Motors
* 420E ESC (Electronic Speed Control)
* Propellers 10 x 4.5in ; 8 x 4.5in

### MCU - LPC1768
<figure class="half center">
	<img src="/images/drone_project/lpc1768.jpg" alt="">
</figure>

[LPC1768](http://www.nxp.com/products/microcontrollers-and-processors/arm-processors/lpc-cortex-m-mcus/lpc-cortex-m3/lpc1700-cortex-m3/arm-mbed-lpc1768-board:OM11043) features:

* High performance ARM® Cortex™-M3 Core
* 96MHz, 32KB RAM, 512KB FLASH
* Ethernet, USB Host/Device, 2xSPI, 2xI2C, 3xUART, CAN, 6xPWM, 6xADC, GPIO
* 5V USB or 4.5-9V supply

### IMU - BNO055
<figure class="half center">
	<img src="/images/drone_project/bno055.jpg" alt="">
</figure>

[BNO055](https://learn.adafruit.com/adafruit-bno055-absolute-orientation-sensor/overview) Intelligent 9-Axis Absolute Orientation Sensor:

* integrating a triaxial 14-bit accelerometer
* a triaxial 16-bit gyroscope with a range of ±2000 degrees per second
* Magnetometer typical ±1300μT (x-, y-axis); ±2500μT (z-axis)
* a triaxial geomagnetic sensor and a 32-bit ARM Cortex M0+ microcontroller running Bosch Sensortec sensor fusion software
* digital bidirectional I²C and UART interfaces

### Transmitter and Receiver

<figure class="half center">
	<img src="/images/drone_project/sky.jpg" alt="">
</figure>

FS-i6 Specifications:

* Channels: 6 Channels
* Model Type: Glider/Heli/Airplane
* RF Range: 2.40-2.48GHz
* Bandwidth: 500KHz
* Band: 142
* RF Power: Less Than 20dBm
* Control Range: 500m
* DSC Port: PS2;Output:PPM

### LiPo Battery and LiPo Charger, balancer, and discharger

LiPo Battery (3s, 11.1V, 2200mA)
<figure class="half center">
	<img src="/images/drone_project/lipo-battery.jpg" alt="">
</figure>

LiPo Charger, balancer, and discharger

<figure class="half center">
	<img src="/images/drone_project/charger.jpg" alt="">
</figure>

### FPV (Receiver and Transmitter) and Camera:
Fist Person View - TS840 RC840:

<figure class="half center">
	<img src="/images/drone_project/FPV.jpg" alt="">
</figure>

Camera ELITE QB58 TX CAMERA COMBO:

<figure class="half center">
	<img src="/images/drone_project/camera.jpg" alt="">
</figure>

### Crazyflie

<figure class="half center">
	<img src="/images/drone_project/crazyflie.png" alt="">
</figure>

This one is for my backup in case I can not finish this project on the time. Then I have to change to this platform to be flight controller (MCU, IMU, Controller). [Crazyflie](https://www.bitcraze.io/) is really interesting open source project with Python API for users want to embedded their purposes.

### GPS (optional)
If possible I will make an auto-pilot mode with GPS module for my quadcopter.
