---
layout: post
title: PlatformIO is a solution
description: "An open source ecosystem for IoT development. This is cross platform code builder and library manager with platforms like Arduino or MBED support..."
tags: [tools, platformio]
categories: [Project]
image:
    feature: platformio.JPG
---

I have had to work on quite lots of embedded platforms like Arduino, mbed, PIC32, Raspberry Pi... and develop them on Window as well as Linux. It is really inconvenient to me because each platform has each IDE to develop, and for some platforms its IDE is quite poor comparing with Text Editor (Atom, Vim, Sublime, Emacs) and I have to change environments many times.
Fortunately, I found this one as the best solution at this time, [PlatformIO](http://platformio.org/). It is an open source ecosystem for "IoT" development and cross platform code builder and library manager with a lot of development platforms and frameworks ([check here](http://platformio.org/platforms/atmelavr)):

<figure class="half center">
	<img src="/images/platformio/2.JPG" alt="">
</figure>

* Colourful command-line output
* IDE Integration with Arduino, Atom, CLion, Eclipse, Emacs, Energia, Qt Creator, Sublime, Vim, even Visual Studio
* Cloud compiling and Continous Integration with AppVeyor, Circle CI, Drone, Shipable
* Build-in Serial Port Monitor and configurable build -flags/-options
* Automatic firmware uploading
* Pre-built toolchains, frameworks for the popular Hardware Platforms

<figure class="half center">
	<img src="/images/platformio/3.JPG" alt="">
</figure>

* Friendly Comaand-Line Interface
* Modern Web 2.0 Library Search
* Open Source Library Registry API
* Library dependency management
* Automatic library updating

<figure>
	<img src="/images/platformio/4.JPG" alt="">
</figure>

## How to build PlatformIO based project

###  Arduino Uno

#### 1. Make a new project directory and initialize an empty project
{% highlight yaml %}
mkdir platformio/test_uno
cd platformio/test_uno
platformio init
{% endhighlight %}

This will create:

* /src
* /lib
* platformio.ini


#### 2. Configure platformio.ini with boards
{% highlight yaml %}
platformio init --board=uno
{% endhighlight %}

platformio.ini looks like this:
{% highlight yaml %}
; Project Configuration File
; Docs: http://docs.platformio.org/en/latest/projectconf.html

[env:uno]
platform = atmelavr
framework = arduino
board = uno

[env:nodemcu]
platform = espressif
framework = arduino
board = nodemcu
build_flags = -D LED_BUILTIN=BUILTIN_LED

[env:teensy31]
platform = teensy
framework = arduino
board = teensy31

[env:lpmsp430g2553]
platform = timsp430
framework = energia
board = lpmsp430g2553
build_flags = -D LED_BUILTIN=RED_LED
{% endhighlight %}

#### 3. Arduino code in src/main.cpp

{% highlight c %}
#include "Arduino.h"

void setup()
{
  // initialize LED digital pin as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop()
{
  // turn the LED on (HIGH is the voltage level)
  digitalWrite(LED_BUILTIN, HIGH);
  // wait for a second
  delay(1000);
  // turn the LED off by making the voltage LOW
  digitalWrite(LED_BUILTIN, LOW);
   // wait for a second
  delay(1000);
}
{% endhighlight %}

#### 4. Upload to arduino
{% highlight yaml %}
platformio run --target upload
{% endhighlight %}


### LPC1768 development board

Basically, It is similar with Arduino. There are different when you initialize platformio:

{% highlight yaml %}
platformio init --board=lpc1768
{% endhighlight %}

Example code for LPC1768:

{% highlight c %}
#include "mbed.h"

Serial pc(USBTX, USBRX); // tx, rx
Serial device(p9, p10);  // tx, rx

int main() {
    while(1) {
        if(pc.readable()) {
            device.putc(pc.getc());
        }
        if(device.readable()) {
            pc.putc(device.getc());
        }
    }
}
{% endhighlight %}

Maybe you will get error at the first line because the library of mbed is not in library manager then you have to add it ([guide here](http://docs.platformio.org/en/stable/userguide/lib/index.html#cmd-lib)).

You can get mbed library [here](https://developer.mbed.org/users/mbed_official/code/mbed/).
