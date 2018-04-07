---
layout: post
status: publish
published: true
title: The Reason RSS Cloud Can Work Now
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
wordpress_id: 515
wordpress_url: http://www.derekville.net/?p=515
date: 2009-09-08 23:23:23.000000000 -07:00
categories:
- Web Development
tags:
- rss
- twitter
- rsscloud
- cloud
- pubsubhubbub
- syndication
comments:
- id: 314
  author: Rogers Cadenhead
  author_email: nomail@cadenhead.org
  author_url: http://workbench.cadenhead.org/
  date: '2009-09-09 01:29:48 -0700'
  date_gmt: '2009-09-09 06:29:48 -0700'
  content: "Under your scenario, Ashton Kutcher will require five million cloud notification
    updates sent from cloud servers to RSS clients over XML-RPC, SOAP or REST. Each
    notification will prompt the client to request Kutcher's RSS feed again, so he'll
    serve it five million times. When all each client wants is the newest update.\r\n\r\nAs
    a general rule, it's a bad plan to create a technology that assumes a massive
    infrastructure will spring up to make its astonishing levels of resource consumption
    possible."
- id: 315
  author: Derek
  author_email: drgath@gmail.com
  author_url: http://
  date: '2009-09-09 01:41:10 -0700'
  date_gmt: '2009-09-09 06:41:10 -0700'
  content: "\"When all each client wants is the newest update.\"\r\n\r\nThe publishing
    server tells the client what URL to go to to grab the latest, so, serve up the
    last couple messages instead of the whole feed if that is necessary.  \r\n\r\nBesides,
    that example was given to show that the RSS Cloud system -isn't- designed for
    5 million pings to be sent out.  You are missing the \"Cloud\" element here (the
    aggregators, Google Reader, Feedburner, Twitter, etc...) and that the publishing
    server can decide who to syndicate content to in real-time if he or she wishes.
    \ In 2009, real-time syndication to millions could be an issue, but in 2015, it
    may be a piece of cake."
- id: 316
  author: mcdtracy
  author_email: mcdtracy@gmail.com
  author_url: http://bloganon.wordpress.com
  date: '2009-09-09 09:13:18 -0700'
  date_gmt: '2009-09-09 14:13:18 -0700'
  content: "Derek:\r\n\r\nIf the \"ping\" also carried the 140 character \"twit\"
    that could be cached in the cloud then RSS Cloud would address the issues if real-time
    and scalability.\r\n\r\nIn it's current form it's distributes the ping service
    and assumes a massive growth of RSS aggregators that are all coordinating well
    with the distributed/cloud ping service.\r\n\r\nAdding the twit to the ping would
    be a better optimization. The delta would go out into the cloud at the same time
    and elimiate duplication."
- id: 318
  author: Rogers Cadenhead
  author_email: nomail@cadenhead.org
  author_url: http://workbench.cadenhead.org/
  date: '2009-09-09 11:29:29 -0700'
  date_gmt: '2009-09-09 16:29:29 -0700'
  content: "\"The publishing server tells the client what URL to go to to grab the
    latest, so, serve up the last couple messages instead of the whole feed if that
    is necessary.\"\r\n\r\nThat's a good idea, but not one that's part of RSSCloud
    at this time. The more I look at PSHB, the more I like how it pushes the actual
    item to interested clients, as opposed to pushing a request to poll a feed."
- id: 319
  author: Derek
  author_email: drgath@gmail.com
  author_url: http://
  date: '2009-09-09 12:02:59 -0700'
  date_gmt: '2009-09-09 17:02:59 -0700'
  content: "Rogers: Am I not reading it right?  <a href=\"http://rsscloud.org/walkthrough.html#theAggregator\"
    rel=\"nofollow\">Implementor's guide to rssCloud: The Aggregator</a>.\r\n\r\n<blockquote>Your
    server will receive a single parameter, the URL of the feed that updated. On receipt
    of the message you should read the feed, and do what you normally do to locate
    and present new items to the user. The return value is ignored by the cloud.</blockquote>\r\n\r\nYou
    must tell the aggregator something in your POST, it can't just be a empty.  That
    \"something\" is the URL that was updated, and you can determine exactly how to
    present new info whether it is a 200 item feed or a 1 item feed.\r\n\r\n\"The
    more I look at PSHB, the more I like how it pushes the actual item to interested
    clients, as opposed to pushing a request to poll a feed.\"\r\n\r\nNow we're back
    to the greatest debate in syndication formats.... Atom vs. RSS (yes I know PSHB
    can hook into RSS).  Both are good protocols and I'm cool with whichever wins
    out.  To me though, the beauty of RSS Cloud is that it's so simple, and when it
    comes to decentralized systems, simplicity usually wins out.  While PSHB could
    potentially be more efficient, the only thing RSS Cloud changes in the RSS picture
    is that it decreases stale polls in return for teeny tiny POST notifications,
    which are cheap to begin with.\r\n\r\nWhen you talk about scaling a system like
    this to 10 million followers, it becomes an issue that has nothing to do with
    RSS Cloud and is a fundamental issue with notifying that many people, regardless
    of protocol."
- id: 320
  author: Nome
  author_email: None@example.com
  author_url: ''
  date: '2009-09-10 04:11:48 -0700'
  date_gmt: '2009-09-10 09:11:48 -0700'
  content: Appengine can't support rsscloud because of the stupid restriction that
    the subscription request must come from the same ip as the subscrption endpoint.
    That's not the case on appengine, nor in a lot of distributed applications
- id: 321
  author: 'pubsubhubub and rss-cloud : changing the way you read the web &laquo; Thoughts
    on technology and social web'
  author_email: ''
  author_url: http://cherukuri.wordpress.com/2009/09/07/pubsubhubub-and-rss-cloud-changing-the-way-you-read-the-web/
  date: '2009-09-10 12:29:42 -0700'
  date_gmt: '2009-09-10 17:29:42 -0700'
  content: '[...] Vs. PubSubHubbub: Why The Fat Pings Win  There&#8217;s a Reason
    RSSCloud Failed to Catch On The Reason RSS Cloud Can Work Now   Possibly related
    posts: (automatically generated)Real time roundup – Part 3 : Instant [...]'
- id: 328
  author: Wes Felter
  author_email: wesley@felter.org
  author_url: http://felter.org/wesley/
  date: '2009-09-16 22:18:02 -0700'
  date_gmt: '2009-09-17 03:18:03 -0700'
  content: It's interesting that you mention bandwidth, since PubSubHubbub uses less
    bandwidth than RSSCloud (especially if posts are little 140-character tweets where
    the overhead will be magnified).
- id: 397
  author: feeds, realtime, and stuff. a link dump. &laquo; turnings
  author_email: ''
  author_url: http://turnings.phrasewise.com/2009/10/21/feeds-realtime-and-stuff-a-link-dump/
  date: '2009-10-21 12:36:17 -0700'
  date_gmt: '2009-10-21 17:36:17 -0700'
  content: '[...] the-reason-rss-cloud-will-catch-on [...]'
---
<div style="text-align:center;"><img src="http://www.derekville.net/wp-content/uploads/2009/09/cloud.jpg" alt="cloud.jpg" border="0" width="506" height="275" /></div>

Rogers Cadenhead recently wrote a post "<a href="http://workbench.cadenhead.org/news/3555/theres-reason-rsscloud-failed-catch/0">The Reason RSS Cloud Failed to Catch On</a>".  In this he argues that RSS Cloud is not sustainable when it begins to scale to thousands of users needing to receive pings every time a post is made.  While he has a point, I believe his argument is much more accurate when put into the context of 1999 as opposed to 2009, and it is even more irrelevant a few years from now.  This points to one thing... <strong>RSS Cloud was ahead of its time</strong>.

Today, supporting RSS Cloud is cheap.  Bandwidth is a fraction of a percent now compared to what is was 10 years ago along with cloud based virtual servers available for ~$10 / month.  I'd suspect a properly tweaked VPS at the Rackspace Cloud or EC2 could handle millions of pings / day without issue.  Unlike PubSubHubBub, the content of the post is not delivered with RSS Cloud, it is just a body-less ping, so bandwidth isn't even an issue.  A server supporting these types of capabilities back in 1999 would have cost thousands of dollars per month.  Now?  Just a few bucks.  5 years from now I suspect it will be free (example: Google App Engine is currently free and could be configured for this service).

Let's go ahead and take into consideration the dream scenario with RSS Cloud, and that is that we have completely replaced Twitter.  In this scenario Ashton Kutcher will have 5 million followers and will need to notify each of those followers when he tweets out 100 mundane posts / day.  Let's not kid ourselves and <strong>not</strong> think there is a middle man in there somewhere.  These services are the "Cloud" portion of whole term.  Just like Feedburner and Google Reader are proxies between publisher and reader now (by storing local caches of RSS feeds), there will be many services that would be happy to host the feeds, providing a web client to the reader and analytics to the publisher in turn receiving all the statistics they chew on.  Proof?  Twitter purchased Summize (search.twitter.com) and Google bought FeedBurner because they saw the value of this type of service.  Afterall, the analytics portion of that is the whole business model that Twitter is rumored to be building.

But ok... let's assume those "Cloud" services never pop up because, hell... I don't see any reason why they wouldn't, but let's just imagine they don't exist.  Solution? TURN OFF THE NOTIFICATIONS!  That's the beauty of RSS Cloud feeds, it's completely backwards compatible with non-Cloud enabled feeds.  If the Cloud server fails to send out notifications, then their subscribers will simply revert back to the old method of routine polls looking for new content.  But, failing to notify your subscribers of new content in a sea of real-time has drastic consequences.  Even if you are the first to report information, you will always be "scooped" by others because the lag caused by your inability to notify your subscribers.  That alone will be enough to even the playing field.  As a compromise, you could get away with just notifying a few dozen RSS aggregators (Google, Yahoo, Feedburner) to take care of the majority of your subscribers, and those using readers you don't notify will revert to polls.

So as you can see, RSS Cloud is currently gaining traction because it wasn't until now that it was a viable service for the masses.  Even now there is very little support within the client portion of RSS Cloud, but I suspect that will be a battleground many will fight for in the next couple years.
