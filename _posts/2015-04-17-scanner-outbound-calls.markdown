---
layout: post
status: publish
published: true
title: Scanner Outbound Calls
excerpt: "Today Burp Suite announced the release of a new feature they call Burp Collaborator which is enabled by default.
\r\n\r\n
By default this new feature makes use of a third-party server hosted by Burp to detect vulnerabilities which are not easily detectable in the usual 'request<->response' method most vulnerability scanners use.
\r\n\r\n
The legitimate concern of some people online has been that client information may now be leaked to Burp or worse leaked to the Internet if the third-party server Burp uses is ever compromised. "
---
Today Burp Suite announced the release of a new feature they call [http://blog.portswigger.net/2015/04/introducing-burp-collaborator.html](Burp Collaborator) which is enabled by default.

By default this new feature makes use of a third-party server hosted by Burp to detect vulnerabilities which are not easily detectable in the usual "request<->response" method most vulnerability scanners use.

The legitimate concern of some people online has been that client information may now be leaked to Burp or worse leaked to the Internet if the third-party server Burp uses is ever compromised. 

Users are able to setup their own "Burp Collaborator" server if they wish, however, this may be a pain to setup and maintain. I haven't tried it so I'm not certain how difficult it may or may not be to setup.

Those concerned with Burp logging these potential vulnerabilities from their client's sites may not realise that Burp and almost every other web application scanner already does this. Not for the intention of logging the data itself, but to check for vulnerabilities that need to call a third-party server, such as a Remote File Inclusion (RFI) vulnerability to be detected.

For example, Burp version 1.6.14, the version prior to this new feature sends this payload:

    http://www.example.com/wordpress-40/?feed=http://portswigger.net/f517a2bc19bdff66d7c64e8a7ad2f043.txt

This request gets sent to the application and if vulnerable, the application will forward the request to portswigger.net where it could be logged. The HTTP Referer header containing the application's domain name, the IP address of the server that made the request, times, dates and more could be logged.

I'm not saying that it is or it is not logged, but it could be. And this is existing functionality, nothing new and definitely not unique to Burp Suite. I'd be surprised if there was a web application vulnerability scanner which didn't use similar payloads.

OWASP's ZAP scanner makes this request, probably looking for the "OWASP ZAP" keyword in the response:

    http://www.example.com/wordpress-40/xmlrpc.php?rsd=http://www.google.com:80/search?q=OWASP ZAP

Arachni will use this payload:

    http://tests.arachni-scanner.com/rfi.md5.txt

My point is if you do not like this new feature for the sole purpose that it may be logging data, well, most scanners already could, including Burp. You could argue that because this new feature attempts to identify a wider variety of vulnerabilities that even more data could potentially be logged. That would be a legitimate argument. However, Burp state "No data of any kind is in recorded in any persistent form: for example, a database or log file.”.

Whether you want to take their word for it or not is up to you. Personally I think they're a great and trustworthy team and would take their word for it.

I haven't had the chance to use this new feature. I think that it has great potential. I may have preferred efforts be put into improving existing functionality but I'm sure they have their reasons and own priorities.
