---
layout: post
title: "HowTo Tweet New Posts in Octopress"
date: 2013-01-13 07:10
comments: true
categories: [Octopress, Twitter, Open Source]
---

Thanks to a [blog post](http://prydoni.us/blog/2012/04/29/tweet-new-posts-in-octopress/) from [Adnan Abdulhussein](http://prydoni.us/blog/), I can now auto-tweet new blog posts on my [Octopress](http://octopress.org) blog.

I used his original blog post as a guideline but his method was a bit dated and here's the process I used to get this functionality working.

The basic idea works this way, when you create a post it prints the tweet message you give it and a link to the post in a `tweet_queue` file. When you deploy, it simply reads this file and tweets what’s in there line-by-line. This also means you can create multiple posts at a time, and they will all be tweeted at the same time when you deploy you blog.

#### Create an application on Twitter

Head over to [https://dev.twitter.com/apps/new](https://dev.twitter.com/apps/new), sign in and create a Twitter application for your blog.

In _Settings:_ ensure _read_ and _write_ access is __enabled__.

In _Details:_ take note of the following details:

* Consumer Key
* Consumer Secret
* Access Token
* Access Token Secret

#### Install the gem

We'll be using the Twitter gem to update statues. So first things first, so go ahead and put this in your `Gemfile` in the development group::

{% highlight ruby %}
gem 'twitter'
{% endhighlight %}

Then from a terminal run `bundle install` to install the gem.

#### Configure Twitter
Open up your `Rakefile` and add the following up near the top with the other requires:

{% highlight ruby %}
require "twitter"
{% endhighlight %}

While you have the `Rakefile` open add the following lines after the `server_port` line:

{% highlight ruby %}
# Twitter config (for tweeting posts)
Twitter.configure do |config|
  config.consumer_key = "YOUR_CONSUMER_KEY"
  config.consumer_secret = "YOUR_CONSUMER_SECRET"
  config.oauth_token = "YOUR_OAUTH_TOKEN"
  config.oauth_token_secret = "YOUR_OAUTH_TOKEN_SECRET"
end

# URL of your blog e.g. http://fusion94.org/blog/
# MAKE SURE THERE IS A TRAILING SLASH, otherwise the linking won't work
blog_url = "YOUR_BLOG_URL"
{% endhighlight %}

Replacing `YOUR_*` with the details from your Twitter app.

Make sure there is a trailing slash (slash at the end of the URL) for the `blog_url`. It needs this because it appends the date-name combo of the post to form the URL of the post.

#### Modify the ‘new_post’ rake task

Look for the `:new_post` rake task in the `Rakefile`. this should be around lines 106 or so. Replace the task with the following:

{% highlight ruby %}
# usage rake new_post[my-new-post] or rake new_post['my new post'] or rake new_post (defaults to "new-post")
desc "Begin a new post in #{source_dir}/#{posts_dir}"
task :new_post, :title, :tweet do |t, args|
  raise "### You haven't set anything up yet. First run `rake install` to set up an Octopress theme." unless File.directory?(source_dir)
  mkdir_p "#{source_dir}/#{posts_dir}"
  args.with_defaults(:title => 'new-post', :tweet => '')
  title = args.title
  filename = "#{source_dir}/#{posts_dir}/#{Time.now.strftime('%Y-%m-%d')}-#{title.to_url}.#{new_post_ext}"
  if File.exist?(filename)
    abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
  end
  puts "Creating new post: #{filename}"
  open(filename, 'w') do |post|
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{title.gsub(/&/,'&amp;')}\""
    post.puts "date: #{Time.now.strftime('%Y-%m-%d %H:%M')}"
    post.puts "comments: true"
    post.puts "categories: "
    post.puts "---"
  end
  tweet = args.tweet
  if not tweet == ''
    # add to twitter status queue
    puts 'Adding post to tweet queue, it will be tweeted after deploying.'
    open('tweet_queue', 'a') do |file|
      file.puts "#{tweet} - #{blog_url}#{Time.now.strftime('%Y/%m/%d')}/#{title.to_url}/"
    end
  end
end
{% endhighlight %}

If you already have a modified task, the only changes are the task declaration `(task :new_post, :title, :tweet do |t, args|)` and the last few lines starting with `tweet = args.tweet.`

#### Setup tweet on deploy

Look for the `:deploy task` in the `Rakefile` this should be around lines 232 or so. Replace the task with the following:

{% highlight ruby %}
desc "Default deploy task"
task :deploy do
  # Check if preview posts exist, which should not be published
  if File.exists?(".preview-mode")
    puts "## Found posts in preview mode, regenerating files ..."
    File.delete(".preview-mode")
    Rake::Task[:generate].execute
  end

  Rake::Task[:copydot].invoke(source_dir, public_dir)
  Rake::Task["#{deploy_default}"].execute

  # Tweet
  next if not File.exists? 'tweet_queue'
  puts "Tweeting..."
  client = Twitter::Client.new
  open('tweet_queue', 'r') do |file|
    while (line = file.gets)
      puts "Tweeting '#{line.gsub("\n", "")}' for @#{client.current_user.screen_name}..."
      Twitter.update line
    end
  end
  puts "Deleting queue..."
  rm 'tweet_queue'
end
{% endhighlight %}

Or indeed just add the last couple of lines starting with `# Tweet`.

#### Usage

The only change here is you’ll need to specify a separate message for the tweet when you create the post. This is the best way to give you the option of choosing whether you want to tweet the post or not. It also allows you to add @’s and #’s to the tweet message separately from the post title.

Here’s an example:

The first section is the title of the post while the second section is the tweet that will go out along with the URL to the blog post.

{% highlight ruby %}
rake new_post["HowTo Tweet New Posts in Octopress","HowTo Tweet New Posts in Octopress @twitter"]
{% endhighlight %}

And here's the message generated after the `rake new_post` task is run.

{% highlight bash %}
mkdir -p source/_posts
Creating new post: source/_posts/2013-01-13-howto-tweet-new-posts-in-octopress.markdown
Adding post to tweet queue, it will be tweeted after deploying.
{% endhighlight %}

Now all that's left to do is create your post and then run `rake generate && rake deploy`. Your post will be deployed and your tweet will be sent.

#### Conclusion

And that's it. Pretty simple eh? Have fun tweeting and blogging from Octopress.
