---
layout: post
status: publish
published: true
title: Netsparker - The next gen web app scanner
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "<img class=\"aligncenter size-full wp-image-328\" title=\"netsparker-logo-splash\"
  src=\"http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/10/netsparker-logo-splash.png\"
  alt=\"netsparker-logo-splash\" width=\"334\" height=\"90\" />\r\n\r\n<strong><span
  style=\"text-decoration: underline;\"></span>\r\n</strong>\r\n\r\nI was lucky enough
  to get my greasy hands on a copy of <em>'Netsparker Final BETA'</em> from Mavituna
  Security's project leader Ferruh Mavituna.\r\n<strong><span style=\"text-decoration:
  underline;\"></span>\r\n</strong>\r\n<blockquote>Netsparker can crawl, attack and
  identify vulnerabilities in all custom web applications regardless of the platform
  and the technology it's built on, just like an actual attacker. It can identify
  web application vulnerabilities like SQL Injection, Cross-site Scripting (XSS),
  Remote Code Execution and many more.</blockquote>\r\n<strong><span style=\"text-decoration:
  underline;\"></span>\r\n</strong>\r\n\r\nI tested Netsparker v0.9.9.9935 (FINAL
  BETA) against DVWA v1.0.6. Setting up a new scan was as easy as putting in the DVWA
  URL, adding the security/PHPSESSID cookies and then selecting the different vulnerabilities
  to scan for. Netsparker picked up on almost all of DVWA's vulnerabilities, even
  the SQL Injection vulnerability which a lot of web application scanners have problems
  picking up for some reason. The vulnerabilities that it did not pick up on I sent
  in an email to Ferruh, he has already added scans for some of these and will implement
  others in future.\r\n\r\n"
wordpress_id: 327
wordpress_url: http://www.ethicalhack3r.co.uk/?p=327
date: '2009-10-11 12:22:54 +0100'
date_gmt: '2009-10-11 12:22:54 +0100'
---
<p><img class="aligncenter size-full wp-image-328" title="netsparker-logo-splash" src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/10/netsparker-logo-splash.png" alt="netsparker-logo-splash" width="334" height="90" /></p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>I was lucky enough to get my greasy hands on a copy of <em>'Netsparker Final BETA'</em> from Mavituna Security's project leader Ferruh Mavituna.<br />
<strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<blockquote><p>Netsparker can crawl, attack and identify vulnerabilities in all custom web applications regardless of the platform and the technology it's built on, just like an actual attacker. It can identify web application vulnerabilities like SQL Injection, Cross-site Scripting (XSS), Remote Code Execution and many more.</p></blockquote>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>I tested Netsparker v0.9.9.9935 (FINAL BETA) against DVWA v1.0.6. Setting up a new scan was as easy as putting in the DVWA URL, adding the security/PHPSESSID cookies and then selecting the different vulnerabilities to scan for. Netsparker picked up on almost all of DVWA's vulnerabilities, even the SQL Injection vulnerability which a lot of web application scanners have problems picking up for some reason. The vulnerabilities that it did not pick up on I sent in an email to Ferruh, he has already added scans for some of these and will implement others in future.</p>
<p><a id="more"></a><a id="more-327"></a></p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>The GUI of Netsparker is really clean and easy to navigate. It includes a dashboard where you can visualise the progress of your scan, a vulnerability chart showing the criticality of the vulnerabilities found, live HTTP packet request/responses and much more.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>After the scan has finished Netsparker allows you to export the results in a nice easy to read HTML or XML report. As well as crawling and scanning for vulnerabilities Netsparker also aids the exploitation of some of the vulnerabilities; it aids you in executing SQL commands against the vulnerable application much like using an SQL client, it also has a 'Get Shell' feature which injects a reverse shell payload into the vulnerable application which connects back to your testing box allowing you to execute commands on the underlying OS.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>Netsparker is still in BETA and I have to say has made it into my top 3 web application tools I have played with. Netsparker will be commercially available, I am told at a lower price than most commercial web application vulnerability scanners.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>For more information: <a title="Netsparker" href="http://www.mavitunasecurity.com/" target="_blank">http://www.mavitunasecurity.com/</a></p>
<p>Follow Netsparker on Twitter: <a title="twitter netsparker" href="http://www.twitter.com/netsparker" target="_blank">http://www.twitter.com/netsparker</a></p>
