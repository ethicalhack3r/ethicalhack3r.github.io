---
layout: post
status: publish
published: true
title: Persistent BeEF
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "No, not that kind of beef!\r\n\r\n<img src=\"http://www.ethicalhack3r.co.uk/wp-content/uploads/2010/11/there-is-no-such-thing-as-mad-cow-disease-300x236.jpg\"
  alt=\"\" title=\"there-is-no-such-thing-as-mad-cow-disease\" width=\"300\" height=\"236\"
  class=\"aligncenter size-medium wp-image-820\" />\r\n\r\n<blockquote>\"BeEF is a
  browser exploitation framework. This tool will demonstrate the collecting of zombie
  browsers and browser vulnerabilities in real-time. It provides a command and control
  interface which facilitates the targeting of individual or groups of zombie browsers.\"</blockquote>\r\n<a
  href=\"http://www.bindshell.net/tools/beef/\" target=\"_blank\">http://www.bindshell.net/tools/beef/</a>\r\n\r\nBeEF
  is a tool used to enhance the exploitation of Cross Site Scripting (XSS) attacks
  by providing a complete and easy to use exploitation framework. It currently sports
  Metasploit integration, keylogging, port scanning, TOR detection and many other
  cool features. You no longer have an excuse to fill your reports with 'XSS' pop-up
  boxes!\r\n\r\n"
wordpress_id: 819
wordpress_url: http://www.ethicalhack3r.co.uk/?p=819
date: '2010-11-05 14:42:06 +0000'
date_gmt: '2010-11-05 13:42:06 +0000'
---
<p>No, not that kind of beef!</p>
<p><img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2010/11/there-is-no-such-thing-as-mad-cow-disease-300x236.jpg" alt="" title="there-is-no-such-thing-as-mad-cow-disease" width="300" height="236" class="aligncenter size-medium wp-image-820" /></p>
<blockquote><p>"BeEF is a browser exploitation framework. This tool will demonstrate the collecting of zombie browsers and browser vulnerabilities in real-time. It provides a command and control interface which facilitates the targeting of individual or groups of zombie browsers."</p></blockquote>
<p><a href="http://www.bindshell.net/tools/beef/" target="_blank">http://www.bindshell.net/tools/beef/</a></p>
<p>BeEF is a tool used to enhance the exploitation of Cross Site Scripting (XSS) attacks by providing a complete and easy to use exploitation framework. It currently sports Metasploit integration, keylogging, port scanning, TOR detection and many other cool features. You no longer have an excuse to fill your reports with 'XSS' pop-up boxes!</p>
<p><a id="more"></a><a id="more-819"></a></p>
<p>The original release of BeEF was written in PHP while the current development version has been ported to good old Ruby (in case you didn't know, Ruby is awesome). The Ruby version of BeEF, 0.4.1-alpha, was released last month and when complete will integrate other awesome XSS/browser exploitation tools such as Browser Rider, XSSShell and XSSTunnel.</p>
<p>The problem when exploiting XSS is that your payload only runs while the victim has the page with the payload open. Most users get bored easily and will quickly browse to another page or close it before you have the chance of launching your meterpreter payload. I have spent the last couple of months thinking of different ways to keep the victim on our infected page and over the past few days I have started to ask how other people solved this problem.</p>
<p>Here are some of my and other peoples suggestions in no particular order, thanks to my Twitter buddies and the BeEF mailing list for some of the following.</p>
<p>1.Pr0n (very affective if it is something out of the ordinary and the victim is a young male not in the work place, this was the most popular suggestion on Twitter)</p>
<p>2. A time wasting video or game (I especially like this one but more targeted ones may be more affective <a href="http://www.youtube.com/watch?v=txz1VyVMy6g" target="_blank">http://www.youtube.com/watch?v=txz1VyVMy6g</a>, video thanks to <a href="http://www.twitter.com/redmeat_uk">@redmeat_uk</a>)</p>
<p>3. Open a new tab with the BeEF hook included (most people won't even notice the new tab, thanks to Sussuro for the suggestion)</p>
<p>4. A pop-under add (this is an awesome idea <a href="https://secure.wikimedia.org/wikipedia/en/wiki/Pop-up_ad#Pop-under_ads" target="_blank">https://secure.wikimedia.org/wikipedia/en/wiki/Pop-up_ad#Pop-under_ads</a>, thanks to Vitaly Osipov from the BeEF mailing list)</p>
<p>5. A 100%x100% iframe to overlay the real page (problem here being the URL bar would be static, thanks to Wade)</p>
<p>6. Google (mail) Gadget (if your like me, I'm constantly logged into the Gmail web interface, problem is Google's cache prevents the persistence, after weeks of playing I've still yet to get this working, here is one of my early attempts <a href="http://pastie.org/private/v69ilhjyr8pcv3xtcq7nyq" target="_blank">http://pastie.org/private/v69ilhjyr8pcv3xtcq7nyq</a>)</p>
<p>So here are a couple of suggestions for you to get your persistent BeEF zombie. I was asked by one of the BeEF devs (Wade) to implement a persistent feature into BeEF itself, I will give it my best shot over the next month or so. In the meantime, what methods can you think of to keep a persistent BeEF zombie?</p>
<p><a href="http://code.google.com/p/beef/" target="_blank">http://code.google.com/p/beef/</a></p>
