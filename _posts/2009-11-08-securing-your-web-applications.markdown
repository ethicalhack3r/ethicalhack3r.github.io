---
layout: post
status: publish
published: true
title: Securing your web applications
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "The World Wide Web and the applications that run on it have come a long
  way since the invention of HTML by Tim Berners-Lee (British man I might add) in
  the early 1990’s. Back then the World Wide Web was a static web of text, images
  and hyperlinks. Nowadays we have the privilege (sometimes not) of having whole communities
  which solely exist in a dynamically evolving cyberspace with wikis, blogs, social
  networking, video sharing and a lot more. “Web 2.0” would not exist without the
  complex web applications that run on the millions of web servers across the globe.\r\n\r\n<strong><span
  style=\"text-decoration: underline;\"></span>\r\n</strong>\r\n\r\n<strong>So how
  do we go about securing our web applications?</strong>\r\n\r\n"
wordpress_id: 408
wordpress_url: http://www.ethicalhack3r.co.uk/?p=408
date: '2009-11-08 13:03:25 +0000'
date_gmt: '2009-11-08 13:03:25 +0000'
---
<p>The World Wide Web and the applications that run on it have come a long way since the invention of HTML by Tim Berners-Lee (British man I might add) in the early 1990’s. Back then the World Wide Web was a static web of text, images and hyperlinks. Nowadays we have the privilege (sometimes not) of having whole communities which solely exist in a dynamically evolving cyberspace with wikis, blogs, social networking, video sharing and a lot more. “Web 2.0” would not exist without the complex web applications that run on the millions of web servers across the globe.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p><strong>So how do we go about securing our web applications?</strong></p>
<p><a id="more"></a><a id="more-408"></a></p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>There are many different ways in which web applications can be made more secure. In this article I am going to cover a few tools and techniques which make this possible.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p><strong>WAF:</strong><br />
Web Application Firewall’s are applications which filter HTTP traffic looking for malicious code which could be used in attacks such as SQL Injection , Cross Site Scripting (XSS), File Inclusion and more. </p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>According to OWASP (Open Web Application Security Project), the important criteria in selecting a WAF is the following:</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>Very Few False Positives<br />
Strength of Default<br />
Power and Ease of Learn Mode<br />
Types of Vulnerabilities it can prevent<br />
Ability to keep individual users constrained to their current session<br />
Ability to be configured to prevent ANY specific problem<br />
Form Factor: Software vs. Hardware</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p><strong>Web Application Vulnerability Scanners:</strong><br />
Web Application vulnerability scanners help improve security and minimise the risk of the application being exploited by automatically crawling the site actively looking for vulnerabilities. Once the scan has been completed the web application scanner will produce a report with its findings which a professional information security practitioner should then investigate and patch. These scans should be run on a regular basis.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p><strong><br />
Updates/Patches:</strong><br />
When using ready-made web applications such as blogs, CMSs, wikis, etc. It pays to keep the application updated to the latest version and patched against the latest bugs. Ready-made web applications are often targeted for their wide deployment. If a SQL Injection vulnerability is found within a bespoke application, it would only affect that particular application. However if a SQL Injection vulnerability was found in WordPress for example it would affect their nearly 8 million version 2.8 users (at the time of writing) including big names such as PlayStation, EBay and others. This is what makes ready-made web applications a bigger target and why it pays to keep software updated and patched.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>References:<br />
<a href="http://www.rfc-editor.org/rfc/rfc1866.txt">http://www.rfc-editor.org/rfc/rfc1866.txt</a><br />
<a href="http://www.owasp.org/index.php/Web_Application_Firewall">http://www.owasp.org/index.php/Web_Application_Firewall</a><br />
<a href="http://wordpress.org/download/counter/">http://wordpress.org/download/counter/</a><br />
<a href="http://wordpress.org/showcase/">http://wordpress.org/showcase/</a></p>
