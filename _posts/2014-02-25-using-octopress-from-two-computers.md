---
layout: post
title: "Using Octopress from Two Computers"
date: 2014-02-25 06:12:33 -0800
comments: true
categories: [Octopress, Open Source]
---
This blog post covers how recreate a local repository of your [Octopress](http://octopress.org) blog. I needed to figure out how to do this so that I could update my blog from both my personal desktop and my laptop.

<div class="info">Note: This solution will only work with the <b>2.x</b> version of Octopress. For the 3.x version there's <a href="https://github.com/octopress/deploy">Octopress Deploy</a></div>

### How Octopress Works
Octopress repositories have two branches, `source` and `master`. The source branch contains the files that are used to generate the blog and the `master` contains the blog itself.

When the local folders are initially configured according to the Octopress Setup Guide, the `master` branch is stored in a subfolder named `_deploy`. Since the folder name begins with an underscore, it is ignored when you `git push origin source`. Instead, the `master` branch (which contains your blog posts) gets updated when you `rake deploy`.

### Recreating an Octopress repository

To recreate the local directory structure of an existing Octopress blog, follow these instructions.

First you will need to clone the `source` branch to a local octopress folder.

{% highlight bash %}
$ git clone -b source git@github.com:username/username.github.com.git octopress
{% endhighlight %}


Then clone the `master` branch to the `_deploy` subfolder.

{% highlight bash %}
$ cd octopress
$ git clone git@github.com:username/username.github.com.git _deploy
{% endhighlight %}

Then run the rake installation to configure everything

{% highlight bash %}
$ gem install bundler
$ rbenv rehash    # If you use rbenv, rehash to be able to run the bundle command
$ bundle install
$ rake setup_github_pages
{% endhighlight %}

It will prompt you for your repository URL.

{% highlight bash %}
Enter the read/write url for your repository
(For example, 'git@github.com:your_username/your_username.github.com)
{% endhighlight %}

You are now setup with a new local copy of your existing Octopress blog.

<div class="hr"></div>

### Pushing changes from two different machines

If you want to blog from more than one computer, you need to make sure that you push everything before switching computers. From the first machine do the following whenever you’ve made changes:

{% highlight bash %}
$ rake generate
$ git add .
$ git commit -am "Some comment here."
$ git push origin source  # update the remote source branch
$ rake deploy             # update the remote master branch
{% endhighlight %}


Then on the second machine, you will need to pull down those changes.

{% highlight bash %}
$ cd octopress
$ git pull origin source  # update the local source branch
$ cd ./_deploy
$ git pull origin master  # update the local master branch
{% endhighlight %}
