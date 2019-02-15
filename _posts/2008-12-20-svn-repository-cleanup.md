---
layout: post
title: 'SVN Repository Cleanup'
date: 2008-12-20 22:25
comments: true
categories : [SVN, Snippets, find]
---  

I've spent the past few hours doing some pretty massive SVN repository cleanup for all of my personal projects. One annoyance is all of the .svn directories that occasionally have to be located and removed before you can recommit.

Here's a quick one-liner to assist you in this. Let's say you have a couple of top level directories that look something like this:

<pre>
foo/
   bar/
bar/
   foo/
</pre>

If you want to find and remove all those pesky .svn directories from within the foo directory all you need to do is run this:

<code>find foo -type d -name ".svn" -exec rm -rf {} \;</code>

If you wanted to hit both directories at the same time you use this:

<code>find * -type d -name ".svn" -exec rm -rf {} \;</code>

Also to note is that you can use this to also locate and remove .DS_Store files that OSX places all over the place. The only difference is that the flag passed to -type would now be a 'f' like this:

<code>find foo -type f -name ".DS_Store" -exec rm -rf {} \;</code>

Hope this is useful to someone.

