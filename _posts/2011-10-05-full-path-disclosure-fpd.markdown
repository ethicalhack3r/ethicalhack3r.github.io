---
layout: post
status: publish
published: true
title: Full Path Disclosure (FPD)
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "Many people including developers, vendors and security professionals believe
  that Full Path Disclosure (FPD) is mainly a Security Misconfiguration problem rather
  than a Input Sanitation or Error Handling problem. I'm not saying that they are
  wrong, but I hope to convince them that it is more of a coding bug than a configuration
  bug. I want to put my argument over as to why I think FPD is a bug in source code
  and not in configuration. \r\n\r\n<strong>What is Full Path Disclosure (FPD)?</strong>\r\n\r\nAccording
  to OWASP:\r\n\"Full Path Disclosure (FPD) vulnerabilities enable the attacker to
  see the path to the webroot/file. e.g.: /home/omg/htdocs/file/. Certain vulnerabilities,
  such as using the load_file() (within a SQL Injection) query to view the page source,
  require the attacker to have the full path to the file they wish to view.\"\r\n<a
  href=\"https://www.owasp.org/index.php/Full_Path_Disclosure\" target=\"_blank\">https://www.owasp.org/index.php/Full_Path_Disclosure</a>\r\n\r\nFor
  me this is a very vague description of what FPD really is. FPD occurs when a web
  application encounters an error that is displayed to the user; the error includes
  the full path to the file the error occurred in possibly along with other debugging
  information.\r\n\r\n<strong>Why is it a problem?</strong>\r\n\r\nIt's just the path
  of the file from the root directory, what's all the fuss about?\r\n\r\n"
wordpress_id: 16575
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16575
date: '2011-10-05 14:19:45 +0100'
date_gmt: '2011-10-05 13:19:45 +0100'
---
<p>Many people including developers, vendors and security professionals believe that Full Path Disclosure (FPD) is mainly a Security Misconfiguration problem rather than a Input Sanitation or Error Handling problem. I'm not saying that they are wrong, but I hope to convince them that it is more of a coding bug than a configuration bug. I want to put my argument over as to why I think FPD is a bug in source code and not in configuration. </p>
<p><strong>What is Full Path Disclosure (FPD)?</strong></p>
<p>According to OWASP:<br />
"Full Path Disclosure (FPD) vulnerabilities enable the attacker to see the path to the webroot/file. e.g.: /home/omg/htdocs/file/. Certain vulnerabilities, such as using the load_file() (within a SQL Injection) query to view the page source, require the attacker to have the full path to the file they wish to view."<br />
<a href="https://www.owasp.org/index.php/Full_Path_Disclosure" target="_blank">https://www.owasp.org/index.php/Full_Path_Disclosure</a></p>
<p>For me this is a very vague description of what FPD really is. FPD occurs when a web application encounters an error that is displayed to the user; the error includes the full path to the file the error occurred in possibly along with other debugging information.</p>
<p><strong>Why is it a problem?</strong></p>
<p>It's just the path of the file from the root directory, what's all the fuss about?</p>
<p><a id="more"></a><a id="more-16575"></a></p>
<p>Let's look at a WordPress FPD:<br />
[code]&lt;b&gt;Fatal error&lt;/b&gt;:  Call to undefined function is_multisite() in &lt;b&gt;/home/bob/public_html/wp/wp-includes/wp-db.php&lt;/b&gt; on line &lt;b&gt;505&lt;/b&gt;&lt;br /&gt;[/code]</p>
<p>From the above error a username is disclosed which can later be used in a brute force attack:<br />
[code]/bob/[/code]</p>
<p>From the above error we know the web root folder name and location, this can be useful when combined with a Local File Inclusion (LFI) if the web root is not in the default location:<br />
[code]/home/bob/public_html/[/code]</p>
<p>In reality it's not a massive deal, we can glean some server side information, so what, it's not as serious as SQL Injection or Cross-Site Scripting (XSS). But, when there is no SQL Injection or XSS, bob's weak password maybe our only way in or that LFI vulnerability we found earlier is now more useful.</p>
<p><strong>Security Misconfiguration or Sloppy Coding?</strong></p>
<p>Many people believe that FPD is a Security Misconfiguration and I can see why they think that. By simply turning 'display_errors' to 'Off' in your php.ini file the problem goes away. The same applies most other web server technologies. (note: FPD is widely known to effect PHP more than any other technology but it does effect most if not all web server technologies)</p>
<p>If we do the above the FPDs are gone, right? No. They are still there, all you have done is hide them. If for example a developer turns 'display_errors' to on by accident, the bug returns. We can say the same about a WAF in an extreme example. Just because the WAF stops the SQL Injection from happening, it does not mean that it is not there and that one day that WAF maybe turned off. *cough* barracuda *cough*</p>
<p>I think it is mostly due to sloppy coding practices because of the following triggers of FPD. (taking some of OWASPs examples)</p>
<p>Empty array: (input sanitation)<br />
[code]<br />
Original: http://site.com/index.php?page=about<br />
Crafted: http://site.com/index.php?page[]=about<br />
[/code]</p>
<p>Fix: Ensure the parameter is a string not an array.</p>
<p>Null Session Cookie: (input sanitation)<br />
[code]<br />
Original: Cookie: PHPSESSID=ef7f786sd78f6ds78f6;<br />
Crafted: Cookie: PHPSESSID=;<br />
[/code]</p>
<p>Fix: Deal with unexpected cookie values.</p>
<p>Direct Object Reference: (error handling)<br />
[code]http://localhost/wp/wp-includes/wp-db.php[/code]</p>
<p>Fix: Deal with errors gracefully when a file is not located in the location is should be.</p>
<p>Invalid File Names: (configuration)<br />
[code]<br />
Original: http://www.host.com/default.aspx<br />
Crafted: http://www.host.com/default~.aspx<br />
[/code]</p>
<p>Fix: Now this one, I think, the only fix is configuration. You could argue that this could be fixed by the ASP developers, but in reality, that's not going to happen.</p>
<p><strong>The bigger problem</strong></p>
<p>The bigger problem for me is not the information disclosure through FPD itself but rather the reluctance of vendors and developers to fix FPD. It's too easy for them to put the blame back onto the user, "not our problem, hide the bug with configuration".</p>
<p>The biggest culprit for me is WordPress. This is from their own <a href="http://codex.wordpress.org/Security_FAQ#Why_are_there_path_disclosures_when_directly_loading_certain_files.3F" target="_blank">Security FAQ</a>:<br />
"Why are there path disclosures when directly loading certain files?<br />
This is considered a server configuration problem. Never enable display_errors on a production site."</p>
<p>The earliest version of WordPress I could get installed (0.71-gold) had 44 FPDs, the newest release at the time of writing (3.2.1) has 155. Most of these are due to "directly loading certain files" but not all of them. One example; http://wordpress-3.2.1/index.php?s[]=FPD</p>
<p>It is not only WordPress either, the YEHG have kindly been collecting logs of vulnerable applications;<br />
<a href="http://code.google.com/p/inspathx/source/browse/#svn%2Ftrunk%2Fpaths_vuln" target="_blank">http://code.google.com/p/inspathx/source/browse/#svn%2Ftrunk%2Fpaths_vuln</a></p>
<p>My job is to reduce software [security] bugs, I think this bug is underestimated and deserves more attention. All FPD bugs found in WordPress will soon be implemented into my tool <a href="http://code.google.com/p/wpscan" target="_blank">WPScan</a>.</p>
<p>To check your web applications for FPD vulnerabilities I recommend using the YEHG's <a href="http://code.google.com/p/inspathx/" target="_blank">inspathx</a> awesome tool which checks for all and more of the triggers outlined above.</p>
