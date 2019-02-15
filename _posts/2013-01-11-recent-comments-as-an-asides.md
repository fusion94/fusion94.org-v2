---
layout: post
title: "Recent Comments as an Asides"
date: 2013-01-11 16:39
comments: true
categories: [Octopress, Open Source]
---

This short tutorial will teach you in creating a "Recent Comments" asides for the Octopress sidebar if you're using Disqus as your commenting system.

__Step 1:__ Let’s create a new aside. Create a new file named `recent_comments.html` under `source/_includes/custom/asides`
<!-- more -->
__Step 2:__ Add the following code

{% highlight html %}
<section>
  <h1>Recent Comments</h1>
  <div id="dsq-recentcomments" class="dsq-widget"><script type="text/javascript" src="http://disqus.com/forums/{{ site.disqus_short_name }}/recent_comments_widget.js?hide_avatars=1"></script></div>
</section>
{% endhighlight %}

Here are the parameters you can use for comments :

* hide_avatars : hides the avatar in comments (values : 0, 1)
* num_items : number of comments to show
* excerpt_length : number of characters to show for each comment

__Step 3:__ Add the aside to `_config.yml`

{% highlight ruby %}
default_asides: [custom/asides/links.html, asides/recent_posts.html, custom/asides/recent_comments.html, asides/github.html, asides/twitter.html, asides/delicious.html, asides/pinboard.html, asides/googleplus.html]
{% endhighlight %}

__Step 4:__ Rebuild your site

{% highlight bash %}
rake generate && rake deploy
{% endhighlight %}
