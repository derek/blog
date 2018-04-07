---
layout: post
status: publish
published: true
title: Google launches Mobile AdSense
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
wordpress_id: 85
wordpress_url: http://blog.derekville.net/?p=85
date: 2007-10-11 11:57:29.000000000 -07:00
categories:
- Technology
tags: []
comments: []
---
In a logical step, Google has launched a mobile version of it's ad network AdSense so users can now visit sponsored links on sites they are browsing on their phone.  The original incarnation of AdSense uses JavaScript to embed ads in a page, which carries little security risks to the user and the server the page is hosted on.  However, because most mobile devices don't support JavaScript, they had to resort to using servers-side scripting languages (PHP, Perl, ASP, etc..) to embed ads prior to delivering the page to the user.  Here's an example of the PHP version of Mobile AdSense.

    <?php
    $GLOBALS['google']['ad_type']='text';
    $GLOBALS['google']['channel']='';
    $GLOBALS['google']['client']='pub-5039159613133207';
    $GLOBALS['google']['format']='mobile_single';
    $GLOBALS['google']['https']=$_SERVER['HTTPS'];
    $GLOBALS['google']['host']=$_SERVER['HTTP_HOST'];
    $GLOBALS['google']['ip']=$_SERVER['REMOTE_ADDR'];
    $GLOBALS['google']['markup']='xhtml';
    $GLOBALS['google']['output']='xhtml';
    $GLOBALS['google']['ref']=$_SERVER['HTTP_REFERER'];
    $GLOBALS['google']['url']=$_SERVER['HTTP_HOST'] . $_SERVER['REQUEST_URI'];
    $GLOBALS['google']['useragent']=$_SERVER['HTTP_USER_AGENT'];

    require('http://pagead2.googlesyndication.com/pagead/show_ads.php');
    ?>

While Google's motto is "Do No Evil" and I don't think they would ever do anything to harm a Mobile AdSense client's server, using server-side scripting languages presents a massive security hole on most servers.  Once I can execute that code on your serer, all bets are off.  One could access the database to gain customer information, redirect users to phishing sites, or even just reformat the hard drive just for the hell of it.  The best method for hacking a server running Mobile AdSense would be <a href="http://en.wikipedia.org/wiki/DNS_cache_poisoning" target="_blank">DNS Cache Poisoning</a>.

While I don't exactly have any solutions on a method to deliver dynamic ads from the AdSense network that doesn't use JavaScript or a server-side scripting language, I find their approach completely unacceptable from a security perspective and you will find a lot of objection in the enterprise community towards this method.
