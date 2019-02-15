---
layout: post
title: 'Upgrading Wordpress'
date: 2006-11-01 18:28
comments: true
categories : []
---  

Well I finally got around to upgrading my wordpress installation from 2.0.1 to the latest greatest of 2.0.5. It was incredibly simple and here's a quick 5 step upgrade plan.

<strong>Step 1: </strong>Backup Database Tables and Files including .htaccess and wp-config.php
<font size="-6px">I used mysqldump to backup the tables and moved my .htaccess and wp-config.php files to a safe directory.</font>
<strong>Step 2: </strong>Deactivate Plugins
<font size="-6px">Go to your WP Admin panel and manually deactivate all your plugins.</font>
<strong>Step 3: </strong>Overwrite Files
<font size="-6px">Download and Unzip the latest version of Wordpress. The copy all the new files over to your current wordpress installation.</font>
<strong>Step 4: </strong>Run the upgrade script
<font size="-6px">Run the upgrade script that should now be located at your local wordpress install. www.yourserver.com/path/to/wordpress/wp-admin/upgrade.php</font>
<strong>Step 5: </strong>Reactivate Plugins one by one
<font size="-6px">Now all you have to do is reactivate your plugins and your upgrade should be complete.</font>


