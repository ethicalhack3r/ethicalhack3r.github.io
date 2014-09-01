---
layout: post
status: publish
published: true
title: DropBox Security
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "For those of you new to Dropbox:\r\n<blockquote>\"Dropbox is a Web-based
  file hosting service operated by Dropbox, Inc. which uses cloud computing to enable
  users to store and share files and folders with others across the Internet using
  file synchronization.\"</blockquote>\r\n<a href=\"http://en.wikipedia.org/wiki/Dropbox_%28service%29\"
  target=\"_blank\">http://en.wikipedia.org/wiki/Dropbox_%28service%29</a>\r\n\r\n<a
  href=\"https://www.dropbox.com/\" target=\"_blank\"><img src=\"http://www.ethicalhack3r.co.uk/wp-content/uploads/2010/08/Dropbox-150x150.jpg\"
  alt=\"\" title=\"Dropbox\" width=\"150\" height=\"150\" class=\"alignright size-thumbnail
  wp-image-757\" /></a>\r\n\r\nDropbox has become very popular and widely used as
  it has so many different uses and makes file sharing over the internet easy. Dropbox
  allows you to make public image galleries, share files publicly, share files between
  computers and manage version control. All this straight from your file system. I
  like to think of it as git or a subversion repository with a nice interface. \r\n\r\n"
wordpress_id: 756
wordpress_url: http://www.ethicalhack3r.co.uk/?p=756
date: '2010-08-03 13:29:06 +0100'
date_gmt: '2010-08-03 12:29:06 +0100'
---
<p>For those of you new to Dropbox:</p>
<blockquote><p>"Dropbox is a Web-based file hosting service operated by Dropbox, Inc. which uses cloud computing to enable users to store and share files and folders with others across the Internet using file synchronization."</p></blockquote>
<p><a href="http://en.wikipedia.org/wiki/Dropbox_%28service%29" target="_blank">http://en.wikipedia.org/wiki/Dropbox_%28service%29</a></p>
<p><a href="https://www.dropbox.com/" target="_blank"><img src="http://www.ethicalhack3r.co.uk/wp-content/uploads/2010/08/Dropbox-150x150.jpg" alt="" title="Dropbox" width="150" height="150" class="alignright size-thumbnail wp-image-757" /></a></p>
<p>Dropbox has become very popular and widely used as it has so many different uses and makes file sharing over the internet easy. Dropbox allows you to make public image galleries, share files publicly, share files between computers and manage version control. All this straight from your file system. I like to think of it as git or a subversion repository with a nice interface. </p>
<p><a id="more"></a><a id="more-756"></a></p>
<p>So how secure is Dropbox? According to the Dropbox FAQ:</p>
<p>    *  Shared folders are viewable only by people you invite</p>
<p>    * All transmission of file data and metadata occurs over an encrypted channel (SSL).</p>
<p>    * All files stored on Dropbox servers are encrypted (AES-256) and are inaccessible without your account password</p>
<p>    * Dropbox website and client software have been hardened against attacks from hackers</p>
<p>    * Online access to your files require your username and password</p>
<p>    * Public files are only viewable by people who have a link to the file(s). Public folders are not browsable or searchable</p>
<p>    * Dropbox employees aren't able to access user files, and when troubleshooting an account they only have access to file metadata (filenames, file sizes, etc., not the file contents)</p>
<p><a href="https://www.dropbox.com/help/27" target="_blank">https://www.dropbox.com/help/27</a></p>
<p>Let's take a look at these claims more closely, "Shared folders are viewable only by people you invite.". True, however if an attacker has access to your local machine they can invite themselves. You may argue that if some one has access to your local machine the game is over anyway. The problem here is, all the attacker has to do is click a few buttons and you will share not only your current Dropbox files but all future files until the victim realises. This can be done via the Dropbox main menu by clicking on 'Browse on Dropbox Website...', this will open your default browser and automatically log you in to your online Dropbox account allowing you to change Sharing and other options.</p>
<p>Using SSL is awesome, "All transmission of file data and metadata occurs over an encrypted channel (SSL).". However we have all seen and witnessed attacks on SSL using man-in-the-middle techniques. But again, here you could argue that if some one has already managed to man-in-the-middle you then you probably have more things to worry about than your Dropbox files.</p>
<p>Using a good encryption algorithm won't protect you against users picking weak passwords. "All files stored on Dropbox servers are encrypted (AES-256) and are inaccessible without your account password" Unfortunately I didn't have time to scrutinize their password policy however I did notice that they do not take any measures to prevent brute force attacks on their HTTP login form. </p>
<p>It's good that Dropbox have 'hardened' against attacks, but what does this entail? SDLC? black box scanning? "Dropbox website and client software have been hardened against attacks from hackers"</p>
<p>Not always. "Online access to your files require your username and password" As mentioned before by clicking on the 'Browse on Dropbox Website...' from the Dropbox menu, no authentication is needed however the attacker would need local access.</p>
<p>Oh really?! "Public files are only viewable by people who have a link to the file(s). Public folders are not browsable or searchable". When you use a common numbering system in your URIs then this becomes false. A link to a Dropbox Public folder looks like so: <a href="http://dl.dropbox.com/u/7000455/index.html" target="_BLANK">http://dl.dropbox.com/u/7000455/index.html</a>. The seven digit number is the Dropbox username, in this case some random user. but what happens if we increment that number? Well, this happens, <a href="http://dl.dropbox.com/u/7001955/index.html" target="_BLANK">http://dl.dropbox.com/u/7001955/index.html</a>. What if some not so bright people stored other not so 'puclic' files in their public folder? We've all come across these types of people before! Dropbox terms and conditions state; "BY PLACING FILES IN YOUR PUBLIC FOLDERS, YOU CONSENT TO SHARE ACCESS TO THE CONTENT OF THOSE FOLDERS WITH OTHER DROPBOX USERS AND/OR THE PUBLIC". Dropbox also states; "It is possible, however unlikely, that someone could guess your link if they knew the file name."</p>
<p>This is good, "Dropbox employees aren't able to access user files, and when troubleshooting an account they only have access to file metadata (filenames, file sizes, etc., not the file contents)". However you can only 'permanently delete' files via the online web interface, just by deleting them from your Dropbox folder does not mean they have been 'permanently deleted'.</p>
<p>Dropbox is a great service however people need to be aware of the risks in sharing sensitive information in the 'cloud'. </p>
<p>UPDATE: 03/08/2010 - 19:30</p>
<p>I hadn't noticed earlier however after a chat over a meal we came to realise that if a Dropbox public file renders HTML, then why not Javascript? It turns out that executing Javascript is possible however the Dropbox login cookies do not apply to the dl subdomain. But it is a dream come true for any wannabee Dropbox phisher! This is a file hosted on my Public folder: <a href="http://dl.dropbox.com/u/7879629/index.html">http://dl.dropbox.com/u/7879629/index.html</a> It does not send the form data any where, it just redirects to this blog on pressing login.</p>
<p>UPDATE: 05/08/2010 20:00</p>
<p>I contacted Dropbox through their support system on August 3rd to highlight the Phishing risk and this blog post. I received an email with a one line reply today from Kevin Chu of Dropbox; "Yes, we are looking at alternative domains to use for hosting public files."</p>
