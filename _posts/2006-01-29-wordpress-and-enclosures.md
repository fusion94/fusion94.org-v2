---
layout: post
title: 'WordPress & Enclosures'
date: 2006-01-29 15:29
comments: true
categories : []
---  

One issue I've had with WordPress (2.0 and previous versions) is the way that it deals with enclosures and the enclosure element. Wordpress by default when you link to a .mp3 or a .mov file will automatically encapsulate the file and create an enclosure for it.

The issue I have with this is that this should be abstracted out into Administrator Options and you should have the ability to turn this On or Off. Unfortunately this isn't possible.

You can however go to line 1020 (Wordpress 2.0) and line 766 (WordPress 1.5.2) in wp-includes/functions.php and comment out that line completely. This line is responsible for "locating" any media file(s) linked in your post and by commenting it out then WordPress won't even search your posts to provide enclosure support.

So what you'll end up with is this:

<blockquote>
Before:
preg_match_all("{\b http : [$any] +? (?= [$punc] * [^$any] | $)}x", $content, $post_links_temp);

After:
//preg_match_all("{\b http : [$any] +? (?= [$punc] * [^$any] | $)}x", $content, $post_links_temp);</blockquote>

  

