---
layout: post
status: publish
published: true
title: DevBUG - Keeping track so you don't have to
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "DevBUG is an idea that came to me while conducting a Vulnerability Assessment
  for University a few months back. We did a service scan on a web server and found
  that way too many ports and services were running! But that wasn't the problem,
  well, not for us anyway. The problem was, is that we had 20 different software services
  and versions to google and write about.\r\n\r\nSo what is the process? We needed
  to find the software package's homepage, find what the latest version of the package
  is for the development tree that was used, find out how old the version the web
  server was running was and then try to find any known vulnerabilities associated
  with that version. This is not too much hassle when you have to do it one to three
  times however when you have to do it twenty to fifty times it starts to become time
  consuming.\r\n\r\nSo in comes DevBUG. DevBUG is a web application which will be
  free for any one to use, no subscriptions or anything. It will be a search engine
  for software packages and their versions. Three times a day (every 8 hours) starting
  at 8AM GMT a backed spider will visit every software package's homepage looking
  for new versions, if it finds a new version this will be added to a database. So
  the idea is, to keep a record of software, their released versions, release dates
  and any vulnerabilities which may affect each version. So this is great to solve
  our original problem! We have a one stop shop for all the information we need! But
  what other uses does it have?\r\n\r\n"
wordpress_id: 695
wordpress_url: http://www.ethicalhack3r.co.uk/?p=695
date: '2010-05-21 16:05:21 +0100'
date_gmt: '2010-05-21 15:05:21 +0100'
---
<p>DevBUG is an idea that came to me while conducting a Vulnerability Assessment for University a few months back. We did a service scan on a web server and found that way too many ports and services were running! But that wasn't the problem, well, not for us anyway. The problem was, is that we had 20 different software services and versions to google and write about.</p>
<p>So what is the process? We needed to find the software package's homepage, find what the latest version of the package is for the development tree that was used, find out how old the version the web server was running was and then try to find any known vulnerabilities associated with that version. This is not too much hassle when you have to do it one to three times however when you have to do it twenty to fifty times it starts to become time consuming.</p>
<p>So in comes DevBUG. DevBUG is a web application which will be free for any one to use, no subscriptions or anything. It will be a search engine for software packages and their versions. Three times a day (every 8 hours) starting at 8AM GMT a backed spider will visit every software package's homepage looking for new versions, if it finds a new version this will be added to a database. So the idea is, to keep a record of software, their released versions, release dates and any vulnerabilities which may affect each version. So this is great to solve our original problem! We have a one stop shop for all the information we need! But what other uses does it have?</p>
<p><a id="more"></a><a id="more-695"></a></p>
<p>Taking Nikto as an example here but not aiming anything directly at it. Nikto when it finds a server header and version will tell you if it is out of date and what the latest version is. Now the latest versions of software are always changing and it's hard for a tool to keep this information up to date. I envision DevBUG being used by tools to provide their users with the latest information!</p>
<p>But that's not all! Each software package indexed by DevBUG will have it's own RSS feed. So if your a server administrator and say you have Apache, PHP and some FTP server running. You can add each software package's RSS feed to your RSS reader and be informed of new releases on the day they are released! Making it easier to keep track of software updates!</p>
<p>The real power of DevBUG will be in its database. The more software packages indexed the better the service will be. I plan to launch DevBUG with a few hundred indexed software packages however I will be continually updating and adding new software packages. I will monitor what people are searching for and if we are not indexing that software package, we will add it. So the more DevBUG is used the better it will become.</p>
<p>DevBUG BETA will be launching sometime in the next couple of months. If you would like a sneak preview before the official launch, reply to this thread and I will PM you as soon as it is ready.</p>
<p><a href="http://www.devbug.co.uk" target="_blank">http://www.devbug.co.uk</a></p>
<p>Originally posted on <a href="http://www.dissectingthehack.com" target="_blank">http://www.dissectingthehack.com</a></p>
