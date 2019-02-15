---
layout: post
title: 'Adding Metadata Tags to iPod Videos'
date: 2006-01-15 21:56
comments: true
categories : []
---  

In an <a href="http://fusion94.org/blog/video-ipod-guide.htm">earlier post</a> I linked to an <a href="http://plasticbugs.com/?p=305">excellent guide</a> that showed video iPod users how to convert their existing movies over to iPod compatible video.

While this is an excellent guide it was lacking in how to read, parse, and set iTunes-style metadata into mpeg4 containers (m4a, m4b, m4p, m4v, mp4).

The video type is stored in the file as an ATOM (metadata for QuickTime and MPEG4) called stik. You can use a hex editor to modify the ATOM directly, but this is very clunky and dangerous (I repeat it's dangerous).


Instead you can use a tool such as <a href="http://atomicparsley.sourceforge.net/">AtomicParsley</a> to do this for you. Once you've dowloaded and installed AtomicParsley you can run the tool from the command line to set the metadata tags properly. For example once I ripped Stargate Atlantis - Season One - Episode 101 to mp4 I ran the following command from the terminal to set the tags.
<code>
<strong><em>/bin/AtomicParsley RisingPart1.mp4 --title "Rising Part 1" --TVEpisode "101" --TVEpisodeNum 101 --tracknum "1/20" --description "The discovery of an amazing city left behind by the Ancients in the most unlikely of places, leads a new Stargate team to the distant Pegasus galaxy. Once there, the new team encounters a planet of primitive humans being decimated by a terrible alien race - the Wraith." --year 2004 --genre "TV Shows" --stik "TV Show" --TVNetwork "SciFi" --TVShowName "Stargate Atlantis" --TVSeasonNum 1 --artist "Stargate Atlantis" --album "Stargate Atlantis, Season 1"</em></strong></code>

The only downside that I see to AtomicParsley is that instead of altering the mp4 directly it copies the file and makes the changes into a temp file which is written to disk.

If you aren't comfortable with using the command line at all you can also download <a href="http://home.comcast.net/~lowellstewart/lostify/">Lostify</a> which is a "gui-wrapper" to AtomicParsley.

Anyways, I hope this helps some of you out. Have fun.

