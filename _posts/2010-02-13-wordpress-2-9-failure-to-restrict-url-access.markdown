---
layout: post
status: publish
published: true
title: WordPress >= 2.9 Failure to Restrict URL Access
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "1. *Advisory Information*\r\n\r\nTitle: WordPress &gt;= 2.9 Failure to Restrict
  URL Access\r\nDate published: 13/02/2010\r\n\r\n2. *Vulnerability Information*\r\n\r\nClass:
  Failure to Restrict URL Access\r\nRemotely Exploitable: Yes\r\nLocally Exploitable:
  Yes\r\n\r\n"
wordpress_id: 569
wordpress_url: http://www.ethicalhack3r.co.uk/?p=569
date: '2010-02-13 18:23:16 +0000'
date_gmt: '2010-02-13 18:23:16 +0000'
---
<p>1. *Advisory Information*</p>
<p>Title: WordPress &gt;= 2.9 Failure to Restrict URL Access<br />
Date published: 13/02/2010</p>
<p>2. *Vulnerability Information*</p>
<p>Class: Failure to Restrict URL Access<br />
Remotely Exploitable: Yes<br />
Locally Exploitable: Yes</p>
<p><a id="more"></a><a id="more-569"></a></p>
<p>3. *Software Description*</p>
<p>WordPress is a state-of-the-art publishing platform with a<br />
focus on aesthetics, web standards, and usability. WordPress<br />
is both free and priceless at the same time. [0]</p>
<p>4. *Vulnerability Description*</p>
<p>Frequently, the only protection for a URL is that links to that page<br />
are not presented to unauthorized users. Security by obscurity is<br />
not sufficient to protect sensitive functions and data in an application.<br />
Access control checks must be performed before a request to a sensitive<br />
function is granted, which ensures that the user is authorized to access<br />
that function. [1]</p>
<p>5. *Vulnerable packages*</p>
<p>Versions &gt;= 2.9</p>
<p>6. *Non-vulnerable packages*</p>
<p>Versions &lt; 2.9</p>
<p>7. *Vulnerability Overview*</p>
<p>Since version 2.9 a new feature was implemented so that users<br />
were able to retrieve posts that they may have deleted by accident.<br />
This new feature was labelled 'trash'. Any posts that are placed within<br />
the trash are only viewable by authenticated and privileged users.</p>
<p>8. *Technical Description*</p>
<p>When WordPress implemented the new feature they failed to change the<br />
permissions granted when the post is in the trash. This means that<br />
an unauthenticated user cannot see the post, however an authenticated<br />
user can, no matter what privileges they have, even 'subcriber'.</p>
<p>"Subscriber [User Level 0] - Somebody who can read comments/comment/receive news letters, etc." [2]</p>
<p>9. *PoC*</p>
<p><a href="http://codeviewer.org/view/code:c03">http://codeviewer.org/view/code:c03</a></p>
<p>10. *Credits*</p>
<p>Thomas Mackenzie (tmacuk) - http://www.thomasmackenzie.co.uk/<br />
Original finder and tester.</p>
<p>Ryan Dewhurst (ethicalhack3r) - http://www.ryandewhurst.co.uk/<br />
PoC creation and analysis.</p>
<p>Arron Finnon (f1nux) - http://www.finux.co.co.uk/<br />
Helped with documentation.</p>
<p>Matthew Hughes - http://www.matthewhughes.co.uk/<br />
Helped with documentation.</p>
<p>Robin Wood (digininja) - http://www.digininja.org/<br />
Helped identify the vulnerability type.</p>
<p>11. *References*</p>
<p>[0] http://wordpress.org/<br />
[1] http://www.owasp.org/index.php/Top_10_2007-Failure_to_Restrict_URL_Access<br />
[2] http://codex.wordpress.org/Roles_and_Capabilities</p>
<p>UPDATE 13/02/2010 --</p>
<p>WP unofficial patch released:<br />
<a href="http://www.2shared.com/file/11360976/9b00062c/diff_wp.html">http://www.2shared.com/file/11360976/9b00062c/diff_wp.html</a></p>
<p>UPDATE 15/02/2010 --</p>
<p>Wordpress 2.9.2 <a href="http://wordpress.org/development/2010/02/wordpress-2-9-2/">released</a> which fixes the Failure to Restrict URL Access vulnerability. </p>
