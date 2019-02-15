---
layout: post
title: 'Mail.app imap-ssl workaround'
date: 2004-03-19 12:08
comments: true
categories : []
---  

I know this is old news but it took me awhile to locate this workaround and thought I'd share.

If you use a mail server with imap-ssl that doesn't have a verified certificate, you get a pop up complaining whenever you open mail. If you click show certificate, there's a certificate icon you can supposedly drag to the desktop and then use in keychain according to apple's support webpages. Well, dragging that image crashes Mail.app.

There is a workaround, if you have access to the certificate (say, you're friends with your sysadmin, which you should be, if you aren't friends with the sysadmin you can always run this from the terminal "openssl s_client -connect host:port" then cut and paste the cert into a file (e.g. "host.crt"):

Accepting a mailserver SSL certificate permanently
1) open Keychain Access (it's in "Utilities")
2) select the menu item: File--Add Keychain...
3) navigate to /System/Library/Keychains/
4) select X509Anchors and click 'Open'
5) close Keychain Access
6) copy the .pem certificate file from your server to your local machine.
7) open the finder and navigate to where you copied the file
8) double click it
9) import into X509Anchors
10) quit Keychain Access and restart Mail - it shouldn't ask for you to accept the certificate anymore

