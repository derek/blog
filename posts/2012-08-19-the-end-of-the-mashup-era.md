---
title: The End of the Mashup Era
date: 2012-08-19
---

Every time Twitter announces some new API initiative that further damages their once great developer community, I always think, _"Alright, this is the last time I'll write about them. I'm done."_ But every time, they always find a way to pull me back into the discussion.

![](https://media.giphy.com/media/B3nATT4FPkb3G/200.gif)

<!--More-->

However, I'll actually try and refrain from commenting too much about their [recent changes](https://dev.twitter.com/blog/changes-coming-to-twitter-api). It's already been discussed to death, everyone hates it, including me, and frankly, I'm not surprised. It's just yet [another](http://derek.io/blog/2010/my-birthday-gift-to-twitter-i-quit/) [move](http://derek.io/blog/2011/some-thoughts-on-twitter-vs-ecosystem/) to close off and control their once free, open, and awesome API. But whatever, they can do what they like.

The reason it did prompt me to begin thinking about the topic though, is the larger significance of the announcement.  Twitter's move is just one more instance of yet another company turning its back on the developer community.  But more importantly though, it's a move that made me realize something... the mashup era is over.

Let's rewind back to 2004.  Google was still a private company, Yahoo was best known as a search engine, Facebook was still running on a computer in a Harvard dorm room, and most important to this story, Microsoft thought the Web had reached its pinnacle.  They won the "browser wars", Internet Explorer had a 92% market share and Netscape was dead, so (as rumor has it) they disbanded the IE team.  Subsequently, innovation on the Web stalled.  It was a dark time as very little work was being done (successfully) to evolve the Web's core technologies (browsers, HTML, CSS, JavaScript).  The Web, as an application platform, had failed.

Well, that's what everyone thought.  At least until Google released two very important products that proved to everyone that there was still a lot that can be done with the Web.  Those being GMail (2004), which popularized Ajax, and Maps (2005), which unintentionally led to the invention of the mashup and contributed to the rise of "Web 2.0".

[HousingMaps.com](http://housingmaps.com) (2005) typically gets credit as the first Web mashup, which blends Craigslist with Google Maps, and this was before Maps even had an official API. [ChicagoCrime.org](http://chicagocrime.org) followed shortly after, and the rest was history. Mashups were popping up by the thousands, and JavaScript was becoming "cool" for the first time, because it could make your once bland and stale Web page come alive!

Over the next 3 or 4 years, Web companies left and right were distributing their data far and wide through a variety of data formats. _"Want XML? Here ya go! RSS for everything!! JSON? Sure. We'll even set up JSONP for you too. Authentication? Nope, not necessary, we trust you to do the right thing with this data. Happy coding and let us know if you build anything cool!"_ It was a very innovative era, and the extent of what you could build were only limited by your knowledge and the amount of time you had to hack something together.

But as you've heard 1,000 times before, all good times eventually come to an end.  Nowadays, it's tough to find an RSS or JSON feed on most sites that aren't blogs.  Sure many of them have that same data available via formal APIs, but that requires an account for authentication, documentation to be read, knowledge of technologies required, and (very likely) limitations placed on the amount of data you can consume.  It's a lot of work.  Also, an API is no longer thought of as a necessity to building a successful product.

Why did this happen? It's tough to say really, but here's a few theories as I think aloud...

* With the rise of JSON and the death of RSS, there was no standard/popular feed format for every Web service to implement, which meant it was a bit more difficult to open up a public API since you had to actually think about your data structure.  On the client-side, while I would absolutely rather work with JSON over XML/RSS, the tools and data are less interchangeable because they are all using custom structures, which leads to more work to build a mashup.

* The bar was raised.  No longer are we amused and entertained by Google Maps mashups or a Web-based Twitter client.  Our expectations are higher, requiring more unique ideas and more resources towards development.  With a higher barrier to entry and higher expectations,

* Facebook and Apple proved you could make $billions off partially-closed environments, which made previously open companies start looking at closed environments for their data. For example, Google, a previously strong advocate of full and open APIs, still has yet to release a full API for Google+ and lets us know we [shouldn't expect one anytime soon](http://techcrunch.com/2012/06/28/dont-expect-a-full-readwrite-google-api-anytime-soon-google-doesnt-want-to-disrupt-something-magical/). Yahoo, who previously would try to out-Open Google, was never able to properly execute on the "Open" concept (see: [YAP](http://blog.programmableweb.com/2008/10/14/a-preview-of-yap-the-yahoo-application-platform/), and many of the APIs from the 2006-2010 era are either gone or no longer useful.

* When companies are young, they are usually very open to the idea of "Open", because that's a great way to gain developers and new ideas while you work on creating your business.  Eventually though, all those investors that gave you millions of dollars will want to be paid back (preferably 100x over), so you need to eventually settle on a business model.

RIP mashups.
