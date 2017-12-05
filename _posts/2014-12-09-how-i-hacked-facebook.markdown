---
layout: post
status: publish
published: true
title: How I hacked Facebook
excerpt: "Ok, ok. I didn't quite 'hack Facebook'. What I did was execute OS level commands on one of Facebook's acquisition's servers. This is how I did it."
---

Ok, ok. I didn't quite "hack Facebook". What I did was execute OS level commands on one of Facebook's acquisition's servers.

This is how I did it.

One day last September I was in bed with terrible flu. While I was bedridden I got bored and started to poke around Facebook's Bug Bounty program. I have participated in Bug Bounties before but never Facebook's.

This is by no means a complicated hack by the way, but it worked.

I started by port scanning Facebook's in scope domains with Nmap. Probed a few listening services on IPs that looked interesting.

I also started to look at Facebook's acquisitions. Doing the same, port scanning common ports, probing services that looked interesting.

On one of Facebook's acquisition's IPs they had Jenkins running on a common port. I opened it up in my browser but unfortunately it prompted me with a Basic Authentication login box. I assume this is where most other bounty hunters and Facebook's own security team stopped testing.

I decided to do a full port scan with nmap. The results showed another Jenkins service running on a less common port. Accessing it over this less common port it did not prompt me for authentication. Bingo!

For those of you that do not know, Jenkins is a 'continuous integration server'. Once authenticated it allows you to run 'Groovy script' through the 'Jenkins Script Console'. 

By using Groovy script and the Jenkins Script Console I was able to execute commands on the server under the 'jenkins' user.

Example Groovy script to run the ```whoami``` command:

```
def command = """whoami"""
def proc = command.execute()
proc.waitFor()

println "stdout: ${proc.in.text}"
```

I reported this issue to Facebook and they patched it very fast. I was awarded $7,500 through their bug bounty program. The payment took a few months to come through and lots of emails back and forth. But it came through in the end.

What's the takeaway? Don't forget the basics. I was able to find a pretty risky bug in one of Facebook's acquisitions from within my bed by just using Nmap.

I would like to say thank you to Facebook for the payment and I hope I can report more bugs to them in the future.
