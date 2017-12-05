---
layout: post
status: publish
published: true
title: Dionaea - Low interaction honeypot
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "After running Glastopf (<a href=\"http://www.ethicalhack3r.co.uk/2010/01/10/glastopf-web-application-honeypot/\">Glastopf
  – Web Application Honeypot</a>) for a few days and not getting any hits, I was a
  bit disappointed. I speculate that maybe you need to give web application honeypots
  more time to propagate across the Internet and get picked up by search engines to
  receive any significant hits, or even give the honeypot its own domain name. From
  my earlier post you will notice that I had tried to get Dionaea to run first.\r\n\r\nMarkus
  the lead developer of Dionaea got in contact after he read my post and saw that
  I was having trouble getting it running. It turned out to be a complete fail on
  my part, after following the instructions on the Dionaea <a href=\"http://dionaea.carnivore.it/\">homepage</a>,
  Dionaea installed perfectly fine, it was just a case of me not knowing how to run
  it properly.\r\n\r\n<strong>What is Dionaea?</strong>\r\n<blockquote>Dionaea is
  meant to be a nepenthes successor, embedding python as scripting language, using
  libemu to detect shellcodes, supporting ipv6 and tls</blockquote>\r\n\r\n<blockquote>Dionaea
  intention is to trap malware exploiting vulnerabilities exposed by services offerd
  to a network, the ultimate goal is gaining a copy of the malware.</blockquote>\r\n\r\n"
wordpress_id: 506
wordpress_url: http://www.ethicalhack3r.co.uk/?p=506
date: '2010-01-17 19:34:26 +0000'
date_gmt: '2010-01-17 19:34:26 +0000'
---
<p>After running Glastopf (<a href="http://www.ethicalhack3r.co.uk/2010/01/10/glastopf-web-application-honeypot/">Glastopf – Web Application Honeypot</a>) for a few days and not getting any hits, I was a bit disappointed. I speculate that maybe you need to give web application honeypots more time to propagate across the Internet and get picked up by search engines to receive any significant hits, or even give the honeypot its own domain name. From my earlier post you will notice that I had tried to get Dionaea to run first.</p>
<p>Markus the lead developer of Dionaea got in contact after he read my post and saw that I was having trouble getting it running. It turned out to be a complete fail on my part, after following the instructions on the Dionaea <a href="http://dionaea.carnivore.it/">homepage</a>, Dionaea installed perfectly fine, it was just a case of me not knowing how to run it properly.</p>
<p><strong>What is Dionaea?</strong></p>
<blockquote><p>Dionaea is meant to be a nepenthes successor, embedding python as scripting language, using libemu to detect shellcodes, supporting ipv6 and tls</p></blockquote>
<blockquote><p>Dionaea intention is to trap malware exploiting vulnerabilities exposed by services offerd to a network, the ultimate goal is gaining a copy of the malware.</p></blockquote>
<p><a id="more"></a><a id="more-506"></a></p>
<p>Dionaea offers the following services by default, SMB (main service offered), HTTP, FTP and TFTP.</p>
<p><strong>Here is an Nmap scan of the honeypot (first 1000 ports):</strong></p>
<blockquote><p>PORT STATE SERVICE<br />
21/tcp open ftp<br />
|_ ftp-anon: Anonymous FTP login allowed<br />
42/tcp open tcpwrapped<br />
80/tcp open http?<br />
|_ html-title: Directory listing for /<br />
135/tcp open msrpc?<br />
443/tcp open ssl/https?<br />
|_ sslv2: server still supports SSLv2<br />
|_ html-title: Directory listing for /<br />
445/tcp open microsoft-ds?</p></blockquote>
<p><strong>Statistics:</strong></p>
<p>Dionaea was running for 1 day, 11 hours and 44 minutes.<br />
The first hit took 14 hours, 10 minutes and 16 seconds.<br />
During that time there were 164 total remote hits.<br />
Top 3 ports: 445, 135 and 0. (in order of hits)</p>
<p>RPC Vulnerabilities exploited:<br />
<a href="http://www.microsoft.com/technet/security/bulletin/MS03-026.mspx">MS03-26</a><br />
<a href="http://www.microsoft.com/technet/security/Bulletin/MS04-011.mspx">MS04-11</a><br />
<a href="http://www.microsoft.com/technet/security/Bulletin/MS04-012.mspx">MS04-12</a><br />
<a href="http://www.microsoft.com/technet/security/Bulletin/ms05-017.mspx">MS05-017</a><br />
<a href="http://www.microsoft.com/technet/security/bulletin/ms07-065.mspx">MS07-065</a><br />
<a href="http://www.microsoft.com/technet/security/bulletin/MS06-066.mspx">MS06-66</a><br />
<a href="http://www.microsoft.com/TECHNET/SECURITY/BULLETIN/MS05-039.MSPX">MS05-39</a><br />
<a href="http://www.microsoft.com/technet/security/Bulletin/MS08-067.mspx">MS08-67</a><br />
<a href="http://www.microsoft.com/technet/security/Bulletin/MS04-011.mspx">MS04-11</a></p>
<p>Captured Malware:<br />
14a09a48ad23fe0ea5a180bee8cb750a<br />
31ab688b36e7d8e5ce1082faa95f730e<br />
53fed7473c878ad4b4e57a42c99df38f<br />
69101c9cbc14f5778efa795bbd25e02c<br />
833cda5b5bef5989deb6bf57c557ce30<br />
93094c5ea5a47e5c5f3e020f2c434c35<br />
df51e3310ef609e908a6b487a28ac068<br />
f2d8d3ef1d5623bdfa9a0eebd4fc2266<br />
f8815cdca238ad5ab566f05f5a6335a4</p>
<p>You can search for the malware associated with the MD5 hashes above here: <a href="http://www.virustotal.com/buscaHash.html" target="_blank">http://www.virustotal.com/buscaHash.html</a></p>
<p>Dionaea is excellent, I feel that I have only scratched the surface of its true potential. For now unfortunately, the honeypot is turned off until I find a more suitable place to store it other than my living room floor. Hopefully I will do more work in the area of honeypots in the near future once I have some more spare time.</p>
