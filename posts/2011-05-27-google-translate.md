---
layout: post
status: publish
published: true
title: Google Shutting Down the Translate API
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
wordpress_id: 927
wordpress_url: http://derekville.net/?p=927
date: 2011-05-27 12:55:19.000000000 -07:00
categories:
- Technology
tags:
- Google
- JavaScript
- language
comments:
- id: 963
  author: Jonathan Griggs
  author_email: jonathan.griggs@gmail.com
  author_url: https://github.com/boatmeme
  date: '2011-05-28 09:00:42 -0700'
  date_gmt: '2011-05-28 16:00:42 -0700'
  content: Java developers who used the Google Translate API should check out my new
    wrapper for the Microsoft Translator API @ <a href="https://github.com/boatmeme/microsoft-translator-java-api"
    title="Microsoft Translator Java API" rel="nofollow">https://github.com/boatmeme/microsoft-translator-java-api</a>.
    It is a surprisingly adequate substitute for Google Translate.
---
When I have conversations with people about what excites me in technology today, I usually start with the fact that the Web is breaking down barriers in a way we've never experienced before.  It is simply amazing that anyone is free to publish anything they want whenever they want, and is it instantly available for global consumption.

<!--more-->

Today, [2 billion people are on the internet](http://www.bulawayo24.com/index-id-news-sc-international-byo-966-article-More+than+2+billion+people+use+the+internet.html).  That means nearly a third of the world's population has access to Wikipedia, Google, Yahoo, Twitter, Facebook, etc...  The Web has finally given us the chance to globally communicate.  The only thing restricting us at this point isn't a technical barrier, but instead is a language barrier. Linguists estimate there are between 5,000-6,000 currently spoken languages on the planet.  Yet, very few of us speak more than one or two of those.  More than ever we need free & accessible ways to easily translate between languages, allowing us to communicate with a global audience.

Since 2008, we've have that.  The [Google Translate API](https://code.google.com/apis/language/translate/overview.html).  It's an API (application programming interface) that allows you to programmatically send text to Google, and they will translate it for you, for free.  It's an amazingly useful service that I have in [one of my Twitter clients](http://tweenky.com) to instantly translate any tweets I can't read.

Sadly, yesterday they posted this message on the API's page.

> Important: The Google Translate API has been officially deprecated as of May 26, 2011. Due to the substantial economic burden caused by extensive abuse, the number of requests you may make per day will be limited and the API will be shut off completely on December 1, 2011. For website translations, we encourage you to use the Google Translate Element.</blockquote>

In other words... "This is why we don't have nice things"

Very disappointing, especially for a company who set out to "Organize the World's Information" a decade ago.  One would assume the goal of organizing is to make it accessible.  Guess not.

When Google implemented the [Speech Input API](http://www.w3.org/2005/Incubator/htmlspeech/2010/10/google-api-draft.html) in Chrome, my mind instantly blew up with ideas.  I loved knowing that we were so close to having an application for your mobile device that allows you to say something, and it will instantly start translating it into text of any language.

Here's an example of how easy it could be.

<pre>
&lt;html&gt;
    &lt;input type=&quot;text&quot; id=&quot;foo&quot; speech&gt;
    &lt;textarea id=&quot;translation&quot;&gt;&lt;/textarea&gt;
    &lt;script src=&quot;https://www.google.com/jsapi&quot;&gt;&lt;/script&gt;
    &lt;script type=&quot;text/javascript&quot;&gt;
        function translate() {
            google.load(&quot;language&quot;, &quot;1&quot;);
            google.setOnLoadCallback(function() {
                var native_text     = document.getElementById(&#039;foo&#039;).value;
                var native_language = &quot;en&quot;; //english
                var target_language = &quot;es&quot;; //spanish
                google.language.translate(native_text, target_language, native_language, function(result) {
                    document.getElementById(&quot;translation&quot;).innerHTML = result.translation;
                });
            });
        }
        document.getElementById(&quot;foo&quot;).addListener(&quot;change&quot;, translate);
    &lt;/script&gt;
&lt;/html&gt;
</pre>

You could solve a problem humans have had for thousands of years, in about 5 lines of JavaScript code.

Well, starting Dec 1st, 2011, you'll have to use another service.

There's no doubt in my mind we'll get this type of capability in the near future, I'm just disappointed Google decided it didn't want to be involved in solving these kinds of real, human problems.

Hopefully Google reconsiders this decision. To help, go post a comment on the [Google Code blog](http://googlecode.blogspot.com/2011/05/spring-cleaning-for-some-of-our-apis.html).
