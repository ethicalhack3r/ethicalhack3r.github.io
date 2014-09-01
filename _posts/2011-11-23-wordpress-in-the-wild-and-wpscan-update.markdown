---
layout: post
status: publish
published: true
title: WordPress 'In the Wild' and WPScan Update
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "As part of my on-going interest in WordPress security I wanted to find out
  for myself what the state of security was like on installations in the wild.\r\n\r\nA
  list of servers running WordPress was acquired from <a href=\"http://www.shodanhq.com/\"
  target=\"_blank\">Shodan</a> by searching for a particular HTTP response header
  and its value. The list contained 10,000 entries, I don't know for sure, but I assume
  the list contained servers from around the world and was fairly random.\r\n\r\nAn
  Open Source project I have been working on, <a href=\"http://code.google.com/p/wpscan/\"
  target=\"_blank\">WPScan</a>, a WordPress security scanner, was used to passively
  scan 100 of those WordPress installations. This was done partly to test the scanner
  for any defects and also to gather data about the security of WordPress installations
  in the wild.\r\n\r\n"
wordpress_id: 16592
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16592
date: '2011-11-23 00:36:47 +0000'
date_gmt: '2011-11-23 00:36:47 +0000'
---
<p>As part of my on-going interest in WordPress security I wanted to find out for myself what the state of security was like on installations in the wild.</p>
<p>A list of servers running WordPress was acquired from <a href="http://www.shodanhq.com/" target="_blank">Shodan</a> by searching for a particular HTTP response header and its value. The list contained 10,000 entries, I don't know for sure, but I assume the list contained servers from around the world and was fairly random.</p>
<p>An Open Source project I have been working on, <a href="http://code.google.com/p/wpscan/" target="_blank">WPScan</a>, a WordPress security scanner, was used to passively scan 100 of those WordPress installations. This was done partly to test the scanner for any defects and also to gather data about the security of WordPress installations in the wild.</p>
<p><a id="more"></a><a id="more-16592"></a></p>
<p>Below are the results:</p>
<p>The readme.html file was present: 85/100<br />
An error_log file was present: 2/100<br />
Was effected by Full Path Disclosure (FPD): 59/100<br />
Were running the latest version (3.2.1): 44/100<br />
The oldest version found running was 2.0.3.<br />
Had the version in the 'generator' meta tag: 95/100<br />
The version was detected through 'advanced' fingerprinting: 4/100<br />
The version was not detected: 1/100<br />
Timthumb file detected: 10/100</p>
<p>Metasploit integration has been put on hold due to the deprecation of the MSF XML-RPC server and implementation of the new MessagePack RPC. There are plans to possibly integrate other tools such as fimap, sqlmap and others, see issue <a href="http://code.google.com/p/wpscan/issues/detail?id=56" target="_blank">56</a>. We hope to release a new version of WPScan before the end of the year. I'd like to thank all of WPScan's contributors for making this possible.</p>
<p>To contribute or report a bug, you can do so here; <a href="http://code.google.com/p/wpscan/issues/list" target="_blank">http://code.google.com/p/wpscan/issues/list </a></p>
<p>The latest code base is available from our subversion repository, which should always be stable enough to run and will contain the latest vulnerability data. The following command can be issued to checkout the code; "svn checkout http://wpscan.googlecode.com/svn/trunk/ ./wpscan"</p>
<p>Some other good news is that WPScan was implemented into <a href="http://www.backtrack-linux.org/" target="_blank">Backtack</a> and will be a part of the next version of <a href="http://samurai.inguardians.com/" target="_blank">SamuraiWTF</a>.</p>
