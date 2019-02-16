---
layout: post
title: "Embedding YouTube Videos in Jekyll Sites"
date: 2017-07-21 19:48:15
comments: true
published: true
tags: blogging
---

If you're embedding YouTube videos on your Jekyll site it can be a pain in the butt to include the YouTube embed code every time. Here is an easy way to use includes instead of using a plugin.

Create a file in your `_includes` folder called `youtubePlayer.html` with this content:

```
<iframe width="640" height="385" src="https://www.youtube.com/embed/{{ include.id }}" frameborder="0" allowfullscreen></iframe>
```

Then include this snippet whenever you want to embed a YouTube video:

{% raw %}
```
{% include youtubePlayer.html id="youtubeId" %}
```
{% endraw %}

Don't forget to replace `youtubeId` with the actual <b>ID</b> of the video.
