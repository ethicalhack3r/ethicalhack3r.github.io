---
layout: post
status: publish
published: true
title: WordPress Brute Force Tool
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "Following on from my previous post <a href=\"http://www.ethicalhack3r.co.uk/security/patching-wordpress-username-disclosure/\">Patching
  WordPress Username Disclosure</a> I got bored over the weekend and decided to implement
  Veronica Valeros's username disclosure technique into a WordPress password brute
  force tool.\r\n\r\nIt is nothing revolutionary or difficult to code, but it may
  come in handy one day on a pentest or web application assessment, mainly to automate
  the process.\r\n\r\nCurrently you can use the tool in 3 different ways.\r\n\r\n"
wordpress_id: 16206
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16206
date: '2011-06-13 14:36:22 +0100'
date_gmt: '2011-06-13 13:36:22 +0100'
---
<p>Following on from my previous post <a href="http://www.ethicalhack3r.co.uk/security/patching-wordpress-username-disclosure/">Patching WordPress Username Disclosure</a> I got bored over the weekend and decided to implement Veronica Valeros's username disclosure technique into a WordPress password brute force tool.</p>
<p>It is nothing revolutionary or difficult to code, but it may come in handy one day on a pentest or web application assessment, mainly to automate the process.</p>
<p>Currently you can use the tool in 3 different ways.</p>
<p><a id="more"></a><a id="more-16206"></a></p>
<blockquote><p>Only the '--url' option:<br />
Enumerate wordpress usernames.</p>
<p>The '--wordlist' option:<br />
Enumerate wordpress usernames.<br />
Start a dictionary attack on all usernames enumerated.</p>
<p>The '--username' option:<br />
Specify a single username to start the dictionary attack on. </p></blockquote>
<p>I won't be releasing the tool, not yet anyway, I may release it in future.</p>
<p>Here is a video of it in action:</p>
<p><iframe width="425" height="349" src="http://www.youtube.com/embed/pRj3G12xFjU" frameborder="0" allowfullscreen></iframe></p>
<p><strong>UPDATE</strong></p>
<p>The video of my tool seems to have raised lots of interest and questions.</p>
<p>Please understand that I think this this tool is quite trivial to code and I am very surprised that it got so much attention.</p>
<p>One question that was raised more than once, was, why did I not release the code?!</p>
<p>The reason I did not release it is because I was considering the ethicality of such a tool being released. I first wanted to guage the interest in such a tool and if interest was positive, expand the tool further.</p>
<p>I will go into further detail as the code base expands. I can confirm that I will be releasing the code as part of a bigger project called <a href="http://code.google.com/p/wpscan/" target="_blank">WPScan</a>.</p>
