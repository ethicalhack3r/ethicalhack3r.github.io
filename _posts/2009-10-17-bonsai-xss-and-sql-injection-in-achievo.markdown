---
layout: post
status: publish
published: true
title: "[BONSAI] XSS and SQL Injection in Achievo <= 1.3.4"
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "Today Andres Riancho owner of <a title=\"BONSAI\" href=\"http://www.bonsai-sec.com/\"
  target=\"_blank\">Bonsai Information Security</a> (Argentina) and lead developer
  of <a title=\"W3AF\" href=\"http://w3af.sourceforge.net/\" target=\"_blank\">w3af</a>
  has released a couple of advisories on vulnerabilities in <a title=\"Achievo\" href=\"http://www.achievo.org/\"
  target=\"_blank\">Achievo</a> &lt;= 1.3.4 which we found a few months ago after
  our vulnerability research into common web applications.\r\n\r\nThe affected web
  application is Achievo &lt;= 1.3.4. Achievo suffered from multiple simple persistent
  XSS vulnerabilities within their scheduler module and an SQL injection vulnerability
  within their dispatch.php file.\r\n\r\nAchievo is a flexible web-based resource
  management tool for business environments. Achievo's resource management capabilities
  will enable organisations to support their business processes in a simple, but effective
  manner.\r\n\r\n"
wordpress_id: 345
wordpress_url: http://www.ethicalhack3r.co.uk/?p=345
date: '2009-10-17 13:10:22 +0100'
date_gmt: '2009-10-17 13:10:22 +0100'
---
<p>Today Andres Riancho owner of <a title="BONSAI" href="http://www.bonsai-sec.com/" target="_blank">Bonsai Information Security</a> (Argentina) and lead developer of <a title="W3AF" href="http://w3af.sourceforge.net/" target="_blank">w3af</a> has released a couple of advisories on vulnerabilities in <a title="Achievo" href="http://www.achievo.org/" target="_blank">Achievo</a> &lt;= 1.3.4 which we found a few months ago after our vulnerability research into common web applications.</p>
<p>The affected web application is Achievo &lt;= 1.3.4. Achievo suffered from multiple simple persistent XSS vulnerabilities within their scheduler module and an SQL injection vulnerability within their dispatch.php file.</p>
<p>Achievo is a flexible web-based resource management tool for business environments. Achievo's resource management capabilities will enable organisations to support their business processes in a simple, but effective manner.</p>
<p><a id="more"></a><a id="more-345"></a></p>
<p>I and Andres worked on quite an novel (to me) payload for the persistent XSS vulnerability which we found. Essentially the payload we worked on was an AJAX script which sent POST requests to the vulnerable application in order to escalate a users privileges. A write up by Andres on the payload can be found here: <a title="Achievo Payload" href="http://www.bonsai-sec.com/blog/index.php/cross-site-scripting-payloads/" target="_blank">http://www.bonsai-sec.com/blog/index.php/cross-site-scripting-payloads/</a></p>
<p>For the original advisories:</p>
<p><a title="Achievo XSS" href="http://www.bonsai-sec.com/research/vulnerabilities/achievo-multiple-xss-0101.txt" target="_blank">Multiple XSS in Achievo</a></p>
<p><a title="Achievo SQL Injection" href="http://www.bonsai-sec.com/research/vulnerabilities/achievo-sql-injection-0102.txt" target="_blank">SQL injection in Achievo</a></p>
<p><em>All vulnerabilities found were disclosed in an ethical manner. We worked along side the affected application developers in order to fix the vulnerabilities found. The advisories were not published until the developers had fixed and updated their software.</em></p>
