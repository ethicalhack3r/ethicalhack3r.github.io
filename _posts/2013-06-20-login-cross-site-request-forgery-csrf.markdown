---
layout: post
status: publish
published: true
title: Login Cross-Site Request Forgery (CSRF)
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "The new OWASP Top 10 2013 was released not so long ago, while reading over
  it I noticed this:\r\n\r\n\"Attackers can trick victims into performing any state
  changing operation the victim is authorized to perform, e.g., updating account details,
  making purchases, logout and <strong>even login</strong>.\" - <a href=\"https://www.owasp.org/index.php/Top_10_2013-A8-Cross-Site_Request_Forgery_(CSRF)\"
  target=\"_blank\">https://www.owasp.org/index.php/Top_10_2013-A8-Cross-Site_Request_Forgery_(CSRF)</a>\r\n\r\nThis
  must be a mistake I thought, why would you ever want to CSRF a user to log them
  into their own account? If you already had their login credentials this must be
  utterly pointless.\r\n\r\nToday I came across an academic paper which gives three
  examples of why Login CSRF can be an issue and how wrong I was.\r\n\r\n<strong>Google</strong>\r\n\r\n\"Search
  History. Many search engines, including Yahoo! and Google, allow their users to
  opt-in to saving their search history and provide an interface for a user to review
  his or her personal search history. Search queries contain sensitive details about
  the user’s interests and activities [41, 4] and could be used by an attacker to
  embarrass the user, to steal the user’s identity, or to spy on the user. An attacker
  can spy on a user’s search history by logging the user into the search engine as
  the attacker; see Figure 1. The user’s search queries are then stored in the attacker’s
  search history, and the attacker can retrieve the queries by logging into his or
  her own account.\"\r\n\r\n"
wordpress_id: 17098
wordpress_url: http://www.ethicalhack3r.co.uk/?p=17098
date: '2013-06-20 21:01:12 +0100'
date_gmt: '2013-06-20 20:01:12 +0100'
---
<p>The new OWASP Top 10 2013 was released not so long ago, while reading over it I noticed this:</p>
<p>"Attackers can trick victims into performing any state changing operation the victim is authorized to perform, e.g., updating account details, making purchases, logout and <strong>even login</strong>." - <a href="https://www.owasp.org/index.php/Top_10_2013-A8-Cross-Site_Request_Forgery_(CSRF)" target="_blank">https://www.owasp.org/index.php/Top_10_2013-A8-Cross-Site_Request_Forgery_(CSRF)</a></p>
<p>This must be a mistake I thought, why would you ever want to CSRF a user to log them into their own account? If you already had their login credentials this must be utterly pointless.</p>
<p>Today I came across an academic paper which gives three examples of why Login CSRF can be an issue and how wrong I was.</p>
<p><strong>Google</strong></p>
<p>"Search History. Many search engines, including Yahoo! and Google, allow their users to opt-in to saving their search history and provide an interface for a user to review his or her personal search history. Search queries contain sensitive details about the user’s interests and activities [41, 4] and could be used by an attacker to embarrass the user, to steal the user’s identity, or to spy on the user. An attacker can spy on a user’s search history by logging the user into the search engine as the attacker; see Figure 1. The user’s search queries are then stored in the attacker’s search history, and the attacker can retrieve the queries by logging into his or her own account."</p>
<p><a id="more"></a><a id="more-17098"></a></p>
<p><strong>PayPal</strong></p>
<p>"PayPal. PayPal lets its users transfer funds to each other. To fund a PayPal account, users enroll their credit card or their bank account. A web attacker can use login CSRF to mount the following attack:</p>
<p>1. The victim visits a malicious merchant’s site and chooses to pay using PayPal.</p>
<p>2. As usual, victim is redirected to PayPal and logs into his or her account.</p>
<p>3. The merchant silently logs the victim into his or her PayPal account.</p>
<p>4. To fund her purchase, the victim enrolls his or her credit card, but the credit card has actually been added to the merchant’s PayPal account."</p>
<p><strong>iGoogle</strong></p>
<p>"iGoogle. Using iGoogle, users can customize their Google homepage by including gadgets. For usability, some gadgets are “inline,” meaning they run in the security context of iGoogle. Before adding such gadgets, users are asked to make a trust decision, but in a login CSRF attack, a web attacker makes the trust decision on behalf of the user:</p>
<p>1. Using his or her own browser, the attacker authors an inline iGoogle gadget (containing a malicious script) and adds it to his or her own personalized home page.</p>
<p>2. The attacker logs the victim into Google as the attacker and opens a frame to iGoogle.</p>
<p>3. Google believes the victim to be the attacker and serves the attacker’s gadget to the victim, letting the attacker to run script in the https://www.google.com origin.</p>
<p>4. The attacker can now either (a) create a fake login page at the correct URL, (b) steal the user’s autocompleted password, or (c) wait for the user to log in using another window and read document.cookie."</p>
<p>The full paper which covers many other CSRF topics can be found here, a great read! - <a href="http://www.adambarth.com/papers/2008/barth-jackson-mitchell-b.pdf" target="_blank">http://www.adambarth.com/papers/2008/barth-jackson-mitchell-b.pdf</a></p>
