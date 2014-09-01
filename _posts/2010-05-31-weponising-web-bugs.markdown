---
layout: post
status: publish
published: true
title: Weponising Web bugs
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "Back in March 2009 I wrote a blog post about using web bugs in information
  gathering, found <a href=\"http://www.ethicalhack3r.co.uk/security/using-a-web-bug-for-information-gathering/\"
  target=\"_blank\">here</a>. For those unfamiliar with web bugs;\r\n\r\n<blockquote>\"A
  web bug is an object that is embedded in a web page  or e-mail  and is usually invisible
  to the user but allows checking that a user has viewed the page or e-mail. One common
  use is in e-mail tracking. Alternative names are web beacon, tracking bug, tracking
  pixel, pixel tag, 1×1 gif, and clear gif.\"</blockquote>\r\n<a href=\"http://en.wikipedia.org/wiki/Web_bug\">http://en.wikipedia.org/wiki/Web_bug</a>\r\n\r\nAt
  the time I thought I had stumbled across something unique and that no one had really
  understood the implications of allowing the posting of remote images in web applications.
  The idea originally came to me when playing around with Adrian Crenshaw's (<a href=\"http://www.irongeek.com/\">IronGeek</a>)
  logo. I wasn't aware of the term 'web bug' so I explained to Adrian my concept,
  he knew what a web bug was and seemed to be well aware of their consequences.\r\n\r\n"
wordpress_id: 697
wordpress_url: http://www.ethicalhack3r.co.uk/?p=697
date: '2010-05-31 16:27:12 +0100'
date_gmt: '2010-05-31 15:27:12 +0100'
---
<p>Back in March 2009 I wrote a blog post about using web bugs in information gathering, found <a href="http://www.ethicalhack3r.co.uk/security/using-a-web-bug-for-information-gathering/" target="_blank">here</a>. For those unfamiliar with web bugs;</p>
<blockquote><p>"A web bug is an object that is embedded in a web page  or e-mail  and is usually invisible to the user but allows checking that a user has viewed the page or e-mail. One common use is in e-mail tracking. Alternative names are web beacon, tracking bug, tracking pixel, pixel tag, 1×1 gif, and clear gif."</p></blockquote>
<p><a href="http://en.wikipedia.org/wiki/Web_bug">http://en.wikipedia.org/wiki/Web_bug</a></p>
<p>At the time I thought I had stumbled across something unique and that no one had really understood the implications of allowing the posting of remote images in web applications. The idea originally came to me when playing around with Adrian Crenshaw's (<a href="http://www.irongeek.com/">IronGeek</a>) logo. I wasn't aware of the term 'web bug' so I explained to Adrian my concept, he knew what a web bug was and seemed to be well aware of their consequences.</p>
<p><a id="more"></a><a id="more-697"></a></p>
<p>What really shocked me was that popular Content Management Systems such as Joomla and forum web applications such as vBulletin and phpBB allowed the posting of web bugs within their web applications. In places such as avatars, comments, posts, ect. So what consequences does this have? You may be asking yourself. </p>
<p>For example; If you were targeting a particular company or individual you could use web bugs to find the web application administrators IP address, the IP address of a particular forum user or the IP addresses of all users that used that application. It's not only limited to IP addresses, Adrian's logo is a good example of some of the information which can be retrieved however it is not excessive. The advertising industry use web bugs regularly to track users activities however I have not seen much information on them being used as part of an attack.</p>
<p>In my original post I used a simple PHP script with image headers which captured the relevant information. It was quite trivial to put together and Adrian's logo source code is a good place to start. I think web application developers should do more in protecting their users privacy when it comes to using web bugs. Much like an upload function the same principle could be used with remote images, or just not allow remote images at all to be embedded in the application.</p>
<p>To see how prevalent web bugs are you can install the 'Web Bug Detector' Greasemonkey script, found <a href="http://userscripts.org/scripts/show/35051" target="_blank">here</a>. </p>
