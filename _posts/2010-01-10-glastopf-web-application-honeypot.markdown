---
layout: post
status: publish
published: true
title: Glastopf - Web Application Honeypot
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "<img src=\"http://www.ethicalhack3r.co.uk/wp-content/uploads/2010/01/glastopf.png\"
  alt=\"\" title=\"glastopf\" width=\"204\" height=\"83\" class=\"alignnone size-full
  wp-image-497\" />\r\n\r\n<strong>\r\n</strong>\r\n\r\nI bought an old battered PC
  over the weekend with the goal of installing a honeypot. I had never installed a
  honeypot before so wasn't quite sure what to expect. At first I decided on <a href=\"http://dionaea.carnivore.it/\"
  target=\"_blank\">Dionaea</a> the succsesor to Nepenthes, I had heard great things
  about Nepenthes from a friend of mine (<a href=\"http://infosanity.wordpress.com/\"
  target=\"_blank\">Infosanity</a>). After going through the installation process,
  I couldn't get Dionaea to 'make' with the right Python version detected (> 3.0),
  after about an hour of playing around I decided to give <a href=\"http://glastopf.org/\"
  target=\"_blank\">Glastopf</a> a try.\r\n\r\n<strong>\r\n</strong>\r\n\r\n"
wordpress_id: 496
wordpress_url: http://www.ethicalhack3r.co.uk/?p=496
date: '2010-01-10 19:08:39 +0000'
date_gmt: '2010-01-10 19:08:39 +0000'
---
<p><img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2010/01/glastopf.png" alt="" title="glastopf" width="204" height="83" class="alignnone size-full wp-image-497" /></p>
<p><strong><br />
</strong></p>
<p>I bought an old battered PC over the weekend with the goal of installing a honeypot. I had never installed a honeypot before so wasn't quite sure what to expect. At first I decided on <a href="http://dionaea.carnivore.it/" target="_blank">Dionaea</a> the succsesor to Nepenthes, I had heard great things about Nepenthes from a friend of mine (<a href="http://infosanity.wordpress.com/" target="_blank">Infosanity</a>). After going through the installation process, I couldn't get Dionaea to 'make' with the right Python version detected (> 3.0), after about an hour of playing around I decided to give <a href="http://glastopf.org/" target="_blank">Glastopf</a> a try.</p>
<p><strong><br />
</strong></p>
<p><a id="more"></a><a id="more-496"></a></p>
<blockquote><p>Glastopf is a Honeypot which emulates thousands vulnerabilities to gather data from attacks targeting web applications. The principle behind it is very simple: Reply the correct response to the attacker exploiting the web application. The project has been kicked off by Lukas Rist around one year ago and the results we are got during this time are very promising and an incentive to put even more effort in the development of this unique tool.</p></blockquote>
<p><strong><br />
</strong></p>
<p>Glastopf was very easy to install and configure, I simply downloaded the subversion trunk and ran it with "sudo python webserver.py". Glastopf was up and running however not configured. Glastopf gives you the option to save the honeypot logs to a MySQL database, for this all you have to do is install MySQL and python-mysql, set up the database/tables and add the 'mysql.py' plugin to the configuration file. Glastopf provides you with the table structure already set out in the '/structure/log.sql' file, to import the file I used 'mysql-navigator' (sudo apt-get install mysql-navigator), mysql-navigator is a GUI client for MySQL, you can however just use the MySQL command line client.</p>
<p><strong><br />
</strong></p>
<p>All I had to do now was forward port 80 on my router to the machine with Glastopf running on it. I will now leave the machine running for a few days and hopefully come back with some statistics, which I will of course be posting and making pretty little graphs out of. :) If the initial statistics and hits are positive I will try to keep the honeypot running indefinitely and some how link the stats to the blog.</p>
