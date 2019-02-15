---
layout: post
title: 'Comcast and the Airport Extreme Base Station'
date: 2008-02-14 20:01
comments: true
categories : [Apple, Comcast]
---  

Awhile back I picked up an Airport Extreme Base Station to replace a Linksys Wireless Access Point. Unfortunately I was brain-dead while getting everything setup and couldn't get it to talk to the Comcast Cable Modem so I ended up putting it behind the Linksys WAP and turning off the Wireless on the Linksys device.

Tonight I fixed the issue. Turns out I needed to turn off the Cable Modem (as well as remove the built-in battery backup) for a few minutes while keeping the AEBS turned off. This allowed for the Comcast Modem to clear both the MAC address of the Linksys and the IP addresses. Next I turned on the Cable modem, waited till it had a good connection then turned on the AEBS. The AEBS was then able to pick up a valid IP address and everything was good to go.


