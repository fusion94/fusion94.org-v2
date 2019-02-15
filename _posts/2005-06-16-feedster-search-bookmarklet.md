---
layout: post
title: 'Feedster Search Bookmarklet'
date: 2005-06-16 10:45
comments: true
categories : []
---  

Here's a quick and dirty <a href="http://bookmarklets.com">Bookmarklet</a> that will allow you to search for terms on <a href="http://feedster.com">Feedster</a>.

To use, drag the link below onto your browser's toolbar (recommended), or save it as a bookmark. Invoking it will display a search box that will allow you to search Feedster.

(These work for Firefox and Safari)

<a href='javascript:q = "" + (window.getSelection ? window.getSelection() : document.getSelection ? document.getSelection() : document.selection.createRange().text); if (!q) q = prompt("Search Feedster For:", ""); if (q!=null) location="http://www.feedster.com/search.php?hl=en&ie=UTF-8&q=" + escape(q).replace(/ /g, "+"); void 0'>Feedster Search</a>

