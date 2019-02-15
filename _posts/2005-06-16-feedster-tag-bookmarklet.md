---
layout: post
title: 'Feedster Tag Bookmarklet'
date: 2005-06-16 12:16
comments: true
categories : []
---  

Here's a quick and dirty <a href="http://bookmarklets.com">Bookmarklet</a> that will allow you to Tag Posts on <a href="http://feedster.com">Feedster</a>.

To use, drag the link below onto your browser's toolbar (recommended), or save it as a bookmark. Invoking it will display a text entry box that will allow you to tag pages on Feedster.

(These work for Firefox and Safari)

<a href='javascript:q = "" + (window.getSelection ? window.getSelection() : document.getSelection ? document.getSelection() : document.selection.createRange().text); if (!q) q = prompt("Tag This Post using Feedster:", ""); if (q!=null) location="http://bookmarks.feedster.com/submit.php?tags=" + escape(q).replace(/ /g, "+") + "&uri="+encodeURIComponent(location.href); void 0'>Feedster Tag This</a>

