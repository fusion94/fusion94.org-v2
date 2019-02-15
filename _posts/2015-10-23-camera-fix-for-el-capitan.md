---
layout: post
title: "Camera Fix for El Capitan"
date: 2015-10-23 17:01:37
comments: true
published: true
categories: [OSX, Bug]
---

If you've upgraded to Mac OS X 10.11.x "El Capitan" you may occasionally see an error that states "No Camera Available" when you open up FaceTime or any other app that requires usage of the camera.

If you are having this problem, or if you see this problem pop up well thankfully the fix is pretty easy:

* Close all the applications that are using the camera (such as FaceTime, Hangouts, Skype, etc).
* Open a terminal (Launchpad -> Terminal).
* Type the following command:
{% highlight bash %}
sudo killall VDCAssistant
{% endhighlight %}
* Re-open your application. You should see that the camera is working now.

The reason for this is due to the fact that Mac OS X launches a background process called “VDCAssistant” when an application that requires the camera is launched. When this background process is not closed properly when the application is closed, it will hog up the resources and prevent other apps from accessing the camera. By force closing this background process, you are freeing up the resources to make the camera available again for applications.

This should fix the “No Camera Available” issue 99% of the time. For the remaining times, you are probably better of restarting your Mac.
