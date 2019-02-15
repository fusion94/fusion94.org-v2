---
layout: post
title: "Arduino + Memsic 2125 Dual-axis Accelerometer"
date: 2012-11-28 15:50
comments: true
categories: [Arduino, Open Source, Memsic 2125 Dual-axis Accelerometer]
---

<div class="info">NOTE: This is a post in a series of blog posts on how to build electronic circuits. If you’re at
all interested then please subscribe to the RSS feed.</div>

### Background

In this blogpost we're going to deal with the [Memsic 2125 Dual-axis Accelerometer](http://learn.parallax.com/KickStart/28017) from Parallax and how to integrate
it into an Arduino.

The Memsic 2125 is a low cost, dual-axis thermal accelerometer capable of measuring tilt, acceleration, rotation,
and vibration with a range of ±3 g. For integration into existing applications, the Memsic 2125 is electrically
compatible with other popular accelerometers.
<!-- more -->
Memsic provides the 2125 in a surface-mount format. Parallax mounts the circuit on a through-hole providing all
I/O connections so it can easily be inserted on a breadboard or through-hole prototype area.

__Features:__

* Measures ±3 g on each axis
* Simple pulse output of g-force for each axis
* Convenient 6-pin 0.1" spacing DIP module
* Analog output fo temperature (Tout pin)
* Low current at 3.3 or 5 V operation: less than 4 mA at 5 VDC

__Sample Applications:__

* Dual-axis tilt sensing for autonomous robotics applications
* Single-axis rotational position sensing
* Movement/Lack-of-movement sensing for alarm systems
* R/C hobby projects such as autopilots

__Key Specifications:__

* Power requirements: +3.3 to +5 VDC
* Communication: TTL/CMOS compatible 100 Hz PWM output signal with duty cycle proportional to acceleration
* Dimensions: 0.42 x 0.42 x 0.45 in (10.7 x 10.7 x 11.8 mm)
* Operating temp range: 32 to +158 °F (0 to +70 °C)

### What It Can Do

* Measures tilt in two axes: forward and back, or side to side
* Registers sudden changes in motion
* Detects even small amounts of vibration and motion

The Memsic 2125 Dual-axis Accelerometer is sensitive to the gravitational pull of the earth, allowing it to measure
tilt, vibration, motion, and acceleration. The sensor provides independent outputs for two axes, labeled X and Y:

* The X axis measures tilt or acceleration forward and back (direction of arrow)
* The Y axis measures tilt or acceleration side to side

![](/images/blog/memsic2125/Memsic2125-2.png)

The Memsic 2125 module registers the constant pull of earth’s gravity. This is specified as 1g (g for gravity). For
the Memsic sensor, the value of 1g is always some positive number, and is about half way between the highest and
lowest readings the module is capable of reporting.

As a tilt sensor, the Memsic 2125 detects when the module is not level. The output of the sensor indicates the amount
of inclination. As a acceleration or vibration sensor, the sensor measures the g-forces acting on it. The greater the
g-force, the higher the acceleration or vibration.

The X and Y axis output of the Memsic 2125 is a pulse that has a period of (that is, it repeats) 100 times a second
(100 Hz). The width of the pulse represents the instantaneous g-force. By measuring the width of the pulse, you can
derive – with high accuracy – the g-force of either axis.

![](/images/blog/memsic2125/Memsic2125-3.png)

__Hardware Required__

* Arduino Board
* (1) Memsic 2125 Accelerometer
* breadboard
* hook-up wire

__Circuit__

![](/images/blog/memsic2125/Mx2125_PINOUT.png)

Use the small triangle on the Memsic to properly orient the sensor on your breadboard. Connect the 5V and GND pins
of the Memsic 2125 to the power and ground ports on the Arduino. Connect digital pin 2 of the Arduino to the X out
pin of the accelerometer, and digital pin 3 to the Y out pin.

The picture below shows you essentially how the circuit should be laid out.

![](/images/blog/memsic2125/Memsic2125-7.png)

Don't forget that your Arduino must be connected to your computer in order for it to transmit serial data and
don't forget to set the Baud Rate of your serial connection to be 9600.

__The Code__

```
   Memsic2125

   Read the Memsic 2125 two-axis accelerometer and prints them over the serial connection to the
   computer.

   The circuit:
    * X output of accelerometer to digital pin 2
    * Y output of accelerometer to digital pin 3
    * +V of accelerometer to +5V
    * GND of accelerometer to ground

    * Copyright (c) 2012 by Tony Guntharp. All Rights Reserved.
    * Licensed under the terms of the Apache Public License
    * Please see the LICENSE included with this distribution for details.

 */

 // these constants won't change:
const int xPin = 2;     // X output of the accelerometer
const int yPin = 3;     // Y output of the accelerometer

void setup() {
  // initialize serial communications:
  Serial.begin(9600);
  // initialize the pins connected to the accelerometer
  // as inputs:
  pinMode(xPin, INPUT);
  pinMode(yPin, INPUT);
}

void loop() {
  // variables to read the pulse widths:
  int pulseX, pulseY;
  // variables to contain the resulting accelerations
  int accelerationX, accelerationY;

  // read pulse from x- and y-axes:
  pulseX = pulseIn(xPin,HIGH);  
  pulseY = pulseIn(yPin,HIGH);

  // convert the pulse width into acceleration
  // accelerationX and accelerationY are in milli-g's:
  // earth's gravity is 1000 milli-g's, or 1g.
  accelerationX = ((pulseX / 10) - 500) * 8;
  accelerationY = ((pulseY / 10) - 500) * 8;

  // print the acceleration
  Serial.print(accelerationX);
  // print a tab character:
  Serial.print("\t");
  Serial.print(accelerationY);
  Serial.println();

  delay(100);
}
```

At the end of uploading and running the code listed above you will start to see some serial output like in the
image below.

![](/images/blog/memsic2125/memsic2125_results.png)

Here's a picture of the actual circuit built.

![](/images/blog/memsic2125/layout.png)

In a follow up blog post I'll discuss how by using additional math, you can use the values provided by the
accelerometer to convert to actual g-forces or degrees of tilt.

__Source Code__

[Github](https://github.com/fusion94/Memsic2125_Arduino)
