---
layout: post
status: publish
published: true
title: 'SSH "accept : too many open files" on OS X when using Burp'
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "<strong>EDIT 19.04.2013 10:17 ---</strong>\r\n<strong>WARNING!</strong>
  This did break the Tor Browser Bundle on my machine. The error was \"Couldn't set
  maximum number of file descriptors: Invalid argument\"\r\n<strong>---</strong>\r\n\r\nFor
  as long as I can remember, when <a href=\"http://ocaoimh.ie/2008/02/13/how-to-use-ssh-as-a-proxy-server/\"
  target=\"_blank\">using SSH as a forward proxy</a> to proxy Burp Suite through an
  upstream server I have gotten a \"accept : too many open files\" error in my Mac
  OS X Terminal after a couple of hours of using Burp's Proxy and/or Scanner.\r\n\r\nWhen
  searching Google the first solution I came across was to set the 'ulimit' to something
  higher, as far as I can tell 'ulimit' sets user system limits such as how many open
  files a user is allowed to have open at once.\r\n\r\nOn OS X when attempting to
  set this limit to 'unlimited' I always got an error, \"Neither the hard nor soft
  limit for \"maxfiles\" can be unlimited. Please use a numeric parameter for both.\",
  or when setting the ulimit to something higher than the default (256) the error
  (accept : too many open files) would still not go away or at least not for long.
  The only thing I found that would get rid of the error was to kill my ssh session
  and spawn a new one.\r\n\r\nAfter further reading, some forums and blogs suggested
  updating openssh, I did this and the issue persisted. I thought the issue may have
  been openssl, so I updated that, the issue persisted.\r\n\r\nI also <a href=\"https://twitter.com/ethicalhack3r/status/313982186695036928\"
  target=\"_blank\">tweeted</a> about the issue where the suggestion of adjusting
  the ulimit resurfaced, but I just couldn't get ulimit to fix the issue.\r\n\r\n"
wordpress_id: 17001
wordpress_url: http://www.ethicalhack3r.co.uk/?p=17001
date: '2013-04-08 14:20:14 +0100'
date_gmt: '2013-04-08 13:20:14 +0100'
---
<p><strong>EDIT 19.04.2013 10:17 ---</strong><br />
<strong>WARNING!</strong> This did break the Tor Browser Bundle on my machine. The error was "Couldn't set maximum number of file descriptors: Invalid argument"<br />
<strong>---</strong></p>
<p>For as long as I can remember, when <a href="http://ocaoimh.ie/2008/02/13/how-to-use-ssh-as-a-proxy-server/" target="_blank">using SSH as a forward proxy</a> to proxy Burp Suite through an upstream server I have gotten a "accept : too many open files" error in my Mac OS X Terminal after a couple of hours of using Burp's Proxy and/or Scanner.</p>
<p>When searching Google the first solution I came across was to set the 'ulimit' to something higher, as far as I can tell 'ulimit' sets user system limits such as how many open files a user is allowed to have open at once.</p>
<p>On OS X when attempting to set this limit to 'unlimited' I always got an error, "Neither the hard nor soft limit for "maxfiles" can be unlimited. Please use a numeric parameter for both.", or when setting the ulimit to something higher than the default (256) the error (accept : too many open files) would still not go away or at least not for long. The only thing I found that would get rid of the error was to kill my ssh session and spawn a new one.</p>
<p>After further reading, some forums and blogs suggested updating openssh, I did this and the issue persisted. I thought the issue may have been openssl, so I updated that, the issue persisted.</p>
<p>I also <a href="https://twitter.com/ethicalhack3r/status/313982186695036928" target="_blank">tweeted</a> about the issue where the suggestion of adjusting the ulimit resurfaced, but I just couldn't get ulimit to fix the issue.</p>
<p><a id="more"></a><a id="more-17001"></a></p>
<p>Finally, I came across <a href="http://superuser.com/questions/302754/increase-the-maximum-number-of-open-file-descriptors-in-snow-leopard" target="_blank">this</a> post on superuser.com where the errant.info user suggests to issue the following commands:</p>
<p>
{% highlight bash %}
echo 'kern.maxfiles=20480' | sudo tee -a /etc/sysctl.conf
echo -e 'limit maxfiles 8192 20480\nlimit maxproc 1000 2000' | sudo tee -a /etc/launchd.conf
echo 'ulimit -n 4096' | sudo tee -a /etc/profile
{% endhighlight %}</p>
<p>As far as I can tell, the above seems to set a kernal limit, system limit and also the user's ulimit. After a system restart, the error has now gone!</p>
<p>The user also adds some additional notes:</p>
<p>
{% highlight text %}
You will need to restart for these changes to take effect.
AFAIK you can no longer set limits to 'unlimited' under OS X
launchctl maxfiles are bounded by sysctl maxfiles, and therefore cannot exceed them
sysctl seems to inherit kern.maxfilesperproc from launchctl maxfiles
ulimit seems to inherit it's 'open files' value from launchctl by default
you can set a custom ulimit within /etc/profile, or ~/.profile ; while this isn't required I've provided an example
Be cautious when setting any of these values to a very high number when compared with their default - the features exist stability/security. I've taken these example numbers that I believe to be reasonable, written on other websites.
{% endhighlight %}</p>
<p>I'm sure I am not the only one who has come across this before, so hopefully it is useful to other Burp Suite user's who use SSH as a forwarding proxy on Mac OS X. It worked for me so should hopefully work for you too.</p>
