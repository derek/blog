---
layout: post
status: publish
published: true
title: Using Git on 1&1 (or any 'shared') hosting
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
wordpress_id: 331
wordpress_url: http://www.derekville.net/2009/01/10/using-git-on-11-or-any-shared-hosting/
date: 2009-01-10 01:05:19.000000000 -08:00
categories:
- Web Development
tags:
- linux
- git
comments:
- id: 392
  author: Mick
  author_email: info@lerlop.com
  author_url: http://lerlop.com
  date: '2009-10-13 18:55:23 -0700'
  date_gmt: '2009-10-13 23:55:23 -0700'
  content: Thanks for the tip. Probably worth mentioning that on some systems it could
    .bash_profile.
- id: 398
  author: Adam
  author_email: ae@adameberlin.com
  author_url: http://www.adameberlin.com
  date: '2009-10-23 10:35:42 -0700'
  date_gmt: '2009-10-23 15:35:42 -0700'
  content: You can also use ./configure --prefix=/kunden/homepages/.../htdocs/bin/git,
    then make &amp;&amp; make install.
- id: 440
  author: Using Git on 1&amp;1 (or any &#39;shared&#39;) hosting - Derek Gathright
    &laquo; Hotwebhostreviews.com
  author_email: ''
  author_url: http://hotwebhostreviews.com/?p=5505
  date: '2009-12-05 14:00:58 -0800'
  date_gmt: '2009-12-05 19:00:58 -0800'
  content: '[...] Link: Using Git on 1&amp;1 (or any &#39;shared&#39;) hosting - Derek
    Gathright [...]'
- id: 1048
  author: Matthias
  author_email: derek.io@matthias.hullin.net
  author_url: ''
  date: '2011-12-18 17:16:56 -0800'
  date_gmt: '2011-12-19 00:16:56 -0800'
  content: Does this allow for http(s) remote access?
- id: 1049
  author: Woody
  author_email: woody@near2.org
  author_url: http://blog.woodylabs.com
  date: '2012-01-16 08:48:45 -0800'
  date_gmt: '2012-01-16 15:48:45 -0800'
  content: "Hi Derek,\r\n\r\nI happened across this post of yours RE getting GIT to
    work on 1and1 as I was trying to make it work for me, using another helpful tutorial
    I managed to get it to work another way (as 1and1 now have it already installed.)\r\n\r\nI
    wrote a guide for people to get a GIT repository up and working on 1and1 here:\r\nhttp://blog.woodylabs.com/2012/01/1and1-web-hosting-git-installing-it-for-singular-dev/\r\n\r\n...this
    way has the added benefit of keeping a \"live\" web root updated which means no
    more manual file uploading :D\r\n\r\nCheers\r\n\r\nWoody"
---
Here's another "How-to" with 1and1 hosting, and this time I want to get the source code control/versioning program "Git" installed on my shared host with 1&amp;1.  This was actually remarkably easy.
<ol>
	<li> Go download Git from http://git-scm.com/download.  At the time of this posting, the latest version can be found at http://kernel.org/pub/software/scm/git/git-1.6.1.tar.gz</li>
	<li>SSH into your 1&amp;1 account</li>
	<li>"wget http://kernel.org/pub/software/scm/git/git-1.6.1.tar.gz", and that will download the package</li>
	<li>"tar -xvzf git-1.6.1.tar.gz" which will decompress the gzip file into a subdirectory</li>
	<li>"cd git*" to change into the subdirctory</li>
	<li>"make" to begin compiling the source.  You won't be able to do "make install" because you likely won't have permission to install anything to the system.</li>
	<li>Now Git is ready to rock with the exception of needing to add it to your $PATH.  This can be done by typing "echo 'PATH=$PATH:~/git-1.6.1/' &gt; ~/.profile"</li>
</ol>
Done!
