---
layout: post
status: publish
published: true
title: Patching WordPress Username Disclosure
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "On May 26th Veronica Valero of Talsoft S.R.L. posted a security advisory
  on the <a href=\"http://seclists.org/fulldisclosure/2011/May/493\" target=\"_blank\">Full
  Disclosure</a> mailing list outlining a username disclosure vulnerability via a
  <a href=\"https://www.owasp.org/index.php/Top_10_2010-A4-Insecure_Direct_Object_References\"
  target=\"_blank\">Direct Object Reference</a>. \r\n\r\nThis is a problem in itself,
  however, what was more interesting to me was Zerial's <a href=\"http://seclists.org/fulldisclosure/2011/May/494\"
  target=\"_blank\">reply</a> to the advisory; \r\n\r\n<blockquote>\"Also you can
  \"enumerate\" wordpress users using the wp-login.php. Whenyou enter a non-existent
  user wordpress returns \"Invalid username\" andwhen you enter a valid user with
  any random/dummie password, wordpressreturns \"Invalid Password\". Now you can use
  brute-force to enumerate allvalid users using, for example, a name&username dictionary.\"</blockquote>\r\n\r\n"
wordpress_id: 16035
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16035
date: '2011-06-01 15:38:30 +0100'
date_gmt: '2011-06-01 14:38:30 +0100'
---
<p>On May 26th Veronica Valero of Talsoft S.R.L. posted a security advisory on the <a href="http://seclists.org/fulldisclosure/2011/May/493" target="_blank">Full Disclosure</a> mailing list outlining a username disclosure vulnerability via a <a href="https://www.owasp.org/index.php/Top_10_2010-A4-Insecure_Direct_Object_References" target="_blank">Direct Object Reference</a>. </p>
<p>This is a problem in itself, however, what was more interesting to me was Zerial's <a href="http://seclists.org/fulldisclosure/2011/May/494" target="_blank">reply</a> to the advisory; </p>
<blockquote><p>"Also you can "enumerate" wordpress users using the wp-login.php. Whenyou enter a non-existent user wordpress returns "Invalid username" andwhen you enter a valid user with any random/dummie password, wordpressreturns "Invalid Password". Now you can use brute-force to enumerate allvalid users using, for example, a name&username dictionary."</p></blockquote>
<p><a id="more"></a><a id="more-16035"></a></p>
<p>As we can see from a simple test on <a href="https://wordpress.org/wp-login.php" target="_blank">https://wordpress.org/wp-login.php</a>, what he was saying was true.</p>
<p>Existent user 'admin':<br />
<img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2011/06/Screen-shot-2011-06-01-at-14.54.58.png" alt="" title="Screen shot 2011-06-01 at 14.54.58" width="408" height="433" class="alignnone size-full wp-image-16037" /></p>
<p>Non-Existent user 'nonexistant':<br />
<img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2011/06/Screen-shot-2011-06-01-at-14.55.15.png" alt="" title="Screen shot 2011-06-01 at 14.55.15" width="455" height="425" class="alignnone size-full wp-image-16038" /></p>
<p>As we can see from the two screenshots above, there is a clear difference in the error message that is displayed by WordPress when a user exists or does not. According to OSVDB <a href="http://osvdb.org/55713" target="_blank">55713</a> this vulnerability was reported to WordPress by Core Security Technologies in June 2009. At the time of writing, the latest version of WordPress is 3.1.3 and is still vulnerable to this vulnerability. </p>
<p>Here is how to patch the vulnerability highlighted by 'Zerial' yourself:</p>
<p><strong>wp-includes/user.php:91</strong></p>
<p>Change:</p>
<p>[php]return new WP_Error('invalid_username', sprintf(__('ERROR: Invalid username. <a href="%s" title="Password Lost and Found">Lost your password< /a>?'), site_url('wp-login.php?action=lostpassword', 'login')));</a>[/php]</p>
<p>To:</p>
<p>[php]return new WP_Error( 'invalid_username', sprintf( __( 'ERROR: Invalid username and/or password.')));[/php]</p>
<p><strong>wp-includes/user.php:111</strong></p>
<p>Change:</p>
<p>[php]return new WP_Error( 'incorrect_password', sprintf( __( 'ERROR: The password you entered for the username <strong>%1$s</strong> is incorrect.      <a href="%2$s" title="Password Lost and Found">Lost your password</a>?' )[/php]</p>
<p>To:</p>
<p>[php]return new WP_Error( 'incorrect_password', sprintf( __( 'ERROR: Invalid username and/or password.')));[/php]</p>
<p>Let's hope WordPress patch this and the one Veronica disclosed sooner rather than later.</p>
<p><strong>UPDATE</strong></p>
<p>After some further searching it seems a bug report was issued in 2007 on WordPress's Trac. <a href="http://core.trac.wordpress.org/ticket/3708" target="_blank">http://core.trac.wordpress.org/ticket/3708</a></p>
<blockquote><p>"There are other ways to verify user names. You can reverse engineer them from the author archive URLs (e.g.  http://example.com/author/mark/). I believe the consensus last time this came up was that it was trivial to figure out the user names anyway, and that it is much more user-friendly to tell them when they messed up their username, and not the password. Also, "admin" is created on install, and can't be changed using WordPress itself, so there's no hiding that."</p></blockquote>
