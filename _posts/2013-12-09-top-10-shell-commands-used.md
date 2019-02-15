---
layout: post
title: "Top 10 Shell Commands used"
date: 2013-12-09 09:26
comments: true
categories: [shell, stats]
---

From time to time, I like to analyze which unix or linux shell commands I'm using most frequently. To do this, all I need is a little awk, like the following:

{% highlight bash %}
history | awk '{print $2}' | sort | uniq -c | sort -rn | head
{% endhighlight %}

So what does this do?

Basically, it parses your history looking at the 2nd column, which is the command you typed and increments it each time it is found. Then it displays a sorted report showing the count of the command and the command, like this example on my MacBook Pro:

{% highlight bash %}
1353 git
749 cd
391 ssh
379 ls
194 rake
168 vagrant
152 sublime
143 rvm
135 rm
119 bundle
{% endhighlight %}

Based on this output of the top 10 most frequently used shell commands, it shows that I'm using git, and ls quite a bit so it would be helpful to create aliases for these commands. Here are a few examples:

{% highlight bash %}
alias g="git"
alias l="ls -al"
{% endhighlight %}

Now that I know git is one of my most used commands I can parse my history to determine what git command I use most frequently:

{% highlight bash %}
history | awk '{print $2 " " $3}' | sort | uniq -c | sort -rn | grep "git" | head     
{% endhighlight %}

The output of that command provides me with this information:

{% highlight bash %}
 200 git push
 191 git commit
 172 git status
 105 git branch
 103 git clone
  99 git checkout
  79 git remote
  49 git fetch
{% endhighlight %}  

This now allows me to tailor my aliases for git accordingly.

{% highlight bash %}
alias gp="git push"
alias gc="git commit -m"
alias gs="git status"
{% endhighlight %}

By tailoring your aliases appropriately you can speed up your workflow significantly, as well as reduce the wear and tear on your fingers.
