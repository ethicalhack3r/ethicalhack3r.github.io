---
layout: post
status: publish
published: true
title: DevBug - PHP Static Code Analysis
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "My final year university dissertation was on the topic of Static Code Analysis,
  specifically the integration of IDEs (Integrated Development Environments) with
  Static Code Analysis. The idea was to make Static Code Analysis accesible to the
  developer, without them having to install and use additional specialist Static Code
  Analysis software.\r\n\r\nDue to my familiarity with PHP and its lack of interpreter
  taint analysis I decided that I would write a PHP Static Code Analysis application.
  The PHP Static Code Analysis tool I developed is called DevBug, it is an online
  PHP Static Code Analysis tool written mostly in JavaScript (jQuery). The Static
  Code Analysis engine uses the sources, securing functions and sinks data from the
  awesome <a href=\"http://sourceforge.net/projects/rips-scanner/\" target=\"_blank\">RIPS</a>
  Static Code Analysis tool to identify specific PHP functions that can cause or remediate
  user input caused vulnerabilities. DevBug uses Taint Analysis to identify tainted
  variables, follows the tainted variables through the code, untaints the variables
  if they are secured and finally detects whether or not tainted variables end up
  in in sensitive sinks.\r\n\r\nThe IDE used is called <a href=\"http://codemirror.net/\"
  target=\"_blank\">CodeMirror</a> that provides a code editing area, syntax highlighting,
  line numbering and an API. CodeMirror was slightly modified to detect deprecated
  PHP functions and highlight them.\r\n\r\n"
wordpress_id: 16810
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16810
date: '2012-05-20 13:13:14 +0100'
date_gmt: '2012-05-20 12:13:14 +0100'
---
<p>My final year university dissertation was on the topic of Static Code Analysis, specifically the integration of IDEs (Integrated Development Environments) with Static Code Analysis. The idea was to make Static Code Analysis accesible to the developer, without them having to install and use additional specialist Static Code Analysis software.</p>
<p>Due to my familiarity with PHP and its lack of interpreter taint analysis I decided that I would write a PHP Static Code Analysis application. The PHP Static Code Analysis tool I developed is called DevBug, it is an online PHP Static Code Analysis tool written mostly in JavaScript (jQuery). The Static Code Analysis engine uses the sources, securing functions and sinks data from the awesome <a href="http://sourceforge.net/projects/rips-scanner/" target="_blank">RIPS</a> Static Code Analysis tool to identify specific PHP functions that can cause or remediate user input caused vulnerabilities. DevBug uses Taint Analysis to identify tainted variables, follows the tainted variables through the code, untaints the variables if they are secured and finally detects whether or not tainted variables end up in in sensitive sinks.</p>
<p>The IDE used is called <a href="http://codemirror.net/" target="_blank">CodeMirror</a> that provides a code editing area, syntax highlighting, line numbering and an API. CodeMirror was slightly modified to detect deprecated PHP functions and highlight them.</p>
<p><a id="more"></a><a id="more-16810"></a></p>
<p>DevBug has some known bugs and limitations at present which I will address in the near future. For now it is still useful as a quick and easy place to run some PHP functions or pages through to check for potential issues. As far as I know DevBug is the only free online PHP Static Code Analysis tool available.</p>
<p>The Taint Analysis takes part in the browser with JavaScript after the PHP source code has been tokenized by the server. This was my first real JavaScript related project so the code may not be as good as it could be, for this reason, I may make the project open source in future so that it can be improved upon and users benefit from the knowledge of the open source community. </p>
<p>I'm still interested in bug reports or feature requests, DevBug can be found here:<br />
<a href="http://www.devbug.co.uk" title="devbug" target="_blank">http://www.devbug.co.uk</a></p>
