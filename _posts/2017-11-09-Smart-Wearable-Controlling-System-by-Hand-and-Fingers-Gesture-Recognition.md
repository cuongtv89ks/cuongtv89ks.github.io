---
layout: post
title: Smart Wearable Controlling System by Hand and Fingers Gesture Recognition
description: "In recent decades, employees who worked in office suffered from bone diseases and muscle stress, mainly due to improper sitting posture. This study is proposed to develop a novel body equilibrium correction to meet solve such issue."
tags: [healthcareSystem]
categories: [Project]
image:
    feature: smart_wearable_gesture_recognition.jpg
---

In this project, a smart wearable controlling system by hand and fingers gesture recognition as home appliances controller is developed on movements of hand and fingers. The proposed smart wearable system is built with least sensors possible for gesture recognition. Thus, motion sensors are placed on two fingers, namely the thumb, index finger to detect fingers’ motions and another sensor at the back of the palm to measure the hand movement. Total of twenty-two gestures are used in this study by analyzing the movements of fingers. The motion sensors data are transmitted to the mobile device through Bluetooth. An application is built by Qt cross-platform and deployed into mobile device (various platform) to detect and stimulate the effectiveness of the gestures recognition by the embedded n-dimension dynamic time warping (ND-DTW) classifier. The proposed smart wearable system was able to detect the gestures at mean accuracy of approximately 97.55%.

**Video Demo**

<iframe width="560" height="315" src="https://www.youtube.com/embed/xYD6fA76y_g" frameborder="0" allowfullscreen></iframe>

...

<!-- more -->

## System Design

<figure>
	<img src="/images/gesture_project/system_design.png" alt="">
    <figcaption><a title="Figure 1. System design overview."> Figure 1. System design overview..</a></figcaption>
</figure>

Essentially, the system is built up with three modules:
* sensor module
* processing module
* mobile application.

The sensor module consisted of three IMU sensors attached on thumb and index finger, and back of the palm are communicated with the processing module. The processing module remove the internal noises and motion artifact of the received sensors data and further transmitted the filtered data to the mobile application via Bluetooth communication. Gestures are classified by the trained ND-DTW model and the respective pre-defined command in the prototype home controller application is triggered as shown in Figure 1 . The proposed smart wearable controller system is depicted in Figure 2.

<figure>
	<img src="/images/gesture_project/Picture1.png" alt="">
    <figcaption><a title="Figure 2. Proposed smart wearable controller system."> Figure 2. Proposed smart wearable controller system.</a></figcaption>
</figure>

Our proposed system can be applied to various applications as described in Figure 3. Qt cross-platform software is used for developing the prototype mobile application in this study as it is capable to run on various software and hardware platforms with little or no change in the underlying code base such as Android, iOS, and embedded system.

<figure>
	<img src="/images/gesture_project/app_overview.png" alt="">
    <figcaption><a title="Figure 3 Proposed smart wearable controller system that can applied to various applications with Qt cross-platform software"> Figure 3 Proposed smart wearable controller system that can applied to various applications with Qt cross-platform software.</a></figcaption>
</figure>

## Smart Home application
<figure>
	<img src="/images/gesture_project/smart_home_application.png" alt="">
    <figcaption><a title="Figure 9. System overview of smart home application."> Figure 9. System overview of smart home application.</a></figcaption>
</figure>

In order to stimulate the effectively of the proposed smart wearable controller system, a smart home application as depicted in Figure is developed in Android platform with encoded template of  7 hand gestures and 2 finger gestures. Figure 9 shows the system overview of smart home application. The functions recognized by the gestures included displaying of date and time, temperature, humidity, at home. Other controller functions included turning the lamps on/off, controlling the brightness of the lamps, displaying the weather forecast, alarm setting or playing songs. The summary of the gestures:
1. Swipe up - turn on the lamp.
2. Swipe down - turn off the lamp.
3. Swipe left - display content of previous tab in application.
4. Swipe right - display content of next tab in application.
5. W shape - display weather forecast.
6. M shape - play music.
7. S shape - stop music.
8. Rotate left (finger gesture) – increase the brightness of lamp.
9. Rotate right (finger gesture) – decrease the brightness of lamp.
<figure>
	<img src="/images/gesture_project/application_interface.png" alt="">
    <figcaption><a title="Figure 10. Screenshot of the smart home application."> Figure 10. Screenshot of the smart home application.</a></figcaption>
</figure>
