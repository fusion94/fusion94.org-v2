---
layout: post
title: 'Movable Type RSS 2 Templates'
date: 2005-07-04 04:02
comments: true
categories : []
---  

So I've been meaning to do this for some time and with the holiday weekend I was able to find a little time to do this.

The default RSS 2 template that comes with Movable Type quite honestly sucks. So I did a bit of research on the net and found this one which actually formats the feed in a somewhat sane manner.

So here you go.

<code>
&lt;?xml version="1.0" encoding="iso-8859-1"?&gt; &lt;rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:sy="http://purl.org/rss/1.0/modules/syndication/" xmlns:admin="http://webns.net/mvcb/" xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#" xmlns:content="http://purl.org/rss/1.0/modules/content/"&gt;<br />
&lt;channel&gt;<br />
&lt;title&gt;&lt;$MTBlogName remove_html="1" encode_xml="1"$&gt;&lt;/title&gt;<br />
&lt;link&gt;&lt;$MTBlogURL$&gt;&lt;/link&gt;<br />
&lt;description&gt;&lt;$MTBlogDescription remove_html="1" encode_xml="1"$&gt;&lt;/description&gt;<br />
&lt;dc:language&gt;en-us&lt;/dc:language&gt;<br />
&lt;dc:creator&gt;&lt;MTEntries lastn="1"&gt;&lt;$MTEntryAuthorEmail$&gt;&lt;/MTEntries&gt;&lt;/dc:creator&gt;<br />
&lt;dc:rights&gt;Copyright &lt;$MTDate format="%Y"&gt;&lt;/dc:rights&gt;<br />
&lt;dc:date&gt;&lt;MTEntries lastn="1"&gt;&lt;$MTEntryDate format="%Y-%m-%dT%H:%M:%S"$&gt;&lt;$MTBlogTimezone$&gt;&lt;/MTEntries&gt;&lt;/dc:date&gt;<br />
&lt;admin:generatorAgent rdf:resource="http://www.movabletype.org/?v=&lt;$MTVersion$&gt;" /&gt;<br />
&lt;admin:errorReportsTo rdf:resource="mailto:&lt;MTEntries lastn="1"&gt;&lt;$MTEntryAuthorEmail$&gt;&lt;/MTEntries&gt;"/&gt;<br />
&lt;sy:updatePeriod&gt;hourly&lt;/sy:updatePeriod&gt;<br />
&lt;sy:updateFrequency&gt;1&lt;/sy:updateFrequency&gt;<br />
&lt;sy:updateBase&gt;2000-01-01T12:00+00:00&lt;/sy:updateBase&gt;<br />
&lt;MTEntries lastn="15"&gt;<br />
&lt;item&gt;<br />
&lt;title&gt;&lt;$MTEntryTitle remove_html="1" encode_xml="1"$&gt;&lt;/title&gt;<br />
&lt;link&gt;&lt;$MTEntryLink encode_xml="1"$&gt;&lt;/link&gt;<br />
&lt;description&gt;&lt;$MTEntryExcerpt remove_html="1" encode_xml="1"$&gt;&lt;/description&gt;<br />
&lt;guid isPermaLink="false"&gt;&lt;$MTEntryID$&gt;@&lt;$MTBlogURL$&gt;&lt;/guid&gt;<br />
&lt;content:encoded&gt;&lt;![CDATA[&lt;$MTEntryBody$&gt;&lt;MTEntryIfExtended&gt;&lt;p&gt;&lt;a href="&lt;$MTEntryLink$&gt;" title="Continue Reading: &lt;$MTEntryTitle$&gt;"&gt;Continue reading &lt;$MTEntryTitle$&gt;...&lt;/a&gt;&lt;/p&gt;&lt;/MTEntryIfExtended&gt;]]&gt;&lt;/content:encoded&gt;<br />
&lt;dc:subject&gt;&lt;MTEntryCategories glue=" | "&gt;&lt;$MTCategoryLabel remove_html="1" encode_xml="1"$&gt;&lt;/MTEntryCategories&gt;&lt;/dc:subject&gt;<br />
&lt;dc:date&gt;&lt;$MTEntryDate format="%Y-%m-%dT%H:%M:%S"$&gt;&lt;$MTBlogTimezone$&gt;&lt;/dc:date&gt;<br />
&lt;/item&gt;<br />
&lt;/MTEntries&gt;<br />
&lt;/channel&gt;<br />
&lt;/rss&gt;
</code>

