---
layout: post
status: publish
published: true
title: Issue when compiling FFMPEG on RHEL4
author: Derek
author_login: admin
author_email: drgath@gmail.com
author_url: http://derek.io
wordpress_id: 328
wordpress_url: http://www.derekville.net/2008/06/25/issue-when-compiling-ffmpeg-on-rhel4/
date: 2008-06-25 05:18:53.000000000 -07:00
categories:
- Web Development
tags:
- linux
- ffmpeg
- rhel4
comments: []
---
<p>A user uploaded a Quicktime video to my website the other day and the server ran into a problem transcoding it to FLV.  I hit up #ffmpeg and it was suggested that I upgrade my install of FFMPEG and libfaad.  Alrighty, no big deal, done it before.  So first thing this morning was going to be update the sources and recompile.</p>
<p>Before I get on with that, first I'll describe the environment.  We're running on RHEL4 and have an install of FFMPEG that works fine (aside from that 1 user uploaded video).  The last upgrade of FFMPEG to get h264 support wasn't done by me, but rather our sysadmin, when we actually had a sysadmin. I believe he used rpms for the libraries and compiled FFMPEG from the SVN repo.</p>
<p>So I did a quick search just to remind myself what libraries I needed and I came across <a href="http://pixels-and-politics.blogspot.com/2008/03/compile-ffmpeg-on-rhel4.html">this post</a> about compiling on RHEL4, our distro. Perfect.  I followed directions to a T (aside from upgrading SVN) and it compiled fine.  Now, time to run a test transcode...</p>
	<blockquote>
		[root@140859-www1 ~]# /home/derek/ffmpeg_sources/ffmpeg/ffmpeg -y -i /media/v2-prod/atlas/8102/20206 -ab 64k -ar 22050 -b 700K -r 15 -y -s 640x480 -ac 1 -padtop -padbottom -s vga /home/derek/blah.flv
		FFmpeg version SVN-r13977, Copyright (c) 2000-2008 Fabrice Bellard, et al.
		  configuration: --enable-libmp3lame --enable-libvorbis --enable-libfaac --enable-libfaad --enable-gpl --enable-libtheora --enable-libx264 --enable-shared
		  libavutil version: 49.7.0
		  libavcodec version: 51.57.2
		  libavformat version: 52.16.0
		  libavdevice version: 52.0.0
		  built on Jun 25 2008 14:49:55, gcc: 3.4.6 20060404 (Red Hat 3.4.6-9)
		Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/media/v2-prod/atlas/8102/20206':
		  Duration: 00:10:55.2, start: 0.000000, bitrate: 406 kb/s
		    Stream #0.0(und): Audio: mpeg4aac, 44100 Hz, stereo
		    Stream #0.1(und): Video: h264, yuv420p, 320x240 [PAR 0:1 DAR 0:1], 30.00 tb(r)
		Output #0, flv, to '/home/derek/blah.flv':
		    Stream #0.0(und): Video: flv, yuv420p, 640x480 [PAR 0:1 DAR 0:1], q=2-31, 700 kb/s, 15.00 tb(c)
		    Stream #0.1(und): Audio: libmp3lame, 22050 Hz, mono, 64 kb/s
		Stream mapping:
		  Stream #0.1 -> #0.0
		  Stream #0.0 -> #0.1
		Press [q] to stop encoding
		/home/derek/ffmpeg_sources/ffmpeg/ffmpeg: symbol lookup error: /home/derek/ffmpeg_sources/ffmpeg/ffmpeg: undefined symbol: av_fifo_generic_write
		You have new mail in /var/spool/mail/root
		</blockquote>
<p>Well shit.  Ok, so I hit up #ffmpeg again, but don't get any help, so I try recompiling without any config options and it works fine.  So I slowly start added on config options and it works until I add "--enable-share", and which point it compiles a version of FFMPEG that throws the "undefined symbol" error.  So that gives me a pretty good idea it has something to do with that.  I go through the symlinks in the guide (linked above) and notice that /usr/lib/libavformat.so.50 is symlinked to a file that doesn't exist.  And that's where I'm at now, kinda stumped.  Am I missing libraries?  how can I ensure any old libraries installed before are cleaned out and not conflicting with new ones?  I'm a developer, not a linux admin.  I know my way around the OS, but when it comes to this type of stuff, I'm stumped.</p>
<p>Any ideas? post a comment or email/gtalk me at drgath at gmail.com.</p>
