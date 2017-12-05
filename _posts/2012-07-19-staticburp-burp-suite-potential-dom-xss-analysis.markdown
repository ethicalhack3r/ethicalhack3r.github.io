---
layout: post
status: publish
published: true
title: StaticBurp - Burp Suite potential DOM XSS Analysis
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "A few weeks a go I had an idea.\r\n\r\n<blockquote class=\"twitter-tweet\"><p>JavaScript
  Taint Analysis for DOM <a href=\"https://twitter.com/search/%2523XSS\">#XSS</a>
  in Burp would be an awesome feature to have! // cc: @<a href=\"https://twitter.com/portswigger\">portswigger</a></p>&mdash;
  Ryan Dewhurst (@ethicalhack3r) <a href=\"https://twitter.com/ethicalhack3r/status/218459472450961408\"
  data-datetime=\"2012-06-28T21:42:51+00:00\">June 28, 2012</a></blockquote>\r\n<script
  src=\"//platform.twitter.com/widgets.js\" charset=\"utf-8\"></script>\r\n\r\nWhen
  I get ideas that I think have something worth while in them I note them down for
  future reference.\r\n\r\nThe three main points to get this working were:\r\n\r\n<li>Take
  Burp response body.</li>\r\n<li>Extract JavaScript.</li>\r\n<li>Perform Taint Analysis.</li>\r\n\r\nThe
  first step was to somehow extract HTML responses from Burp Suite, luckily someone
  had already written a Ruby Burp extender called <a href=\"http://emonti.github.com/buby/\">Buby</a>.
  I followed <a href=\"http://carnal0wnage.attackresearch.com/2011/05/buby-script-basics-part-1.html\">this</a>
  awesome series of blog posts to get myself aquatinted with Buby.\r\n\r\nThe next
  step is to extract the JavaScript from the HTML responses, this is quite trivial
  to do with the <a href=\"http://nokogiri.org/\">Nokogiri</a> Ruby gem.\r\n\r\nThe
  third step is to analyse the extracted JavaScript for Sinks, Sources and Securing
  functions (Taint Analysis). This was the hard part, for me at least. Finding this
  information proved to be hard, I did find some data, however, in the end this is
  where I stopped pursuing my idea.\r\n\r\n"
wordpress_id: 16822
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16822
date: '2012-07-19 13:38:39 +0100'
date_gmt: '2012-07-19 12:38:39 +0100'
---
<p>A few weeks a go I had an idea.</p>
<blockquote class="twitter-tweet"><p>JavaScript Taint Analysis for DOM <a href="https://twitter.com/search/%2523XSS">#XSS</a> in Burp would be an awesome feature to have! // cc: @<a href="https://twitter.com/portswigger">portswigger</a></p>
<p>&mdash; Ryan Dewhurst (@ethicalhack3r) <a href="https://twitter.com/ethicalhack3r/status/218459472450961408" data-datetime="2012-06-28T21:42:51+00:00">June 28, 2012</a></p></blockquote>
<p><script src="//platform.twitter.com/widgets.js" charset="utf-8"></script></p>
<p>When I get ideas that I think have something worth while in them I note them down for future reference.</p>
<p>The three main points to get this working were:</p>
<li>Take Burp response body.</li>
<li>Extract JavaScript.</li>
<li>Perform Taint Analysis.</li>
<p>The first step was to somehow extract HTML responses from Burp Suite, luckily someone had already written a Ruby Burp extender called <a href="http://emonti.github.com/buby/">Buby</a>. I followed <a href="http://carnal0wnage.attackresearch.com/2011/05/buby-script-basics-part-1.html">this</a> awesome series of blog posts to get myself aquatinted with Buby.</p>
<p>The next step is to extract the JavaScript from the HTML responses, this is quite trivial to do with the <a href="http://nokogiri.org/">Nokogiri</a> Ruby gem.</p>
<p>The third step is to analyse the extracted JavaScript for Sinks, Sources and Securing functions (Taint Analysis). This was the hard part, for me at least. Finding this information proved to be hard, I did find some data, however, in the end this is where I stopped pursuing my idea.</p>
<p><a id="more"></a><a id="more-16822"></a></p>
<p>So today Michele "antisnatchor" Orru' posts a blog post titled <a href="http://antisnatchor.com/Enumerate_potential_DOM-based_XSS_vulnerable_code">'Enumerate potential DOM-based XSS vulnerable code'</a> in which Michele uses a regular expression originally written by Mario ".mario" Heiderich to find JavaScript Sinks and Sources.</p>
<p>In my original plan I had planned to use Dynamic Taint Analysis, this would have compromised of arrays of Sinks, Sources and Securing functions, however, the regular expression route is much easier as it has already been done for us by Mario. :)</p>
<p>StaticBurp ALPHA (it's had limited testing and was written during my lunch break) can be found here:</p>
<p><a href="http://pastie.org/4283545">http://pastie.org/4283545</a></p>
<p>To run it first install Buby. Then I used the following command:</p>
<p>jruby -S buby -i -B /pentest/web/burpsuite/burpsuite_v1.4.01.jar -r Desktop/StaticBurp.rb</p>
<p>As Michele states in his blog post the output will need manual verification, it will probably produce a lot of false negatives and false positives. It is for now better than nothing.</p>
