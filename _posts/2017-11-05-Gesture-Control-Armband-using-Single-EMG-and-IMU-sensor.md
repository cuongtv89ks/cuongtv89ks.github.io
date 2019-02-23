---
layout: post
title: Gesture Control Armband using Single EMG and IMU sensor
description: "This project is focused to develop a wearable device system to recognize hand gestures in real-time that utilizes a single surface electromyogram (EMG) sensor positioned on the forearm and an inertial measurement unit (IMU - accelerometer and gyroscope) to realize user-friendly interation between human and computers."
tags: [HCI]
categories: [Project]
image:
    feature: EMG_and_IMU.jpg
---
This project is focused to develop a wearable device system to recognize hand gestures in real-time that utilizes a single surface electromyogram (EMG) sensor positioned on the forearm and an inertial measurement unit (IMU - accelerometer and gyroscope) to realize user-friendly interaction between human and computers. We analyze the EMG signals coming from seven different subjects using a novel integration of wavelet and K-nearest Neighbor (KNN). The efficiency of wavelet transform in surface EMG feature extraction is investigated from 3 levels of wavelet decomposition to common statistical features such as mean, root square mean, and standard deviation. KNN classifier is used to recognize 3 gestures (hand close, hand open and hand extension). IMU streams are utilized as decision fusion method to recognize the hand movements. Overall, results revealed the true accuracy of 3 gestures detection is greater than 95% in average by using the KNN classifier. The performance of the interfacing system was evaluated by camera controller application that is controlled by the hand gestures and hand movements. The proposed method facilitates intelligent and natural control based on gesture interaction.

**Video Demo**


{::nomarkdown}
<iframe width="560" height="315" src="https://www.youtube.com/embed/PC6AopXy3LM" frameborder="0" allowfullscreen></iframe>
{:/nomarkdown}

...

<!-- more -->

## System Design and implementation
Here, the system overview design and experiments setup are being discussed (Figure 1). The proposed system is divided into two parts that are (1) hand gesture and movement acquisition module on the wearable armband, and (2) gestures analysis module by end terminal application.
<figure>
	<img src="/images/EMG_IMU_Project/fig1.png" alt="">
    <figcaption><a title="Figure 1. System design"> Figure 1. System design.</a></figcaption>
</figure>

The EMG signal of the performing arm muscles is obtained by an EMG sensor (myoware muscle mensor [13]), that is attached on a forearm to capture the gestures of the hand. Myoware muscle sensor is a new wearable design that attached the biomedical sensor pads directly to the board itself which getting rid of those pesky cables with single-supply voltage (+2.9V to +5.7V, two outputs (EMG Envelope, Raw EMG)), polarity protected power pins. Moreover, an absolute 9 degree-of-freedom inertial motion unit (IMU) orientation sensor [14] is attached in the wearable armband at the back of the wearable MCU platform. The IMU is an intelligent 9-axis absolute orientation sensor consists of an accelerometer, a gyroscope, and a magnetometer sensor (10-pins) operated at 3.3V, footprint of 3.8 x 5.2 mm 2, height of 11.3 mm 2 and integrated under a high speed ARM Cortex-M0 based processor to process all the data. These sensors are connected to an Arduino-compatible, Adafruit FLORA wearable electronic platform micro-controller (MCU) [15], powered by a small size 3.7V ion Lithium polymer battery. A HC-06 Bluetooth module [16] transmits the received signals to the end terminal application as described in Figure 2(b). Once the signals are received by the end terminal application, features are extracted from the respective sensors reading, and serve as input parameters to a pattern classifier for hand gestures evaluation.

<figure>
	<img src="/images/EMG_IMU_Project/wearable_system.jpg" alt="">
    <figcaption><a title="Figure 2. (a) the proposed wearable arm, consisting of EMG sensor, an inertial motion unit, a wearable electronic platform, a Bluetooth and a lithium polymer battery operated at 3.3V and (b) the camera controller application running on a desktop computer, controlled by the wearable armband attached on the right hand."> Figure 2. (a) the proposed wearable arm, consisting of EMG sensor, an inertial motion unit, a wearable electronic platform, a Bluetooth and a lithium polymer battery operated at 3.3V and (b) the camera controller application running on a desktop computer, controlled by the wearable armband attached on the right hand.</a></figcaption>
</figure>
