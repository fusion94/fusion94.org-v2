---
layout: post
title: 'Disable Space Switching - 10.5.2'
date: 2008-02-25 18:44
comments: true
categories : [Apple/OSX, Spaces, Snippets]
---  

The 10.5.2 version of OS X has a new preferences command for Spaces although tt's hidden and not available through the System Preferences.

What it does is allow one to Command-Tab to the app you want and create a new window in the current space. No more switching to the space that the app was originally launched in.

Here's the terminal command:

<code>defaults write com.apple.Dock workspaces-auto-swoosh -bool NO</code>

Then just restart the dock using:

<code>killall Dock</code>

If you need to back out your changes just change the first command from NO to a YES then restart the Dock once more.

