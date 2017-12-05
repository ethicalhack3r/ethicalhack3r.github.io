---
layout: post
status: publish
published: true
title: Windows 2000 & Fast|Track
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "A couple of weeks ago I was going to test Fast|Track against a Windows 98
  machine however I couldn't get my wireless card to work on it and I couldn't be
  arsed moving the PC out of the spare room. I finally got Windows 2000 with no patches
  or updates up and running. I installed Windows 2000 as according to many its very
  vulnerable.\r\n\r\nFast|Track is an automated tool that comes pre installed in BackTrack.
  It scans an ip address or range for open ports using NMap, once it has scanned the
  machine(s) it trys every exploit for the open ports found using NMap's autopwn feature
  via Metasploit. It doesn't take any notice of NMap's OS discovery, so even if NMap
  discovers that the machine is running Windows 2000 with 100% accuracy (it didn't),
  it will still try other OS exploits.\r\n\r\nAfter Fast|Track had finished scanning
  and exploiting It gave me 4 active shell sessions that it had spawned from successful
  exploits."
wordpress_id: 55
wordpress_url: http://www.ethicalhack3r.co.uk/?p=55
date: '2008-11-17 18:18:52 +0000'
date_gmt: '2008-11-17 18:18:52 +0000'
---
<p>A couple of weeks ago I was going to test Fast|Track against a Windows 98 machine however I couldn't get my wireless card to work on it. I finally got Windows 2000 with no patches or updates up and running. I installed Windows 2000 as according to many it's quite a vulnerable OS.</p>
<p>Fast|Track is an automated tool that comes pre installed in BackTrack. It scans an ip address or range for open ports using NMap, once it has scanned the machine(s) it tries every exploit for the open ports found using NMap's autopwn feature via Metasploit. It doesn't take any notice of NMap's OS discovery, so even if NMap discovers that the machine is running Windows 2000 with 100% accuracy (it didn't), it will still try other OS exploits.</p>
<p>After Fast|Track had finished scanning and exploiting It gave me 4 active shell sessions that it had spawned from successful exploits.</p>
<p>Windows 2000 with no updates or patches was successfully exploited via the following vulnerabilities:</p>
<p>SMB:</p>
<p>MS06_040_netapi</p>
<p>MS05_039_pnp</p>
<p>MS04_011_lsass</p>
<p>DCERPC:</p>
<p>MS03_026_dcom</p>
<p>After playing around with the remote shells for a few minutes I decided to replicate my findings using Metasploit3 only. I managed to replicate them all using the windows/shell/reverse_tcp payload, I originally tried them with the generic/perl/reverse_shell payload however this did not work, it gave an error which I did not write down. While I was there I thought I would try Metasploit's newish VNC reverse shell payload so I could have a visual representation of my Windows 2000 machine. In order to do this you have to start the built in VNC server in BackTrack, worked like a charm however the colour was a bit off and the connection was slow.</p>
<p>The moral of the story is to keep your systems updated and fully patched.</p>
<p>More info on <a title="FAST|TRACK" href="http://www.securestate.com/pages/press-release009.aspx" target="_blank">Fast|Track</a>.</p>
<p>More info on <a title="METASPLOIT" href="http://www.metasploit.com/" target="_blank">Metasploit</a>.</p>
<p>P.S. I also tried Metasploit's new MS08_067 RPC exploit however was unsuccessful.</p>
