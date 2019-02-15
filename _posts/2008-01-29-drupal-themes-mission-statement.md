---
layout: post
title: 'Drupal Themes Mission Statement'
date: 2008-01-29 09:33
comments: true
categories : [Drupal, Open Source, Themes, Code, Technology, Snippets]
---  

In some <a href="http://drupal.org/project/Themes">Drupal Themes</a> there is support for displaying the "Mission Statement" across all pages and in others this support is limited to the "Front Page" or "Main Page". 

If you are ever using one of the themes with limited mission statement support and want to display the mission statement across all pages you can use this to do so. 

In template.php add the following to the bottom of the file:

<code>function _phptemplate_variables($hook, $vars = array()) {
  // Make custom variables available to theme templates
  switch ($hook) {
    // Send new variable $custom_mission to page.tpl.php
    case 'page':
      $vars['custom_mission'] = variable_get('site_mission', '');
      break;
  }
  return $vars;
}
</code>

Then in page.tpl.php change:

<code><?php if ($mission) { ?><h3 id="mission"><?php print $mission ?></h3><?php } ?></code>
to be

<code><?php if ($custom_mission) { ?><h3 id="mission"><?php print $custom_mission ?></h3><?php } ?></code>


These 2 changes should allow the "Mission Statement" to be displayed across all pages.

