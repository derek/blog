---
layout: post
status: publish
published: true
title: New Wordpress Theme
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
wordpress_id: 107
wordpress_url: http://blog.derekville.net/?p=107
date: 2007-10-20 02:19:04.000000000 -07:00
categories:
- Unsorted
tags: []
comments:
- id: 245
  author: Mary1440
  author_email: mary1440@gmail.com
  author_url: http://www.revealedreflections.com
  date: '2008-03-26 09:21:19 -0700'
  date_gmt: '2008-03-26 13:21:19 -0700'
  content: "Off Mahalo topic here, but like your new template. As I visit around the
    blogging neighborhood I can spot a WP user. Richer/sharper look to their templates....
    \r\n\r\nRe: your revisiting Mahalo, the open, willing to find positives as well,
    is the mark of a wide open mind. A rare thing in this day and age.  Kudos to you
    for that.\r\n\r\nSearch Auschwitz, Phantom of the Opera, Jane Eyre, Maya Angelou.
    Awesome work on these. Where else on the net can you find that kind of information
    on a given topic?  \r\n\r\nI think that techno-geeks often have tunnel vision
    and the fact that Jason could get out of his own techno-head and into this wider
    realm of the everyday user is amazing. \r\n\r\nYour input is valuable and appreciated,
    though.\r\nMary"
---
<p><a href="http://themes.wordpress.net/columns/3-columns/3639/snoods-10/" target="_blank"><img id="id" height="146" src="http://s.themes.wordpress.net/snapshots/3639-medium.jpg" width="195" align="right"/></a>I figured it was about time to upgrade to a new theme, so I found this one, <a href="http://themes.wordpress.net/columns/3-columns/3639/snoods-10/" target="_blank">Snoods theme</a>.&nbsp; Whaddya think?</p> <p>Because this theme doesn't accommodate the native tagging capability of Wordpress 2.3, I had to hack into the wp functions to add the capability to display tagging in the post.&nbsp; What Wordpress really just needs to do is append the tag info to the end of all posts, like I've done for this theme.&nbsp; </p> <p>If you need to do the same, update "the_content()" function in wp-includes/post-template.php to the following code (additions in yellow):</p> <blockquote> <p>function the_content($more_link_text = '(more...)', $stripteaser = 0, $more_file = '') { <br />&nbsp;&nbsp;&nbsp; $content = get_the_content($more_link_text, $stripteaser, $more_file); <br />&nbsp;&nbsp;&nbsp; $content = apply_filters('the_content', $content); <br />&nbsp;&nbsp;&nbsp; $content = str_replace(']]&gt;', ']]&amp;gt;', $content); <br />&nbsp;&nbsp;&nbsp; <span style="color: yellow">ob_start(); <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; the_tags('Tags: ', ', ', '&lt;br /&gt;'); <br />&nbsp;&nbsp;&nbsp; $tag_html .= ob_get_clean(); <br />&nbsp;&nbsp;&nbsp; if (!empty($tag_html)) <br />&nbsp;&nbsp;&nbsp; { <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $content .="&lt;br /&gt;&lt;div align='center' style='clear:both;'&gt;&lt;span style='border:solid #333333 1px; padding:3px;'&gt;"; <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $content .= $tag_html; <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $content .= "&lt;/span&gt;&lt;/div&gt;";; <br />&nbsp;&nbsp;&nbsp; } <br /></span>&nbsp;&nbsp;&nbsp; echo $content; <br />}</p></blockquote> <p>This really the first time I've dove into the innards of Wordpress, and wow is it rather horrid.&nbsp; Considering how important Wordpress is to the evolution of the blogging community, developers are important, and with the way the code looks now, I can't imagine anyone would take up Wordpress development as a hobby.</p>
