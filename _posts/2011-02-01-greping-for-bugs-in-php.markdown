---
layout: post
status: publish
published: true
title: Grepping for bugs in PHP
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "Today I used the following commands to grep through PHP source code to find
  some bugs. I thought they may be useful to someone else so I thought I would stick
  them on here. This list is by no means extensive however they are the ones I found
  most useful. \r\n\r\n<strong>Find user input/output for possible XSS:</strong>\r\n\r\n<blockquote>grep
  -i -r \"echo\" *\r\ngrep -i -r \"\\$_GET\" *\r\ngrep -i -r \"\\$_\" * | grep \"echo\"\r\ngrep
  -i -r \"\\$_GET\" * | grep \"echo\"\r\ngrep -i -r \"\\$_POST\" * | grep \"echo\"\r\ngrep
  -i -r \"\\$_REQUEST\" * | grep \"echo\"</blockquote>\r\n\r\n"
wordpress_id: 862
wordpress_url: http://www.ethicalhack3r.co.uk/?p=862
date: '2011-02-01 15:40:21 +0000'
date_gmt: '2011-02-01 15:40:21 +0000'
---
<p>Today I used the following commands to grep through PHP source code to find some bugs. I thought they may be useful to someone else so I thought I would stick them on here. This list is by no means extensive however they are the ones I found most useful. </p>
<p><strong>Find user input/output for possible XSS:</strong></p>
<blockquote><p>grep -i -r "echo" *<br />
grep -i -r "\$_GET" *<br />
grep -i -r "\$_" * | grep "echo"<br />
grep -i -r "\$_GET" * | grep "echo"<br />
grep -i -r "\$_POST" * | grep "echo"<br />
grep -i -r "\$_REQUEST" * | grep "echo"</p></blockquote>
<p><a id="more"></a><a id="more-862"></a></p>
<p><strong>Find potential command execution:</strong></p>
<blockquote><p>grep -i -r "shell_exec(" *<br />
grep -i -r "system(" *<br />
grep -i -r "exec(" *<br />
grep -i -r "popen(" *<br />
grep -i -r "passthru(" *<br />
grep -i -r "proc_open(" *<br />
grep -i -r "pcntl_exec(" *</p></blockquote>
<p><strong>Find potential code execution:</strong></p>
<blockquote><p>grep -i -r "eval(" *<br />
grep -i -r "assert(" *<br />
grep -i -r "preg_replace" * | grep "/e"<br />
grep -i -r "create_function(" *</p></blockquote>
<p><strong>Find potential SQL injection:</strong></p>
<blockquote><p>grep -i -r "\$sql" *<br />
grep -i -r "\$sql" * | grep "\$_"</p></blockquote>
<p><strong>Find potential information disclosure:</strong></p>
<blockquote><p>grep -i -r "phpinfo" *</p></blockquote>
<p><strong>Find potential development functionality:</strong></p>
<blockquote><p>grep -i -r "debug" *<br />
grep -i -r "\$_GET['debug']" *<br />
grep -i -r "\$_GET['test']" *</p></blockquote>
<p><strong>Find potential file inclusion:</strong></p>
<blockquote><p>grep -i -r "file_include" *<br />
grep -i -r "include(" *<br />
grep -i -r "require(" *<br />
grep -i -r "require(\$file)" *<br />
grep -i -r "include_once(" *<br />
grep -i -r "require_once(" *<br />
grep -i -r "require_once(" * | grep "\$_"</p></blockquote>
<p><strong>Other:</strong></p>
<blockquote><p>
grep -i -r "header(" * | grep "\$_"</p></blockquote>
<p><strong>References:</strong><br />
<a href="http://stackoverflow.com/questions/3115559/exploitable-php-functions" target="_blank">http://stackoverflow.com/questions/3115559/exploitable-php-functions</a><br />
<a href="http://www.bonsai-sec.com/blog/index.php/using-grep-to-find-0days/" target="_blank">http://www.bonsai-sec.com/blog/index.php/using-grep-to-find-0days/</a></p>
<p><strong>EDIT</strong><br />
<a href="http://www.twitter.com/securityninja" target="_blank">@securityninja</a> pointed out the <a href="http://sourceforge.net/projects/rips-scanner/" target="_blank">RIPS scanner</a>, I can confirm that it is awesome and does the above plus a lot more! (damn ninjas! ;)</p>
