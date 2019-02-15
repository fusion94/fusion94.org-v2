---
layout: post
title: "Arduino + Compass Module 3-Axis HMC5883L"
date: 2012-11-29 13:14
comments: true
categories: [Arduino, Open Source, Compass Module 3-Axis HMC5883L]
---

<div class="info">NOTE: This is a post in a series of blog posts on how to build electronic circuits. If you’re at
all interested then please subscribe to the RSS feed.</div>

### Background

In this blogpost we're going to deal with the [Compass Module 3-Axis HMC5883L](http://www.parallax.com/tabid/768/ProductID/779/Default.aspx) from Parallax and how to
integrate it into an Arduino.

The Compass Module 3-Axis HMC5883L is designed for low-field magnetic sensing with a digital interface.
This compact sensor fits into small projects such as UAVs and robot navigation systems.
<!-- more -->
The sensor converts any magnetic field to a differential voltage output on 3 axes. This voltage shift
is the raw digital output value, which can then be used to calculate headings or sense magnetic fields
coming from different directions. Example code in PBASIC, Spin, and C are provided in the downloads.

__Features:__

* Measures Earth’s magnetic fields
* 3-axis magnetoresistive sensor
* Wide magnetic field range (+/-8 gauss)
* 1 to 2 degree compass heading accuracy
* Precision in-axis sensitivity and linearity
* I2C digital Interface
* Fast 160 Hz maximum output rate
* Designed for use with a large variety of microcontrollers with different voltage requirements

__Application Notes:__

* Auto and personal navigation
* UAV systems
* Robotic navigation
* Location-based services (LBS)

__Key Specifications:__

* Power Requirements: 2.7 to 6.5 VDC
* Communication Interface: I2C (up to 400 kHz)
* Operating temperature: -22 to +185 °F (-30 to +85 °C)
* Dimensions: 0.725 x 0.650 in (1.8 x 1.7 cm)

### What It Can Do

* Measures the earth’s magnetic field in three axes, with a 1–2 degree accuracy
* Provides individual readings for each axis, which may be used separately or together for 3D calculations
* Measures raw strength (gauss) of a nearby magnetic source

The 3-Axis Compass module measures magnetic fields in three directions – or axes, labeled X, Y, and Z.
In its most simple form, the module can be used as a basic compass to find earth’s magnetic north.

The compass module can also sense the relative strength of a nearby magnetic source, such as those
caused by magnets or electric fields. As the sensor detects magnetism in three dimensions, it can
determine relative distance and direction to these sources.

![](/images/blog/compass/Compass-2.png)

Compasses are commonly uses with accelerometers, where the data from both the compass and
accelerometer can provide extended information.

One application of adding an accelerometer is to compensate for any tilt of the compass. As with
most any compass, the reading is affected if the compass is not level.

__Hardware Required__

* Arduino Board
* (1) Compass Module 3-Axis HMC5883L
* breadboard
* hook-up wire

__Circuit__

![](/images/blog/compass/Compass-3.png)

Connect the 5V and GND pins of the compass to the power and ground ports on the Arduino. Connect
analog pin 4 of the Arduino to the SDA (Data) out pin of the compass, and analog pin 5 to the SCL
(Clock) out pin.

The picture below shows you essentially how the circuit should be laid out.

![](/images/blog/compass/Compass-6_0.png)

Don’t forget that your Arduino must be connected to your computer in order for it to transmit serial
data and don’t forget to set the Baud Rate of your serial connection to be 9600.

__The Code__

```
/*
   Compass Module 3-Axis HMC5883L

   Read the Compass Module 3-Axis HMC5883L and prints them over the serial connection to the computer.

   The circuit:
    * SDA (Data) output of compass to analog pin 4
    * SCL (Clock) output of compass to analog pin 5
    * +V of accelerometer to +5V
    * GND of accelerometer to ground

   created 29 Nov 2012
   by Tony Guntharp

 */
#include

#define Addr 0x1E               // 7-bit address of HMC5883 compass

void setup() {
  Serial.begin(9600);
  delay(100);                   // Power up delay
  Wire.begin();

  // Set operating mode to continuous
  Wire.beginTransmission(Addr);
  Wire.write(byte(0x02));
  Wire.write(byte(0x00));
  Wire.endTransmission();
}

void loop() {
  int x, y, z;

  // Initiate communications with compass
  Wire.beginTransmission(Addr);
  Wire.write(byte(0x03));       // Send request to X MSB register
  Wire.endTransmission();

  Wire.requestFrom(Addr, 6);    // Request 6 bytes; 2 bytes per axis
  if(Wire.available() <=6) {    // If 6 bytes available
    x = Wire.read() << 8 | Wire.read();
    z = Wire.read() << 8 | Wire.read();
    y = Wire.read() << 8 | Wire.read();
  }

  // Print raw values
  Serial.print("X=");
  Serial.print(x);
  Serial.print(", Y=");
  Serial.print(y);
  Serial.print(", Z=");
  Serial.println(z);

  delay(500);
}
```

At the end of uploading and running the code listed above you will start to see some serial output
like in the image below.

![](/images/blog/compass/compass_results.png)

Here’s a picture of the actual circuit built.

![](/images/blog/compass/compass_circuit.png)

__Source Code__

[Github](https://github.com/fusion94/HMC5883L_Arduino)

In a follow up blog post I’ll discuss how you can use both the Compass Module 3-Axis HMC5883L in
conjunction with the Memsic 2125 Dual-axis Accelerometer to compensate for any tilt of the compass.
