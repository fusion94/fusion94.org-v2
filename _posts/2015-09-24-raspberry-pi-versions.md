---
layout: post
title: "Raspberry Pi Versions"
date: 2015-09-24 09:38:42
comments: true
published: true
categories: [Raspberry Pi, Open Source]
---
### Introduction
There have now been a number of revisions to the Raspberry Pi PCB so the device you have in front of you could be any one of a number of variations. The changes include mounting holes, modifications to the power supply circuitry, different GPIO headers and varying numbers of USB ports. Additionally the Pi 2 introduced a new CPU, additional memory and additional USB Ports.

The variations/revisions currently available are :

Model and Pi Revision | RAM Amount | Hardware Revision Code from cpuinfo
--- | --- | ---
Model B Revision 1.0 | 256MB | 0002
Model B Revision 1.0 + ECN0001 (no fuses, D14 removed)	| 256MB| 	0003
Model B Revision 2.0 Mounting holes	| 256MB |	0004 <br>0005<br> 0006
Model A Mounting holes	| 256MB	| 0007 <br>0008 <br>0009
Model B Revision 2.0 Mounting holes	| 512MB	| 000d <br>000e <br>000f
Model B+	| 512MB	| 0010
Compute Module	| 512MB	| 0011
Model A+	| 256MB |	0012
Pi 2 Model B	| 1GB |	a01041 (Sony, UK) <br>a21041 (Embest, China)

In order to find out what hardware revision you have then run the following command at the command prompt or via a terminal window :

{% highlight bash %}
cat /proc/cpuinfo
 {% endhighlight %}

This will give you output that looks something like this :

{% highlight bash %}
 pi@octopi01 ~ $ cat /proc/cpuinfo
processor	: 0
model name	: ARMv6-compatible processor rev 7 (v6l)
BogoMIPS	: 2.00
Features	: half thumb fastmult vfp edsp java tls
CPU implementer	: 0x41
CPU architecture: 7
CPU variant	: 0x0
CPU part	: 0xb76
CPU revision	: 7

Hardware	: BCM2708
Revision	: 000e
Serial		: 00000000cc62aac1
{% endhighlight %}

In this example I’ve got a Pi with a Revision code of 000e. That makes it a: Model B Revision 2.0 Mounting holes with 512MB RAM.

The differences between the board revisions are minor but if you're like me and can't recall which Pi's you've purchased you can now at least  identify the board properly.
