---
layout: post
title: Gesture Control Armband
description: "Using EMG and IMU"
tags: [Project]
categories: [Project]
image:
    feature: device.jpg
---

## Introduction

Recently, a significant amount of effort in human-computer interaction (HCI) has been dedicated to the development of user-friendly interfaces employing voice, vision, gesture, and other innovative I/O channels. One of the most challenging approaches in this research field is to link a human's neural signals with computers by exploiting the electrical nature of human nervous system. For the neural linkage with computer, various biomedical signals (biosignals) can be used, which can be acquired from a specialize tissue, organ, or cell system like the nervous system. Examples include electro-encephalogram (EEG), electro-oculogram (EOG) and electromyogram (EMG). Furthermore, it combines with IMU that is the challenging of turning the sensor data from an accelerometer, gyroscope and magnetometer into actual "3D space orientation" in real-time.

EMG and IMU can be used for a various of applications including clinical applications, human-computer interaction and interactive computer gaming etc. Specially, EMG and IMU are combined and they can be used to sense isometric muscular activity which does not translate into movement. This makes it possible to classify subtle motionless gestures and control interfaces without being noticed and without disrupting the surrounding environment. On the other hand, one of the main difficulties in analyzing the EMG signal is due to its noisy characteristics. Compared to other biosignals, EMG contains complicated types of noise that are caused by, for example, inherent equipment noise, electromagnetic radiation, motion artifacts, and the interaction of different tissues. Hence, preprocessing is needed to filter out the unwanted noises in EMG.

In most previous works, multi-channel EMG sensors are used at the same time to detect relevant EMG patterns by a combined signal analysis. In this case, however, users suffer from the inconvenience of carrying many cabled electrodes.

In this project I therefore present an EMG-based controlling interface using a single channel EMG sensor positioned on armband and IMU sensor positioned on forearm. As sample applications I developed the Powerpoint Controller, Game Controller and Camera Controller so that they could be controlled by a user's hand signs and hand movements. The interfacing system first calculates relevant features in the EMG signal of 3 gestures, classifies the hand gestures into the 3 classes and IMU signal of Euler angles.

<iframe width="560" height="315" src="https://www.youtube.com/embed/PC6AopXy3LM" frameborder="0"></iframe>

## Materials
<figure class="half center">
	<img src="/images/EMG_IMU_Project/prototype.jpg" alt="">
	<figcaption>Prototype</figcaption>
</figure>


1. MCU: LilyPad
2. EMG sensor: Myoware
3. IMU sensor: BNO055
4. Bluetooth Module: HC-06
5. Case: 3D printer

<figure class="half center">
	<img src="/images/EMG_IMU_Project/case1.png" alt="">
	<img src="/images/EMG_IMU_Project/case2.png" alt="">
	<figcaption>Case</figcaption>
</figure>

## Methodology

### System structure:
<figure class="half center">
	<img src="/images/EMG_IMU_Project/structure.JPG" alt="">
	<figcaption>System Structure</figcaption>
</figure>

### EMG sensor:

#### 1. Gestures selection
For applications, three gestures are required. These gestures should be equally easy to perform and form patterns in the EMG signal which are as discriminative as possible. Before the start and after the finish of each gesture, the hand should be situated in a posture called the home position, in which hardly any signal amplitude occurs. After testing over 8 different gestures, the three gestures were selected.

The first gesture, Hand Close Gesture
<figure class="half center">
	<img src="/images/EMG_IMU_Project/close.png" alt="">
	<figcaption>Hand Close Gesture</figcaption>
</figure>


The second gesture, Hand Open Gesture
<figure class="half center">
	<img src="/images/EMG_IMU_Project/open.png" alt="">
	<figcaption>Hand Open Gesture</figcaption>
</figure>


The third gesture, Hand Close Gesture
<figure class="half center">
	<img src="/images/EMG_IMU_Project/extension.png" alt="">
	<figcaption>Hand Extension Gesture</figcaption>
</figure>

#### 2. Feature Extraction
Wavelet Transform is a time-frequency analysis method that is successful in the analysis of non-stationary signals including the EMG signals. The main advantage of wavelet transform is that  the selection of dimensions of feature vector is very flexible and it provides approximately same results for various dimensions of feature vector. Therefore, I selected WT to extract feature.

Wavelet analysis was developed from Fourier analysis which was performed in short time period. The size of window can be modified by using the real time frequency analysis. consequently, the signal analysis can be performed at the high signal frequency leading to the same results with the analysis at the low frequency.

To be able to classify a performed gesture some distinctive features have to be found and taken from each matched pattern. Therefore several features were extracted, including common statistical features like Maximum, Minimum, Root Mean Square at cA3, cD3 (level 3).

<figure class="half center">
	<img src="/images/EMG_IMU_Project/wavelet.jpg" alt="">
	<figcaption>A three Level Decomposition of the DWT Coefficients</figcaption>
</figure>

#### 3. Classification

Firstly, I tried to use Support Vector Machine (SVM) classifier algorithm. Although SVM can be used in linear or non-linear ways with the use of a Kernel, SVM needs the a lot of training data to have a accurate results.

Then when I tried to K-nearest Neighbor (KNN) and compare score between KNN and SVM, KNN gave results better than SVM. The reasons for this, KNN is automatically non-linear, it can detect linear or non-linear distribute data and it needs less data points than SVM to have good result.

### IMU sensor:

According BNO055 datasheet, I used Euler data (accelerometer and gyroscope values) to mapping to controlling applications.

## Relative Work
In area using biosignals offers brand new possibilities when compared to the conventional. Thus, with the help of biosignals, it is today possible to detect emotions, make music or develop smart clothes. The famous polygraph is also based on biosignals.

Many biosignal based interfaces are used for controlling and communication. For disabled people especially, they offer the possibility of making their lives easier.

The EMG signal represents the natural electrical activity of the human body, which is used to control the skeletal muscles. Nowadays it is possible to control, in addition to the aforementioned prostheses, robot, mobile phones, drone, ect..., with the help of EMG signals.

## To improve the device
I am trying to make dry electrodes for more convenient and make PCB for customizing the price as well as the size.
