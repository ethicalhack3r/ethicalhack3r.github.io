---
layout: post
status: publish
published: true
title: Webserverwatcher.py
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
wordpress_id: 150
wordpress_url: http://www.ethicalhack3r.co.uk/?p=150
date: '2009-02-15 01:25:16 +0000'
date_gmt: '2009-02-15 01:25:16 +0000'
---
<p>During our last information gathering and vulnerability assessment project our team realised that the IP address and web server software had changed from when we initially started out. Some time during the project the IT department had changed servers, which meant that some of our data from before the change was now obsolete.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>Some one on our team came up with an idea for a program that would monitor the server for any changes and notify us when it had happened. We would then know as soon as possible and could document this in our final report.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>The following Python code checks the web server every hour for changes in IP address, HTTP server header and x-powered-by header. If it notices any change it logs it to a log file aptly named log.txt.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>Here is the code:</p>
<p><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/02/webserverwatcher.py">webserverwatcher.py</a></p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>Any feedback welcomed!</p>
