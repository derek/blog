---
title: Why YUI's Philosophy is Better
date: 2010-10-21
---

I was digging through some old email today and came across a post I made to jquery-en@googlegroups.com back in 2007.

> _On a side note, as I mentioned, I'm new to jQuery. In fact, my jQuery expertise goes back a full 24 hours. The website I'm coding now did use prototype and scriptaculous, but once I looked at the 1.2 version of jQuery, I knew I'd found a better solution (for me, anyways). So I spent the rest of the day recoding the site for jQuery. It was this post that convinced me I needed to change, "[Why jQuery’s Philosophy is Better](http://blog.jquery.com/2006/08/20/why-jquerys-philosophy-is-better/)"_

In the post, Yehuda Katz compares a relatively young jQuery to Prototype.js.  Rewinding back to 2007, I was a Prototype user and it was apparently that post that sold me on jQuery being a better library.  For the next 2 years I was a (mostly) happy jQuery user.

<!-- more -->

When I [started at Yahoo](http://derek.io/blog/2009/im-a-yahoo/), that was the beginning of my journey into the world of YUI. I was excited to learn something new, and pretty quickly learned to love the library because there is so much that it does right. Sure there's a little big of a learning curve compared to jQuery, but if you [know](http://www.jsrosettastone.com/) [where](http://yuilibrary.com/yui/docs/guides/) [to](http://yuilibrary.com/forum/) [look](http://yuitheater.com/) [for](http://twitter.com/yuilibrary) [help](http://webchat.freenode.net/?channels=yui), you can easily get answers to whatever questions you have. YUI has a full-time staff, and part of the team's job is to help you with whatever issues/questions you have about the library.

Before I get started, I at least wanted to clarify something. I'm not going to make an argument that as a whole, one library is "better" than the other, they're both good. The title of this post is mostly just an homage to Yehuda's post that inspired me almost 5 years ago. On the first day of my "Introduction to Programming: QBASIC" course in high school, I vividly remember my teacher telling me "_In programming, there are a hundred ways to solve every problem. Pick the one that is best for you._" That is especially true when it comes to JavaScript libraries.

YUI and jQuery do share some similar functionality, but they approach the problem from a completely different perspective. jQuery is about simplicity and usability. YUI is about performance and scalability. Neither ignores those other qualities, they just take a backseat to the primary goal of the library.

So here we go, my list of things I like about YUI compared to jQuery. Unlike Yehuda's post, I'm not going to focus much on specific API differences, because those can be sugared up as much as you like. Besides, just take a look at [JSRosettaStone.com](http://www.jsrosettastone.com/) and you'll see that many of the APIs are very similar, if not identical.

What I will instead focus on are fundamental differences between the libraries and why I think YUI is the best JS library out there for building web pages and modern web applications.

## Modules

The biggest difference between the libraries is the organization of the code. While most other programming languages natively support packages & modules, JavaScript won't see [those](http://wiki.ecmascript.org/doku.php?id=harmony:modules) widely adopted in a browser for many more years. So it was left up to the developer community to create our own [module pattern](http://www.yuiblog.com/blog/2007/06/12/module-pattern/).

Modules are little bits of code that serve a limited purpose and can be combined and swapped out as you see fit within your application. In one of his YUIConf talks on "[Scalable JavaScript Application Architecture](http://yuilibrary.com/theater/nicholas-zakas/zakas-architecture/)", Nicholas Zakas compared this to [space station modules](http://images.wikia.com/astronomy/images/c/c1/ISSComponents2.jpg), which I think is rather accurate. In order to get a space station in outer space, you don't construct it on the ground and launch the entire thing all at once. You build it as many separate, smaller modules, launch them up, and construct it in space. You only use what you need, when you need it.

You should take the same approach when constructing your web application. Break it up into as many small bits as possible and only include exactly what you need. In doing so, you will save on download and execution time, and it will be much less cluttered. It's just good design, and as long as you know what you are doing, there's no limit to how small you should break up your code into modules. You can even go as far as 1 function per file. The topic of "ultra-modularization" once [came up](http://groups.google.com/group/requirejs/browse_thread/thread/a9587d4abb108869) on the RequireJS mailing list.

Within jQuery, you are basically including 1 super-module, jQuery itself.  There's no (good) way to just pull jQuery's Ajax component if that is all you need.  Too much of it is inter-dependent.  This design of course led to jQuery's simplicity, at the risk of flexibility.  A good trade given its goal of ease-of-use.

Within YUI, all the functionality you include comes from various modules. In YUI's core set, there are 300+ modules. Things like "Calendar", "DD" (drag and drop), "Graphics", etc… In the [YUI Gallery](http://yuilibrary.com/gallery/) (community contributed modules) contains even more than that! 431 at the time of this writing, and continually growing.

To use any of these modules, just include them in your `YUI().use()` statement.

If you don't include any modules, by simply executing `YUI().use( function(Y){ } )`, you only start with a few core ones. Specifically: [DOM](http://yuilibrary.com/yui/docs/api/modules/dom.html), [Event](http://yuilibrary.com/yui/docs/api/modules/event.html), [Node](http://yuilibrary.com/yui/docs/api/modules/node.html), and [OOP](http://yuilibrary.com/yui/docs/api/modules/oop.html) (Object Oriented Programming).

To use anything else you need, it's simply

    YUI().use("someModule", "anotherModule", function(Y) {
	    // Do something
    });

And to make things really easy, all your dependencies will be calculated and included for you.

In jQuery, you don't really have a native concept of modules, so the library is all or nothing.  Sure the jQuery is relatively small (32k gzipped), but that doesn't make up for the fact that you are always going to be downloading and executing more than you need. Few people use -all- of jQuery on every page.

Now, one of the problems you can run into if you break up your application into dozens of separate files is that you'll execute dozens of HTTP requests to include all those via `<script>` tags. Well, here comes the concept of combo-loading.

## CDN Combo-loading

All YUI modules, whether they are YUI Core or YUI Gallery (community contributed) modules are by default loaded from the Yahoo CDN, all as a single request.  This is an amazing feature.  Sure you get URLs that look like:

    http://yui.yahooapis.com/combo?3.4.1/build/oop/oop-min.js&amp;3.4.1/build/event-custom-base/event-custom-base-min.js&amp;3.4.1/build/dom-core/dom-core-min.js&amp;3.4.1/build/dom-base/dom-base-min.js&amp;3.4.1/build/selector-native/selector-native-min.js&amp;3.4.1/build/selector/selector-min.js&amp;3.4.1/build/node-core/node-core-min.js&amp;3.4.1/build/node-base/node-base-min.js&amp;3.4.1/build/event-base/event-base-min.js&amp;3.4.1/build/event-custom-complex/event-custom-complex-min.js&amp;3.4.1/build/event-synthetic/event-synthetic-min.js&amp;3.4.1/build/event-mouseenter/event-mouseenter-min.js&amp;3.4.1/build/event-hover/event-hover-min.js&amp;3.4.1/build/event-delegate/event-delegate-min.js&amp;3.4.1/build/node-event-delegate/node-event-delegate-min.js&amp;3.4.1/build/intl/intl-min.js&amp;3.4.1/build/array-extras/array-extras-min.js&amp;3.4.1/build/attribute-base/attribute-base-min.js&amp;3.4.1/build/attribute-complex/attribute-complex-min.js&amp;3.4.1/build/base-base/base-base-min.js&amp;3.4.1/build/base-build/base-build-min.js&amp;3.4.1/build/escape/escape-min.js

But who cares? You aren't the one constructing it, YUI's loader does it for you.  The loader even takes into account URL size limits and properly chunks it up into multiple requests if need be.

In jQuery, you are typically either hosting the jQuery.min.js file yourself, or pulling it from a CDN somewhere. You then also typically host the plugins yourself. Also, if you want to minify and concatenate your JS & CSS for optimal performance, you have to do that yourself by using something like [YUI Compressor](http://developer.yahoo.com/yui/compressor/) as part of a build process.

Why not just let Yahoo do all of that for you? Use the exact same process, the same CDN, and the same files that Yahoo properties use themselves. You can build entire applications hosting nothing more than a single HTML file yourself because everything you need is hosted on Yahoo's CDN.  And as a bonus, due to it being served off Yahoo's CDN, you are guaranteed uptime equivalent to Yahoo.

## Loader
My favorite part of YUI is the Loader component. This is the utility that you use to dynamically include whatever JS and CSS you need in the most optimal method possible. Gone are the days of loading in every js script and css stylesheet that you need using HTML tags. Take a look at the new Delicious `<head>` tag since they moved from YUI to jQuery. It's a pretty typical jQuery page.

```
<head>
  <link rel="stylesheet" type="text/css" media="screen" href="/static/css/del-new.css?v=307" />
  <link rel="stylesheet" type="text/css" media="screen" href="/static/css/flick/jquery-ui-1.8.13.custom.css?v=307" />
  <link rel="stylesheet" type="text/css" media="screen" href="/static/css/jcrop/jquery.Jcrop.css" />
  <link rel="stylesheet" type="text/css" media="screen" href="/static/css/960grid.css" />
  <link rel="stylesheet" type="text/css" media="screen" href="/static/css/selectbox/selectbox.css" />
  <script type="text/javascript" src="/static/js/jquery-1.6.1.min.js"></script>
  <script type="text/javascript" src="/static/js/jquery-ui-1.8.13.custom.min.js"></script>
  <script type="text/javascript" src="/static/js/jquery.json-2.2.min.js"></script>
  <script type="text/javascript" src="/static/js/jquery-hoverintent.js"></script>
  <script type="text/javascript" src="/static/js/jquery.Jcrop.min.js"></script>
  <script type="text/javascript" src="/static/js/jquery.metadata.min.js"></script>
  <script type="text/javascript" src="/static/js/jquery.swapimage.min.js"></script>
  <script type="text/javascript" src="/static/js/jquery.selectBox.min.js"></script>
  <script type="text/javascript" src="/static/js/tiny_mce/jquery.tinymce.js"></script>
  <script type="text/javascript" src="/static/js/jcarousellite_1.0.1.min.js"></script>
  <script type="text/javascript" src="/static/js/del.js?v=307"></script>
</head>
```

11 scripts + and 5 stylesheets = 15 HTTP requests.  And because they placed it all in the `<head>`, all 15 files need to be downloaded prior to the page being rendered.  Yeesh.

So let's look at a small YUI app

```
<html>
  <head>
    <!-- Include the YUI seed -->
    <script src="http://yui.yahooapis.com/3.5.1/build/yui/yui-min.js"></script>
  </head>
  <body>
    <script>
      YUI().use("json", "graphics", "calendar", "yql", function(Y){
        // Do something magical
      });
    </script>
  </body>
  <html>
```

The combination of those 4 modules and all the dependencies those require, actually loads in 49 modules.  Again, this is all done for you!  YUI's loader is very mature and is used on some of the largest Yahoo and non-Yahoo websites on the internet.

One of the great things about the YUI Loader is that you can even use it to include non-YUI modules.  Here's a jsFiddle to demonstrate using it to include jQuery, a jQuery plugin, a CSS stylesheet, and combining it with some YUI modules. (hint: click the Play button)

<iframe style="width: 100%; height: 400px" src="http://jsfiddle.net/derek/sfcsE/embedded/"></iframe>

## Environment Agnostic

There is no "YUI for Mobile" or "YUI for Node.js".  Why? Because YUI is a JavaScript library and does not assume it is running in any specific environment.  This has allowed the project to be nimble and flexible.  This also allows you to reuse code you've already written for one environment in other places.

If server + client-side JavaScript is something that seems useful, then YUI can be a great solution. Here's an <a href="http://express.davglass.com/">example site</a> that Dav created to demonstrate the power of using YUI and ExpressJS to use standard YUI widgets to pre-render the HTML markup on the server instead of the browser. The advantage here is that you can get JavaScript-like behavior, without needing JavaScript enabled, and using all the same code.

YUI is continually getting even easier to use inside Node.js. Dav Glass is the owner of the Loader component (previously mentioned), and he's done some amazing stuff to get YUI to "just work" inside Node.js. Here's <a href="http://www.youtube.com/watch?v=vQC3gsz6YXY">a recent video</a> of some work he's done to make YUI even easier to use on the server. Yahoo uses YUI, in Node.js, on some of our largest sites, and it's largely due to YUI being an awesome all-around JavaScript library. YUI is not just a DOM manipulation library, like jQuery.

YUI has spent, and will continue to spend considerable resources to ensure it runs just as good server-side as well as in the browser.  There are some announcements coming within the next few months that will make it very apparent that Yahoo's web-serving platform of the future is JavaScript, and YUI is a big part of that.

How does YUI work so well across all environments?  We target the lowest levels possible, and build up from there.

## Lower-level

I've never been a fan of rigid frameworks. I toyed with Rails, and Django, and CakePHP, and CodeIgnitor, and was never really happy, so I eventually ended up rolling [my own PHP framework](https://github.com/derek/Daffy). Very simple, and possibly only appeals to me, but it's exactly what I need to get started. Nothing more. Customizing someone else's framework is typically more trouble than it is worth. Heck, that's one of the reasons why I have never spent much time documenting or making Derek's Anti-Framework Framework more friendly, because I don't really want others to use it. That defeats the purpose of why I made it.

jQuery certainly isn't as rigid as most frameworks. It's much more of a library after-all.  Still, my feelings are the same, freedom is more important to me than being told how to do something.  For that, I appreciate that YUI is a little lower-level than jQuery.  jQuery and many plugins for it ignores edge cases, and they can get away with it because their target is the 90% use-case.  Well, YUI's target is the 99%.  YUI needs to accommodate all the various use-cases and customizations requirements needed for use on Yahoo websites.  This is a strength of the project as it means it will be as robust and thought-out as possible.

YUI works along-side Yahoo projects to develop components for the library. For example, the new Y! Mail uses the exact same base rich text editor that is available as the [Editor module](http://yuilibrary.com/yui/docs/api/modules/editor.html). At first glance, you aren't going to see a fancy editor with 80 buttons that does everything under the sun (and usually poorly). You are going to see a solid foundation for which to build an editor on top of. For customization, building up is usually easier and more maintainable than hacking something apart and cramming in your functionality.

In jQuery-land, if you need an editor, you are likely going to search around for "jQuery rich text editor" and come across an article like "[12 JQuery Based Rich Text Editor](http://superdit.com/2011/05/21/12-jquery-based-rich-text-editor/)" (sic) and play around with each of them, figure out which one works best for you, integrate, then launch it. Then 3 months in, your boss comes to you and asks for a new feature to be added to the editor. So you crack open the plugin code and start hacking around. Maybe you hack it in there, but more often, you give up digging through the convoluted mess of code that you didn't write, and go back to searching for a new editor that does what you need. Repeat this process every 3-6 months. I know, because I've been in that exact situation. Eventually you might go with something like [TinyMCE](http://www.tinymce.com/) because it supports the kitchen sink, but isn't even jQuery-based (oh sure, [there's a plugin for that](http://www.tinymce.com/tryit/jquery_plugin.php)). So you are now duplicating all this code you are making your users download. Multiply that times an RTE, a date-picker, an uploader, a carousel, a lightbox, and you eventually end up with something like the Delicious <head> code I pasted above.

## Conclusion

As I mentioned above, I'm not claiming that YUI is definitively better than jQuery, or any other library/framework. They each solve the problem of web development  differently.  What I will say is that if you give YUI enough time to get over an admittedly steeper learning curve, you'll be on a fantastic track to build highly performant, scalable, web applications. C'mon, we are programmers, developers, front-end engineers.  We should strive to be more than cut, paste, then glue-together artists.  Let's build stuff!
