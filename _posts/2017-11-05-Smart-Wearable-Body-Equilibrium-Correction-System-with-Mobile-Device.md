---
layout: post
title: Smart Wearable Body Equilibrium Correction System with Mobile Device
description: "In recent decades, employees who worked in office suffered from bone diseases and muscle stress, mainly due to improper sitting posture. This study is proposed to develop a novel body equilibrium correction to meet solve such issue."
tags: [healthcareSystem]
categories: [Project]
image:
    feature: Equilibrium_Correction_System.jpg
---

In recent decades, employees who worked in office suffered from bone diseases and muscle stress, mainly due to improper sitting posture. This paper is proposed to develop a novel body equilibrium correction to meet solve such issue. The system consists of four modules. A motion sensor module is placed on the center of the user’s chest to measure the sitting orientation. Moreover, an electromyography (EMG) module is located at the both side of the shoulders to measure the user’s muscle tension as incorrect sitting position over a long period of time tends to increase the pain and tense at the shoulders. Thus, it is reliable to serve as references in accordance to the sitting orientation.  Both sensor modules transmit the raw data to a processing module. This module integrates the raw data under a packet and further transmits the data packet to a mobile device. A mobile application is implemented to classify the correctness of sitting position. In case the incorrect position is detected, alert is triggered to user by the vibrator motor and light emitting diodes (LEDs) installed along with the system. The proposed system is able to measure and detect any abnormal sitting positon with average true accuracy of 98% with low-cost implementation.

The proposed system tends to utilize the m-Health technology to evaluate the correctness of the subject’s sitting posture based on the analysis of the muscle tension and body orientation. Features are extracted from the EMGs and motion sensors which are served as inputs to a support vector machine (SVM) classifier. Information of current sitting posture is displayed on the mobile device concurrently and warning is triggered if incorrect posture is detected.

## System Design

<figure>
	<img src="/images/equilibrium_correction_project/system_overview.png" alt="">
    <figcaption><a title="Figure 1. The proposed wearable system design that consists of sensors module, processing module and mobile application module."> Figure 1. The proposed wearable system design that consists of sensors module, processing module and mobile application module.</a></figcaption>
</figure>

The proposed system is divided into four modules: a) an EMG sensors module, b) an Inertial Motion Unit (IMU) sensor module, c) a processing unit module, and lastly d) a mobile application as illustrated in Figure 1. The EMG sensors adopted in this study is the surface dry electronic EMG sensors (sEMGs) which eliminate the usage of gel for measurement. The sEMGs measure the muscle strains of the back of subjects’ shoulders. Studies in [4-5] proved that improper sitting posture for consecutive period of time increases the muscle strains. Thus, the EMGs are applied in this study. Meanwhile, IMU sensor from Adafruit BNO055 [10] computes the orientation of the body in three axes: pitch, roll and yaw. This IMU is integrated with an MEMS accelerometer, gyroscope and magnetometer under a single die, processed using a high-speed ARM Cortex-M0 processor. The installation and placement of the sensors modules are depicted in Figure 2. Sensors data from both sensors modules are gathered and processed by a CortexTM-M0 embedded processor to integrate data under a single packet. A mobile application is developed to receive the data packet through Bluetooth low energy (BLE) wireless communication. Features are extracted from the received data and served as input to a SVM classifier to determine the correctness of the user’s sitting posture.

<figure>
	<img src="/images/equilibrium_correction_project/installation.png" alt="">
    <figcaption><a title="Figure 2. The installation of the proposed system on the body for detecting the normality and correctness of the user body posture."> Figure 2. The installation of the proposed system on the body for detecting the normality and correctness of the user body posture.</a></figcaption>
</figure>

Lastly, Figure 3 illustrates the sample design and prototype of the proposed mobile application to detect body posture in real-time.

<figure>
	<img src="/images/equilibrium_correction_project/application.png" alt="">
    <figcaption><a title="Figure 3. The prototype of the developed mobile application for the proposed body equilibrium correction system."> Figure 3. The prototype of the developed mobile application for the proposed body equilibrium correction system.</a></figcaption>
</figure>

## Methods
<figure>
	<img src="/images/equilibrium_correction_project/methods.png" alt="">
    <figcaption><a title="Figure 4. The flow diagram of the body equilibrium correction system that consists of two modes: calibration mode and normal analysis mode."> Figure 4. The flow diagram of the body equilibrium correction system that consists of two modes: calibration mode and normal analysis mode.</a></figcaption>
</figure>

Figure 4 illustrates flow diagram of software design of the mobile application for the proposed system. There are two modes available in the system: calibration and normal sensing mode. The calibration is required for setting up the initial or default values of the EMG and IMU as each different individual has different muscle strains level by default. The qualitative comments indicated that sitting posture which best matched the natural shape of the spine, and appeared comfortable and/or relaxed without excessive muscle tone and is adopted as the standard or correct posture in this study. As the neutral sitting position varied between subjects during calibration mode, a ±10 degrees of sitting posture is taken into consideration to cope in this study. The linear orientation of the body posture is computed with complimentary filter method accordingly in three axes where the orientation doesn’t take the gravity into computation. Alert is triggered in two ways: via a vibration motor and LEDs indicator on the chest. LEDs in green lights indicated normal or neutral mode whereas red lights depicted incorrect or abnormal modes of sitting posture.
