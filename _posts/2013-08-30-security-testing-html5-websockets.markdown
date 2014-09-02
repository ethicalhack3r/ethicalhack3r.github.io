---
layout: post
status: publish
published: true
title: Security Testing HTML5 WebSockets
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "Recently I became faced with my first Web Application Security Assessment
  which relied heavily on HTML5's <a href=\"http://www.html5rocks.com/en/tutorials/websockets/basics/\">WebSockets</a>.\r\n\r\nThe
  first clue that the application was using WebSockets was when the application kept
  giving me a timeout error while using my proxy of choice, <a href=\"http://portswigger.net/burp/\">Burp
  Suite</a>. Looking at the HTTP requests/responses in Burp I noticed that a large
  JavaScript file was requested and downloaded from the server. Within this file I
  noticed a URL with the <em>ws://</em> scheme, the WebSocket scheme.\r\n\r\n<h1>TCP/HTTP?</h1>\r\n\r\nThe
  initial WebSocket handshake is carried out over HTTP using an '<a href=\"https://en.wikipedia.org/wiki/HTTP/1.1_Upgrade_header\">upgrade
  request</a>'. After the initial exchange over HTTP all future communication is carried
  out over TCP. On the application I was testing the WebSocket handshake over HTTP
  within <a href=\"https://www.wireshark.org/\">WireShark</a> looked like this:\r\n\r\n"
wordpress_id: 17130
wordpress_url: http://www.ethicalhack3r.co.uk/?p=17130
date: '2013-08-30 18:57:45 +0100'
date_gmt: '2013-08-30 17:57:45 +0100'
---
<p>Recently I became faced with my first Web Application Security Assessment which relied heavily on HTML5's <a href="http://www.html5rocks.com/en/tutorials/websockets/basics/">WebSockets</a>.</p>
<p>The first clue that the application was using WebSockets was when the application kept giving me a timeout error while using my proxy of choice, <a href="http://portswigger.net/burp/">Burp Suite</a>. Looking at the HTTP requests/responses in Burp I noticed that a large JavaScript file was requested and downloaded from the server. Within this file I noticed a URL with the <em>ws://</em> scheme, the WebSocket scheme.</p>
<h3>TCP/HTTP?</h3>
<p>The initial WebSocket handshake is carried out over HTTP using an '<a href="https://en.wikipedia.org/wiki/HTTP/1.1_Upgrade_header">upgrade request</a>'. After the initial exchange over HTTP all future communication is carried out over TCP. On the application I was testing the WebSocket handshake over HTTP within <a href="https://www.wireshark.org/">WireShark</a> looked like this:</p>
<p>Request:<br />
{% highlight text %}
GET /SocketHandler HTTP/1.1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.8; rv:23.0) Gecko/20100101 Firefox/23.0
Sec-WebSocket-Version: 13
Origin: http://www.example.com
Sec-WebSocket-Key: iiral7et1zfQMGu9udIYHA==
Cookie: Login=1234567
Connection: keep-alive, Upgrade
Upgrade: websocket
Content-length: 0
Host: www.example.com
{% endhighlight %}</p>
<p>Response:<br />
{% highlight text %}
HTTP/1.1 101 Switching Protocols
Upgrade: Websocket
Server: Microsoft-IIS/8.0
Sec-WebSocket-Accept: 9ZPK0lC0SB6dhIJHRt3q/GN88Ng=
Connection: Upgrade
Date: Fri, 30 Aug 2013 13:33:42 GMT
{% endhighlight %}</p>
<p><a id="more"></a><a id="more-17130"></a></p>
<h3>Capturing WebSockets</h3>
<p>For some reason the WebSocket handshake was not captured by Burp's Proxy (even though the WireShark capture shows that the handshake was over HTTP), however, it can be viewed within Google Chrome's Developer Tools and OWASP's <a href="https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project">ZAP Proxy</a>.</p>
<p>Using <a href="http://www.websocket.org/echo.html">this</a> example WebSocket application (which is vulnerable to '<a href="https://www.facebook.com/photo.php?v=956977232793">Self-XSS</a>' BTW) you can see that Google Chrome's Developer Tools captures the initial WebSocket handshake:</p>
<p><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2013/08/chrome-developer-tools-web-sockets.png"><img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2013/08/chrome-developer-tools-web-sockets.png" alt="chrome developer tools web sockets" width="775" height="202" class="alignnone size-full wp-image-17139" /></a></p>
<p>And also the subsequent WebSocket communication (frames) over TCP:</p>
<p><a href="http://www.ethicalhack3r.co.uk/wp-content/uploads/2013/08/chrome-developer-tools-web-sockets-2.png"><img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2013/08/chrome-developer-tools-web-sockets-2.png" alt="chrome developer tools web sockets 2" width="739" height="201" class="alignnone size-full wp-image-17143" /></a></p>
<p>If you want to fuzz and replay WebSocket communications you can use OWASP's <a href="https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project">ZAP Proxy</a> which supports capturing and replaying WebSockets.</p>
<h3>Encryption (SSL/TLS)</h3>
<p>WebSockets can be used over unencrypted TCP or over encrypted TLS. To use unencrypted WebSockets the <em>ws://</em> URI scheme is used (default port 80), to use encrypted (TLS) WebSockets the <em>wss://</em> URI scheme is used (default port 443).</p>
<p>Here you probably want to look out for the OWASP Top 10 2013 <a href="https://www.owasp.org/index.php/Top_10_2013-A6-Sensitive_Data_Exposure">A6-Sensitive Data Exposure</a> type issues. Is sensitive data being transported over unencrypted channels? Has SSL been implemented securely?</p>
<h3>Origin</h3>
<p>It is the web server's responsibility to verify the <em>Origin</em> header in the initial HTTP WebSocket handshake. If the Origin header is not properly checked, the application may be vulnerable to OWASP Top 10 2013 <a href="https://www.owasp.org/index.php/Top_10_2013-A8-Cross-Site_Request_Forgery_(CSRF)">A8-Cross-Site Request Forgery (CSRF)</a>.</p>
<p>There's a great blog post <a href="http://www.christian-schneider.net/CrossSiteWebSocketHijacking.html">here</a> describing a 'Cross-Site WebSocket Hijacking' technique which is possible when the application/server does not check the Origin header.</p>
<p>I also created a WebSocket client which can be used to test origin issues which can be found <a href="https://raw.github.com/RandomStorm/scripts/master/WebSockets.html">here</a>.</p>
<h3>Authentication</h3>
<p>WebSockets do not handle authentication, instead normal application authentication mechanisms apply, such as cookies, HTTP Authentication or TLS authentication. Here you probably want to check for OWASP Top 10 2013 <a href="https://www.owasp.org/index.php/Top_10_2013-A2-Broken_Authentication_and_Session_Management">A2-Broken Authentication and Session Management</a> type issues.</p>
<h3>Authorisation</h3>
<p>WebSockets do not handle authorisation, normal application authorisation mechanisms apply. Here you want to test for OWASP Top 10 2013 <a href="https://www.owasp.org/index.php/Top_10_2013-A4-Insecure_Direct_Object_References">A4-Insecure Direct Object References</a> and OWASP Top 10 2013 <a href="https://www.owasp.org/index.php/Top_10_2013-A7-Missing_Function_Level_Access_Control">A7-Missing Function Level Access Control</a>.</p>
<h3>Input Sanitisation</h3>
<p>As with any data originating from untrusted sources the data should not be trusted. The OWASP Top 10 2013 <a href="https://www.owasp.org/index.php/Top_10_2013-A1-Injection">A1-Injection</a> and the OWASP Top 10 2013 <a href="https://www.owasp.org/index.php/Top_10_2013-A3-Cross-Site_Scripting_(XSS)">A3-Cross-Site Scripting (XSS)</a> issues would apply here. </p>
<p>There's a great post <a href="http://juerkkil.iki.fi/2013/03/17/compromising-html5-websockets-with-an-xss-vulnerability/">here</a> showing how an XSS issue on a page can be used to compromise WebSockets to eavesdrop on the WebSocket communications by modifying the JavaScript WebSocket functions.</p>
<h3>Conclusion</h3>
<p>Testing WebSockets can seem daunting when you first come across them during a Web Application Security Assessment. Hopefully you now have some insight of how WebSockets work, what tools you can use and what security issues to look out for.</p>
<p>I have probably not covered all bases here and I'm sure there is a lot more to be discussed surrounding testing WebSockets during a Web Application Security Assessment. If you think that I have missed anything out, please comment below!</p>
<h1>Further Reading</h1>
<p><a href="https://tools.ietf.org/html/rfc6455">https://tools.ietf.org/html/rfc6455</a><br />
<a href="https://www.owasp.org/index.php/HTML5_Security_Cheat_Sheet">https://www.owasp.org/index.php/HTML5_Security_Cheat_Sheet</a><br />
<a href="http://www.digininja.org/blog/zap_web_sockets.php">http://www.digininja.org/blog/zap_web_sockets.php</a><br />
<a href="http://www.digininja.org/blog/zap_fuzzing.php">http://www.digininja.org/blog/zap_fuzzing.php</a></p>
