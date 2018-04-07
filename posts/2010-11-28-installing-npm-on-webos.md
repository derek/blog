---
layout: post
status: publish
published: true
title: Installing npm on webOS 2.0
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
wordpress_id: 909
wordpress_url: http://derekville.net/?p=909
date: 2010-11-28 02:30:15.000000000 -08:00
categories:
- Web Development
tags:
- webos
- npm
- nodejs
comments: []
---
<img class="alignright" title="NPM + webOS" src="http://s89997654.onlinehome.us/screencaps/Photoshop-20101125-233609.jpg" alt="NPM + webOS" width="268" height="187" /> Now that webOS 2.0 ships with Node.js, one of the first things I tried to do when I got the webOS 2.0 SDK a while back was get <a href="http://npmjs.org/">npm</a> installed.  While successful, it took a little bit of work, so figured it was worth a post to help aid anyone else trying to get it installed.  For those that aren't familiar with npm, it is a package manager for Node.js (<strong>N</strong>ode <strong>P</strong>ackage <strong>M</strong>anager).  In short, it's a easiest way to get Node.js modules installed on your system.  It is Node's equivalent to Ruby's Gems, Ubuntu's APT, PHP's PEAR, and Perl's CPAN.  So instead of manually downloading libraries/modules, explicitly including them in your source code, and having to manually resolve dependency issues, you can just let npm handle that for you.  Now, installing a new module is as easy as typing <strong><code>npm install &lt;module&gt;</code></strong>.  The version of Node.js that webOS 2.0 ships with (at the moment) is v0.1.102, which is rather old.  The build scripts for the latest npm installer does not work with older versions of Node.js, so with trial and error, the most recent version I've been able to install on webOS 2.0 is npm v0.1.23.  Luckily it's pretty easy to install that specific version, so here's how you do it on your webOS device.

<!--more-->

<script src="https://gist.github.com/708091.js"></script>If you are looking for a list of packages, check out <a href="http://npm.mape.me/">http://npm.mape.me/</a>. Or, you can just type <strong><code>npm ls</code></strong>.  Are there any plans for npm to be included in webOS? HP/Palm engineers confirmed at the webOS Developer Day event a few weeks ago that there are no plans for npm to ship with webOS.  That's fine with me.  Modules should be included in the application package anyways.
