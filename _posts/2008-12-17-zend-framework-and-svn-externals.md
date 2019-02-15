---
layout: post
title: 'Zend Framework and svn:externals'
date: 2008-12-17 23:41
comments: true
categories : [PHP, Snippets, SVN, Zend Framework, Software Engineering]
---  

The majority of the work I've been involved with at <a href="http://www.skyfire.com">Skyfire</a> has involved the <a href="http://framework.zend.com/">Zend Framework</a>. When I first got there they were downloading the latest copy from the Zend website and checking into their repository.

I had used svn:externals quite a bit while at <a href="http://contentcircles.com">Content Circles</a> to pull down vendor branches and decided to re-implement this at <a href="http://www.skyfire.com">Skyfire</a>.

In case you aren't aware of <a href="http://svnbook.red-bean.com/nightly/en/svn-book.html#svn.advanced.externals">svn:externals</a> here's a bit of a description. 

> An externals definition is a mapping of a local directory to the URL—and ideally a particular revision—of a versioned directory. In Subversion, you declare externals definitions in groups using the svn:externals property. You can create or modify this property using svn propset or svn propedit. It can be set on any versioned directory, and its value describes both the external repository location and the client-side directory to which that location should be checked out.

>The convenience of the svn:externals property is that once it is set on a versioned directory, everyone who checks out a working copy with that directory also gets the benefit of the externals definition. In other words, once one person has made the effort to define the nested working copy structure, no one else has to bother—Subversion will, after checking out the original working copy, automatically also check out the external working copies.

To implement this is fairly easy and straightforward. Lets say that we have two (2) Zend Framework projects that we want to implement this with and our project repository layout looks like this:

<pre>code/
    branches/
        reporting/
            application/
            library/
            web/
        corporate/
            application/
            library/
            web/
    tags/
    trunk/
</pre>

<ol>
<li>Navigate to the top level of the branches directory and run:

<code>svn propedit svn:externals reporting/library/.</code>

<li>This will open an editor session. To pull in the external revision of Zend Framework just type in:

<code>Zend http://framework.zend.com/svn/framework/standard/tags/release-1.7.1/library/Zend/</code>

<li>Save and exit.
<li>Now update the repository and commit:
<code>svn update
svn commit
</code>
</ol>

Now our project repository will look something like this:

<pre>code/
    branches/
        reporting/
            application/
            library/
                Zend/
            web/
        corporate/
            application/
            library/
            web/
    tags/
    trunk/
</pre>

With the tagged release of the 1.7.1 version of Zend Framework nestled inside the library directory of the reporting branch. 

Also to note is that using this method you can set different branches to pull in different versions of the Zend Framework for production or legacy sake. For example the reporting branch pulls down the 1.7.1 version for use but we could pull in the 1.0.1 version for the corporate branch by executing this:

<ol>
<li>Navigate to the top level of the branches directory and run:

<code>svn propedit svn:externals corporate/library/.</code>

<li>This will open an editor session. To pull in the external revision of Zend Framework just type in:

<code>Zend http://framework.zend.com/svn/framework/standard/tags/release-1.0.1/library/Zend/</code>

<li>Save and exit.
<li>Now update the repository and commit:
<code>svn update
svn commit
</code>
</ol>

We now have Zend Framework 1.0.1 pulled down for use for the corporate branch.

If you ever get confused as to which version you've got pulled down you can just open up Zend/Version.php and take a look at the <code>const VERSION = "x.x.x ";</code> string.



