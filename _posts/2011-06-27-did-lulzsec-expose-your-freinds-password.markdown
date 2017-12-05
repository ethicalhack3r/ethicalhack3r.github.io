---
layout: post
status: publish
published: true
title: Did lulzsec expose your friends password?
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "I assume you have all heard about Lulzsec over the past few months so I
  will not go into their backstory and instead get straight to the point.\r\n\r\nYesterday,
  26th June 2011, they released their last data dump on ThePirateBay (TPB) containing
  usernames and passwords from a few different sources. One of those sources was hackforums.net,
  I myself had registered here once upon a time. Luckily I had signed up with a disposable
  password. It turns out however that, yes, that password was leaked in the final
  lulzsec data dump.\r\n\r\nThe data dump has now been removed from TPB due to some
  of the files allegedly being infected with malware. So I found this site which allows
  you to search for your email address to see if you may have been effected; <a href=\"http://dazzlepod.com/lulzsec/final/\"
  target=\"_blank\">http://dazzlepod.com/lulzsec/final/</a>\r\n\r\n"
wordpress_id: 16446
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16446
date: '2011-06-27 00:45:22 +0100'
date_gmt: '2011-06-26 23:45:22 +0100'
---
<p>I assume you have all heard about Lulzsec over the past few months so I will not go into their backstory and instead get straight to the point.</p>
<p>Yesterday, 26th June 2011, they released their last data dump on ThePirateBay (TPB) containing usernames and passwords from a few different sources. One of those sources was hackforums.net, I myself had registered here once upon a time. Luckily I had signed up with a disposable password. It turns out however that, yes, that password was leaked in the final lulzsec data dump.</p>
<p>The data dump has now been removed from TPB due to some of the files allegedly being infected with malware. So I found this site which allows you to search for your email address to see if you may have been effected; <a href="http://dazzlepod.com/lulzsec/final/" target="_blank">http://dazzlepod.com/lulzsec/final/</a></p>
<p><a id="more"></a><a id="more-16446"></a></p>
<p>So then I began to wonder, If I was on that list, who else I knew may have been on it.</p>
<p>So I decided to write a quick Ruby script which would check just that.</p>
<p>First off, I had to download my Google contacts. To do this simply go to <a href="http://contacts.google.com">http://contacts.google.com</a>.</p>
<p>I exported all of my contacts in Excel format. Highlighted the email column and pasted them into a file called contacts.txt. (remove the column name from the text file)</p>
<p>Then simply run my (very rushed, it's 1AM) Ruby script which can be found here; <a href="http://www.pastie.org/2126584" target="_blank">http://www.pastie.org/2126584</a> (you will need to install the Typhoeus gem)</p>
<p>{% highlight ruby %}
#!/usr/bin/env ruby

require 'rubygems'
require 'net/http'
require 'typhoeus'

found_emails = []
hydra = Typhoeus::Hydra.new(:max_concurrency => 20, :timeout => 2000)

file_contents = File.open("contacts.txt","r") {|file| file.readlines.collect{|line| line.chomp}}
emails = file_contents

emails.each do |email|

  request = Typhoeus::Request.new("http://dazzlepod.com/lulzsec/final/?email="+email.to_s)

  request.on_complete do |response|
    puts "Trying " + email
    if response.body =~ %r{<strong>1 account</strong>}
      found_emails.push(email)
   end
  end

  hydra.queue(request)

end

hydra.run

puts found_emails.size.to_s
puts found_emails.inspect
{% endhighlight %}</p>
<p>Out of my 900 contacts, 4 of them were in the lulzsec data dump. I have informed them.</p>
<p>Try it out and inform your contacts too!</p>
