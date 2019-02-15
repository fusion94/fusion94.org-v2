---
layout: post
title: 'Gmail Contacts to OS X Address Book'
date: 2006-03-18 10:44
comments: true
categories : []
---  

As mentioned before on this blog, Nicole has made the switch over to OS X with the purchase of a Mac Book Pro. One of the issues that has arisen is that when she left her old company she also made the move from hotmail to gmail and she had converted all of her contacts into a format that gmail could deal with. ***She is still using gmail but has since moved off the web based client and is now using Mail.App as her client of choice primarily due to the fact that she can use "folders" under Mail.App.***

Well now that she's using Mail.App it was time to export her gmail contacts into a file then import them into Address Book. Only issue is that Address Book doesn't like importing .csv files (it will only import  vCards, LDIF, Text) and gmail doesn't export into any other format.

After doing a bit of research I was able to locate <a href="http://homepage.mac.com/sroy/addressbookimporter/">Address Book Importer</a>. This tool performed the import flawlessly after a modification or two to the original .csv file. The main issue was that gmail exports the contacts first name, last name into a single name field and Address Book didn't appreciate that. After breaking the name field into 2 separate fields the import went smoothly.

The tool itself is free (for a single use) although the author requests that if you use more than that you donate $10.00. A big thank you Steve Roy for writing this wonderful tool.

