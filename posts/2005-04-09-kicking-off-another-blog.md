---
layout: post
status: publish
published: true
title: Kicking Off Another Blog
author: Derek
author_email: drgath@gmail.com
author_url: http://derek.io
date: 2005-04-09 13:54:48.000000000 -07:00
categories:
tags:
- blogging
- web
- ajax
- google
- microsoft
- wordpress
- java
- javascript
- flash
---
Going on a 5th incarnation of my personal blog, I think I might actually stick with this one as opposed to the others that I've tried.  I tried [PHP-Nuke](https://www.phpnuke.org/), but didn't have use for 99% of their capabilities.  Plus, I don't need a whole CMS for a simple blog.  As a PHP developer, I tried writing my own, but seemed like too much effort for something I didn't even know if I'd end up using.  Then, I went against my programmer roots and went with *gasp*... a hosted blog.  But as I assumed, the lack of control killed it for me.  Since I have plenty of experience managing my own Windows and Linux servers, going with someone else to host my blog just wasn't going to fly.  So here we are, I just discovered [WordPress](https://wordpress.org/) and am fairly happy with it so far.  Installation was a breeze and the interface is great, so it's easy to understand why this is becoming one of the more popular blog platforms out there.
<!-- more -->
Anyways, enough about nothing, let's get into the fun stuff. What led me to Wordpress was [this blog](http://www.gabrielserafini.com/archives/category/ajax/), which I came across doing research on [SAJAX](http://www.modernmethod.com/sajax/) and [JPSpan](http://jpspan.sourceforge.net/wiki/doku.php).  Why SAJAX and JPSpan?  Ever since I first saw [GMail](http://gmail.google.com) and [Google Maps](http://maps.google.com), the idea of using a single web page as an application intrigued me.  You can only make so many HTML forms and PHP scripts before you become a bit disgusted with the clunky nature of the Post->Process->Respond->Reload model that typically intertwines multiple languages, leaving complex and convoluted code for rather simple tasks.  Sure part of it might be my programming style, but the inherent nature of the whole system is also a big problem.  There must be a better way to do all this, right? More importantly, people are getting tired of the surfing the internet in the same way they did 10 years ago, the only thing that has drastically changed is the content.  But we are still stuck in the the following pattern...

    Client: Send the server a request;
    Server: Respond to client with HTML page;
    Server: Close connection;

    Client: Re-establish connection with Server, send another request;
    Server: Respond to client with HTML page;
    Server: Close connection;

Repeat...

It is a dated process that needs to be replaced by something that behaves more like a true application.  Luckily we are starting to get glimpse of the web's future with some new concepts and approaches to developing web sites.  For example, check out [XUL-Amazon](http://www.faser.net/mab/chrome/content/mab.xul), an Amazon application written in [XUL](https://developer.mozilla.org/en-US/docs/XUL). *Yes, you need to use Firefox because IE doesn't have XUL support*.  Also, check out what [it looks like](http://homepage.mac.com/ctholland/blog_assets/faser.net.amazon.xul.pdf) on OSX, a real application!  In addition to XUL, I wouldn't be surprised if Microsoft has a few things up its sleeve in the upcoming "[Longhorn](http://msdn.microsoft.com/Longhorn/productinfo/conceptvid/default.aspx)" release of Windows to improve the web experience.

So now you might be asking an obvious question, "But where's Java and Flash in all this?" Isn't this whole client-server interaction on a universal platform what those are all about? Well, if they really were the solution, would we even be having this discussing right now?

So I'd encourage you to put on your thinking cap and ponder these new tools, technologies, and concepts.  There isn't one clear vision at this point, and each has their downside. XUL has potential, but IE probably won't ever support it. AJAX is a technology some developers have fallen in love with, but then others think it's just the latest Google fad and will disappear.  Application frameworks like JPSpan and SAJAX show promise, yet they approach developing web applications *very* differently.  Microsoft's "[Avalon](http://msdn.microsoft.com/en-us/magazine/cc188739.aspx)" (paired with .NET) should be able to solve this problem, but only for Windows PCs.

To conclude... I think it's safe to say it will be tough to predict exactly how things will play out and the tools we'll be using years from now, but I'm sure it will be a fun ride.
