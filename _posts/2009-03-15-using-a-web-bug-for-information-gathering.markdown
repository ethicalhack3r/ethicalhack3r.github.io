---
layout: post
status: publish
published: true
title: Using a web bug for information gathering
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "Abstract:\r\nAny one can post an image anywhere that allows the posting
  of remote images, grab the http header information of any one who views the image
  and save it to a log file on a remote server. This has been done for a while by
  the advertisement industry to track users activities. It can also be used by mail
  clients to check that an email has been read by the recipient. It is known as a
  'web bug'."
wordpress_id: 160
wordpress_url: http://www.ethicalhack3r.co.uk/?p=160
date: '2009-03-15 16:55:07 +0000'
date_gmt: '2009-03-15 16:55:07 +0000'
---
<p>Abstract:<br />
Any one can post an image anywhere that allows the posting of remote images, grab the http header information of any one who views the image and save it to a log file on a remote server. This has been done for a while by the advertisement industry to track users activities. It can also be used by mail clients to check that an email has been read by the recipient. It is known as a 'web bug'.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>How its done:</p>
<p>1. You need a php script that will capture the GET HTTP headers, echo an image and have the content-type header set as a jpg.</p>
<p>2. A directory called /image.jpg/</p>
<p>3. htaccess file to automatically load index files within directories</p>
<p>3. Some where you can post the &lt;img&gt; HTML tag.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>Exploit:</p>
<p>Post the following code into any forum, blog, guestbook, website that accepts images from remote servers.</p>
<p>&lt;img&gt;<a href="http://www.mysite.com/image.jpg" target="_blank">http://www.mysite.com/image.jpg</a>&lt;/img&gt;<br />
OR<br />
&lt;img src="<a href="http://www.mysite.com/image.jpg" target="_blank">http://www.mysite.com/image.jpg</a>"&gt;</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>How it works:</p>
<p><a id="more"></a><a id="more-160"></a></p>
<p>The php script has a jpg header, echos an image and stores http header information to a log file. This is great but still has the .php extension rather than the .jpg extension.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>You create a directory called /image.jpg/</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>You tell the htaccess to show any file named index when you access the /image.jpg/ directory. So when you access <a href="http://www.mysite.com/image.jpg" target="_blank">www.mysite.com/image.jpg</a> it will automatically load the php script (index.php) which looks like an ordinary jpg.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>So we now have a php script that acts and looks like an image, that records http headers and we also have it looking like it has the .jpg extension rather than the .php extension.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>So what you can do is post the image.jpg directory to a forum as an image and it will record any one who views its http header information. e.i. ip, referer, user-agent, etc...</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>Impact:</p>
<p>You can grab sensitive information from any one you can social engineer into viewing an image.</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p><span style="color: #ff0000;">This is legal behaviour however maybe considerd unethical depending on the intent of the person doing it. I have not included the PHP file that stores the GET HTTP header information due to posible misuse.<br />
</span></p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>So far it has been tested on:</p>
<p>vBulletin 3.8.1 - in posts - not in avatar<br />
vBulletin 3.6.8 - in posts - not in avatar<br />
phpBB 3.0.3 - in post - in avatar<br />
Facebook - not vulnerable<br />
imageshack - not vulnerable<br />
Joomla com jomcomment - Vulnerable</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>More info:</p>
<p><a title="wikipedia web bug" href="http://en.wikipedia.org/wiki/Web_bug" target="_blank">http://en.wikipedia.org/wiki/Web_bug</a></p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>As for the post underneath about weather or not what the BBC did was legal or illegal, in short it was illegal however who's going to legally challenge them?</p>
<p><strong><span style="text-decoration: underline;"></span><br />
</strong></p>
<p>Here's a good debate on the topic:</p>
<p><a title="guardian bbc legality" href="http://www.guardian.co.uk/technology/blog/2009/mar/12/bbc-botnet-legality-questioned" target="_blank">http://www.guardian.co.uk/technology/blog/2009/mar/12/bbc-botnet-legality-questioned</a></p>
