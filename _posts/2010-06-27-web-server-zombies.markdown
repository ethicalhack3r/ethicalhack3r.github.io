---
layout: post
status: publish
published: true
title: Web server zombies
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "Every now and then I like to visit black-hat community forums for a number
  of legitimate reasons. I like to see what the other side are up to, what they are
  buying/selling, at what price, who they are targeting, the skill level of the attackers,
  what exploitation techniques they use, etc. Visiting these underground community
  forums passively can be a great learning experience.\r\n\r\nI had read stories about
  servers or web servers more specifically being targeted over personal computers
  for their use in DDoS attacks. Using a server rather than a client as a zombie means
  that the attackers have higher bandwidth,  RAM, CPU and other resources at their
  disposal. Servers are generally more secure than clients as you would expect the
  people who set them up and manage them have a greater awareness of the risks involved.
  Although servers are generally more difficult to compromise, compromising 100 servers
  may be worth more than 1000 clients.\r\n\r\nWhile browsing a particular black-hat
  community forum I came across a post by a user who wanted to purchase compromised
  web servers and made a particular request that the servers should have his supplied
  PHP script pre-uploaded.\r\n\r\nThe PHP script was named 'shell.php' and contained
  the following lines;\r\n[php]\r\n $rand = rand(1,65000);\r\n $fp = fsockopen('udp://'.$host,
  $rand, $err, $errstr, 5);\r\n[/php]\r\n\r\n<a href=\"http://www.ethicalhack3r.co.uk/wp-content/uploads/2010/06/Screen-shot-2010-06-27-at-21.25.27.png\"><img
  src=\"http://www.ethicalhack3r.co.uk/wp-content/uploads/2010/06/Screen-shot-2010-06-27-at-21.25.27-300x144.png\"
  alt=\"\" title=\"Screen shot 2010-06-27 at 21.25.27\" width=\"300\" height=\"144\"
  class=\"alignnone size-medium wp-image-731\" /></a>\r\n\r\n"
wordpress_id: 723
wordpress_url: http://www.ethicalhack3r.co.uk/?p=723
date: '2010-06-27 21:21:26 +0100'
date_gmt: '2010-06-27 20:21:26 +0100'
---
<p>Every now and then I like to visit black-hat community forums for a number of legitimate reasons. I like to see what the other side are up to, what they are buying/selling, at what price, who they are targeting, the skill level of the attackers, what exploitation techniques they use, etc. Visiting these underground community forums passively can be a great learning experience.</p>
<p>I had read stories about servers or web servers more specifically being targeted over personal computers for their use in DDoS attacks. Using a server rather than a client as a zombie means that the attackers have higher bandwidth,  RAM, CPU and other resources at their disposal. Servers are generally more secure than clients as you would expect the people who set them up and manage them have a greater awareness of the risks involved. Although servers are generally more difficult to compromise, compromising 100 servers may be worth more than 1000 clients.</p>
<p>While browsing a particular black-hat community forum I came across a post by a user who wanted to purchase compromised web servers and made a particular request that the servers should have his supplied PHP script pre-uploaded.</p>
<p>The PHP script was named 'shell.php' and contained the following lines;<br />
[php]<br />
 $rand = rand(1,65000);<br />
 $fp = fsockopen('udp://'.$host, $rand, $err, $errstr, 5);<br />
[/php]</p>
<p><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2010/06/Screen-shot-2010-06-27-at-21.25.27.png"><img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2010/06/Screen-shot-2010-06-27-at-21.25.27-300x144.png" alt="" title="Screen shot 2010-06-27 at 21.25.27" width="300" height="144" class="alignnone size-medium wp-image-731" /></a></p>
<p><a id="more"></a><a id="more-723"></a></p>
<p>The <a href="http://php.net/manual/en/function.fsockopen.php" target="_blank">fsockopen</a> PHP function opens a socket connection to a resource. As you can see from the code contained within the script, they are using the UDP protocol and opening sockets to random ports. This is known as a UDP Flood Attack. If you can imagine hundreds of web servers hosting this script, the attacker could write a simple script on his host machine to send simultaneous commands to all of them. With hundreds of web servers sending thousands of UDP packets each to a victim, it wouldn't take long for it to go down. The PHP script could be uploaded to the compromised web server in a number of different ways.</p>
<p>Moral of the story?<br />
This confirms to be what I had previously read. Attackers are starting to favor targeting servers rather than clients as their chosen zombies. Browsing black hat community forums now and then can be an enlightening exercise. I also ran across some other shenanigans while on the forums which certainly got me thinking.</p>
