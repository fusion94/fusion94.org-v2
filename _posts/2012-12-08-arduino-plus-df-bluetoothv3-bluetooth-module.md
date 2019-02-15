---
layout: post
title: "Arduino + DF-BluetoothV3 Bluetooth module"
date: 2012-12-08 13:27
comments: true
categories: [Arduino, DF-BluetoothV3 Bluetooth module, Open Source]
---

<div class="info">NOTE: This blog post is part of a series of blog posts on how to build electronic circuits. If you’re
at all interested then please subscribe to the RSS feed.</div>

### Background

In this blog post we're going to deal with the [DF-BluetoothV3 Bluetooth module](http://www.dfrobot.com/index.php?route=product/product&filter_name=TEL0026&product_id=360#.UMODVpPjlnM)
from DFRobot and how to integrate it into an Arduino.

This DF-Bluetooth module offers an affordable way to let your microcontroller talk to your Bluetooth
devices such as Bluetooth mobile phones, laptop, and Bluetooth adapter. The Bluetooth module provides
TTL level UART interface which is supported by almost every microcontroller in the market.
<!-- more -->
It is also designed to be compatible with most popular Arduino controller. Simply plug into Arduino
IO Expansion Shield, and the Bluetooth Arduino is ready to use.

__Key Specfications__

* Chips: CSR BC417143
* Bluetooth Protocol: Bluetooth Specification v2.0 +EDR
* Working Frequency: 2.4-2.48GHz unlicensed ISM Band
* Modulation Mode: GFSK (Gaussian Frequency Shift Keying)
* Power: ≤4dBm, Class 2
* Transmission Distance: 20-30 in free space
* Sensitivity: ≤-84 dBm at 0.1% BER
* Transmission rate: Asynchronous: 2.1 Mbps (Max)/160 kbps; Synchronous: 1Mbps/1Mbps
* Security: Authentication and encryption
* Support profiles: Bluetooth serial port
* LED indicator: LINK
* Power Supply: +3.5V-+8V DC/50 mA
* Working Temperature: -20°C-+55°C
* Dimension: 43x19.3x11mm
* Default serial setting: 9600/N/8/1
* Default Pairing Code: 1234

### What It Can Do

DF-BluetoothV3 Bluetooth module uses a unique double-board design, it is beautiful and aims to
prevent electrostatic damage to the module. It is designed to have 2 DC power input, wide voltage
supply (3.5V ~ 8V) and 3.3V power supply, suitable for various applications. STATE LINK is indicated
by a clear and bright LED which is used to display module status and connection status (STATE state:
Search state (high 104ms 342ms 2.9Hz cycle flicker) connection status (high 104ms period 2s 0.5Hz
flashing), LINK state: paired ). It has build-in on-board antenna which provides high quality signals.

![](/images/blog/bluetooth/bt1.png)

DIP switch is designed to set the module status, LED Off to turn off the LINK light to enter power
saving mode, AT Mode allows the module to enter AT command mode, AT commands can modify the baud rate
and the master and slave mode.

* This module can also be used as a pair which provides a transparent serial data communication.
* This module has been tested and compatible with most Bluetooth adapter in the market (Bluetooth dongle, including laptops and mobile phones).
* This module has been tested and compatible with Android Phones.

__Hardware Required__

There are two different hardware setups that I've tested this on.

__Setup One__

* DF-BluetoothV3 Bluetooth module
* DF-IO Expansion Shield for Arduino (v5)
* Arduino Uno

![](/images/blog/bluetooth/setup_one.png)

__Setup Two__

* DF-BluetoothV3 Bluetooth module
* Romeo-All in one Controller (Arduino Compatible Atmega 328) (V1.0)

![](/images/blog/bluetooth/setup_two.png)

<div class="warning">Please note that when you use the Romeo-All in one Controller (Arduino Compatible Atmega 328) (V1.0)
then you're going to have to install the <a href="http://www.ftdichip.com/Drivers/VCP.htm">FTDI Drivers</a>.</div>

### Additional Setup Notes

<div class="info">When the DF-Bluetooth is used on Arduino, please make sure you disconnect the DF-Bluetooth module
before uploading any code to your Arduino. It won’t burn your Arduino, but the uploading will fail as
the DF-Bluetooth module occupying the TX/RX pins.</div>

The next step is that making pairs between the computer and the Bluetooth module. By doing this, from
the computer  communicating with a Bluetooth module is now just simple serial communications.

Detail steps depend on the operating system. Followings are from Mac OS X. Choose the Set Up Bluetooth
Devices menu item. Select the Bluetooth_V3 item.

![](/images/blog/bluetooth/bluetooth_setup.jpeg)

The default passcode of the Bluetooth module is ’1234.’ When you are prompted use the passcode.

![](/images/blog/bluetooth/passcode.jpeg)

When the pairing is completed successfully the window below will be shown.

![](/images/blog/bluetooth/pairing_sucess.jpeg)

__The Code__

```
/*

 DF-BluetoothV3 Bluetooth module

 Intefaces the DF-BluetoothV3 Bluetooth module with most Arduino contollers.

 When the DF-Bluetooth is used on Arduino, please make sure you disconnect the
 DF-Bluetooth module before uploading any code to your Arduino. It won’t burn
 your Arduino, but the uploading will fail as the DF-Bluetooth module occupying
 the TX/RX pins.

 * Copyright (c) 2012 by Tony Guntharp. All Rights Reserved.
 * Licensed under the terms of the Apache Public License
 * Please see the LICENSE included with this distribution for details.

 */

void setup() {
  // Initialize serial communications: Set serial baud rate to 9600
  Serial.begin(9600);          
}

void loop() {
  // Print out our Hello World string followed by a newline
  Serial.print("Hello World from the DF-BluetoothV3 Bluetooth module");        
  Serial.println();
  // 1 second delay
  delay(1000);                  
}
```

At the end of uploading and running the code listed above you will start to see some serial output
like in the image below.

![](/images/blog/bluetooth/bt_results.png)

__Source Code__

[Github](https://github.com/fusion94/DF-BluetoothV3_Arduino)
