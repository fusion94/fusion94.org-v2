---
layout: post
title: "Home Automation with home-assistant"
date: 2019-02-02 08:35:11
comments: true
published: true
tags: ha, automation, home automation
featured_image: /img/featured/ha.webp
---

Late in 2017 I started to automate as much as our home as possible. After much trial and error I settled on [Home Assistant](https://www.home-assistant.io).

### What is Home Assistant?

> Open source home automation that puts local control and privacy first. Powered by a worldwide community of tinkerers and DIY enthusiasts. Perfect to run on a Raspberry Pi or a local server.

Home Assistant was/is written in Python and was originally created by Paulaus Schoutsen in 2013 "as a simple script to turn on the lights when the sun was setting".

### Basic Components of a Automated Home Project

There are a few basic components of an Automated Home. Regardless of the technology that's used there are the basic components.

* Home Controller or Hub
* Sensors
* Actuators
* Interfaces

#### Home Controller
We can think of the controller as the brain of the system. It is the tool that basically holds everything together. The controller is the headquarters of the Automated Home. It communicates with other devices to get information and directs the to do things like "turn on the lights".

#### Sensors
Generally they are the remote correspondents of the controller placed throughout the house. They can gather information such as temperature, humidity and light level and send that information back to the controller. With the controller now having this information the controller can make decisions based on automation rules that we have configured.

#### Actuators
Actuators are the devices that can take an action and carry out tasks based on our automation rules as well as the information transmitted from the sensors.

#### Interfaces
Interfaces are nothing more than how we interact with the controller. It can be a mobile or web interface or even a device such as [Google Home](https://store.google.com/us/product/google_home?hl=en-US) or the [Amazon Alexa](https://www.amazon.com/Amazon-Echo-And-Alexa-Devices/b?ie=UTF8&node=9818047011).

#### My Setup
I decided to start with the basics back then and set everything up using the following devices:

* Google Chromecast
* Philips Hue Bridge
* Nest Cameras
* Nest Thermostat
* Nest Protect
* WeMo Smart Switch

![alt text](/images/ha-screenshot.png "HA Setup")

You can find my setup over on [GitHub](https://github.com/fusion94/home-assistant)

I will be writing longer posts over the next few weeks going into greater details as it pertains to my setup.
