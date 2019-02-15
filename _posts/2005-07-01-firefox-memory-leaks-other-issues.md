---
layout: post
title: 'Firefox Memory Leaks/Other Issues.'
date: 2005-07-01 02:36
comments: true
categories : []
---  

So if you've used Firefox you've probably noticed that it suffers from what can be described as a fairly harsh <i>"memory leak"</i>. The main cause of the problem appears to lie within the plugin for Flash content. There are 2 workarounds that I've located.

The first is rather straightforward and simple but wasn't practical for me. All you have to do is un-install/remove the flash plugin and performance increases significantly.

The other option (and the one I'm using) requires you to make some changes to the Firefox configuration. This is how you fix this "memory leak" problem. (It's not actually a leak, it just doesn't flush the cache it has.)

1)Type <i>about:config</i> into the location bar and press enter
2)Right click any line to bring up a sub-menu
3)Choose "new">"integer"
4)paste this into the dialogue that appears: <i>browser.cache.memory.capacity</i>
5)Next click Okay
6)Specify the amount in kb (about 60000 should do) in the next dialogue that appears
7)Restart Firefox and happy surfing.

