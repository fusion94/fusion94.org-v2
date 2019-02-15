---
layout: post
title: 'Intel Mac’s and Eclipse'
date: 2006-04-27 01:30
comments: true
categories : []
---  

The <a href="http://www.eclipse.org/downloads/">current version</a> of <a href="http://www.eclipse.org">Eclipse</a> will NOT work (at least out of the box) with the new Intel Based Mac's. Andre Weinand over at IBM has posted this <a href="https://bugs.eclipse.org/bugs/attachment.cgi?id=34552&action=view">file</a> that will fix the issues.

Once you download the file unzip it and then move org.eclipse.swt.carbon.macosx.ppc_3.1.0.jar into the eclipse/plugins folder. Also make sure you delete the org.eclipse.swt.carbon.macosx.ppc_3.1.1.jar file located within the plugins folder.

Rumour has it that <a href="http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/S-3.2M5-200602171115/eclipse-SDK-3.2M5-macosx-carbon.tar.gz">eclipse-SDK-3.2M5-macosx-carbon.tar.gz</a> will also fix these issues although I haven't tried it yet.

