---
layout: post
status: publish
published: true
title: Auto-versioning JavaScript & CSS files
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
wordpress_id: 438
wordpress_url: http://www.derekville.net/?p=438
date: 2009-09-04 11:45:26.000000000 -07:00
categories:
- Web Development
tags:
- JavaScript
- css
- versioning
- htaccess
comments:
- id: 764
  author: jj
  author_email: speshal@gmail.com
  author_url: ''
  date: '2010-03-19 17:31:07 -0700'
  date_gmt: '2010-03-19 22:31:07 -0700'
  content: "Good article, this is the preferred method for sure.\r\nHowever, you should
    be using this on any static file- images, pdfs, etc.\r\n\r\nAlso, would be nice
    to see how you're updating image references 'within' a css file.  I still don't
    have a good methodology for this."
- id: 765
  author: Derek
  author_email: drgath@gmail.com
  author_url: ''
  date: '2010-03-19 19:16:29 -0700'
  date_gmt: '2010-03-20 00:16:29 -0700'
  content: |-
    @JJ, There are two ways that I do this.  I usually prefer (A).

    A) I will actually move the dynamic styles out of the CSS file and into your main site template (ex. index.php).  Then, for example:


    #some_node{background:url('&lt;?php auto_version("/images/foobar.jpg"); ?&gt;');)


    I use that method for JavaScript variables that are generated from PHP.  That way I can still have the majority of my JavaScript in its own .js files.

    ==Another method==

    B) You can actually run any type of file through the PHP parser, it doesn't have to end in .php. Also, you can use any type of file as a CSS file, it doesn't have to end in .css.  This gives you the ability to either put all your CSS code inside a .php file, but make sure you have it throw the CSS mime type header   at the top.  If you wanted to have the PHP parser actually parse your .css files, you can add the following line to your .htaccess file.

    AddType application/x-httpd-php .css
- id: 768
  author: Dave Styles
  author_email: styleyd@msn.com
  author_url: ''
  date: '2010-04-09 06:44:24 -0700'
  date_gmt: '2010-04-09 11:44:24 -0700'
  content: Not sure why but I had to change \d to [0-9] in the ReWrite rule to get
    this working. Otherwise very, very helpful and clear.
- id: 803
  author: Rob
  author_email: robertino@tlen.pl
  author_url: http://ruppo.pl
  date: '2010-06-22 18:25:29 -0700'
  date_gmt: '2010-06-22 23:25:29 -0700'
  content: "It's a pitty but the rewrite rule doesn't work for me (either [/d] nor
    [0-9]). It doesn't strip out the timestamp :( Link to the test page: http://ruppo.pl/test/
    \r\n\r\nCould someone please help me, because the method posted by Derek is excellent!"
- id: 804
  author: Rob
  author_email: robertino@tlen.pl
  author_url: http://ruppo.pl
  date: '2010-06-22 18:57:34 -0700'
  date_gmt: '2010-06-22 23:57:34 -0700'
  content: i don't know really how but is has started to work finally :)
- id: 805
  author: Derek
  author_email: drgath@gmail.com
  author_url: ''
  date: '2010-06-22 19:31:25 -0700'
  date_gmt: '2010-06-23 00:31:25 -0700'
  content: Thanks Rob.  Glad to hear it worked for you.
- id: 806
  author: Rob
  author_email: robertino@tlen.pl
  author_url: http://ruppo.pl
  date: '2010-06-23 18:01:04 -0700'
  date_gmt: '2010-06-23 23:01:04 -0700'
  content: 'Ok, at last i''ve found the reason: i''ve been modifying some .htaccess
    file with MAC format, than with notepad++ i changed it to DOS/WINDOWS and voile
    :) Thanks Derek!'
- id: 937
  author: Leola Lloyd
  author_email: leolalloyd@gmail.com
  author_url: http://leolalloyd.co.cc/
  date: '2010-12-23 17:36:23 -0800'
  date_gmt: '2010-12-23 22:36:23 -0800'
  content: 'It''s a pitty but the rewrite rule doesn''t work for me (either [/d] nor
    [0-9]). It doesn''t strip out the timestamp :( Link to the test page: http://ruppo.pl/test/
    Could someone please help me, because the method posted by Derek is excellent!'
- id: 938
  author: Yvette Ball
  author_email: yvetteball@msn.com
  author_url: http://yvetteball.co.cc/
  date: '2010-12-24 06:22:03 -0800'
  date_gmt: '2010-12-24 11:22:03 -0800'
  content: i don't know really how but is has started to work finally :)
- id: 945
  author: Thompson
  author_email: thompson749v2@yahoo.com
  author_url: ''
  date: '2011-01-26 23:47:57 -0800'
  date_gmt: '2011-01-27 04:47:57 -0800'
  content: "This is REALLY cool. I got it working on the first try.\r\n\r\nIs it possible
    to modify this to work with a fully qualified url?\r\n(e.g. http://img.domain.com/js/actions.js).
    I use a cookieless subdomain to serve static content like JS, so I have to specify
    the full url for that."
- id: 946
  author: Thompson
  author_email: thompson749v2@yahoo.com
  author_url: ''
  date: '2011-01-28 03:01:36 -0800'
  date_gmt: '2011-01-28 08:01:36 -0800'
  content: "I came up with a really simple solution to be able to use a fully qualified
    url. I just put the function around the url that is relative to the root, and
    then wrote the rest of my fully qualified url in front of it like so:\r\n\r\n<code>\r\n'http://img.domain.com'
    . auto_version('/site/themes/mytheme/js/global.js')\r\n</code>\r\n\r\nSo obvious
    now. Yet so effective. :) And now I can even serve it off a CDN if I want!"
- id: 1033
  author: Ryan Sharp
  author_email: ryansharp31@gmail.com
  author_url: ''
  date: '2011-08-15 18:02:33 -0700'
  date_gmt: '2011-08-16 01:02:33 -0700'
  content: Wow, you really are quite clueless.
- id: 1213
  author: cold call scripts
  author_email: elvinmonaghan@t-online.de
  author_url: http://www.scribd.com/doc/72184214/Sales-Cold-Calling-and-Time-Management
  date: '2012-09-10 15:35:56 -0700'
  date_gmt: '2012-09-10 22:35:56 -0700'
  content: "For most recent news you have to pay a visit world-wide-web and on web
    I found this site as a best web \r\npage for latest updates."
- id: 1254
  author: Fjr advisors complaints
  author_email: bridgettebroyles@gmail.com
  author_url: http://www.blogger.com/profile/13969731722960838362
  date: '2012-09-24 11:39:07 -0700'
  date_gmt: '2012-09-24 18:39:07 -0700'
  content: "I'm not sure exactly why but this blog is loading extremely slow for me.
    Is anyone else having this problem or is it a issue on my end? I'll check back
    later and see if \r\nthe problem still exists."
- id: 1282
  author: Daivd Huosãr
  author_email: david@haustraliaer.com
  author_url: http://haustraliaer.com
  date: '2012-10-02 22:28:48 -0700'
  date_gmt: '2012-10-03 05:28:48 -0700'
  content: "Just thought I'd let anyone know who stumbles across this as I have...\r\n\r\nI
    had to write my CSS url like this:\r\n\r\n&lt;link rel=&quot;stylesheet&quot;
    href=&quot;\" type=\"text/css\" /&gt;\r\n\r\nThanks Derek for the great script!"
- id: 1283
  author: Daivd Huosãr
  author_email: david@haustraliaer.com
  author_url: http://haustraliaer.com
  date: '2012-10-02 22:30:11 -0700'
  date_gmt: '2012-10-03 05:30:11 -0700'
  content: "hmmm code editor fail... lets try that again.\r\n\r\n\r\n<code>&lt;link
    rel=&quot;stylesheet&quot; href=&quot;\" type=\"text/css\" /&gt;</code>"
- id: 1284
  author: Daivd Huosãr
  author_email: david@haustraliaer.com
  author_url: http://haustraliaer.com
  date: '2012-10-02 22:32:40 -0700'
  date_gmt: '2012-10-03 05:32:40 -0700'
  content: "Nope - it's wiping my php.\r\n\r\nThat href should read:\r\n\r\n?php echo
    auto_version('/base.css'); ?\r\n\r\n+ obviously add in the  on either end."
- id: 1285
  author: Daivd Huosãr
  author_email: david@haustraliaer.com
  author_url: http://haustraliaer.com
  date: '2012-10-02 22:33:41 -0700'
  date_gmt: '2012-10-03 05:33:41 -0700'
  content: "Oh ffs.. \r\n\r\n* + obviously add in the TRIANGLE brackets on either
    end."
- id: 1329
  author: Reni Margold
  author_email: reni.margold@gmail.com
  author_url: ''
  date: '2013-04-29 23:49:31 -0700'
  date_gmt: '2013-04-30 06:49:31 -0700'
  content: thank you, this is really a very elegant technique!
- id: 1336
  author: Alexander
  author_email: webmaster@sergeevabc.com
  author_url: ''
  date: '2013-05-27 14:07:56 -0700'
  date_gmt: '2013-05-27 21:07:56 -0700'
  content: God bless you, sir.
- id: 1353
  author: Denise
  author_email: deniseochoa@hotmail.com
  author_url: ''
  date: '2013-07-18 06:06:19 -0700'
  date_gmt: '2013-07-18 13:06:19 -0700'
  content: "I've been looking for this a long time! Thanks for sharing it!\r\nI need
    some help here.!\r\nI tried to follow your instructions, changed the htaccess
    file, inserted on the PHP funtion on one of my pages and so on..\r\nBut once I
    upload the modified page to the server and try to see it, it get this error: \"internal
    server error\".\r\nI can't figure out what I did wrong.\r\nThanks!"
---
As JavaScript becomes a more integral part to the core functionality of websites, ensuring that a user has a fresh copy of the latest code is as important as ever.  Normally a browser will cache certain filetypes (CSS, JS, JPG, etc...) for an indefinite period of time.  If the code within one of these cached files is updated, sometimes a browser will not know to reload that file.  So, if those changes are important for the functionality of your website, your users may run into issues and not be able to use your site properly.  Worse, they likely won't have any idea what the issue is and will eventually give up and go elsewhere. But have no fear, there's a solution to this problem... versioning your static files.

By "versioning" these files, I'm referring to changing their filenames from "my_styles.css" to "my_styles.version274.css" for example.  The problem with that example is it relies on you renaming the file and updating your includes <strong>every time</strong> you make a change.  That sounds like an nightmare, right?  Luckily there's a neat tactic you can you to make it appear to the browser to be a new file, but it will actually be the same file and will require no effort on your part.  This variation of the versioning tactic is often referred to as "Auto-versioning".  Here's an example...

First, we use the following rewrite rule in .htaccess:
<pre lang="ini">
RewriteEngine on
RewriteCond %{REQUEST_FILENAME} !-s # Make the file doesn't actually exist
RewriteRule ^(.*)\.[\d]+\.(css|js)$ $1.$2 [L] # Strip out the version number
</pre>

Now, we write the following PHP fuction:
<pre lang="php">
/**
 *  Given a file, i.e. /css/base.css, replaces it with a string containing the
 *  file's mtime, i.e. /css/base.1221534296.css.
 *  
 *  @param $file  The file to be loaded.  Must be an absolute path (i.e.
 *                starting with slash).
 */
function auto_version($file)
{
  if(strpos($file, '/') !== 0 || !file_exists($_SERVER['DOCUMENT_ROOT'] . $file))
    return $file;

  $mtime = filemtime($_SERVER['DOCUMENT_ROOT'] . $file);
  return preg_replace('{\\.([^./]+)$}', ".$mtime.\$1", $file);
}
</pre>

Now, wherever you include your CSS, change it from this:
<pre lang="html">
<link rel="stylesheet" href="/css/base.css" type="text/css" />
</pre>
To this:
<pre lang="html">
<link rel="stylesheet" href="<?=auto_version('/css/base.css')?>" type="text/css" />
</pre>
And when rendered, will appear as:
<pre lang="html">
<link rel="stylesheet" href="/css/base.1251992914.css" type="text/css" />
</pre>

<p>How does this work?  Because that mod_rewrite rule above will strip out the timestamp, your server will deliver /css/base.css as the requested file.  But to the user's browser, it will appear as a different file whenever it is updated.</p>

<p>Neat!</p>

<br />
<hr />
<br />

<p><strong>Note</strong>: Some strategies to fix this caching issue is to append a version # onto the end of the css or JavaScript file with a querystring, such as:</p>
<pre lang="html">
<link rel="stylesheet" href="/css/base.css?version=1234" type="text/css" />
</pre>

<p>This method will actually prevent the file from being cached, period!  This is bad.  You want the benefits of caching.  You don't want to make your users pull down 100k of JavaScript & CSS files on every page load.  More importantly, your servers could start to strain under the additional load.</p>

<p>Why is it not cached?  See <a href="http://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html">Section 13 from the HTTP Specification</a>, in particular Section 13.9</p>

<blockquote>
<strong>13.9 Side Effects of GET and HEAD</strong>

Unless the origin server explicitly prohibits the caching of their responses, the application of GET and HEAD methods to any resources SHOULD NOT have side effects that would lead to erroneous behavior if these responses are taken from a cache. They MAY still have side effects, but a cache is not required to consider such side effects in its caching decisions. Caches are always expected to observe an origin server's explicit restrictions on caching.

We note one exception to this rule: since some applications have traditionally used GETs and HEADs with query URLs (those containing a "?" in the rel_path part) to perform operations with significant side effects, caches MUST NOT treat responses to such URIs as fresh unless the server provides an explicit expiration time. This specifically means that responses from HTTP/1.0 servers for such URIs SHOULD NOT be taken from a cache. See section 9.1.1 for related information. 
</blockquote>
