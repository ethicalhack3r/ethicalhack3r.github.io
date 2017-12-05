---
layout: post
status: publish
published: true
title: IE8 XSS Filter bypasses
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "When Microsoft launched their new Internet Explorer (IE) 8 browser in March
  of this year, it boasted a new security feature which filtered malicious scripting
  code to prevent reflected type 1 XSS attacks known as the 'XSS Filter'.\r\n\r\n<strong>\r\n</strong>\r\n\r\nCesar
  Cerrudo, while IE8 was still in BETA found a way to bypass the filter by using a
  '2 stage XSS attack':\r\n<blockquote>A 2 stage XSS attack is when the user has to
  browse to a second URL after browing the initial URL for the XSS attack to take
  place, people may think that this attack is compliated and not reliable but it's
  simple and very realiable and has almost the same success rate as 1 stage XSS attack
  since people want to get what they were looking when browsing to the first URL they
  will continue browsing most of the time.</blockquote>\r\n<strong>\r\n</strong>\r\n\r\n"
wordpress_id: 443
wordpress_url: http://www.ethicalhack3r.co.uk/?p=443
date: '2009-11-20 00:03:20 +0000'
date_gmt: '2009-11-20 00:03:20 +0000'
---
<p>When Microsoft launched their new Internet Explorer (IE) 8 browser in March of this year, it boasted a new security feature which filtered malicious scripting code to prevent reflected type 1 XSS attacks known as the 'XSS Filter'.</p>
<p><strong><br />
</strong></p>
<p>Cesar Cerrudo, while IE8 was still in BETA found a way to bypass the filter by using a '2 stage XSS attack':</p>
<blockquote><p>A 2 stage XSS attack is when the user has to browse to a second URL after browing the initial URL for the XSS attack to take place, people may think that this attack is compliated and not reliable but it's simple and very realiable and has almost the same success rate as 1 stage XSS attack since people want to get what they were looking when browsing to the first URL they will continue browsing most of the time.</p></blockquote>
<p><strong><br />
</strong></p>
<p><a id="more"></a><a id="more-443"></a></p>
<p>Here is a screenshot from a test against DVWA using the 2 stage attack payload which he provides on his blog:</p>
<p><strong><br />
</strong></p>
<p><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/11/reflected_xss2.jpg"><img class="alignnone size-thumbnail wp-image-444" title="reflected_xss2" src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/11/reflected_xss2-150x150.jpg" alt="reflected_xss2" width="150" height="150" /></a></p>
<p><strong><br />
</strong></p>
<p>As you can see I was using the latest IE8 at the time on a fully patched Windows Vista box with the filter enabled:<br />
<a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/11/IE8_XSS_Filter_Enabled.jpg"><img class="alignnone size-thumbnail wp-image-445" title="IE8_XSS_Filter_Enabled" src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/11/IE8_XSS_Filter_Enabled-150x150.jpg" alt="IE8_XSS_Filter_Enabled" width="150" height="150" /></a><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/11/Fully_Patched_IE8.jpg"><img class="alignnone size-thumbnail wp-image-446" title="Fully_Patched_IE8" src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/11/Fully_Patched_IE8-150x150.jpg" alt="Fully_Patched_IE8" width="150" height="150" /></a><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/11/windows_update.jpg"><img class="alignnone size-thumbnail wp-image-447" title="windows_update" src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/11/windows_update-150x150.jpg" alt="windows_update" width="150" height="150" /></a></p>
<p><strong><br />
</strong></p>
<p>Here is another bypass using a different payload:<br />
<a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/11/reflected_xss.jpg"><img class="alignnone size-thumbnail wp-image-448" title="reflected_xss" src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2009/11/reflected_xss-150x150.jpg" alt="reflected_xss" width="150" height="150" /></a></p>
<p><strong><br />
</strong></p>
<p>Microsoft have taken a great step forward in actively protecting their customers against XSS attacks and I believe that in part they have, however the XSS Filter still has a lot of room for improvement. There are other known bypasses against the filter which can be found in the reference list below along with other sources of information.</p>
<p><strong><br />
</strong></p>
<p>References:<br />
<a href="http://en.wikipedia.org/wiki/Internet_Explorer_8" target="_blank">http://en.wikipedia.org/wiki/Internet_Explorer_8</a><br />
<a href="http://blogs.msdn.com/ie/archive/2008/07/02/ie8-security-part-iv-the-xss-filter.aspx" target="_blank">http://blogs.msdn.com/ie/archive/2008/07/02/ie8-security-part-iv-the-xss-filter.aspx</a><br />
<a href="http://nomoreroot.blogspot.com/2008/08/ie8-xss-filter.html" target="_blank">http://nomoreroot.blogspot.com/2008/08/ie8-xss-filter.html</a><br />
<a href="http://kuza55.blogspot.com/2008/09/ie8-xss-filter.html" target="_blank">http://kuza55.blogspot.com/2008/09/ie8-xss-filter.html</a><br />
<a href="http://www.80sec.com/ie8-security-alert.html" target="_blank">http://www.80sec.com/ie8-security-alert.html</a></p>
