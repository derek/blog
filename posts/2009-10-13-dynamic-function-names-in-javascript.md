---
layout: post
status: publish
published: true
title: Dynamic function names in JavaScript
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
wordpress_id: 553
wordpress_url: http://www.derekville.net/?p=553
date: 2009-10-13 20:48:13.000000000 -07:00
categories:
- Web Development
tags:
- JavaScript
comments:
- id: 948
  author: Ambili Surendran
  author_email: ambilisurendran@gmail.com
  author_url: ''
  date: '2011-02-11 09:02:58 -0800'
  date_gmt: '2011-02-11 14:02:58 -0800'
  content: "Hi Derek,\r\n\r\nThanks for this blog. It helped me in solving my problem.\r\n\r\n\r\nRgrds,\r\nAmbili"
- id: 1154
  author: Marcos Caceres
  author_email: marcos@marcosc.com
  author_url: http://marcosc.com/
  date: '2012-03-30 10:44:58 -0700'
  date_gmt: '2012-03-30 17:44:58 -0700'
  content: "This only really helps you if you want to bind things to the <code>window</code>
    object, which is not ideal all the time. It also just creates anonymous functions,
    rather than named functions of a particular type. What you want is something more
    like:\r\n\r\nvar someThing = new Thing();   \r\n\r\nand <code>someThing instanceof
    \ Thing<code>; \r\n\r\nI got an bit inspired by your article and wrote this alternative
    thing:\r\n \r\nhttp://marcosc.com/2012/03/dynamic-function-names-in-javascript/"
- id: 1156
  author: Leo
  author_email: lfofanov@hotmail.com
  author_url: http://leonidius2010.wordpress.com/
  date: '2012-04-14 16:02:28 -0700'
  date_gmt: '2012-04-14 23:02:28 -0700'
  content: Cool tip ! Thank you !
- id: 2174
  author: http://www.seo-p2p.com/groups/novoline-download
  author_email: alfredo.toups@yahoo.com
  author_url: http://www.seo-p2p.com/groups/novoline-download/
  date: '2014-01-31 04:58:35 -0800'
  date_gmt: '2014-01-31 11:58:35 -0800'
  content: "Howdy! Do you know if they make any plugins to safeguard against hackers?\r\nI'm
    kinda paranoid about losing everything \r\nI've worked hard on. Any tips?"
---
If you are doing some more advanced JavaScript applications, you'll likely run into the problem at one point or another when you need to dynamically generate the name of a function you wish to call. This is the equivalent of PHP's <a href="http://php.net/manual/en/function.call-user-func.php" target="_blank">call_user_func()</a>.  

Here's how you can do it.

<pre lang="javascript">
// Define some vars
var foo = "hello";
var bar = "world";
var function_name = "say_" + foo + bar;

// Since its name is being dynamically generated, always ensure your function actually exists
if (typeof(window[function_name]) === "function")
{
	window[function_name](" World!");
}
else
{
	throw("Error.  Function " + function_name + " does not exist.");
}

function say_helloworld(the_word)
{
	alert("Hello " + the_word);
}

// Browser will alert "Hello World!"
</pre>

When you think about it, it makes a lot of sense considering all global objects in JavaScript are actually properties of the "window" object.  Take a look at this example to understand that concept a bit more.

<pre lang="javascript">
var foo = "apple";

function foobar()
{
	var foo = "orange";
	alert(window["foo"]); // alerts "apple"
	alert(foo); // alerts "orange"
	alert(window["foobar"]); // alerts the foobar function
}

foobar();
</pre>

Here's another example of when using a string to call a function could come in handy.  This time we're calling the property of an object we've created.

<pre lang="javascript">
function Person()
{
	this.message = "Hello World!";
	this.say_hello = function(to)
	{
		alert(this.message);
	}
}

var Derek = new Person();
function_name = "say_hello";
Derek[function_name]();
</pre>

See how it looks pretty much the same as the method above using a global function?  

Hope that shed some light on your problem.
