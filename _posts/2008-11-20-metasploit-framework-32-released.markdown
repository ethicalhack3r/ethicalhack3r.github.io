---
layout: post
status: publish
published: true
title: Metasploit Framework 3.2 Released
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
wordpress_id: 68
wordpress_url: http://www.ethicalhack3r.co.uk/?p=68
date: '2008-11-20 17:45:41 +0000'
date_gmt: '2008-11-20 17:45:41 +0000'
---
<p>The new Metasploit Framework was released on the 19th November (yesterday). It has a massive change log with lots of tweaks and add ons. I will try and list the interesting ones here.</p>
<blockquote><p>Version 3.2 includes exploit modules for recent Microsoft flaws, such<br />
as MS08-041, MS08-053, MS08-059, MS08-067, MS08-068, and many more.</p></blockquote>
<p>I think I may have to test my Windows 2000 box again and see if any of the above work.</p>
<blockquote><p>The Windows payload stagers have been updated to support targets with<br />
NX CPU support. These stagers now allocate a read/write/exec segment of<br />
memory for all payload downloads and execution.</p></blockquote>
<p>Staggered payloads are the only ones I could get working against Windows 2000.</p>
<blockquote><p>This release includes a set of man-in-the-middle, authentication relay,<br />
and authentication capture modules. These modules can be integrated with<br />
a fake proxy (WPAD), a malicious access point (Karmetasploit), or basic<br />
network traffic interception to gain access to client machines. These<br />
modules tie together browser_autopwn, SMB relaying, and HTTP credential<br />
and form capturing to pillage data from client systems.</p></blockquote>
<p>Metasploit can now sniff traffic too!</p>
<blockquote><p>Egypt's new PHP payloads provide complete bind, reverse, and findsock<br />
support for PHP web application exploits. If you are sick of C99 and R57<br />
and looking to gain a "real" shell from one of the hundreds of RFI flaws<br />
listed on milw0rm, the new PHP payloads work great against multiple<br />
operating systems.</p></blockquote>
<p>Will have to have play with this one!</p>
<blockquote><p>The db_autopwn command has been revamped to support port-based limits,<br />
regex-based module matching, and limits on the number of spawned jobs. The<br />
end result is a way to quickly launch specific modules against a specific<br />
set of target machines. These changes were suggested and implemented by<br />
Marcell 'SkyOut' Dietl (Helith).</p></blockquote>
<p>This is the feature used by Fast|Track, doesn't mention an OS limitation, that would be the next logical step.</p>
<p>To download Metasploit Framework 3.2 <a title="metasploit 3.2" href="http://metasploit.com/framework/" target="_blank">click here.</a></p>
<p>To view the full change log <a title="metasploit 3.2 changelog" href="http://metasploit.com/documents/RELEASE-3.2.txt" target="_blank">click here.</a></p>
