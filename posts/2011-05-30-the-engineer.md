---
layout: post
status: publish
published: true
title: The Engineer
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
wordpress_id: 966
wordpress_url: http://derek.io/blog/?p=966
date: 2011-05-30 18:00:46.000000000 -07:00
categories:
- Career
tags:
- engineering
comments: []
---
According to <a href="http://en.wikipedia.org/wiki/Engineering">Wikipedia</a>, Engineering is...
<blockquote><em>"...the discipline, art and profession of acquiring and applying scientific, mathematical, economic, social, and practical knowledge to design and build structures, machines, devices, systems, materials and processes that safely realize solutions to the needs of society."</em></blockquote>

<!--more-->

This morning I was watching <a href="http://news.cnet.com/8301-13577_3-20023018-36.html">Carol Bartz's interview</a> at the Web 2.0 Summit, and John Battelle asked her the question about acquiring engineering talent in the software/web world. When he asked that question, I stopped what I was doing and focused on the conversation because it's important to me that our CEO understands what motivates us. If she doesn't "get" it, then the company has a serious problem. Here was her answer:

"<em>[Engineers] want a really interesting job to do, they want to have the tools to do it, they want to work on large data sets and large problems, and [Yahoo] has that.</em>"

Exactly what I wanted to here. And it's not just lip-service, there is really awesome stuff we're working on at the moment, things that haven't been done elsewhere, so it is clear she does get it.

Then, a theme began to emerge for the day. A friend that works in developer relations at HP/Palm tweeted...

<a id="more"></a><a id="more-966"></a>

<img title="@adora: One of my greatest pleasures in life is giving developers interesting problems to solve" src="http://s89997654.onlinehome.us/screencaps/skitched-20101116-223758.jpg" alt="" />

And that's what makes <a href="http://twitter.com/adora">Lisa</a> great at what she does, she understands developers very well. She knows what makes us tick.

I work with an engineer (<a href="http://twitter.com/danbeam">@danbeam</a>) is so compulsive with solving problems that sometimes just to mess with him I'll say "<em>I bet you can't figure this out</em>." I know that after 30 seconds of resisting, he has no choice but to drop everything and focus on solving it. Seriously, it works every time, it's pretty funny. We once spent hours battling back &amp; forth trying to generate the shortest shell script that will output every Friday the 13th. Why? Because it was Friday the 13th and we were curious. (Solution: <em>echo -e {$((2e5)).1}13\\n|date -f-|grep ^F</em>)

I am obviously not immune to it myself. Recently, a friend sent me a link to the <a href="http://seatgeek.com/blog/hiring/henceforth-all-job-applicants-must-hack-into-our-backend">SeatGeek applicant hacking challenge</a>, I had no choice but to drop what I was doing and "hack" into the system even though I'm happily employed. 15 minutes later, mission accomplished, back to work. It was fun for a few minutes, and I learned a couple things. (Tip: Try using nothing but cURL. Using a browser is cheating)

Solving these little problems is what keeps the engineer occupied. It is our form of entertainment. But if you are working with engineers, you don't want them to simply be entertained, you want them to be inspired. You want them so full of determination that they'll stop at nothing to figure out a solution. How do you do that? Give them something that isn't possible. That's like a mother telling her 13 year old son he can't do something. Oh yeah? Watch. (sorry mom!)

For instance, last year I wanted to figure out the best method to do OAuth using nothing but client-side JavaScript. It can't actually be impossible to do, can it? After a few weeks of hacking around, I came up with a solution and wrote a post about it, <a href="http://derek.io/blog/2010/how-to-secure-oauth-in-javascript/">How-to: Secure OAuth in JavaScript</a>. Yeah, it is using a proxy (YQL), but my code is all JS and I can host it anywhere. Close enough.

There was little practical reason for doing it, other than I just wondered how it could be done. There is a lot to learn by challenging yourself to do something you don't know how to do. The biggest lesson I learned from that project was to quit trying to coerce a library into doing something for you it wasn't intended to do. It's usually quicker to sack up, read the spec, and write a solution yourself. Me &amp; the <a href="http://oauth.net/core/1.0/">OAuth 1.0 spec</a> are like best buddies now.

Anyways, later on that same day, yet another relevant tweet rolled across my timeline...

<img title="@BeOurGuestMike: #nasatweetup shows me each and every day how important it is to share with my students the passion of doing the once " src="http://s89997654.onlinehome.us/screencaps/Twitter___%40Mike_Rahlmann__%23nasatweetup_shows_me_each_...-20101116-224559.jpg" alt="" />

That, is an excellent teacher. I'm a huge science nerd, and the NASA tweet reminded me of my favorite scene from Apollo 13. Yes, I'm so nerdy that the scene where the engineers save the day is my favorite. In it, the crippled Lunar Module is flying back to Earth when engineers determine that the astronauts may soon die of carbon dioxide poisoning unless they devise a solution.

Here's the clip...

<iframe src="http://www.youtube.com/embed/Z3csfLkMJT4" frameborder="0" width="560" height="349"></iframe>

Those are the moments the engineer lives for. Solving interesting problems keep us occupied. Solving impossible problems is why we’re engineers.
