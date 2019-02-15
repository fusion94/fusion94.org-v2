---
layout: post
title: 'How to Change __MyCompanyName__ in Xcode ... Permanently '
date: 2008-06-11 09:58
comments: true
categories : [Apple/OSX, Xcode, Software Engineering, Snippets]
---  

If you're tired of seeing __MyCompanyName__ automatically in all copyright notices of all your XCode source files then here's a quick and easy fix. You can set the XCode default company name for copyright notice as follows:

Go to /Applications/Utilities and open Terminal.app and enter the following code:

<code>defaults write com.apple.Xcode PBXCustomTemplateMacroDefinitions '{"ORGANIZATIONNAME"="SomeOther Co.";}'</code>

Make sure you replace SomeOtherCo. with whatever name you want. I used:

<code>defaults write com.apple.Xcode PBXCustomTemplateMacroDefinitions '{"ORGANIZATIONNAME"="damagestudios.net";}'</code>

