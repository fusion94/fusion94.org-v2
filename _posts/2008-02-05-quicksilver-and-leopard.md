---
layout: post
title: 'Quicksilver and Leopard'
date: 2008-02-05 09:31
comments: true
categories : [Apple/OSX, Leopard, Quicksilver]
---  

Ever since I upgraded all my boxes to <a href="http://www.apple.com/macosx/">Leopard</a> <a href="http://www.blacktree.com/">Quicksilver</a> has been having issues. While searching for a new release I've located a solution that seems to have fixed most of my issues. Here's what to do.

<ol>
<li>Quit Quicksilver if running.</li>
<li>Delete all traces of Quicksilver by deleting these 4 files.</li>

<ul>    
<li>/Applications/Quicksilver.app</li>
<li>~/Library/Application Support/Quicksilver</li>
<li>~/Library/Preferences/com.blacktree.Quicksilver.plist</li>
<li>~/Library/Caches/Quicksilver</li>
</ul>

<li>Head over to <a href="http://lipidity.com/software/quicksilver/">http://lipidity.com/software/quicksilver/</a> and download and install Quicksilver B5X.</li>
<li>Launch Terminal and run the following commands.</li>

<ul>
<li>chmod 0644 /Applications/Quicksilver.app/Contents/Info.plist
</ul>

<li>Open Quicksilver and go through the setup WITHOUT installing any plugins.</li>
<li>Open or relaunch Terminal and run the following commands.</li>

<ul>
<li>defaults write com.blacktree.Quicksilver "Cutting Edge Features" -bool yes</li>
<li>defaults write com.blacktree.Quicksilver "Feature Level" 3</li>
</ul>

<li>Quit and relaunch Quicksilver.</li>
<li>You can now adjust your settings and preferences and install some plugins.</li>

</ol>

I'm not saying this will work for you but is has made Quicksilver more stable for me.

Also to note is that the <a href="http://www.mygnu.com/julius/proj_bezel.html">Quicksilver Interface plugin - Bezel HUD</a> is pretty sweet.



