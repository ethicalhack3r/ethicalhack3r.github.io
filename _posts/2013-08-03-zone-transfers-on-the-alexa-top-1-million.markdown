---
layout: post
status: publish
published: true
title: Zone Transfers on The Alexa Top 1 Million
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "At work as part of every assessment we do a some reconnaissance which includes
  attempting a <a href=\"https://en.wikipedia.org/wiki/DNS_zone_transfer\">DNS Zone
  Transfer (axfr)</a> and conducting a subdomain brute force on the target domain/s.
  The subdomain brute force is only as good as your wordlist, the Zone Transfer is
  a matter of luck.\r\n\r\nAlexa release a list of the <a href=\"http://s3.amazonaws.com/alexa-static/top-1m.csv.zip\">top
  1 million sites</a> which is updated on a daily basis. To create a better subdomain
  wordlist to conduct subdomain brute forcing I attempted a DNS Zone Transfer against
  the first 2000 sites in the Alexa Top 1 Million list. With every successful Zone
  Transfer the DNS A records were stored in a CSV file.\r\n\r\nThis was all done using
  Carlos Perez's <a href=\"https://github.com/darkoperator/dnsrecon\">dnsrecon</a>
  DNS enumeration tool. Dnsrecon was ever so slightly modified to only save A records,
  apart from that I just used a <a href=\"https://gist.github.com/ethicalhack3r/6145925\">bash
  script</a> to iterate over the Top 1 Million list and ran dnsrecon's axfr option
  for each site with CSV output enabled.\r\n\r\n"
wordpress_id: 17108
wordpress_url: http://www.ethicalhack3r.co.uk/?p=17108
date: '2013-08-03 12:37:33 +0100'
date_gmt: '2013-08-03 11:37:33 +0100'
---
<p>At work as part of every assessment we do a some reconnaissance which includes attempting a <a href="https://en.wikipedia.org/wiki/DNS_zone_transfer">DNS Zone Transfer (axfr)</a> and conducting a subdomain brute force on the target domain/s. The subdomain brute force is only as good as your wordlist, the Zone Transfer is a matter of luck.</p>
<p>Alexa release a list of the <a href="http://s3.amazonaws.com/alexa-static/top-1m.csv.zip">top 1 million sites</a> which is updated on a daily basis. To create a better subdomain wordlist to conduct subdomain brute forcing I attempted a DNS Zone Transfer against the first 2000 sites in the Alexa Top 1 Million list. With every successful Zone Transfer the DNS A records were stored in a CSV file.</p>
<p>This was all done using Carlos Perez's <a href="https://github.com/darkoperator/dnsrecon">dnsrecon</a> DNS enumeration tool. Dnsrecon was ever so slightly modified to only save A records, apart from that I just used a <a href="https://gist.github.com/ethicalhack3r/6145925">bash script</a> to iterate over the Top 1 Million list and ran dnsrecon's axfr option for each site with CSV output enabled.</p>
<p><a id="more"></a><a id="more-17108"></a></p>
<p><strong>The Results</strong></p>
<p>A nice side effect to creating the subdomain wordlist is knowing how many DNS Name Servers have Zone Transfers enabled and which sites. Out of the top 2000 sites, 98 had at least one Name Server with Zone Transfer enabled (4.9%). This included sites we all know and/or use such as <a href="https://www.pingdom.com/">Pingdom</a>, <a href="https://mega.co.nz/">Mega Upload</a>, <a href="https://www.spotify.com/">Spotify</a>, <a href="https://gravatar.com/">Gravatar</a>, <a href="https://www.americanexpress.com/">American Express</a> and 93 other sites in the top 2000. Some of these sites may have Zone Transfers enabled on purpose, the majority probably don't know it is enabled. The full list of domains with Zone Transfers enabled and their Alexa Ranking can be found here - <a href="http://ethicalhack3r.co.uk/files/misc/axfr_domains.txt">http://ethicalhack3r.co.uk/files/misc/axfr_domains.txt</a></p>
<p>Top 10 Alexa domains with Zone Transfers enabled:</p>
<p>{% highlight text %}
  Rank,Domain
7,wikipedia.org
87,about.com
119,livedoor.com
120,weather.com
147,kickass.to
156,wikimedia.org
173,liveinternet.ru
194,goo.ne.jp
216,ehow.com
233,hardsextube.com
{% endhighlight %}</p>
<p>In total there were 55,450 A records gathered from the 98 sites. After sorting the list of subdomains by the number of sites each subdomain was found on, removing any duplicates (some sites listed more than one of the same subdomain) and removing subdomains that were only found on one site, the final subdomain list consists of 859 lines. The final list including the number of instances each subdomain was seen across the 98 sites can be found here - <a href="http://ethicalhack3r.co.uk/files/misc/subdomain_count.txt">http://ethicalhack3r.co.uk/files/misc/subdomain_count.txt</a></p>
<p>The top 10 subdomains were:<br />
{% highlight text %}
54 mail
47 www
35 ns2
34 ns1
28 blog
26 localhost
25 m
23 ftp
19 mobile
16 ns3
{% endhighlight %}</p>
<p>The ns2 subdomain is apparently more popular than the ns1 subdomain which is unexpected. The localhost subdomain seemed to always point to the localhost (127.0.0.1). The mail subdomain was the most popular subdomain overall.</p>
<p>And finally, the subdomain wordlist itself sorted by popularity can be found here - <a href="http://ethicalhack3r.co.uk/files/fuzzing/subdomains.txt">http://ethicalhack3r.co.uk/files/fuzzing/subdomains.txt</a> (859 lines). I would recommend combining this list with the list you're already using for the best results.</p>
<p>And this is the code used to sort the dnsrecon CSV output files:<br />
{% highlight ruby %}
#!/usr/bin/env ruby

require 'public_suffix'
require 'uri'

results = `cat axfr_results/*.csv`
output = Hash.new(0)
already_seen = []

results.split("\n").each do |line|
  domain    = line.split(',')[1]
  if ! already_seen.include?(domain)
    already_seen << domain
    subdomain = PublicSuffix.parse( domain ).trd if PublicSuffix.valid?( domain )
    output[subdomain] += 1
  end
end

Hash[output.sort_by{|k, v| v}.reverse].each_pair do |key, value|
 next if key == '@' || key == '*'
 puts "#{value} #{key}" if value != 1
end
{% endhighlight %}</p>
<p>The next step if anyone has the time and resources is to conduct the test against the full top 1 million list. The top 2000 took about 12 hours or so.</p>
