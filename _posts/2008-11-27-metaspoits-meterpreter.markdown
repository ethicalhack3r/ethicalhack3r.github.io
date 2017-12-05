---
layout: post
status: publish
published: true
title: Metaspoit's meterpreter
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
wordpress_id: 105
wordpress_url: http://www.ethicalhack3r.co.uk/?p=105
date: '2008-11-27 16:38:29 +0000'
date_gmt: '2008-11-27 16:38:29 +0000'
---
<p>Meterpreter is a Metasploit payload designed for post-exploitation tasks.<br />
<strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<blockquote><p>One of the steps involved in completely automating exploitation is post-exploitation automation. This is where steps are taken to automate the tasks that are performed after successfully exploiting a target host. The meterpreter implementation in Metasploit 3.0 defines a programmatic interface for the attacker that helps to facilitate this automation, such as by making it easy to interact with processes, networking, and the file system. While all of this has been present for some time, we have only recently added support for Meterpreter scripts. The purpose of meterpreter scripts are to give end-users an easy interface to write quick scripts that can be run against remote targets after successful exploitation. In the long term, we'll make it so that these scripts can run automatically each time a Meterpreter session is created, thus making the post-exploitation process completely automated.</p></blockquote>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>After playing around with it for a few hours Ive realised that its a very powerful tool for any pen tester to have. I tried in vain to record the exploitation and post exploitation process using the open source screen recorder 'CamStudio' however I was unsuccessfully due to it not recording some of the screen. I will try and find alternative software or have another go with CamStudio in the near future to show you all how powerful the meterpreter payload really is.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>Meterpreter has been around since Metasploit version 3 however in the newest version of Metasploit it seems that the meterpreter DLL that gets uploaded to the target machine is no longer detected by anti virus software. In theory Metasploit could scan random IP ranges, exploit targets using autopwn, grab the administrator hashes and then email them to the attacker. A script kiddies wet dream.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>For more info on meterpreter <a href="http://blog.metasploit.com/2006/10/meterpreter-scripts-and-msrt.html">click here.</a></p>
<p>To view a video of meterpreter in action <a href="http://www.irongeek.com/i.php?page=videos/bypassing-anti-virus-with-metasploit">click here.</a></p>
