---
layout: post
status: publish
published: true
title: Enabling WordPress 2.3 Tagging in Windows Live Writer
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
wordpress_id: 110
wordpress_url: http://blog.derekville.net/?p=110
date: 2007-10-20 03:13:19.000000000 -07:00
categories:
- Unsorted
tags: []
comments: []
---
<p>Part of the reason for my recent increase in blogging is mostly due to my discovery of <a href="http://www.derekgathright.com/2007/10/09/first-post-from-windows-live-writer/" target="_blank">Windows Live Writer</a>, I absolutely love it.&nbsp; The only complaint I've had so far is that it doesn't support tagging for Wordpress 2.3, something recently introduced with the <a href="http://wordpress.org/development/2007/09/wordpress-23/" target="_blank">release of Wordpress 2.3</a>.&nbsp; I assumed I'd have to wait for an update from Microsoft to be able to use WP 2.3 tagging, but it turns out that isn't the case.&nbsp; Check out this post from Ruhani Rabin who provides a great tutorial on how to enable tags support in WLW for WordPress:  <ul> <li><a href="http://www.ruhanirabin.com/2007/09/29/wordpress-23-tag-support-for-windows-live-writer">Enabling Tag support in Windows live writer for Wordpress</a><a href="http://www.derekgathright.com/blog/wp-content/uploads/2007/10/wlw-wordpress-tags3.png"><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" height="196" alt="wlw-wordpress-tags" src="http://www.derekgathright.com/blog/wp-content/uploads/2007/10/wlw-wordpress-tags-thumb3.png" width="240" align="right" border="0"/></a></li></ul> </p><p>In a nutshell all you have to do is download the wlwmanifest.xml file and upload it to wp-includes.&nbsp; This file is what tells WLW a bit more about the blog and it's capabilities.&nbsp; Once that is uploaded, update the blog in WLW (Weblog &gt; Manage Weblog) and viola, the "keywords" box shows up in the advanced options menu below your post in WLW.</p>
