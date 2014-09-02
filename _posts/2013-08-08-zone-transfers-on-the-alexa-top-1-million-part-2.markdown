---
layout: post
status: publish
published: true
title: Zone Transfers on The Alexa Top 1 Million Part 2
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "In <a href=\"http://www.ethicalhack3r.co.uk/zone-transfers-on-the-alexa-top-1-million/\">part
  1</a> of this blog post I conducted a DNS Zone Transfer (axfr) against the top 2000
  sites of the Alexa Top 1 Million. I did this to create a better subdomain brute
  forcing word list. At the time, conducting the Zone Transfer against the top 2000
  sites took about 12 hours, this was using a single threaded bash script. I was pretty
  proud of this achievement at the time and thought that doing the same for the whole
  top 1 million sites was beyond the time and resources that I had.\r\n\r\nAfter creating
  a multithreaded and parallelised PoC in Ruby to do the Zone Transfers, it took about
  5 minutes to conduct the Zone Transfers against the top 2000 compared to the 12
  hours it took me to do the top 2000 using a single thread. I decided it was possible
  to do a Zone Transfer against the whole top 1 million sites.\r\n\r\nThere were 60,472
  successful Zone Transfers (%6) out of the Alexa Top 1 Million, this equates to 566MB
  of raw data on disk. This amount of data brings its own challenges when attempting
  to manipulate it.\r\n\r\n"
wordpress_id: 17123
wordpress_url: http://www.ethicalhack3r.co.uk/?p=17123
date: '2013-08-08 22:06:36 +0100'
date_gmt: '2013-08-08 21:06:36 +0100'
---
<p>In <a href="http://www.ethicalhack3r.co.uk/zone-transfers-on-the-alexa-top-1-million/">part 1</a> of this blog post I conducted a DNS Zone Transfer (axfr) against the top 2000 sites of the Alexa Top 1 Million. I did this to create a better subdomain brute forcing word list. At the time, conducting the Zone Transfer against the top 2000 sites took about 12 hours, this was using a single threaded bash script. I was pretty proud of this achievement at the time and thought that doing the same for the whole top 1 million sites was beyond the time and resources that I had.</p>
<p>After creating a multithreaded and parallelised PoC in Ruby to do the Zone Transfers, it took about 5 minutes to conduct the Zone Transfers against the top 2000 compared to the 12 hours it took me to do the top 2000 using a single thread. I decided it was possible to do a Zone Transfer against the whole top 1 million sites.</p>
<p>There were 60,472 successful Zone Transfers (%6) out of the Alexa Top 1 Million, this equates to 566MB of raw data on disk. This amount of data brings its own challenges when attempting to manipulate it.</p>
<p>The top 10 subdomains in the Alexa Top 1 Million are:<br />
{% highlight text %}
Instances, Subdomain
54520 www
41581 mail
39873 ftp
38590 localhost
22771 webmail
17643 smtp
17410 webdisk
15439 pop
15155 cpanel
14904 whm
{% endhighlight %}</p>
<p>There are some big differences in this top 10 compared to the top 10 against the top 2000. In this one the www subdomain takes the number one spot. The m subdomain is not in this list. The cpanel subdomain is in this list but didn't feature in the top 2000 list.</p>
<p><a id="more"></a><a id="more-17123"></a></p>
<p><strong>The data </strong></p>
<p>In the lists below any subdomain with a '*' or a '@' character were removed, as well as any subdomain that was seen only once.</p>
<p>Subdomains including instances: <a href="http://ethicalhack3r.co.uk/files/fuzzing/top1mil-subdomains/subdomains-top1mil-with-rank.txt">subdomains-top1mil-with-rank.txt</a> (42MB)<br />
Subdomains not including instances: <a href="http://ethicalhack3r.co.uk/files/fuzzing/top1mil-subdomains/subdomains-top1mil.txt">subdomains-top1mil.txt</a> (1.1MB)<br />
Subdomains top 20,000: <a href="http://ethicalhack3r.co.uk/files/fuzzing/top1mil-subdomains/subdomains-top1mil-20000.txt">subdomains-top1mil-20000.txt</a> (146KB)<br />
Subdomains top 5000: <a href="http://ethicalhack3r.co.uk/files/fuzzing/top1mil-subdomains/subdomains-top1mil-5000.txt">subdomains-top1mil-5000.txt</a> (33KB)</p>
<p>On a daily basis I would probably use the subdomains-top1mil-5000.txt list over the others due to the time it takes to complete the subdomain brute force. You may want to use the subdomains-top1mil-20000.txt list to be more thorough, and for the best results but the more time investment I'd use the subdomains-top1mil.txt list.</p>
