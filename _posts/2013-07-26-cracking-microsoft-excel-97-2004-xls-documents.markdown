---
layout: post
status: publish
published: true
title: Cracking Microsoft Excel 97-2004 .xls Documents
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "A client emailed to say they had forgotten a password for their Microsoft
  Excel .xls document and asked if it was possible to recover it. After searching
  on Google it was clear that there was plenty of shi...bloatware, which may have
  worked if you were willing to go through a few of them and pay a few dollars. It
  wasn't that important of a document according to the client but nevertheless a challenge
  is a challenge.\r\n\r\nThe document was encrypted when using 'save as', according
  to various sources online the encryption algorithm is 40bit RC4. As it is encrypted
  nothing could be gleaned by opening the document with a hex editor.\r\n\r\nAs always
  when Google turns up nothing useful I turn to Twitter. A few people recommended
  <a href=\"http://www.elcomsoft.co.uk/\">Elcomsoft</a> which do Windows software
  to both recover and obtain the password of a Microsoft Excel document. This looked
  like a good bet and they offer free trials! The recover software which seems to
  do a brute force attack looked like it could have worked (especially now I know
  how weak the password was) but I was running the software on a Virtual Machine.
  The recovery tool unfortunately didn't reveal the password, the paid for version
  may have, I don't know.\r\n\r\n"
wordpress_id: 17104
wordpress_url: http://www.ethicalhack3r.co.uk/?p=17104
date: '2013-07-26 16:58:57 +0100'
date_gmt: '2013-07-26 15:58:57 +0100'
---
<p>A client emailed to say they had forgotten a password for their Microsoft Excel .xls document and asked if it was possible to recover it. After searching on Google it was clear that there was plenty of shi...bloatware, which may have worked if you were willing to go through a few of them and pay a few dollars. It wasn't that important of a document according to the client but nevertheless a challenge is a challenge.</p>
<p>The document was encrypted when using 'save as', according to various sources online the encryption algorithm is 40bit RC4. As it is encrypted nothing could be gleaned by opening the document with a hex editor.</p>
<p>As always when Google turns up nothing useful I turn to Twitter. A few people recommended <a href="http://www.elcomsoft.co.uk/">Elcomsoft</a> which do Windows software to both recover and obtain the password of a Microsoft Excel document. This looked like a good bet and they offer free trials! The recover software which seems to do a brute force attack looked like it could have worked (especially now I know how weak the password was) but I was running the software on a Virtual Machine. The recovery tool unfortunately didn't reveal the password, the paid for version may have, I don't know.</p>
<p><a id="more"></a><a id="more-17104"></a></p>
<p>Justin kennedy (<a href="https://twitter.com/jstnkndy">@jstnkndy</a>) on Twitter recommended John The Ripper (not sure why I didn't consider this before!) and linked to a '<a href="https://github.com/magnumripper/JohnTheRipper/blob/unstable-jumbo/run/office2john.py">office2john.py</a>' file.</p>
<p>So I ran the office2john.py file against the Excel document and it spat out what looked like John's password file type format. I booted up my most powerful Linux machine (i7, 16GB RAM), installed John 1.8.0 from binary but John errored with "No password hashes loaded (see FAQ)". This looked as though the office2john.py script hadn't worked correctly...</p>
<p>I then noticed that John had 'community-enhanced' versions available for download, so I download and compiled John 1.7.9 Jumbo 7. Same error.</p>
<p>Finally I decided to try and use the code from the <a href="https://github.com/magnumripper/JohnTheRipper">GitHub repository</a> where the office2john.py file was hosted. During compiling I did get an error, something something pcap.h file or folder not found. This was remedied by installing the 'libpcap-dev' dependency (sudo apt-get install libpcap-dev) on Ubuntu.</p>
<p>Using the GitHub version of John, which I assume is the latest unstable community-enhanced codebase the Microsoft Excel document password (cocacola) was cracked in a matter of milliseconds. Yea, cocacola...</p>
<p>TLDR: Use the <a href="https://github.com/magnumripper/JohnTheRipper/blob/unstable-jumbo/run/office2john.py">office2john.py</a> file to create a JTR compatible password hash file, also use <a href="https://github.com/magnumripper/JohnTheRipper">this</a> version of JTR.</p>
