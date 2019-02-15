---
layout: post
title: 'Delivering and Redirecting Movable Type Feeds'
date: 2005-07-04 14:35
comments: true
categories : []
---  

Here's a little nugget to redirect feeds in Movable Type that's transparent to the end user and will not affect new or existing subscribers.

It's really very simple and is nothing more than a 302 Redirect setup using a .htaccess file.

From the Movable Type Admin Menu go to Manage-->Templates.
Click "Create New Index Template".
Fill out "Template Name" and "Output File". I called my Template Name 'HTACCESS' and make sure you set the "Output File" to be '.htaccess'

In the "Template Body" field insert only the following lines as appropriate.

Redirect temp /index.rdf http://location.to.new.file/index.rdf
Redirect temp /index.xml http://location.to.new.file/index.xml
Redirect temp /atom.xml http://location.to.new.file/atom.xml

Then Save and Rebuild.

There's also a way to do Conditional Rewrites through .htaccess but I'll save that for another day.

