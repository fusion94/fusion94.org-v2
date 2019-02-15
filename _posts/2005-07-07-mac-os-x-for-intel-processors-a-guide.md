---
layout: post
title: 'Mac OS X for Intel Processors (A Guide)'
date: 2005-07-07 10:57
comments: true
categories : []
---  

So the following guide comes from Steven Troughton-Smith over at <a href="http://grabberslasher.no-ip.com/macosx/">http://grabberslasher.no-ip.com/macosx/</a> mirrored with his permission.


<center><strong>Mac OS X for Intel Processors (A Guide)</strong></center>

Ok, well after seeing how popular my original guide to getting OS X running on Intel machines was, I decided to write up a newer one with more information and updated instructions.

To give the hoardes of people who think they've got OS X, I'm writing this little guide to get as far as you can with the leak. Bear in mind that the leak is incomplete.

<center><strong>THIS WILL NOT EVER BOOT TO THE GUI AS-IS</strong></center>

1) The first step is to get Darwin 8.0.1 from Apple's darwin site. You can get that from <a href="http://www.opensource.apple.com/darwinsource/images/darwinx86-801.iso.gz">http://www.opensource.apple.com/darwinsource/images/darwinx86-801.iso.gz</a>

2) Once downloaded, you must install Darwin. I am not providing any instructions for that part. If Darwin doesn't work on your system, there's nothing I can do to help. I usually install Darwin on a HFS+ filesystem, which is an option in the installer.

3) Once you have Darwin installed, you must upgrade to Darwin 8.1. This can only be done by compiling the source for 8.1 and installing. Luckily, there's a premade 8.1 package with an installer script. Get it from <a href="http://www.rejgond.com/Darwin-8.0.1to8.1.0.tar.gz">here</a>. Copy it to your Darwin hard disk (ftp, network, however you like) and run the script aptly named "script" included in the package (this you must do from within Darwin... I guess you figured that).

4) When Darwin 8.1 is finished, reboot. When you're started up again, run "uname -a" from the command line to make sure that 8.1 is properly installed.

5) Next is the important bit. Get your mactelbase.tar onto the Darwin hard disk, then from within Darwin run "tar xpvf mactelbase.tar -C /".

6) Now, you must run "chmod -R 777 /". This step is vital.

7) Some people report problems now if you don't copy the Extensions folder from the Darwin installer CD. You can mount the CD by typing "mount -t CD9660 /dev/disk1s1 /mnt" depending on which disk is your CD ROM. You want to run "cp -RLv /mnt/System/Library/Extensions /System/Library/Extensions", assuming your mount point is /mnt. If doing this from a GUI (like I did) you want to copy and replace all.

8) Run "sync & sync" for old time's sake.

9) In theory, OS X should be installed by now, and you should be able to reboot and log in to your installation. Remember, that you will only get a command-line, since nobody has been able to start up the GUI.

<center><strong>To start the GUI</strong></center>

Significant progress has been made on getting the GUI to run. My main problem is that the video drivers won't load for me. You have to copy files from "/etc" from real Mac to get WindowServer to even think of booting up. "/etc/mach_init.d/WindowServer.plist" might be nice. We are also missing the loading screen - you will never see that progress bar and "Starting Mac OS X".

Also, Apple seem to have crippled the drivers included with the Developer Transition Kit - i.e. the only ones that seem to run are the Intel Integrated Graphics drivers, like the GMA 900 included in the kit. In my case, I'm using a GeForce 6800 GT and I get all sorts of errors about not being able to load the kernel extension.

You need to run two applications to theoretically boot the GUI, <strong>WindowServer</strong> (in CoreGraphics.framework of ApplicationServices.framework) and <strong>loginwindow</strong>.

WindowServer must be run with the "-daemon" switch, but on all my attempts I get a bus error when trying to run it.

This updated guide uses information from a good friend of mine, <a href="http://omegnet.net/daisuke744/macos.html">Daisuke</a>, and Cmoski.

