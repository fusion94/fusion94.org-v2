---
layout: post
title: "Titanium Studio Issues"
comments: true
date: 2013-01-10 00:41
categories: [Open Source, Mobile, Appcelerator Titanium]
---

I just installed the latest Titanium Studio from Appcelerator and a Titanium Update window pops up when I open TiStudio and asks me to install Titanium CLI and Alloy.

When I press the install button a dialog pops up that says "Titanium wants to make changes. Provide your password to allow installation". I enter my password and TiStudio tells me that my password is incorrect and TiStudio asks me to enter it again.
<!-- more -->
This is due in part to the fact that Titanium Studio has no clue how to deal with Node.js packages. Which is fucking ironic considering how much of the new Titanium platform is based on Node.js.

To get around this all you need to do is manually install alloy and titanium cli using this:

{% highlight bash %}
npm install -g alloy titanium
{% endhighlight %}
