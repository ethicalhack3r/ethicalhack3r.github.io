---
layout: post
status: publish
published: true
title: WordPress Plugin Disqus Comment System XSS
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "# Exploit Title: WordPress Plugin Disqus Comment System < = 2.68 Reflected
  Cross-Site Scripting (XSS)\r\n# Google Dork: inurl:/wp-content/plugins/disqus-comment-system/\r\n#
  Date: 11.12.11\r\n# Author: Ryan Dewhurst (@ethicalhack3r)\r\n# Software Link: http://downloads.wordpress.org/plugin/disqus-comment-system.2.68.zip\r\n#
  Version: 2.68\r\n# Tested on: Cross-Platform\r\n\r\n** Vulnerability Description
  **\r\n\r\nThe WordPress Disqus Commment System version 2.68 was found to be effected
  by Reflected Cross-Site Scripting (XSS). At the time of writing the plugin (not
  version) had been downloaded 504,746 times. [0]\r\n\r\n"
wordpress_id: 16648
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16648
date: '2011-12-11 16:15:17 +0000'
date_gmt: '2011-12-11 16:15:17 +0000'
---
<p># Exploit Title: WordPress Plugin Disqus Comment System < = 2.68 Reflected Cross-Site Scripting (XSS)<br />
# Google Dork: inurl:/wp-content/plugins/disqus-comment-system/<br />
# Date: 11.12.11<br />
# Author: Ryan Dewhurst (@ethicalhack3r)<br />
# Software Link: http://downloads.wordpress.org/plugin/disqus-comment-system.2.68.zip<br />
# Version: 2.68<br />
# Tested on: Cross-Platform</p>
<p>** Vulnerability Description **</p>
<p>The WordPress Disqus Commment System version 2.68 was found to be effected by Reflected Cross-Site Scripting (XSS). At the time of writing the plugin (not version) had been downloaded 504,746 times. [0]</p>
<p><a id="more"></a><a id="more-16648"></a></p>
<p>** Software Description **</p>
<p>DISQUS is a comments platform that helps you build an active community from your website's audience. It has awesome features, powerful tools, and it's easy to install. [1] The Disqus comment system replaces your WordPress comment system with your comments hosted and powered by Disqus. [0]</p>
<p>** Proof of Concept (PoC) **</p>
<p>Vulnerable page: /wp-content/plugins/disqus-comment-system/lib/wp-cli.php<br />
Vulnerable parameter: User-Agent HTTP Header<br />
XSS payload: script alert(1) script</p>
<p>** Vulnerability Timeline **</p>
<p>2011-09-25: Vendor Informed.<br />
2011-11-30: Vendor released patched version 2.69.<br />
2011.12.11: Vulnerability Disclosed.</p>
<p>** References **</p>
<p>[0] http://wordpress.org/extend/plugins/disqus-comment-system/<br />
[1] http://disqus.com/</p>
