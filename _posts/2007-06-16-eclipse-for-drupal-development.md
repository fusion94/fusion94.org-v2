---
layout: post
title: 'Eclipse for Drupal Development'
date: 2007-06-16 18:07
comments: true
categories : [Drupal, Open Source, Eclipse]
---  

After trying out several editors and IDE's for software development I've decided to settle on using <a href="http://www.eclipse.org/pdt/index.php">Eclipse</a> for 95% of the work I do and I'll use Xcode only when forced to.

This quick blog post will assist you in getting Eclipse configured for developing anything to do with <a href="http://drupal.org">Drupal</a>.

There are a few versions of Eclipse but the one I've found that works best for Drupal Development is the version put out by the <a href="http://www.eclipse.org/pdt/index.php">PDT Project</a>. The PDT project is working towards providing a PHP Development Tools framework for the Eclipse platform. This project will encompass all development components necessary to develop PHP and will facilitate extensibility.

After you have it installed, go to Windows -> Preferences and make the following changes:
<ol>
<li><strong>Content Types</strong>
<ol>
   <li>Expand the left-hand menu to General -> Content Types
   <li>Under "Content types" on the right, click Text -> PHP Source File
   <li>Add the *.info, *.engine, *.theme, *.install, *.inc, and *.module file types
</ol>

<li><strong>Tab formatting for PHP</strong>
<ol>
   <li>Expand the left-hand menu to PHP -> Formatter
   <li>Check the "Indent using spaces" radio button.
   <li>Change the indent size to 2.
</ol>

<li><strong>Tab formatting for CSS</strong>
<ol>
   <li>Expand the left-hand menu to Web and XML -> CSS Files -> CSS Source
   <li>Select 'Indent using spaces'
   <li>Set 'Intentation size' to 2
</ol>

<li><strong>Tab formatting for JavaScript</strong>
<ol>
   <li>Expand the left-hand menu to Web and XML -> Javascript Files -> Javascript Source
   <li>Select 'Indent using spaces'
   <li>Set 'Intentation size' to 2
</ol>

<li><strong>Tab formatting for HTML</strong>
<ol>
   <li>Expand the left-hand menu to Web and XML -> HTML Files -> HTML Source
   <li>Select 'Indent using spaces'
   <li>Set 'Intentation size' to 2
</ol>

<li><strong>Tab formatting for XML</strong>
<ol>
   <li>Expand the left-hand menu to Web and XML -> XML Files -> XML Source
   <li>Select 'Indent using spaces'
   <li>Set 'Intentation size' to 2
</ol>

<li><strong>Make it Unix-friendly</strong>
<ol>
   <li>Expand the left-hand menu to General ->Workspace
   <li>Text File encoding should be UTF-8
   <li>New text file line delimeter should be Unix
</ol>

<li><strong>Set default text mode to -kkv</strong>
<ol>
   <li>Expand the left-hand menu to Team -> CVS
   <li>Click on the Files and Folders tab
   <li>set the "Default text mode" dropdown to "ASCII with keyword expansion (-kkv)"
</ol>

<li><strong>Tabulators</strong>
<ol>
   <li>Expand the left-hand menu to PHP -> Editor -> Typing
   <li>Check the "Tab key indents the current line" under Tabulators
</ol>

You should now have Eclipse properly configured for Drupal development work.

