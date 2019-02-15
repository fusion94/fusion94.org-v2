---
layout: post
title: 'Subversion Tip'
date: 2006-04-28 08:40
comments: true
categories : []
---  

Grabbed this little tip from the web. If you've ever had to add multiple files to a subversion repository from the command line then you understand the pain involved. This pain can be reduced by running:
<em>
svn status | grep \? | cut -f7 -d' ' | xargs svn add</em>

This series of commands will run run <em>svn stat</em>us, the output from that is then run through <em>grep \?</em> which finds all lines containing a question mark. The output from grep is passed to <em>cut -f7 -d' '</em> which selects the path name, and these multiple lines are then passed on to <em>xargs svn add</em> which combines all of the unknown paths into a single call to svn add.

