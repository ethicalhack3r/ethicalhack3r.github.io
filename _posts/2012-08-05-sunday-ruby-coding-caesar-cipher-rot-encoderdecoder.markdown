---
layout: post
status: publish
published: true
title: 'Sunday Ruby Coding: Caesar Cipher (ROT) Encoder/Decoder '
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
wordpress_id: 16840
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16840
date: '2012-08-05 19:01:03 +0100'
date_gmt: '2012-08-05 18:01:03 +0100'
---
<p>It has been a rainy Sunday so I wrote a Caesar Cipher (ROT) Encoder/Decoder in Ruby to ease the boredom.</p>
<p>[ruby]<br />
#!/usr/bin/env ruby</p>
<p>#<br />
# Caesar Cipher (ROT) Encoder/Decoder - Ryan 'ethicalhack3r' Dewhurst - 05.08.2012<br />
#</p>
<p>@alphabet = ('a'..'z').to_a</p>
<p>def encode(plaintext)<br />
  plaintext = plaintext.gsub(/\s+/, '').downcase</p>
<p>  @alphabet.each do |letter|<br />
    encoded_forward = ''</p>
<p>    plaintext_position = @alphabet.index(plaintext[0].chr)<br />
    cipher_position = @alphabet.index(letter)<br />
    position_difference = plaintext_position - cipher_position</p>
<p>    plaintext.split('').each do |char|<br />
      encoded_forward += @alphabet.at(position_forward_count(@alphabet.index(char), position_difference)).to_s<br />
    end</p>
<p>    puts "Shifted #{position_difference} to '#{letter}' - #{encoded_forward}"<br />
  end</p>
<p>end</p>
<p>def decode(cipher)<br />
  cipher = cipher.gsub(/\s+/, '').downcase</p>
<p>  @alphabet.each do |letter|<br />
    deciphered_forward = ''</p>
<p>    cipher_position = @alphabet.index(cipher[0].chr)<br />
    clear_position = @alphabet.index(letter)<br />
    position_difference = cipher_position - clear_position</p>
<p>    cipher.split('').each do |char|<br />
      deciphered_forward += @alphabet.at(position_forward_count(@alphabet.index(char), position_difference)).to_s<br />
    end</p>
<p>    puts "Shifted #{position_difference} to '#{letter}' - #{deciphered_forward}"<br />
  end</p>
<p>end</p>
<p>def position_forward_count(current_position, position_difference)<br />
  position_total = (current_position + position_difference)<br />
  position_total > 25 ? position_total - 25 : position_total<br />
end</p>
<p>puts '[Decode]'<br />
decode('W KHTXLFNEUZQ IRA MXPSVR  YHU WKH ODCB GRJ')<br />
puts '[Encode]'<br />
encode('plaintext')<br />
[/ruby]</p>
