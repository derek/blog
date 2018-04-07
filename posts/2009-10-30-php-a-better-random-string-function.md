---
layout: post
status: publish
published: true
title: A Better Random String Function for PHP
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
wordpress_id: 570
wordpress_url: http://www.derekville.net/?p=570
date: 2009-10-30 15:57:25.000000000 -07:00
categories:
- Web Development
tags: []
comments:
- id: 1032
  author: Leo
  author_email: le_gber@hotmail.com
  author_url: ''
  date: '2011-08-10 03:13:31 -0700'
  date_gmt: '2011-08-10 10:13:31 -0700'
  content: yes except that in your solution you "only" have 4368 variations (md5 is
    0-9 a-f) while with the other you have 376992
- id: 1158
  author: Matthew
  author_email: j.matthew.a@gmail.com
  author_url: ''
  date: '2012-04-26 06:23:30 -0700'
  date_gmt: '2012-04-26 13:23:30 -0700'
  content: '@Leo: The bulkier function without a doubt gives many more combinations.
    But Derek''s solution still provides enough variation. Not sure how you figure
    4368, as there are 32 chars each having one of 16 unique values (0-9A-F)... this
    allows for 16^32 combinations (which is HUGE) with replacement. In practice, we
    feed microtime() into MD5, so we really have at best 2^32 combinations coming
    out of MD5, but then we scramble the hash again using shuffle... bottom line is
    that there are more than enough salts for all users/accounts you will have.'
- id: 1159
  author: Matthew
  author_email: j.matthew.a@gmail.com
  author_url: ''
  date: '2012-04-26 06:28:15 -0700'
  date_gmt: '2012-04-26 13:28:15 -0700'
  content: '@Leo: Sorry, a bit tired this morning! I was comparing ways of generating
    salts, and stumbled across this page... Didn''t notice the length of the substring,
    5, until after my last post... still, this approach might be elegant for salts
    which are typically a lot longer than 5 chars.'
- id: 1255
  author: Michael
  author_email: michael.prewitt@gmail.com
  author_url: ''
  date: '2012-09-25 08:17:23 -0700'
  date_gmt: '2012-09-25 15:17:23 -0700'
  content: "Here is my mod, which uses your base code, but allows for lengths greater
    than 32 (MD5 generates 32-character hashes):\r\n\r\nfunction generateRandomString($length
    = 10) {\r\n\t$randomstring = '';\r\n\tif($length &gt; 32) {\r\n\t\t$multiplier
    = round($length/32,0,PHP_ROUND_HALF_DOWN);\r\n\t\t$remainder = $length % 32;\r\n\t\tfor
    ($i = 0; $i &lt; $multiplier; $i++) {\r\n\t\t\t$randomstring .= substr(str_shuffle(md5(rand())),
    0, 32);\r\n\t\t}\r\n\t\t$randomstring .= substr(str_shuffle(md5(rand())), 0, $remainder);\r\n\t}\r\n\telse
    $randomstring = substr(str_shuffle(md5(rand())), 0, $length);\r\n\treturn $randomstring;\r\n}"
- id: 1306
  author: Kalphiter
  author_email: kalphiter@gmail.com
  author_url: ''
  date: '2012-11-13 15:43:44 -0800'
  date_gmt: '2012-11-13 22:43:44 -0800'
  content: You need to subtract the length by 1 when you use mt_rand, because the
    highest position in the 36-character long string is 35.
- id: 1314
  author: Dan
  author_email: dansbaker@gmail.com
  author_url: ''
  date: '2013-03-13 04:11:41 -0700'
  date_gmt: '2013-03-13 11:11:41 -0700'
  content: Like Kalphiter said, you need to use strlen($characters) -1. Without that
    your code will work just fine most of the time but will occasionally throw an
    'invalid index'. It's always a pain in the arse trying to debug errors that occur
    randomly like that.
- id: 2173
  author: JRB
  author_email: jrbascom@hotmail.com
  author_url: ''
  date: '2014-01-02 17:18:51 -0800'
  date_gmt: '2014-01-03 00:18:51 -0800'
  content: Thank you. Very simple and useful function.
---
Often times you'll come across the need to generate a random string.  When you search for something like "PHP random string function" which will probably just be cut & pasted into your code, you'll typically find something like this function:

<pre lang="php">
function genRandomString($length = 10) {
    $characters = ‘0123456789abcdefghijklmnopqrstuvwxyz’;
    $string = ”;
    for ($p = 0; $p < $length; $p++) {
        $string .= $characters[mt_rand(0, strlen($characters))];
    }

    return $string;
}
</pre>

While that's great and all, don't you just feel like there's some better, simpler way to generate a random string?  Preferably something done all in one line, so you don't even need a function inside your code?

There is a way.  Actually, there are lots of ways.  There are numerous functions in PHP that can be used to generate a string of random characters, and the one I typically use here is something you've probably used quite a bit... md5().  

If you aren't familiar with it, <a href="http://en.wikipedia.org/wiki/MD5">MD5</a> is a commonly used hashing technique that can be used to generate a unique 32-character "fingerprint" of a string. While it has been shown to have some security holes and not be collision proof, that isn't really a concern the majority of the time you need to generate a random string.  So, we'll go ahead and use it here.  

<pre lang="php">
echo MD5(); // PHP Warning:  md5() expects at least 1 parameter, 0 given 
</pre>

So, we need to pass in something, anything, but try to be unique.  microtime() is a good choice.

<pre lang="php">
echo MD5(microtime()); // 5959e4c551ee3a91d89449437b681ead
</pre>

Great, now we have a random 32 character string.  But what if you only want a slice of that, like 5 characters?  substr() is your answer.

<pre lang="php">
echo substr(MD5(microtime(), 0, 5); // 5959e
</pre>

If you are concerned about security and making this string even more random, just shuffle it with str_shuffle().

<pre lang="php">
echo substr(str_shuffle(MD5(microtime())), 0, 5); // 6c468
</pre>

Now wasn't that easy?
