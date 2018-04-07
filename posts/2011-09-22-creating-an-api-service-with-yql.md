---
layout: post
status: publish
published: true
title: Creating an API Service with YQL
date: 2011-09-22 13:20:28.000000000 -07:00
categories:
- Web Development
tags:
- javascript
- yql
---
I spent a few days last week in New York City at Yahoo's <a href="http://developer.yahoo.com/blogs/ydn/posts/2011/09/yahoo-open-hack-all-stars-in-new-york-city/">Open Hack All-stars event</a>.  At this hack day, I was mentoring a team of 3 students from the University of Texas who set out to create a hack that allows you to control a media experience on your TV by using your iPad.

<!--more-->

For this hack, they needed to talk to search APIs from 4 different services (Youtube, Justin.tv, Flickr, Netflix), parse the results, and display a thumbnail for each item with a link to play/view it.  Traditionally, this would be a rather bulky iPad application where you'd have to include all the code and logic to communicate with the various JSON, XML, & ATOM service APIs, parse the results, combine them, and finally render the content.  Likely, the HTTP calls would be synchronous, which would certainly present some issues as you get to 5+ APIs and you have to wait for one response to return before making the next.

Alternatively, you could create an API service that will do all of this for you.  When that option was presented, I immediately realized YQL would be perfect for this task.  Why?<br />
<ul>
<li>It can communicate with any HTTP-based APIs, asyncronously, so your response time is always as fast as the slowest API you have to talk to</li>
<li>Use custom JavaScript to parse the results and form the return set</li>
<li>Reduces the number of requests your client makes to a single HTTP request</li>
</ul>

So, I strapped on the headphones and began coding.  A few hours later, <a href="http://derek.github.com/sandbox/hackallstars/mediasearch.xml">here's the result</a>.  It's YQL <a href="http://developer.yahoo.com/yql/guide/yql-opentables-chapter.html">datatable</a> that heavily uses the &lt;execute&gt; feature, which allows you to run arbitrary JavaScript.  Within &lt;execute&gt;, you get a simple library that allows you to do things like parse JSON, make HTTP calls, and create XML structures with <a href="http://en.wikipedia.org/wiki/ECMAScript_for_XML">E4X</a>.  The datatable code is pretty straight-forward really.  <em>Here's the service to talk to, the URLs to send the search query to, and the callback to parse each result set. Now go!</em>

The beauty of this YQL datatable is that you have now created a fully-functional high-performance API server without the need for a server of your own to run it on.  

Here's a JSFiddle of the script in action.  Click the play button to see the combined search results.

<iframe style="width: 100%; height: 300px" src="http://jsfiddle.net/9S3UK/embedded/"></iframe>

You can also toy around with the query in the YQL console <a href="http://y.ahoo.it/lDld8">here</a>.

If you are interested in learning more fun stuff you can do with YQL, here's another post, <a href="http://derek.io/blog/2010/how-to-secure-oauth-in-javascript/">How-to: Secure OAuth in JavaScript</a>
