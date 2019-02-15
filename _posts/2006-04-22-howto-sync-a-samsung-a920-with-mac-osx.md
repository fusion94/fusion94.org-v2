---
layout: post
title: 'HOWTO Sync a Samsung A920 with Mac OSX'
date: 2006-04-22 00:22
comments: true
categories : []
---  

I've had my <a href="http://sprintpcs.com">Sprint Power Vision</a> <a href="http://www.samsung.com/Products/MobilePhones/Sprint/SPH_A920WSSXAR.asp">Samsung A920</a> now for going on 40 days or so and for the most part have been very pleased with the functionality of the phone and the quality of service that Sprint has provided. I was able to get it to function as a <a href="http://en.wikipedia.org/wiki/EV-DO">EVDO</a> device and surf the web on my Windows laptop but have yet to try to do so on my <a href="http://www.apple.com/macbookpro/">MacBook Pro</a> (primarily because it just arrived).

One of my biggest gripes to date has been the fact that while it's a Bluetooth enabled phone I've not been able to get my <a href="http://www.apple.com/macosx/features/addressbook/">Address Book</a> synced over.

That is...until now.

A little background first though. iSync syncs with Bluetooth enabled phones using a standard called <a href="http://www.openmobilealliance.org/tech/affiliates/syncml/syncmlindex.html">SyncML</a>. Now it's up to the phone manufacturer to support that protocol and if they don't then you're pretty much out of luck. Samsung supports the SyncML standard on the p777 and p207 phone (I believe these are Cingular phones) but that's pretty much it. In other words this isn't Apple's fault. It's Samsungs.

So without anymore ramblings here is what worked for me.

<ol>
	<li>Configure Address Book to use the vCard 3.0 format.</li>
	<li>Download <a href="http://homepage.mac.com/gaz/">vCard Splitter</a>.</li>
	<li>Install vCard Splitter to a location on your hard drive (NOTE: * Read the bottom of this post for more instructions).</li>
	<li>Open up Address Book and highlight ALL the cards you want to transfer to your phone.</li>
	<li>From the File menu choose "Export vCard...". This will export all the highlighted entries into a single vCard entry.</li>
	<li>Drag that single exported vCard onto the vCard Splitter application. This will split that single vCard into vCards for every entry.</li>
	<li>Pair your Samsung A920 with your computer from System Preferences-->Bluetooth-->Devices.</li>
	<li>Also make sure that System Preferences-->Bluetooth-->Settings has the "Show Bluetooth status in the menu bar" option checked.</li>
	<li>From the Bluetooth Status Menu Bar select "Send File".</li>
	<li>Select all vCards that you wish to send to your phone and hit "Send".</li>
	<li>Accept the push from your phone (you should be prompted on the phone).</li>
</ol>

And that's it. You should now have imported the content of your Address Book into your Samsung A920 phone. Now this isn't by any means perfect (it wont actually import street addresses just phone numbers and email addresses), but if you have a fair number of contacts in your Address Book (as I do) it sure beats manually entering them one by one. The other downside is that it can be difficult to maintain later on down the road as after the initial import you're going to have to do "selective exports/imports" to keep them in sync. Also to note is this is a "One Way Sync" going from Phone-->Address Book.

Anyways, I hope that this helps someone.

(*) When you download the file you might get a "double .DMG file". In other words the Applescript file located in the .DMG you downloaded will also have a .DMG extension. You can change this by highlighting the file, press CMD-I to bring up the "Get Info" window. From there go to the "Name & Extension:" option and remove the .DMG extension and confirm.

