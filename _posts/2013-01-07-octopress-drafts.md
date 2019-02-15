---
layout: post
title: "Octopress Drafts"
comments: true
date: 2013-01-07 16:13
categories: [Octopress, Open Source]
---

I've really enjoyed my recent conversion to [Octopress](http://octopress.org) but do wish that it by default had a "drafts" mode so that one can write a post over time. This was really bugging me as I was trying to import old posts from awhile back and the workaround was kind of a pain in the ass.

Today of course I located this [post](http://neverstopbuilding.net/how-to-enhance-your-octopress-draft-and-heroku-deploy-process/) by [Jason Fox](http://neverstopbuilding.net) and used it as a reference.

## Creating a new draft

{% highlight bash %}
rake new_draft["Octopress Drafts"]
{% endhighlight %}  

This tasks does essentially what the `new_post` task does except it:

* Puts the file in a _drafts directory.
* Eliminates the date from both the file name and the yaml front matter.
* Adds published: false to the front matter.

Here's the code for the `rakefile`

{% highlight bash %}
# usage rake new_draft["my new draft"]
desc "Begin a new draft in #{source_dir}/#{drafts_dir}"
task :new_draft, :title do |t, args|
  if args.title
    title = args.title
  else
    title = get_stdin("Enter a title for your post: ")
  end
  raise "### You haven't set anything up yet. First run `rake install` to set up an Octopress theme." unless File.directory?(source_dir)
  mkdir_p "#{source_dir}/#{drafts_dir}"
  filename = "#{source_dir}/#{drafts_dir}/#{title.to_url}.#{new_post_ext}"
  if File.exist?(filename)
    abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
  end
  puts "Creating new draft: #{filename}"
  open(filename, 'w') do |post|
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{title.gsub(/&/,'&amp;')}\""
    post.puts "comments: true"
    post.puts "published: false"
    post.puts "categories: "
    post.puts "---"
  end
end
{% endhighlight %}  

## Publishing an existing draft

{% highlight bash %}
rake publish_draft
{% endhighlight %}  

This task lists all of the draft posts, prompting you to select one. After you select one it:

* Adds the current date to the file name and front matter.
* Removes the published: false item.
* Moves the post to the _posts directory.

Here's the code for the `rakefile`

{% highlight bash %}
# usage rake publish_draft
desc "Select a draft to publish from #{source_dir}/#{drafts_dir} on the current date."
task :publish_draft do
  drafts_path = "#{source_dir}/#{drafts_dir}"
  drafts = Dir.glob("#{drafts_path}/*.#{new_post_ext}")
  drafts.each_with_index do |draft, index|
    begin
      content = File.read(draft)
      if content =~ /\A(---\s*\n.*?\n?)^(---\s*$\n?)/m
        data = YAML.load($1)
      end
    rescue => e
      puts "Error reading file #{draft}: #{e.message}"
    rescue SyntaxError => e
      puts "YAML Exception reading #{draft}: #{e.message}"
    end
    puts "  [#{index}]  #{data['title']}"
  end
  puts "Publish which draft? "
  answer = STDIN.gets.chomp
  if /\d+/.match(answer) and not drafts[answer.to_i].nil?
    mkdir_p "#{source_dir}/#{posts_dir}"
    source = drafts[answer.to_i]
    filename = source.gsub(/#{drafts_path}\//, '')
    dest = "#{source_dir}/#{posts_dir}/#{Time.now.strftime('%Y-%m-%d')}-#{filename}"
    puts "Publishing post to: #{dest}"
    File.open(source) { |source_file|
      contents = source_file.read
      contents.gsub!(/^published: false$/, "date: #{Time.now.strftime('%Y-%m-%d %H:%M')}")
      File.open(dest, "w+") { |f| f.write(contents) }
    }
    FileUtils.rm(source)
  else
    puts "Index not found!"
  end
end
{% endhighlight %}  

This way you can compose draft posts at will. Then when you are ready you can publish them and they will appear that you “published” that post on that day.

Here's the full code for the `rakefile` which you can just put at the bottom.

{% highlight bash %}
# usage rake new_draft["my new draft"]
desc "Begin a new draft in #{source_dir}/#{drafts_dir}"
task :new_draft, :title do |t, args|
  if args.title
    title = args.title
  else
    title = get_stdin("Enter a title for your post: ")
  end
  raise "### You haven't set anything up yet. First run `rake install` to set up an Octopress theme." unless File.directory?(source_dir)
  mkdir_p "#{source_dir}/#{drafts_dir}"
  filename = "#{source_dir}/#{drafts_dir}/#{title.to_url}.#{new_post_ext}"
  if File.exist?(filename)
    abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
  end
  puts "Creating new draft: #{filename}"
  open(filename, 'w') do |post|
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{title.gsub(/&/,'&amp;')}\""
    post.puts "comments: true"
    post.puts "published: false"
    post.puts "categories: "
    post.puts "---"
  end
end

# usage rake publish_draft
desc "Select a draft to publish from #{source_dir}/#{drafts_dir} on the current date."
task :publish_draft do
  drafts_path = "#{source_dir}/#{drafts_dir}"
  drafts = Dir.glob("#{drafts_path}/*.#{new_post_ext}")
  drafts.each_with_index do |draft, index|
    begin
      content = File.read(draft)
      if content =~ /\A(---\s*\n.*?\n?)^(---\s*$\n?)/m
        data = YAML.load($1)
      end
    rescue => e
      puts "Error reading file #{draft}: #{e.message}"
    rescue SyntaxError => e
      puts "YAML Exception reading #{draft}: #{e.message}"
    end
    puts "  [#{index}]  #{data['title']}"
  end
  puts "Publish which draft? "
  answer = STDIN.gets.chomp
  if /\d+/.match(answer) and not drafts[answer.to_i].nil?
    mkdir_p "#{source_dir}/#{posts_dir}"
    source = drafts[answer.to_i]
    filename = source.gsub(/#{drafts_path}\//, '')
    dest = "#{source_dir}/#{posts_dir}/#{Time.now.strftime('%Y-%m-%d')}-#{filename}"
    puts "Publishing post to: #{dest}"
    File.open(source) { |source_file|
      contents = source_file.read
      contents.gsub!(/^published: false$/, "date: #{Time.now.strftime('%Y-%m-%d %H:%M')}")
      File.open(dest, "w+") { |f| f.write(contents) }
    }
    FileUtils.rm(source)
  else
    puts "Index not found!"
  end
end
{% endhighlight %}  
