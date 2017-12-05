---
layout: post
status: publish
published: true
title: WordPress 3.3 Cross-Site Scripting (XSS)
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "Yesterday two Indian security researchers, Aditya Modha & Samir Shah, released
  an <a href=\"http://oldmanlab.blogspot.com/2012/01/wordpress-33-xss-vulnerability.html\"
  target=\"_blank\">advisory</a> outlining a Cross-Site Scripting (XSS) vulnerability
  within the latest version (at the time of writing) of WordPress 3.3. Many people
  started re-tweeting the news (including myself) and <a href=\"http://thehackernews.com/2012/01/zero-day-reflected-cross-site-scripting.html\"
  target=\"_blank\">blogging</a> about it. The problem came when I tried to reproduce
  the vulnerability, I couldn't.\r\n\r\nI started to think that the vulnerability
  was a miss-understanding or publicity stunt and was getting annoyed at the many
  people who were spreading miss-information. I contacted the researchers over <a
  href=\"http://www.twitter.com/oldmanlab\" target=\"_blank\">Twitter</a> and told
  them that I was unable to reproduce the vulnerability in any browser or on any WordPress
  installation including vanilla installs.\r\n\r\nThe researchers got back in touch
  with a link to a WordPress installation on which the vulnerability worked. The URL
  they gave me was an IP address. Within their environment the XSS worked.\r\n\r\nAt
  this point I think even the researchers were puzzled. They sent me this code that
  they believed was the function causing the XSS within wp-includes/functions.php
  <a href=\"http://pastebin.com/iBnpN8Zm\" target=\"_blank\">http://pastebin.com/iBnpN8Zm</a>.\r\n\r\n"
wordpress_id: 16709
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16709
date: '2012-01-03 18:56:14 +0000'
date_gmt: '2012-01-03 18:56:14 +0000'
---
<p>Yesterday two Indian security researchers, Aditya Modha & Samir Shah, released an <a href="http://oldmanlab.blogspot.com/2012/01/wordpress-33-xss-vulnerability.html" target="_blank">advisory</a> outlining a Cross-Site Scripting (XSS) vulnerability within the latest version (at the time of writing) of WordPress 3.3. Many people started re-tweeting the news (including myself) and <a href="http://thehackernews.com/2012/01/zero-day-reflected-cross-site-scripting.html" target="_blank">blogging</a> about it. The problem came when I tried to reproduce the vulnerability, I couldn't.</p>
<p>I started to think that the vulnerability was a miss-understanding or publicity stunt and was getting annoyed at the many people who were spreading miss-information. I contacted the researchers over <a href="http://www.twitter.com/oldmanlab" target="_blank">Twitter</a> and told them that I was unable to reproduce the vulnerability in any browser or on any WordPress installation including vanilla installs.</p>
<p>The researchers got back in touch with a link to a WordPress installation on which the vulnerability worked. The URL they gave me was an IP address. Within their environment the XSS worked.</p>
<p>At this point I think even the researchers were puzzled. They sent me this code that they believed was the function causing the XSS within wp-includes/functions.php <a href="http://pastebin.com/iBnpN8Zm" target="_blank">http://pastebin.com/iBnpN8Zm</a>.</p>
<p><a id="more"></a><a id="more-16709"></a></p>
<p>{% highlight php %}
  function wp_guess_url() {
  if ( defined('WP_SITEURL') && '' != WP_SITEURL ) {
    $url = WP_SITEURL;
  } else {
    $schema = is_ssl() ? 'https://' : 'http://';
    $url = preg_replace('|/wp-admin/.*|i', '', $schema . $_SERVER['HTTP_HOST'] . $_SERVER['REQUEST_URI']);
  }
  return rtrim($url, '/');
}
{% endhighlight %}</p>
<p>The XSS occurs because $_SERVER['REQUEST_URI'] (the URI which was given in order to access the page) was used within output before first being sanitized. Or better yet, it shouldn't have been used at all.</p>
<p>The reason I couldn't reproduce it or why the researchers couldn't reproduce outside of their environment? The reason is the 'else' never gets triggered when WordPress was installed via a domain.</p>
<p>If you installed WordPress by accessing http://192.168.100.110/, for example, you are vulnerable. If however, like most people, but not all, installed WordPress via the domain name, http://www.ethicalhack3r.co.uk you are not vulnerable.</p>
<p>Quick and easy fix until WordPress release a patch? Put $_SERVER['REQUEST_URI'] through esc_html() first, esc_html($_SERVER['REQUEST_URI']).</p>
<p>Example (tested):</p>
<p>wp-includes/functions.php:3756<br />
{% highlight php %}
$url = preg_replace('|/wp-admin/.*|i', '', $schema . $_SERVER['HTTP_HOST'] . esc_html($_SERVER['REQUEST_URI']));
{% endhighlight %}
</p>
<p><strong>UPDATE --</strong></p>
<p>WordPress 3.3.1 has been released that seems to fix the issue.</p>
