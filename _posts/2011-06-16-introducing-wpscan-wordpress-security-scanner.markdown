---
layout: post
status: publish
published: true
title: Introducing WPScan - WordPress Security Scanner
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "After creating the <a href=\"http://www.ethicalhack3r.co.uk/security/wordpress-brute-force-tool/\">WordPress
  Brute Force Tool</a> last weekend, I decided to create a bigger project out of it,
  called WPScan. \r\n\r\nWPScan is a black box WordPress Security Scanner written
  in Ruby which attempts to find known security weaknesses within WordPress installations.
  Its intended use it to be for security professionals or WordPress administrators
  to asses the security posture of their WordPress installations. The code base is
  Open Source and licensed under the <a href=\"http://www.gnu.org/licenses/gpl.html\"
  target=\"_blank\">GPLv3</a>.\r\n\r\n<strong>Features include:</strong>\r\n\r\nUsername
  enumeration\r\nWeak password cracking (multithreaded)\r\nVersion enumeration\r\nVulnerability
  enumeration (based on version)\r\nPlugin enumeration <del datetime=\"2013-01-29T14:40:27+00:00\">(todo)</del>\r\nPlugin
  vulnerability enumeration (based on version) <del datetime=\"2013-01-29T14:40:27+00:00\">(todo)</del>\r\nOther
  miscellaneous checks\r\n\r\n"
wordpress_id: 16298
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16298
date: '2011-06-16 14:29:01 +0100'
date_gmt: '2011-06-16 13:29:01 +0100'
---
<p>After creating the <a href="http://www.ethicalhack3r.co.uk/security/wordpress-brute-force-tool/">WordPress Brute Force Tool</a> last weekend, I decided to create a bigger project out of it, called WPScan. </p>
<p>WPScan is a black box WordPress Security Scanner written in Ruby which attempts to find known security weaknesses within WordPress installations. Its intended use it to be for security professionals or WordPress administrators to asses the security posture of their WordPress installations. The code base is Open Source and licensed under the <a href="http://www.gnu.org/licenses/gpl.html" target="_blank">GPLv3</a>.</p>
<p><strong>Features include:</strong></p>
<p>Username enumeration<br />
Weak password cracking (multithreaded)<br />
Version enumeration<br />
Vulnerability enumeration (based on version)<br />
Plugin enumeration <del datetime="2013-01-29T14:40:27+00:00">(todo)</del><br />
Plugin vulnerability enumeration (based on version) <del datetime="2013-01-29T14:40:27+00:00">(todo)</del><br />
Other miscellaneous checks</p>
<p><a id="more"></a><a id="more-16298"></a></p>
<p><strong>Installation:</strong></p>
<p>**Please use the up to date instructions found here; <a href="http://wpscan.org/" target="_blank">http://wpscan.org/</a></p>
<p>WPScan requires two non native Ruby gems, <a href="http://rubygems.org/gems/typhoeus" target="_blank">typhoeus</a> and <a href="http://xml-simple.rubyforge.org/" target="_blank">xml-simple</a>. It should work on both Ruby 1.8.x and 1.9.x.</p>
<blockquote><p>
sudo apt-get install libcurl4-gnutls-dev<br />
sudo gem install --user-install typhoeus<br />
sudo gem install --user-install xml-simple
</p></blockquote>
<p>(I developed WPScan on Backtrack5 Gnome 32bit, if installing on another OS, you may not need the --user-install option when installing the non native gems)</p>
<p><strong>Download:</strong></p>
<p>WPScan will be hosted on <del datetime="2013-01-29T14:40:27+00:00">Google Code</del> GitHub at <a href="https://github.com/wpscanteam/wpscan" target="_blank">https://github.com/wpscanteam/wpscan</a>.</p>
<p>You can download and start running WPScan <strong>ALPHA</strong> by <del datetime="2013-01-29T14:40:27+00:00">checking out</del> cloning the <del datetime="2013-01-29T14:40:27+00:00">SVN trunk</del> git trunk.<br />
<del datetime="2013-01-29T14:40:27+00:00">"svn checkout http://wpscan.googlecode.com/svn/trunk/ wpscan-read-only"</del><br />
git clone https://github.com/wpscanteam/wpscan.git</p>
<p><strong>Example usage:</strong></p>
<blockquote><p>
Examples:<br />
ruby wpscan.rb --url www.example.com<br />
ruby wpscan.rb --url www.example.com --wordlist darkc0de.lst --threads 50<br />
ruby wpscan.rb --url www.example.com --wordlist darkc0de.lst --username admin
</p></blockquote>
<p>Contributions, feedback, comments are welcome.</p>
<p>Happy Hacking!</p>
