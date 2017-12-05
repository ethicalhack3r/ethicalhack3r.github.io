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
<p>{% highlight ruby %}#!/usr/bin/env ruby

#
# Caesar Cipher (ROT) Encoder/Decoder - Ryan 'ethicalhack3r' Dewhurst - 05.08.2012
#

@alphabet = ('a'..'z').to_a

def encode(plaintext)
  plaintext = plaintext.gsub(/\s+/, '').downcase

  @alphabet.each do |letter|
    encoded_forward = ''

    plaintext_position = @alphabet.index(plaintext[0].chr)
    cipher_position = @alphabet.index(letter)
    position_difference = plaintext_position - cipher_position

    plaintext.split('').each do |char|
      encoded_forward += @alphabet.at(position_forward_count(@alphabet.index(char), position_difference)).to_s
    end

    puts "Shifted #{position_difference} to '#{letter}' - #{encoded_forward}"
  end

end

def decode(cipher)
  cipher = cipher.gsub(/\s+/, '').downcase

  @alphabet.each do |letter|
    deciphered_forward = ''

    cipher_position = @alphabet.index(cipher[0].chr)
    clear_position = @alphabet.index(letter)
    position_difference = cipher_position - clear_position

    cipher.split('').each do |char|
      deciphered_forward += @alphabet.at(position_forward_count(@alphabet.index(char), position_difference)).to_s
    end

    puts "Shifted #{position_difference} to '#{letter}' - #{deciphered_forward}"
  end

end

def position_forward_count(current_position, position_difference)
  position_total = (current_position + position_difference)
  position_total > 25 ? position_total - 25 : position_total
end

puts '[Decode]'
decode('W KHTXLFNEUZQ IRA MXPSVR  YHU WKH ODCB GRJ')
puts '[Encode]'
encode('plaintext')
{% endhighlight %}</p>
