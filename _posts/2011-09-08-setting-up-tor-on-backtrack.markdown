---
layout: post
status: publish
published: true
title: Setting up Tor on BackTrack
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "I was playing around with getting <a href=\"http://www.randomstorm.com/wpscan-security-tool.php\"
  target=\"_blank\">wpscan</a> to run through the <a href=\"http://www.torproject.org/\"
  target=\"_blank\">Tor</a> network so I needed to setup Tor (from source) and <a
  href=\"http://www.privoxy.org/\" target=\"_blank\">Privoxy</a> on <a href=\"http://www.backtrack-linux.org/\"
  target=\"_blank\">BackTrack</a>. These are the steps I took to setup Tor and Privoxy
  on Backtrack 5 R1. (wpscan does not yet support scanning through the Tor network)\r\n\r\nI
  am no Tor expert and there are probably easier/better ways of doing this.\r\n\r\n<strong>Installing
  Tor (Anonymous SOCKS proxy):</strong>\r\n\r\n<blockquote>\r\n$apt-get install libssl-dev\r\n$wget
  https://www.torproject.org/dist/tor-0.2.2.32.tar.gz\r\n$tar -xzvf tor-0.2.2.32.tar.gz\r\n$cd
  tor-0.2.2.32\r\n$chmod +x configure\r\n$./configure && make && src/or/tor\r\n</blockquote>\r\n\r\n"
wordpress_id: 16496
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16496
date: '2011-09-08 17:33:59 +0100'
date_gmt: '2011-09-08 16:33:59 +0100'
---
<p>I was playing around with getting <a href="http://www.randomstorm.com/wpscan-security-tool.php" target="_blank">wpscan</a> to run through the <a href="http://www.torproject.org/" target="_blank">Tor</a> network so I needed to setup Tor (from source) and <a href="http://www.privoxy.org/" target="_blank">Privoxy</a> on <a href="http://www.backtrack-linux.org/" target="_blank">BackTrack</a>. These are the steps I took to setup Tor and Privoxy on Backtrack 5 R1. (wpscan does not yet support scanning through the Tor network)</p>
<p>I am no Tor expert and there are probably easier/better ways of doing this.</p>
<p><strong>Installing Tor (Anonymous SOCKS proxy):</strong></p>
<blockquote><p>
$apt-get install libssl-dev<br />
$wget https://www.torproject.org/dist/tor-0.2.2.32.tar.gz<br />
$tar -xzvf tor-0.2.2.32.tar.gz<br />
$cd tor-0.2.2.32<br />
$chmod +x configure<br />
$./configure && make && src/or/tor
</p></blockquote>
<p><a id="more"></a><a id="more-16496"></a></p>
<p>To check that <strong>Tor</strong> has been setup properly, add the following settings to your Firefox browser and then visit; <a href="https://check.torproject.org/" target="_blank">https://check.torproject.org/</a></p>
<p><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2011/09/tor_firefox_config.png"><img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2011/09/tor_firefox_config-300x294.png" alt="" title="tor_firefox_config" width="300" height="294" class="alignnone size-medium wp-image-16498" /></a></p>
<p><strong>Installing Privoxy (HTTP proxy):</strong></p>
<blockquote><p>
$apt-get install privoxy<br />
$vim /etc/privoxy/config (uncomment line 1257, see comments[1] below)<br />
$kill -9 (privoxy pid, there is probably a much nicer/easier way to do this)<br />
$/usr/sbin/privoxy --pidfile /var/run/privoxy.pid --user privoxy /etc/privoxy/config
</p></blockquote>
<p>To check that <strong>Privoxy</strong> has been setup properly, add the following settings to your Firefox browser and then visit; <a href="http://config.privoxy.org/show-status/" target="_blank">http://config.privoxy.org/show-status/</a></p>
<p><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2011/09/privoxy_setup.png"><img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2011/09/privoxy_setup-300x294.png" alt="" title="privoxy_setup" width="300" height="294" class="alignnone size-medium wp-image-16501" /></a></p>
<p>Now all you have to do is point your applications to Privoxy on "127.0.0.1:8118".</p>
<p>For example, to setup <a href="http://cirt.net/nikto2" target="_blank">Nikto</a> to use Tor/Privoxy, edit the nikto.conf file, lines 52-53:</p>
<blockquote><p>
# Proxy settings -- still must be enabled by -useproxy<br />
PROXYHOST=127.0.0.1<br />
PROXYPORT=8118
</p></blockquote>
<p>And then run Nikto with the following command:</p>
<blockquote><p>
./nikto.pl -host 192.168.1.112 -useproxy
</p></blockquote>
<p>Please read the Tor warning before using Tor:<br />
<a href="https://www.torproject.org/download/download.html.en#warning" target="_blank">https://www.torproject.org/download/download.html.en#warning</a></p>
<p>References:<br />
<a href="https://trac.torproject.org/projects/tor/wiki" target="_blank">https://trac.torproject.org/projects/tor/wiki</a><br />
<a href="https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO" target="_blank">https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO</a><br />
<a href="http://www.privoxy.org/faq/misc.html#TOR" target="_blank">http://www.privoxy.org/faq/misc.html#TOR</a></p>
<p>Comments:</p>
<p>[1] Also uncomment the following lines to use tor/privoxy when connecting to machines on your LAN:</p>
<blockquote><p>
#        forward         192.168.*.*/     .<br />
#        forward            10.*.*.*/     .<br />
#        forward           127.*.*.*/     .
</p></blockquote>
