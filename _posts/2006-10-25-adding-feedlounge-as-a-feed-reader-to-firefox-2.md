---
layout: post
title: 'Adding FeedLounge as a Feed Reader to Firefox 2'
date: 2006-10-25 12:36
comments: true
categories : []
---  

<a href="http://www.getfirefox.com">Firefox 2</a> has been released and after using the last 2 Release Candidates it's as good as promised.

One new features is Previewing and subscribing to Web feeds: Users can decide how to handle Web feeds, either subscribing to them via a Web service or in a standalone RSS reader, or adding them as Live Bookmarks. My Yahoo!, Bloglines and Google Reader come pre-loaded as Web service options, but users can add any Web service that handles RSS feeds.

This relatively short blog post will show you how to replace Bloglines with <a href="http://feedlounge.com">FeedLounge</a>.

1. The first thing you need to do is go into about:config. Just type “about:config” into your address bar.

2. Now scroll down in about:config till you find the string called:

    browser.contentHandlers.types.0.title

Right-click this string and choose “Modify”. Now get rid of the name Bloglines and replace it with the name FeedLounge. Then hit “OK”.

3. Next you will need to look a little further down in about:config till you find the string called:

    browser.contentHandlers.types.0.uri

Right-click this string and choose “Modify” again. This time you are going to have to change the URL that your service in question uses. In the place where the feed would go, put in “%s”. So for FeedLounge, You should type this into that box:

http://my.feedlounge.com/subscribe/feed?url=%s

Then hit “OK”.

After completing these steps just restart Firefox 2 and you'll be good to go.

