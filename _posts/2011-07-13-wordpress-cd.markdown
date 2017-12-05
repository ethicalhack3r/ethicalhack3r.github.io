---
layout: post
status: publish
published: true
title: WordPress CD
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "I needed a research environment to help develop <a href=\"http://www.randomstorm.com/wpscan-security-tool.php\"
  target=\"_blank\">WPScan</a> so I put together a <a href=\"http://www.virtualbox.org/\"
  target=\"_blank\">VirtualBox</a> virtual machine with every <a href=\"http://wordpress.org/download/release-archive/\"
  target=\"_blank\">WordPress release</a> installed (not including MU or BETA/Candidates).
  The download, untar and database creation was all automated. The manual bit was
  installing them all.\r\n\r\n<strong>Installed are the following versions of Wordpress:</strong>\r\nwordpress-0.71-gold\r\nwordpress-1.0-platinum\r\nwordpress-1.0.1-miles\r\nwordpress-1.0.2-blakey\r\nwordpress-1.2-delta\r\nwordpress-1.2-mingus\r\nwordpress-1.2.1\r\nwordpress-1.2.2\r\nwordpress-1.5-strayhorn\r\nwordpress-1.5.1.1\r\nwordpress-1.5.1.2\r\nwordpress-1.5.1.3\r\nwordpress-1.5.1\r\nwordpress-1.5.2\r\nwordpress-2.0.1\r\nwordpress-2.0.10\r\n"
wordpress_id: 16472
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16472
date: '2011-07-13 18:35:26 +0100'
date_gmt: '2011-07-13 17:35:26 +0100'
---
<p>I needed a research environment to help develop <a href="http://www.randomstorm.com/wpscan-security-tool.php" target="_blank">WPScan</a> so I put together a <a href="http://www.virtualbox.org/" target="_blank">VirtualBox</a> virtual machine with every <a href="http://wordpress.org/download/release-archive/" target="_blank">WordPress release</a> installed (not including MU or BETA/Candidates). The download, untar and database creation was all automated. The manual bit was installing them all.</p>
<p><strong>Installed are the following versions of Wordpress:</strong><br />
wordpress-0.71-gold<br />
wordpress-1.0-platinum<br />
wordpress-1.0.1-miles<br />
wordpress-1.0.2-blakey<br />
wordpress-1.2-delta<br />
wordpress-1.2-mingus<br />
wordpress-1.2.1<br />
wordpress-1.2.2<br />
wordpress-1.5-strayhorn<br />
wordpress-1.5.1.1<br />
wordpress-1.5.1.2<br />
wordpress-1.5.1.3<br />
wordpress-1.5.1<br />
wordpress-1.5.2<br />
wordpress-2.0.1<br />
wordpress-2.0.10<br />
<a id="more"></a><a id="more-16472"></a><br />
wordpress-2.0.11<br />
wordpress-2.0.4<br />
wordpress-2.0.5<br />
wordpress-2.0.6<br />
wordpress-2.0.7<br />
wordpress-2.0.8<br />
wordpress-2.0.9<br />
wordpress-2.0<br />
wordpress-2.1.1<br />
wordpress-2.1.2<br />
wordpress-2.1.3<br />
wordpress-2.1<br />
wordpress-2.2.1<br />
wordpress-2.2.2<br />
wordpress-2.2.3<br />
wordpress-2.2<br />
wordpress-2.3.1<br />
wordpress-2.3.2<br />
wordpress-2.3.3<br />
wordpress-2.3<br />
wordpress-2.5.1<br />
wordpress-2.5<br />
wordpress-2.6.1<br />
wordpress-2.6.2<br />
wordpress-2.6.3<br />
wordpress-2.6.5<br />
wordpress-2.6<br />
wordpress-2.7.1<br />
wordpress-2.7<br />
wordpress-2.8.1<br />
wordpress-2.8.2<br />
wordpress-2.8.3<br />
wordpress-2.8.4<br />
wordpress-2.8.5<br />
wordpress-2.8.6<br />
wordpress-2.8<br />
wordpress-2.9.1<br />
wordpress-2.9.2<br />
wordpress-2.9<br />
wordpress-3.0.1<br />
wordpress-3.0.2<br />
wordpress-3.0.3<br />
wordpress-3.0.4<br />
wordpress-3.0.5<br />
wordpress-3.0.6<br />
wordpress-3.0<br />
wordpress-3.1.1<br />
wordpress-3.1.2<br />
wordpress-3.1.3<br />
wordpress-3.1.4<br />
wordpress-3.1<br />
wordpress-3.2.1<br />
wordpress-3.2</p>
<blockquote><p>
Install:<br />
1. To install, simply download the OVA file (link below).<br />
2. Open VirtualBox and import the appliance.<br />
3. Add a static DNS entry to your firewall or edit your local hosts file. Add the VM hostname "lamp" and its IP address.<br />
4. Browse to the DHCP assigned IP address in your browser.
</p></blockquote>
<p>This virtual machine makes an excellent vulnerable box for a lab, WordPress development, etc..</p>
<p><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2011/07/Screen-shot-2011-07-13-at-13.57.54.png"><img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2011/07/Screen-shot-2011-07-13-at-13.57.54-300x217.png" alt="" title="Screen shot 2011-07-13 at 13.57.54" width="300" height="217" class="alignnone size-medium wp-image-16475" /></a></p>
<p><strong>Download:</strong></p>
<p>MD5: 8b8dbead74f6ba9f7935625ff2d24392</p>
<p><a href="http://www.ethicalhack3r.co.uk/wpcd/WPCD.ova">http://www.ethicalhack3r.co.uk/wpcd/WPCD.ova</a></p>
<p><strong>UPDATE:</strong></p>
<p>The download link has been changed and installation instructions updated.</p>
<p>The WordPress installs wouldn't work as they were configured to my local IP of "192.168.1.103". Thanks to <a href="http://www.twitter.com/biosshadow" target="_blank">@biosshadow</a>, he has gone through every install and changed the configured IP to the hostname of the virtual machine "lamp".</p>
<p>To get it up and running, you will need to add a static DNS entry to your firewall or edit your local hosts file to point the "lamp" hosthame to the vitual machines IP.</p>
<p>Thanks to <a href="http://www.twitter.com/biosshadow" target="_blank">@biosshadow</a> for changing all of the installs to the hostname.</p>
