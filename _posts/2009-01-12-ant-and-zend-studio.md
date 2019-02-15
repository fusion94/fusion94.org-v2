---
layout: post
title: 'ANT and Zend Studio'
date: 2009-01-12 08:25
comments: true
categories : [PHP, Zend Studio]
---  

Zend Studio for Eclipse is a commercial edition of Eclipse plus the PDT plugin and various other additions. Unfortunately Zend decided to disable the Ant plugin in it's distribution of the Eclipse platform. Nonetheless if you'd like to run Ant scripts or simple Phing scripts it would be really useful to be able to use the Ant integration of Eclipse. 

<b>Preparation</b> 
First you need to make sure that the Eclipse Java Development Tools are available in Zend Studio for Eclipse.
<ul> 
<li>From the Help menu click Software Updates > Manage Configuration. 
<li>Check for the entry Eclipse Java Development Tools. 
</ul>
If the entry is not listed or disabled, you need to install the Eclipse feature. 
<ul>
<li>From the Help menu click Software Updates > Find and Install. 
<li>Click Search for new features to install. 
<li>Check Europa Discovery Site and click Next. 
<li>Select Java Development Tools and click Finish to install the feature. 
<li>Restart Zend Studio for Eclipse. 
</ul>

<b>How to enable the Ant integration</b> 
Now it gets a little tricky. 
<ul>
<li>From the File menu click New > Project. 
<li>Check Show All Wizards. 
<img src="/images/zend-ant/1.jpg">
<li>In the Wizards text field enter Ant, select Java Project from Existing Ant Buildfile and click Next. 
<img src="/images/zend-ant/2.jpg">
<li>You will be asked to enable Ant Development - confirm with Yes. 
<img src="/images/zend-ant/3.jpg">
<li>Now you can cancel the new Java Project - Ant has been activated. 
</ul>


