---
layout: post
status: publish
published: true
title: HTTP Form Password Brute Forcing - The Need for Speed
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "HTTP Form password brute forcing is not rocket science, you try multiple
  username/password combinations until you get a correct answer (or non-negative answer).\r\n\r\nPassword
  brute forcing, especially over a network, takes time and while your software is
  attempting to find a correct username/password combination it is taking up your
  and the remote system's resources. While the brute force is being carried out you
  might not want to run an automated scan, for example, as the remote server may not
  be able to cope with the amount of connections or the rapid succession of connections.
  At the same time, your network bandwidth and system memory are also limited. It
  makes sense that when you conduct a weak password brute force it is done as fast
  as possible so that your time and resources are restored for other tasks.\r\n\r\nAnd
  of course not forgetting that you're always going to be limited by time on a pentest/web
  app assessment as the client's budget is never unlimited.\r\n\r\nSo what is the
  fastest way to brute force a HTTP form today? I use Burp Suite for my Web Application
  Security Assessments and I would normally use Burp's Intruder, but is this the fastest
  tool to do it with?\r\n\r\nOf course, there are other limiting factors when brute
  forcing remotely such as your Internet/Network speed, CPU speed, RAM and the remote
  system's response times, as well as other factors. For this experiment we'll only
  be focusing on the software used to carry out the password brute force attack. This
  is far from being a perfect in-depth study but it should hopefully give an idea
  which tool out of my small collection (Burp Intruder Spider Vs Hydra http-post-form)
  is fastest.\r\n\r\n<strong>The Setup</strong>\r\n\r\nOn both tools I set one user
  to brute force, admin, and used the <a href=\"http://ethicalhack3r.co.uk/files/fuzzing/rockyou-75.txt\"
  target=\"_blank\">rockyou-75.txt</a> wordlist (19963 lines), which has one addition
  which is the correct password which was added to the last line of the file. Both
  the same username and password list was used for Burp's Intruder (Sniper) and Hydra.
  Each tool was run one after the other, not at the same time.\r\n\r\nBurp Suite Professional
  Intruder (Sniper) Version: 1.5.11\r\nHydra (http-post-form) Version: 7.4.2\r\n\r\nA
  \"Local\" test was carried out on a localhost Apache 2 web server as well as a \"Remote\"
  test against the www.ethicalhack3r.co.uk Nginx web server.\r\n\r\nThe <a href=\"http://pastebin.com/xV80ZHBj\"
  target=\"_blank\">Test Form</a> that I created to test against (both locally and
  remotely) does not make a database call which is what would normally be expected
  on a real HTTP login form. I'd expect my test login form to reply quicker than if
  it had to make a database call. The 'Local' and 'Remote' columns represent the time
  it took the tool to find the correct password which was at the end of the wordlist.\r\n\r\n"
wordpress_id: 17009
wordpress_url: http://www.ethicalhack3r.co.uk/?p=17009
date: '2013-04-17 21:04:33 +0100'
date_gmt: '2013-04-17 20:04:33 +0100'
---
<p>HTTP Form password brute forcing is not rocket science, you try multiple username/password combinations until you get a correct answer (or non-negative answer).</p>
<p>Password brute forcing, especially over a network, takes time and while your software is attempting to find a correct username/password combination it is taking up your and the remote system's resources. While the brute force is being carried out you might not want to run an automated scan, for example, as the remote server may not be able to cope with the amount of connections or the rapid succession of connections. At the same time, your network bandwidth and system memory are also limited. It makes sense that when you conduct a weak password brute force it is done as fast as possible so that your time and resources are restored for other tasks.</p>
<p>And of course not forgetting that you're always going to be limited by time on a pentest/web app assessment as the client's budget is never unlimited.</p>
<p>So what is the fastest way to brute force a HTTP form today? I use Burp Suite for my Web Application Security Assessments and I would normally use Burp's Intruder, but is this the fastest tool to do it with?</p>
<p>Of course, there are other limiting factors when brute forcing remotely such as your Internet/Network speed, CPU speed, RAM and the remote system's response times, as well as other factors. For this experiment we'll only be focusing on the software used to carry out the password brute force attack. This is far from being a perfect in-depth study but it should hopefully give an idea which tool out of my small collection (Burp Intruder Spider Vs Hydra http-post-form) is fastest.</p>
<p><strong>The Setup</strong></p>
<p>On both tools I set one user to brute force, admin, and used the <a href="http://ethicalhack3r.co.uk/files/fuzzing/rockyou-75.txt" target="_blank">rockyou-75.txt</a> wordlist (19963 lines), which has one addition which is the correct password which was added to the last line of the file. Both the same username and password list was used for Burp's Intruder (Sniper) and Hydra. Each tool was run one after the other, not at the same time.</p>
<p>Burp Suite Professional Intruder (Sniper) Version: 1.5.11<br />
Hydra (http-post-form) Version: 7.4.2</p>
<p>A "Local" test was carried out on a localhost Apache 2 web server as well as a "Remote" test against the www.ethicalhack3r.co.uk Nginx web server.</p>
<p>The <a href="http://pastebin.com/xV80ZHBj" target="_blank">Test Form</a> that I created to test against (both locally and remotely) does not make a database call which is what would normally be expected on a real HTTP login form. I'd expect my test login form to reply quicker than if it had to make a database call. The 'Local' and 'Remote' columns represent the time it took the tool to find the correct password which was at the end of the wordlist.</p>
<p><a id="more"></a><a id="more-17009"></a></p>
<p><strong>The Results</strong></p>
<p>The first test was done with Hydra's and Burp's default thread/task settings, by default Hydra sets '16 tasks' and by default Burp's Intruder sets '5 threads'.</p>
<p><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2013/04/Screen-Shot-2013-04-17-at-15.28.20.png"><img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2013/04/Screen-Shot-2013-04-17-at-15.28.20.png" alt="default burp vs hydra" width="606" height="134" class="alignnone size-full wp-image-17033" /></a></p>
<p>As you can see from the above table, Hydra vastly outperforms Burp when using the default settings both locally and remotely.</p>
<p>The second test was done with Burp's threads set to 16, to match Hydra's default tasks setting.</p>
<p><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2013/04/Screen-Shot-2013-04-17-at-15.35.19.png"><img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2013/04/Screen-Shot-2013-04-17-at-15.35.19.png" alt="burp 16 threads" width="605" height="133" class="alignnone size-full wp-image-17038" /></a></p>
<p>The above table gives some unexpected results. Locally Hydra vastly outperforms Burp, but remotely Burp vastly outperforms Hydra.</p>
<p>It looks as though to get the most out of my <em>remote</em> HTTP Form password brute forcing I should be using Burp's Intruder and changing the default 5 threads to something higher, like 16 (depending on how the remote server handles the attack). Of course, this is not conclusive evidence of which tool is faster than the other due to the many variables involved. If you get different results let me know! As Hydra is a dedicated password brute forcing tool I did expect it to outperform Burp's Intruder as Burp is an all round Web Application Security Assessment tool. This doesn't mean I won't be using Hydra to brute force other services, like FTP for example. They have done a comparison themselves using FTP and SSH which shows them as being the fastest for these services out of a few different tools, the comparison can be found at the bottom of <a href="http://www.thc.org/thc-hydra/network_password_cracker_comparison.html" target="_blank">this</a> page. </p>
<p><strong>WordPress</strong></p>
<p>Recently there was a <a href="http://blog.sucuri.net/2013/04/the-wordpress-brute-force-attack-timeline.html" target="_blank">spike in WordPress brute force attacks</a>, here is a table comparing Hydra, Burp's Intruder and WPScan's bruter against local and remote WordPress installs.</p>
<p><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2013/04/Screen-Shot-2013-04-17-at-20.47.26.png"><img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2013/04/Screen-Shot-2013-04-17-at-20.47.26.png" alt="Screen Shot 2013-04-17 at 20.47.26" width="606" height="184" class="alignnone size-full wp-image-17068" /></a></p>
<p>WPScan came in behind Burp's Intruder but in front of Hydra's http-post-form module in both local and remote tests. If you're going to brute force WordPress and you are determined (using a large list) you may want to use Burp Suite Professional's Intruder tool, otherwise use WPScan. ;)</p>
<p>If you compare this table against the brute force against the Test Form table, you can see the difference the login form itself makes on the time a brute force takes to complete. In Hydra's case, this is significant.</p>
<p><strong>Hydra Commands Used in Testing</strong></p>
<p>Local at default tasks:<br />
[code]$ hydra -l admin -P ~/Tools/wordlists/rockyou-75.txt 127.0.0.1 http-post-form &quot;/login.php:username=^USER^&amp;password=^PASS^&amp;submit=Submit:Incorrect&quot;[/code]</p>
<p>Remote at default tasks:<br />
[code]$ hydra -l admin -P ~/Tools/wordlists/rockyou-75.txt www.ethicalhack3r.co.uk http-post-form &quot;/files/misc/login.php:username=^USER^&amp;password=^PASS^&amp;submit=Submit:Incorrect&quot;[/code]</p>
<p>Local WordPress (this did not output that it had found the valid pass due to what looks like a WP infinite redirect bug, it did actually authenticate though):<br />
[code]hydra -l admin -P ~/Tools/wordlists/rockyou-75.txt 127.0.0.1 http-post-form &quot;/wordpress/wordpress-351/wp-login.php:log=^USER^&amp;pwd=^PASS^:login_error&quot;[/code]</p>
<p><strong>WPScan Commands Used in Testing</strong></p>
<p>WPScan command used (local):<br />
[code]$ ./wpscan.rb -u http://127.0.0.1/wordpress/wordpress-351/ -U admin -w ~/Tools/wordlists/rockyou-75.txt -t 16[/code]</p>
<p>WPScan command used (remote):<br />
[code]$ ./wpscan.rb -u www.REDACTED.com -U admin -w ~/Tools/wordlists/rockyou-75.txt -t 16[/code]</p>
