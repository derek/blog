---
layout: post
status: publish
published: true
title: Secure OAuth in JavaScript
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
excerpt: "Wouldn't it be awesome if we could use OAuth in JavaScript-only apps? JS
  is a powerful, expressive programming language, and the browser engines are getting
  <a title=\"arewefastyet.com\" href=\"http://arewefastyet.com/\">faster and faster
  all the time</a>. Why not use JavaScript to conduct your API calls and parse your
  data? In many cases, it is unnecessary to maintain a server-side proxy if all it
  is doing is making API calls for you and hiding your OAuth keys.\r\n\r\nThink about
  this... If you don't need any server-side processing, your applications suddenly
  become infinitely scaleable, right? We could host on the cheapest of cheap commodity
  hosting. Heck, if all we're doing is serving static HTML/CSS/JS files, just throw
  it on a CDN like S3 or CloudFiles and pay per GB.\r\n\r\nBefore you get too excited,
  realize that there is a fundamental problem with OAuth in JS. Because JavaScript
  in the browser is \"view-source\", you are always forced to expose your consumer
  key pair, which compromises the security of your application. *sigh*\r\n\r\nFor
  example, when Twitter recently deprecated their Basic Auth services, that left OAuth
  as the only authentication method. It was supposed to be <a title=\"OAuth-only Twitter:
  What it Means for JavaScript Apps\" href=\"http://blog.programmableweb.com/2010/08/31/oauth-only-twitter-what-it-means-for-javascript-apps/\">the
  death of JS-only Twitter apps</a>. This was unfortunate for quite a few developers
  who leveraged the browsers ability to do Basic auth, to help with scaling their
  Twitter apps. I know, I was one of them.\r\n\r\nSo then I began to think what if
  you weren't forced to expose your keys? What if your JS app could talk to any web
  API out there, in a secure, user-authenticated way?\r\n\r\nIs that actually possible?
  Yup.\r\n\r\n<strong>"
wordpress_id: 780
wordpress_url: http://www.derekville.net/?p=780
date: 2010-10-21 01:33:51.000000000 -07:00
categories:
- Unsorted
tags: []
comments:
- id: 857
  author: Kent Brewster
  author_email: kent_brewster@yahoo.com
  author_url: http://kentbrewster.com
  date: '2010-10-23 15:19:03 -0700'
  date_gmt: '2010-10-23 20:19:03 -0700'
  content: 'Nicely done, Derek; please see if they''ll link to this from the YQL/YDN
    blog. One tiny quibble: I''m much more likely to try out a GitHub-hosted example
    that does not ask for write permissions to my Twitter stream.'
- id: 858
  author: Eugene
  author_email: webby2@gmail.com
  author_url: ''
  date: '2010-10-24 23:56:33 -0700'
  date_gmt: '2010-10-25 04:56:33 -0700'
  content: "Holy Crap.\r\nAll that's left is a way to pay Yahoo for higher rate limits."
- id: 859
  author: Derek
  author_email: drgath@gmail.com
  author_url: ''
  date: '2010-10-25 00:45:43 -0700'
  date_gmt: '2010-10-25 05:45:43 -0700'
  content: "Kent, thanks.  Will keep you suggestion in mind for future hacks. Good
    point.\r\n\r\nEugene, YQL's current rate limit is 100k calls per day (if you call
    w/ your access keys).  If you expect you need to go over that, try sending an
    email to yql-questions@yahoo-inc.com.  More info @ http://developer.yahoo.com/yql/guide/usage_info_limits.html"
- id: 860
  author: Eugene
  author_email: webby2@gmail.com
  author_url: ''
  date: '2010-10-25 01:10:26 -0700'
  date_gmt: '2010-10-25 06:10:26 -0700'
  content: "Derek, I'm not at the rate limit yet but the trajectory is there. I certainly
    intend to send that email soon.\r\n\r\nBUT, I'd feel much better not being an
    edge case but part of a growing pool of customers who provide a recurring revenue
    source for Yahoo. Amazon has stuff in this vain like Amazon SimpleDB, which if
    I were inclined to use I could do without worrying that it might go away (or terms
    changed) tomorrow."
- id: 867
  author: Markandey Singh
  author_email: mark.dawn@gmail.com
  author_url: http://markandey.com
  date: '2010-10-26 14:16:32 -0700'
  date_gmt: '2010-10-26 19:16:32 -0700'
  content: AWESOME !!!!! U really solved it !!
- id: 870
  author: Kyle Simpson
  author_email: getify@gmail.com
  author_url: http://blog.getify.com
  date: '2010-10-28 10:09:56 -0700'
  date_gmt: '2010-10-28 15:09:56 -0700'
  content: "Well written article, and cool stuff.\r\n\r\nBut I must protest, this
    is NOT pure JS solution to secure OAuth. YQL has a huge server-side backend, and
    you've just shifted the burden from your backend to their backend. It's the shell-game
    approach.\r\n\r\nThe other thing is (ironically), if you want to use YQL with
    higher rate limits (and not be in some special exception) you have to use....
    you guessed it, OAuth to sign your YQL queries. Chicken-and-the-egg...\r\n\r\nThat
    having been pointed out, YQL is awesome and I'm glad you wrote this great article
    about how to use it in this way."
- id: 871
  author: Drew LeSueur
  author_email: drewalex@gmail.com
  author_url: http://twitter.com/drewlesueur
  date: '2010-10-28 10:42:39 -0700'
  date_gmt: '2010-10-28 15:42:39 -0700'
  content: OAuth 2.0 has a "User-Agent" profile that addresses OAuth in pure client-site
    JavaScript.
- id: 872
  author: Ryan Kennedy
  author_email: ryan.kennedy@yahoo.com
  author_url: http://unclehulka.com/ryan/
  date: '2010-10-28 11:26:35 -0700'
  date_gmt: '2010-10-28 16:26:35 -0700'
  content: "Derek…if you fancy another solution to this problem, dig around internally
    for \"Fulcrum\". I built it while I was still in Y!OS specifically to solve this
    problem. It started life as Yahoo! Connect (not the current Yahoo! Connect, more
    of a direct Facebook Connect competitor) and ended up morphing into OAuth Connect…a
    way to securely talk to OAuth 1.0/1.0a protected resources from the client. It
    protects against the final holes in your implementation…namely the ability to
    authorize users with your consumer key and secret.\r\n\r\nThe code is in source
    control…I forget if it went into CVS or SVN. I can't remember if I ever wrote
    a twiki document for it or not, either."
- id: 873
  author: Matas Petrikas
  author_email: matas@soundcloud.com
  author_url: http://soundcloud.com/matas
  date: '2010-10-28 11:35:45 -0700'
  date_gmt: '2010-10-28 16:35:45 -0700'
  content: "@Drew:  the OAuth 2.0 'User-Agent' flow works super. The only thing you
    have to keep in mind that this case the authorization expires in one hour (less
    or more depending on the implementation) It's nice for the some immediate interaction,
    but not something you'd like to build e.g. a Twitter client, where a persistant
    authorization is needed.\r\n\r\nwe are using the flow in our JS API wrapper, you
    can check out the code on GitHub:\r\nhttp://github.com/soundcloud/SoundCloud-API-jQuery-plugin"
- id: 875
  author: Felix
  author_email: felixboehm55@googlemail.com
  author_url: http://www.feedic.com/
  date: '2010-10-28 17:26:04 -0700'
  date_gmt: '2010-10-28 22:26:04 -0700'
  content: "I already implemented a similar script a couple of weeks ago, I just got
    no project for it (for now). Some thoughts I had when reading your implementation:\r\n\r\n-YQL
    rate limits depend on IP adresses, so when a user accesses your script, it wouldn't
    lower any limits. (I don't expect a user to login a billion times, but even just
    he would be blocked.) You can even push data to your or other services inside
    the requests as often as you want.\r\n-Twitter actually got a callback_url parameter,
    and it works pretty well. It's just that the tables you use don't (as far as I
    know) support it. I used the OAuth tables in the github repo, they offer these
    params. (I tested my script inside my public Dropbox and redirected the user to
    a child domain, so that worked out.)\r\n-If you don't want your user to get any
    keys, just store his keys in a seperate DB as <a href=\"http://support.quetzall.com/cloudcache/rest-api\"
    rel=\"nofollow\">Cloudcache</a>\r\n\r\nI hope that helped in any way :D"
- id: 926
  author: Greg Thorson
  author_email: Engywook2005@gmail.com
  author_url: ''
  date: '2010-12-13 16:05:15 -0800'
  date_gmt: '2010-12-13 21:05:15 -0800'
  content: "I've tried this a bit... and it _sometimes_ works. But more often than
    not, I see this message:\r\n\r\n\"Table _____ requires https but requested through
    http.\"\r\n\r\nWhat am I overlooking here?"
- id: 927
  author: Derek
  author_email: drgath@gmail.com
  author_url: ''
  date: '2010-12-13 16:15:35 -0800'
  date_gmt: '2010-12-13 21:15:35 -0800'
  content: Greg, the YQL URL you are requesting is likely "http" instead of "https".  Double-check
    that.
- id: 928
  author: Greg Thorson
  author_email: Engywook2005@gmail.com
  author_url: ''
  date: '2010-12-14 14:41:36 -0800'
  date_gmt: '2010-12-14 19:41:36 -0800'
  content: "It's definitely not a matter of calling query.yahooapis.com without an
    https... I have refreshed the page, and sometimes gotten the expected results,
    sometimes the error message.  I am certain of this, because I have simply refreshed
    without any change to the URL.\r\n\r\nI _always_ get the error message when I
    try to run this in the context of a web page, though."
- id: 997
  author: rahul
  author_email: rahulpandey2009@hotmail.com
  author_url: ''
  date: '2011-06-15 22:20:46 -0700'
  date_gmt: '2011-06-16 05:20:46 -0700'
  content: "thanks for this article..\r\none more thing i want to know i have downloaded
    your twitter client code from git. i dont know how to create yql tables..and the
    tables that are already present where i have to mention consumer key , consumer
    secret and oauth token key and secret for my twitter application \r\nwaiting for
    your response"
- id: 1015
  author: Francois Lafortune
  author_email: me@quickredfox.at
  author_url: ''
  date: '2011-07-07 07:13:49 -0700'
  date_gmt: '2011-07-07 14:13:49 -0700'
  content: "I have not even finished reading the article but I must say: congrats!
    That is one of the niftiest workarounds I've seen when it comes to OAuth and Javascript.
    YQL... why didnt we all think of that? Well, you did and I thank you for it.  Off
    to hack this up!\r\n\r\nP.S.: I regret not having  found this article when it
    was fresh!"
- id: 1018
  author: errumm
  author_email: lewis.barclay@gmail.com
  author_url: ''
  date: '2011-07-20 03:41:21 -0700'
  date_gmt: '2011-07-20 10:41:21 -0700'
  content: Nice. This should come in really handy on multiple future projects.
- id: 1148
  author: Douglas Hiles
  author_email: being_et_nothingness@yahoo.com
  author_url: ''
  date: '2012-03-15 09:45:28 -0700'
  date_gmt: '2012-03-15 16:45:28 -0700'
  content: "Thanks for the YQL/oauth introduction!  However, something bothered me
    about your solution to using oauth in javascript. This is the problem:  \r\n\r\nOnce
    the link to your 'store://derekgathright.com/oauthdemo' is public, there is nothing
    stopping a rogue programmer from using your store any program. Imagine if the
    program pretends to be written by you. Trusting in your excellent reputation,
    the unsuspecting person running 'your' program sees the twitter authorization
    screen matching your name and naturally gives the program the right to access
    his or her twitter account. I discovered this nagging problem when I was exploring
    your 'Tweetanium' program. \r\n\r\nWhat disturbed me was that I was able to call
    your store from my test program, display your Tweetanium twitter authorization
    screen and then have twitter return back to any url on my calling site by setting
    the oauth_callback in twitter.oauth.requesttoken. \r\n \r\nYou have hidden your
    consumer key and secret but have by sharing your store, you have exposed the ability
    to display your twitter authorization screen and return back to the calling program.
    This is like giving your car keys to an untrusted valet who won't give up the
    car keys, but who can be told by anyone to drive your car anywhere. \r\n\r\nWhat
    I did to solve the problem was to create a YQL open data table, for example, myauth.xml,
    which returned the results of this query:\r\n          var q = y.query('select
    * from twitter.oauth.requesttoken where oauth_callback=\"http://www.mywebsite.com/index.html\"');\r\n\r\nI
    appended myauth.xml to a YQL env file similar to your oauthdemo.txt and made a
    store out of it.   \r\n\r\nBy hiding the oauth_callback in a yql open data table,
    nobody will hijack my store because the twitter authorization screen can only
    return to  the url that is defined in the store, not in the calling program. In
    this scenario, my 'valet' can be told to drive the car, but he is forced to return
    the 'car' back to a defined location.  This added security makes YQL a completely
    viable solution for javascript oauth."
- id: 1157
  author: Douglas Hiles
  author_email: douglashiles@gmail.com
  author_url: ''
  date: '2012-04-23 06:57:56 -0700'
  date_gmt: '2012-04-23 13:57:56 -0700'
  content: The page that twitter calls back to can be 'locked in' by setting oauth_callback
    as an environment variable along with oauth_consumer_key and oauth_consumer_secret
    in the store.  This is a much better solution than passing in oauth_callback from
    another xml open data table.
- id: 1293
  author: Talha
  author_email: talhakamran2006@hotmail.com
  author_url: ''
  date: '2012-10-05 12:50:32 -0700'
  date_gmt: '2012-10-05 19:50:32 -0700'
  content: "Could you please give vimeo a try as well. I came across problem that
    my boss wants me to go through a vimeo channel which has 150+ videos and pull
    the one that have specific keywords in them. Problem is that basic api allows
    to pull only 60 videos and 20 videos per page. I ended up in making three calls
    to load all in one big array of 60 videos. \r\nIn order to query all 150+ i will
    need to use advance api that uses OAuth. Luckily YQL has oauth tables defined
    that you can use in playground but I cant get it to work with YUI . I can pull
    result in YQL playground. Please see if you can spare few minutes on this."
- id: 1312
  author: Beppo
  author_email: phoenix_page@gmx.at
  author_url: ''
  date: '2013-02-12 11:40:42 -0800'
  date_gmt: '2013-02-12 18:40:42 -0800'
  content: Is there anything stored on your Server ? Because in twitter.js there is
    a line params.env = "store://tweetanium.net/tweetanium06"; ?
- id: 2177
  author: budporn
  author_email: abelholcomb@peacemail.com
  author_url: http://www.budporn.org
  date: '2014-02-17 05:30:21 -0800'
  date_gmt: '2014-02-17 12:30:21 -0800'
  content: "Hey! I know this is kinda off topic however , I'd figured I'd ask.\r\n\r\nWould
    you be interested in exchanging links or maybe guest writing a blog article or
    vice-versa?\r\nMy blog discusses a lot of the same topics as yours and I think
    we could \r\ngreatly benefit from each other. If you happen to be interested feel
    free \r\nto send me an e-mail. I look forward to hearing from you!\r\nAwesome
    blog by the way!"
---
Wouldn't it be awesome if we could use OAuth in JavaScript-only apps? JS is a powerful, expressive programming language, and the browser engines are getting <a title="arewefastyet.com" href="http://arewefastyet.com/">faster and faster all the time</a>. Why not use JavaScript to conduct your API calls and parse your data? In many cases, it is unnecessary to maintain a server-side proxy if all it is doing is making API calls for you and hiding your OAuth keys.

<!-- more -->

Think about this... If you don't need any server-side processing, your applications suddenly become infinitely scaleable, right? We could host on the cheapest of cheap commodity hosting. Heck, if all we're doing is serving static HTML/CSS/JS files, just throw it on a CDN like S3 or CloudFiles and pay per GB.

Before you get too excited, realize that there is a fundamental problem with OAuth in JS. Because JavaScript in the browser is "view-source", you are always forced to expose your consumer key pair, which compromises the security of your application. *sigh*

For example, when Twitter recently deprecated their Basic Auth services, that left OAuth as the only authentication method. It was supposed to be <a title="OAuth-only Twitter: What it Means for JavaScript Apps" href="http://blog.programmableweb.com/2010/08/31/oauth-only-twitter-what-it-means-for-javascript-apps/">the death of JS-only Twitter apps</a>. This was unfortunate for quite a few developers who leveraged the browsers ability to do Basic auth, to help with scaling their Twitter apps. I know, I was one of them.

So then I began to think what if you weren't forced to expose your keys? What if your JS app could talk to any web API out there, in a secure, user-authenticated way?

Is that actually possible? Yup.

<strong><a id="more"></a><a id="more-780"></a>Backstory</strong>

Unknowingly at the time, my quest for a JS only OAuth app began two years ago.

When TechCrunch covered <a href="http://techcrunch.com/2008/07/24/tweenky-brings-gmails-good-looks-to-twitter/">the launch of my Twitter client</a>, the app pretty quickly died from the traffic they were sending my way. The problem is 90% of it was written in PHP and used a relational database to store waaaaaay to much data. Neither of them were designed to scale to 20k users in just a few minutes. After days of tweaking and optimizing, I finally gave up on the design. I realized I didn't need PHP to parse the data, or a database to host the data, so I began a rewrite with the goal of removing as much server-side code as possible. I threw away the database, moved off expensive EC2 and onto commodity hosting where it worked great for the next year or so with some occasional tweaking. As hard as I tried, I never thought I'd be able to completely get rid of the backend because I needed a proxy to securely handle the OAuth requests to Twitter. "That's ok, close enough" I thought.

One day I was reading the Yahoo Query Language <a href="http://developer.yahoo.com/yql/guide/">documentation</a>, and I came across a section about using YQL's storage API to hide authentication info to be used in your queries. Ah ha! Could I actually use that for OAuth? I set to find out. I began learning the ins &amp; outs of OAuth, which includes reading <a href="http://tools.ietf.org/html/rfc5849">RFC 5849: The OAuth 1.0 Protocol</a> many, many times, and staring at the <a href="http://p2p.wrox.com/content/sites/default/files/users/17/image/figures%20ch6/531327%20f0602.png">OAuth Authentication Flow diagram</a> for loooooong time. By the end of the weekend, I had successfully modified my recently rewritten Twitter client's code-base (now YUI3 based) to remove all server-side programming.

Finally! A secure, pure JavaScript solution to OAuth.

<strong>Some Prep Work</strong>

So let's crack the code of what is necessary to do OAuth securely in JavaScript.
<ul>
	<li>You cannot store your consumer keys inside your JS code. Not even obfuscated. But it has to be stored somewhere web-accessible so your JS code can talk to it.</li>
	<li>Because of the same-origin policy, that 'somewhere' has to be the same domain as your JS app. Unless of course you only rely on HTTP GET, in which case you can do JSONP.</li>
	<li>Your storage location cannot transmit your consumer key pair back to you. So that means it needs to do the OAuth request on your behalf.</li>
</ul>
So hmm.... what is web accessible, can talk to APIs, and also has data storage? YQL.

<strong>Yahoo Query Language</strong>

<img style="float: left; margin: 0px 10px 10px 0px;" src="http://farm3.static.flickr.com/2601/3858500752_9c3a39e4af.jpg" alt="" width="100" />

<a title="Yahoo Query Language" href="http://developer.yahoo.com/yql/">YQL</a> is an expressive SQL-like language that lets you query, filter, and join data across web servers. Along with YUI, it is by far my favorite product Yahoo has for developers. Both are simply amazing tools. I won't go into detail on the specifics of what YQL is in this post, and instead point you to slides from one of my recent talks on the subject <a href="http://drgath.github.com/talks/20101011_SoCaljs/index.html">here</a> (best viewed in Chrome). All you need to know for this post is that you can use it to access any web-accessible API. In the case of this post, we'll talk to the Twitter API.

So now that we know it is possible, let's see it in action.

<strong>How It Works</strong>

First let's take a look at how you would call your Twitter friends timeline via YQL w/ OAuth. Using my @derektest user, I created a new OAuth app at <a href="http://dev.twitter.com">dev.twitter.com</a> and used the keys it generated for my user/app combo to generate this YQL query.
<pre lang="sql">SELECT * FROM twitter.status.timeline.friends
WHERE oauth_consumer_key = '9DiJt6Faw0Dyr61tVOATA'
AND oauth_consumer_secret = 'XBF9j0B2SZAOWg44QTu6fCwYy5JtivoNNpvJMs6cA'
AND oauth_token = '18342542-NkgUoRinvdJVILEwCUQJ3sL2CIm2ZwzS5jjj2Lg7y'
AND oauth_token_secret = 'D6ewAzsueTzQmrAJGFH0phV5zgWT88FOtcMeqW4YeI';</pre>
So take that query, URL encode it, and throw it into a URL querystring. Like so...
https://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20twitter.status.timeline.friends%20where%20oauth_consumer_key%20%3D%20'9DiJt6Faw0Dyr61tVOATA'%20AND%20oauth_consumer_secret%20%3D%20'XBF9j0B2SZAOWg44QTu6fCwYy5JtivoNNpvJMs6cA'%20AND%20oauth_token%20%3D%20'18342542-NkgUoRinvdJVILEwCUQJ3sL2CIm2ZwzS5jjj2Lg7y'%20and%20oauth_token_secret%20%3D%20'D6ewAzsueTzQmrAJGFH0phV5zgWT88FOtcMeqW4YeI'%3B&amp;diagnostics=true&amp;env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys

That unique URL will give you a list of the people @derektest follows (which is only @derek). You can play around with the query in the <a href="https://developer.yahoo.com/yql/console/?q=select%20*%20from%20twitter.status.timeline.friends%20where%20id%3D1972%3B&amp;env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys#h=select%20*%20from%20twitter.status.timeline.friends%20where%20oauth_consumer_secret%20%3D%20%27foo%27%20AND%20oauth_consumer_key%20%3D%20%27bar%27%20AND%20oauth_token%20%3D%20%27baz%27%20and%20oauth_token_secret%20%3D%20%27biz%27%3B">YQL Console</a>, or view the results in an <a href="https://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20twitter.status.timeline.friends%20where%20oauth_consumer_key%20%3D%20'9DiJt6Faw0Dyr61tVOATA'%20AND%20oauth_consumer_secret%20%3D%20'XBF9j0B2SZAOWg44QTu6fCwYy5JtivoNNpvJMs6cA'%20AND%20oauth_token%20%3D%20'18342542-NkgUoRinvdJVILEwCUQJ3sL2CIm2ZwzS5jjj2Lg7y'%20and%20oauth_token_secret%20%3D%20'D6ewAzsueTzQmrAJGFH0phV5zgWT88FOtcMeqW4YeI'%3B&amp;diagnostics=true&amp;env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys">XML feed</a>.

But there's a problem using that query, because? You guessed it, you've exposed your consumer key-pair. So let's work on hiding those.

First step, turn the embedded parameters into environment variables by using the <em>SET</em> command.
<pre lang="sql">set oauth_consumer_key='9DiJt6Faw0Dyr61tVOATA' on twitter;
set oauth_consumer_secret='XBF9j0B2SZAOWg44QTu6fCwYy5JtivoNNpvJMs6cA' on twitter;
set oauth_token='18342542-NkgUoRinvdJVILEwCUQJ3sL2CIm2ZwzS5jjj2Lg7y' on twitter;
set oauth_token_secret='D6ewAzsueTzQmrAJGFH0phV5zgWT88FOtcMeqW4YeI' on twitter;
select * from twitter.status.timeline.friends;</pre>
Now that we've turned all the parameters into environment variables, the next step is to throw the consumer key pair into YQL's storage so only YQL can access it.

To do this, create a YQL environment file, similar to this one, <a href="http://derekgathright.com/code/yahoo/yql/oauthdemo.txt">http://derekgathright.com/code/yahoo/yql/oauthdemo.txt</a>

As you'll see, it's just a regular text file where I pasted my consumer key pair, along with importing the YQL community tables using the <em>ENV</em> command. Since we're replacing the previously included env file (store://datatables.org/alltableswithkeys) with our own, we need to chain-load it back in because it includes the Twitter tables. If you miss that step, you'll get a "<em>No definition found for Table twitter.status.timeline.friends</em>" error.

Before we store the env file in YQL, let's test it with this new query:
<pre lang="sql">set oauth_token='18342542-NkgUoRinvdJVILEwCUQJ3sL2CIm2ZwzS5jjj2Lg7y' on twitter;
set oauth_token_secret='D6ewAzsueTzQmrAJGFH0phV5zgWT88FOtcMeqW4YeI' on twitter;
select * from twitter.status.timeline.friends;</pre>
Also, you'll have to change the env file loaded in the querystring to "<em>?env=http://derekgathright.com/code/yahoo/yql/oauthdemo.txt</em>"

(<em>View: <a href="https://developer.yahoo.com/yql/console/?env=http://derekgathright.com/code/yahoo/yql/oauthdemo.txt#h=set%20oauth_token%3D%2718342542-NkgUoRinvdJVILEwCUQJ3sL2CIm2ZwzS5jjj2Lg7y%27%20on%20twitter%3B%0Aset%20oauth_token_secret%3D%27D6ewAzsueTzQmrAJGFH0phV5zgWT88FOtcMeqW4YeI%27%20on%20twitter%3B%0A%0Aselect%20*%20from%20twitter.status.timeline.friends%3B&amp;q=set%20oauth_token%3D%2718342542-NkgUoRinvdJVILEwCUQJ3sL2CIm2ZwzS5jjj2Lg7y%27%20on%20twitter%3B%0Aset%20oauth_token_secret%3D%27D6ewAzsueTzQmrAJGFH0phV5zgWT88FOtcMeqW4YeI%27%20on%20twitter%3B%0A%0Aselect%20*%20from%20twitter.status.timeline.friends%3B">YQL Console</a> - <a href="https://query.yahooapis.com/v1/public/yql?q=set%20oauth_token%3D'18342542-NkgUoRinvdJVILEwCUQJ3sL2CIm2ZwzS5jjj2Lg7y'%20on%20twitter%3B%0Aset%20oauth_token_secret%3D'D6ewAzsueTzQmrAJGFH0phV5zgWT88FOtcMeqW4YeI'%20on%20twitter%3B%0A%0Aselect%20*%20from%20twitter.status.timeline.friends%3B&amp;diagnostics=true&amp;env=http%3A%2F%2Fderekgathright.com%2Fcode%2Fyahoo%2Fyql%2Foauthdemo.txt">Results</a></em>)

Now that we have our environment file created and tested, let's tell YQL to import it. To do that, we'll construct a YQL query similar to:
<pre lang="sql">insert into yql.storage.admin (name,url)
values ("oauthdemo","http://derekgathright.com/code/yahoo/yql/oauthdemo.txt")</pre>
Which returns:
<pre lang="xml">
       store://derekgathright.com/oauthdemo
<select>store://VfoIoYWhLWLxYzRTcrbvNb</select>

       [hidden]</pre>
You now have 3 keys pointing to your data, and each does something different (think: unix permissions, R/W/X). For more information on what each of the 3 does, <a href="http://developer.yahoo.com/yql/guide/yql-storage-select-update-delete.html">Using YQL to Read, Update, and Delete Records</a>.

For this example we want the <em>execute</em> key, which is really just an alias to our stored env file. So if we change our query's URL to <em>?env=store://derekgathright.com/oauthdemo</em> and use the same YQL query as last time, you'll see we have now hidden our consumer key pair from the public.

(View: <a href="https://developer.yahoo.com/yql/console/?env=store://derekgathright.com/oauthdemo#h=set%20oauth_token%3D%2718342542-NkgUoRinvdJVILEwCUQJ3sL2CIm2ZwzS5jjj2Lg7y%27%20on%20twitter%3B%0Aset%20oauth_token_secret%3D%27D6ewAzsueTzQmrAJGFH0phV5zgWT88FOtcMeqW4YeI%27%20on%20twitter%3B%0A%0Aselect%20*%20from%20twitter.status.timeline.friends%3B">YQL Console</a> - <a href="https://query.yahooapis.com/v1/public/yql?q=set%20oauth_token%3D'18342542-NkgUoRinvdJVILEwCUQJ3sL2CIm2ZwzS5jjj2Lg7y'%20on%20twitter%3B%0Aset%20oauth_token_secret%3D'D6ewAzsueTzQmrAJGFH0phV5zgWT88FOtcMeqW4YeI'%20on%20twitter%3B%0A%0Aselect%20*%20from%20twitter.status.timeline.friends%3B&amp;diagnostics=true&amp;env=store%3A%2F%2Fderekgathright.com%2Foauthdemo">Results</a>)

Well there you have it, an example of how to hide your consumer key pair, which now allows you to use YQL as your server-side proxy as opposed to writing &amp; maintaining your own!

<strong>A Pure JS Twitter Client is Born</strong>

When I started at Yahoo, I wanted an excuse to learn YUI3 and expand my knowledge of YQL. So porting my jQuery/PHP based Twitter client seemed like a logical choice. The result of this work is an open-source project I call <a href="http://github.com/derek/Tweetanium">Tweetanium</a>. I'm not going to argue it is the most polished or feature-rich Twitter client. In fact, it is quite buggy, and will likely always be that way. It's just something I toy around with occasionally to try out new things. But feel free to use it if you like. You can play around in it at <a href="http://tweetanium.net">tweetanium.net</a>.

As proof that there is no server-side JS, you can even use <a href="http://derek.github.com/Tweetanium/docroot/">a version of it</a> hosted on Github Pages, which is a static file host (no PHP, Ruby, Python, etc...). Hosting off Github Pages was a neat test for it, which basically proves you can host JS-only apps on commodity hosting. If you actually need to process data externally, you can use YQL tables for any APIs on the web, even your own custom-built ones (See: <a href="http://developer.yahoo.com/yql/guide/yql-opentables-chapter.html">YQL Open Data Tables</a>). Any scaling bottlenecks have now been offloaded to Github and Yahoo. The best part about this solution? It's free!

Post some comments if you have questions.

<strong>UPDATE:</strong> A few people have asked, "<em>But can't I execute YQL queries with your consumer keys now?</em>" The answer is, yes. But that isn't as bad as you think because you only have half of the keys necessary. You are missing the unique keys assigned to a user on behalf of my application, and without those, you cannot make authenticated calls. If you get those, well... there's a whole other security issue of you having physical access to their computer or man-in-the-middle attacks.

"<em>Ok, but can't I authenticate new keys posing as your app?</em>" To my knowledge, Twitter does not currently support the oauth_callback parameter, which allows the requester to Twitter to redirect the user to the URL of their choice. So if EvilHacker tries to authenticate InnocentUser using my consumer keys, InnocentUser will just be directed back to my app's preset URL stored in Twitter's database. In the future, who knows how the OAuth spec, or Twitter's implementation of it, will change. This is mostly a proof-of-concept hack at this point.
