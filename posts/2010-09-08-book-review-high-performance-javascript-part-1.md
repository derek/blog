---
layout: post
status: publish
published: true
title: High Performance JavaScript (Book Review)
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
excerpt: "<div style=\"float:right; padding:20px;\"> <img src=\"http://covers.oreilly.com/images/9780596802806/lrg.jpg\"
  width=\"200\" /></div>\r\n\r\nWhen I saw on NCZ's blog that he was <a href=\"http://www.nczonline.net/blog/2010/02/09/announcing-high-performance-javascript/\">writing
  a new book</a> on JavaScript performance techniques, I instantly went to pre-order
  it.  Having partially read through <em><a href=\"http://www.amazon.com/gp/product/059680279X?ie=UTF8&tag=deresblog-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=059680279X\">High
  Performance JavaScript</a></em> by now, I figured I'd start writing a review of
  this excellent book.\r\n\r\nSince JavaScript is such an expressive language, there
  are dozens of different ways to do the same thing.  Some of them good, some mediocre,
  and a lot of them bad.  It's amazing how much awful JS info is on the web, all leftover
  from the dark ages of JS ('96 - '05). Up until this point, we haven't had an authoritative
  source on the topic of how to write JavaScript that performs well, both in and out
  of the browser.  Sure we're had great books about web performance (<a href=\"http://www.amazon.com/gp/product/0596529309?ie=UTF8&tag=deresblog-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=0596529309\">High
  Performance Web Sites</a> is my favorite), but we haven't had anything specific
  to JavaScript.  Now we do.\r\n\r\nNicholas is widely known as one of the best minds
  in the JavaScript world today.  He joined Yahoo! in 2006 as a front end engineer
  and has been working on one of the most trafficked pages on the interwebs, the Yahoo!
  home page.  His blog (<a href=\"http://nczonline.net\">nczonline.net</a>) is a treasure
  trove of information on all things JavaScript & web performance.  Some recent gems
  include <a href=\"http://www.nczonline.net/blog/2010/01/05/interviewing-the-front-end-engineer/\">Interviewing
  the front-end engineer</a> &amp; <a href=\"http://www.nczonline.net/blog/2009/12/15/writing-maintainable-code/\">Writing
  maintainable code</a>.  It goes without saying that he knows his stuff when it comes
  to JavaScript & performance.  As his books and blog posts have shown, he's also
  a very skilled technical writer, keeping topics fresh, concise, & relevant.\r\n\r\nI'm
  writing this as I read along, so the verbosity of this post is due to me taking
  reference notes on interesting things as I go.\r\n"
wordpress_id: 769
wordpress_url: http://www.derekville.net/?p=769
date: 2010-09-08 00:44:48.000000000 -07:00
categories:
- Web Development
tags: []
comments: []
---
![book cover](http://covers.oreilly.com/images/9780596802806/lrg.jpg)

When I saw on NCZ's blog that he was [writing a new book](http://www.nczonline.net/blog/2010/02/09/announcing-high-performance-javascript/) on JavaScript performance techniques, I instantly went to pre-order it. Having partially read through _[High Performance JavaScript](http://www.amazon.com/gp/product/059680279X?ie=UTF8&tag=deresblog-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=059680279X)_ by now, I figured I'd start writing a review of this excellent book.

<!--more-->

Since JavaScript is such an expressive language, there are dozens of different ways to do the same thing.  Some of them good, some mediocre, and a lot of them bad.  It's amazing how much awful JS info is on the web, all leftover from the dark ages of JS ('96 - '05). Up until this point, we haven't had an authoritative source on the topic of how to write JavaScript that performs well, both in and out of the browser.  Sure we're had great books about web performance (<a href="http://www.amazon.com/gp/product/0596529309?ie=UTF8&tag=deresblog-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=0596529309">High Performance Web Sites</a> is my favorite), but we haven't had anything specific to JavaScript.  Now we do.

Nicholas is widely known as one of the best minds in the JavaScript world today.  He joined Yahoo! in 2006 as a front end engineer and has been working on one of the most trafficked pages on the interwebs, the Yahoo! home page.  His blog (<a href="http://nczonline.net">nczonline.net</a>) is a treasure trove of information on all things JavaScript & web performance.  Some recent gems include <a href="http://www.nczonline.net/blog/2010/01/05/interviewing-the-front-end-engineer/">Interviewing the front-end engineer</a> &amp; <a href="http://www.nczonline.net/blog/2009/12/15/writing-maintainable-code/">Writing maintainable code</a>.  It goes without saying that he knows his stuff when it comes to JavaScript & performance.  As his books and blog posts have shown, he's also a very skilled technical writer, keeping topics fresh, concise, & relevant.

I'm writing this as I read along, so the verbosity of this post is due to me taking reference notes on interesting things as I go.
<a id="more"></a><a id="more-769"></a>
<hr />

<h2>Chapter 1: Loading & Execution</h2>
Nick doesn't waste any time getting into what the reader wants, fresh tips! Right away we begin to learn the specifics of how browsers react depending on where & how you include your JS.  There are many ways that work, but few ways that work <strong>well</strong>.

Specifically:
<ul>
<li>Why is it important to put your &lt;script&gt; includes just above the closing &lt;/body&gt; tag?</li>
<li>What is the browser doing while loading those external files?</li>
<li>Why should you put all your in-page JS code <strong>above</strong> your CSS includes? <em>(A: If you put it after a &lt;/link&gt; tag referencing an external stylesheet, the browser will block execution while waiting for that stylesheet to download)</em></li>
<li>How you can use the <em>defer</em> attribute in &lt;script&gt; tags to delay non-essential execution of code.</li>
<li>A thorough look at dynamic script loading to import & execute your JS without blocking the browser.</li>
<li>An overview of some of the common JS loaders used today (YUI3, LazyLoader, & LABjs).</li>
</ul>

While much of the content in this chapter contains common knowledge among experienced developers, it is important knowledge to cover as it serves as the foundation for the rest of the book.  Don't worry, we'll get more advanced.

<hr />

<h2>Chapter 2: Data Access</h2>
Here's where the sexy parts come into play; diagrams, graphs, and benchmarks!  This second chapter is where you'll learn about how exactly the JS engine accesses data depending on how you store it.  The steepest learning curve within JavaScript for beginning developers is understanding variable scope.  This is the first time I've ever come across an explanation of JavaScript's <a href="http://www.jibbering.com/faq/faq_notes/closures.html#clScCh">[[Scope]]</a> property, now all the scoping & speed issues make perfect sense!

Major topics covered in this chapter:

<ul>
<li>Why do global variables perform so slowly?</li>
<li>Why creating data as local variables as opposed to object properties is 10%-50% faster (depending on the browser).</li>
<li>Why is it a good idea to create local instances of global variables?</li>
<li>Why <em>with</em>, <em>try/catch</em>, and <em>eval</em> are bad ideas from a performance perspective. (<em>A: they augment the scope by inserting themselves first on the tree</em>)</li>
<li>What truly happens under the hood when a variable is found to be <em>undefined</em>?</li>
<li>Closure scope and why they can cause memory leaks.</li>
<li>How prototype's work and performance issues related to traversing up the prototype chain.</li>
<li>Why is it bad to use deeply nested object members (i.e. foo.bar.baz.bop())?</li>
</ul>

There were so many "Ah hah! I get it now!" moments in this chapter for me that it alone was worth the price of the book.  It took me about 5x as long as it should have to get through this chapter because I was too busy playing with Firebug as I began to learn some of these concepts.

<hr />

<h2>Chapter 3: DOM Scripting</h2>
This book contains a few guest author chapters, and this is one of them.  In this chapter we learn about DOM scripting by another Yahoo, Stoyan Stefanov.

Many web developers don't understanding what exactly "DOM scripting" is, even though they likely do it on a daily basis.  Many could tell you what the acronym stands for and that it represents the structure of an (X)HTML/XML document, but most don't know that it also represents the API part of how you interact with the document.  When you are using <em>document.getElementById("foobar")</em> or <em>myelement.style.color = "blue"</em>, you are utilizing a DOM API function accessible via JavaScript, but it has nothing to do with the ECMAScript (aka: JavaScript) standard.

This chapter is chalk-full of great best practices & overviews of DOM principles.  The first thing we learn is that accessing the DOM is so slow because we're crossing the bridge between JavaScript and native browser code.  Jumping between the two is expensive, and should be kept to a minimum.  There are a lot of tricks & tips that are very under-utilized by most developers when DOM scripting.  

For example:

<ul>
<li>Using the non-standard <em>innerhtml</em> is way faster than creating nodes via the native <em>document.createElement()</em> method.</li>
<li>When looping through a NodeCollection you should cache the length of the node in a local variable because it's own <em>length</em> property is very slow.</li>
<li>Iterating through <em>nextSibling()</em> can be 100x faster than using <em>childNodes()</em></li>
</ul>

This chapter also goes into a detailed explanation of what repaint &amp; reflow are, when they occur, and how understanding them will improve your application performance.  The realization I had after reading the R&R explanation is we do stupid stuff all the time simply because we don't understand how the browser renders and updates our pages.  You know how you've always heard using <em>margin-left</em> &amp; <em>margin-right</em> as separate styles is a bad idea? Well, here you find out why.  Oh, and did you know there was a <em>cssText</em> property you can use to batch your CSS modifications? I didn't.

As JS libraries get more &amp; more popular, knowledge of good DOM scripting is becoming increasingly rare.  Take event delegation for example. Many developers just presume jQuery's <em>live()</em> or YUI3's <em>delegate()</em> methods are just magic.  They're far from it, and are actually easy to understand concepts. When interviewing candidates for front end jobs at Yahoo!, this is one of the primary concepts we expect candidates to understand.  They may have never used it, but the good ones will figure it out as they are whiteboarding and we walk them through the challenges.

JS libraries are awesome, but it's because they abstract out the cross-browser differences &amp; fix a flawed language, not because they allow you to forget what it actually going on under the hood.

<hr />

<h2>Chapter 4: Algorithms & Flow Control</h2>
Chapter 4 kicks off with a quick overview of the 4 different types of loops in JavaScript (<em>while</em>, <em>do-while</em>, <em>for</em>, <em>for-in</em>).  The first 3 have equivalent performance, but <em>for-in</em> is the one to watch out for and should only be used when iterating an unknown number of elements (i.e. object properties). We then learn about important concepts like length caching and various other optimization techniques focused on reducing the number of operations per iteration.

Next up are conditionals, such as <em>if-else</em> and <em>switch</em>.  We learn when it is appropriate to use each one, and when they can be ditched for a much faster method, like using arrays as lookup tables.

Finally we come to the topic of recursion.  We skip the basics of "What is recursion" and jump straight into browser limitations with call stacks and advanced recursion topics such as memoization to cut out the fat in your stack.

Since the majority of our time spent coding is inside of loops, conditionals, and (if we really want to optimize) recursion, this chapter has great, basic information on efficient shortcuts that will set you apart from the other developers on your team.  Techniques learned in this chapter extend beyond the scope of JavaScript and can be used in just about every other programming language.

<hr />

<h2>Chapter 5: Strings and Regular Expressions</h2>
<em>Another guest author chapter, this time by regex guru Steve Levithan</em>

Along with loops, another very common task in JavaScript is string manipulation, most commonly one by concatenation or regular expressions, so it makes sense to have a whole chapter to itself.

When most people start out with JS, their concatenation method is likely <em>var str = "foo"; str = str + "bar"; //str = "foobar"</em>, then they discover the += operator and it becomes <em>var str = "foo"; str += "bar"; //str = "foobar"</em>.  It turns out that one of those is more efficient when it comes to memory usage, and it happens to not be the latter.  This chapter provides some memory allocation table diagrams to explain the difference and how different browsers perform that operation. It should also be noted that another alternate method of concatenation, <em>['foo','bar'].join('');</em> is the preferred method in IE 6 &amp; 7, so that should be considered depending on your userbase.

The second half of this chapter covers regular expressions, which usually make me cringe. I have no problem writing them, but they're an absolute nightmare to maintain sometimes.  Douglas Crockford has a saying, "If a regular expression is longer than 2 inches, find another method."  I couldn't agree more.

<hr />

In this review, I only covered the first half of the book.  Here are the remaining chapters:

<ul>
<li>Chapter 6: Responsive Interfaces</li>
<li>Chapter 7: Ajax</li>
<li>Chapter 8: Programming Practices</li>
<li>Chapter 9: Building and Deploying high performance JavaScript applications</li>
<li>Chapter 10: Tools</li>
</ul>

If you like what you've seen so far, <a href="http://www.amazon.com/Performance-JavaScript-Faster-Application-Interfaces/dp/059680279X">go buy it</a>!
