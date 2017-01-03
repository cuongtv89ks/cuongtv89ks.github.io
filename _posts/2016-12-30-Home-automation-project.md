---
layout: post
title: Home automation with Jarvis Assistant project - [Part 1]
description: "Install essential modules on Python"
tags: [tools, platformio]
categories: [Project]
image:
    feature: home_automation_project.JPG
---
For making my apartment more comfortable, without a PhD in computer science linguistics, I used a library for speech recognition and synthesis. Fortunately, Python is the best choice for this purpose. This part is to install essential modules.

It is divided into 3 modules. There are Jarvis's Ears (for recognizing the speech) and Jarvis's Mouth (for speaking what she wants to say ^^!) and API or modules that support for home automation and IoT

## Jarvis's Ears: Speech Recognition

[Speech Recognition](https://pypi.python.org/pypi/SpeechRecognition) is library for performing speech recognition, with support for several engines and APIs, online and offline (CMU Sphinx, Google Speech Recognition, Wit.ai, Microsoft Bing Voice Recognition, Houndify API, IBM Speech To Text).

{% highlight yaml %}
pip install SpeechRecognition
{% endhighlight %}

It also needs [PyAudio](http://people.csail.mit.edu/hubert/pyaudio/#downloads) that is required if you want to use microphone input.

{% highlight yaml %}
pip install pyaudio
{% endhighlight %}

In this project I used Google Speech Recognition (online)
