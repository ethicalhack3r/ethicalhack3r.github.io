---
layout: post
status: publish
published: false
title: OSVDB Gone
excerpt: ""
---

<p align="center"><img src="http://i.imgur.com/ffTzX2e.jpg" alt="OSVDB" /></p>

On April 5th the Open Sourced Vulnerability Database (OSVDB) announced that they were [shutting down](https://blog.osvdb.org/2016/04/05/osvdb-fin/) their vulnerability database. For me, the writing was on the wall when OSVDB permanently implemented CloudFlare's DDoS protection which makes you wait 5 seconds on a loading screen before you are able to access the site. It was not so much the waiting that alluded to the potential ending of OSVDB, it was that OSVDB's Google PageRank was taking a battering, so much so that searching for terms such as "OSVDB $somid" would not result in a osvd.org hit on Google's front page.

On Twitter most people have had good things to say about the legacy of OSVDB, however, there have been some which dimiss its value. This is entirely fine of course, everyone is entitled to their own opinions. But, I wanted to point out the value I believe OSDVB provided to the information security community.

My perspective is probably biased as I helped build and run WPVULNDB, a WordPress Vulnerability Database. However, this may also give me some unique insight, even if only slightly, of what it is like to run a popular vulnerability database.

One thing people like to point out is that OSVDB wasn't "Open Source", as if this detracted from its value. I used and contributed (ever so slightly) to OSVDB when it was still named the 'Open Source Vulnerability Database' rather than the 'Open Sourced Vulnerability Database'. From memory the name changed a few years ago, and along with the name change OSVDB stopped taking open contributions, restricted their API and stopped distributing their database dump freely. They say they did this because they were not recieving enough contributions to merit the giving away of the data for free (gratis). The vast majority of the work was being done by them, however, many others were benefiting from this work, [even abusing it](https://blog.osvdb.org/2014/05/07/the-scraping-problem-and-ethics/).

OSVDB's initial idea must have been that a lot of the community would chip in with the workload to help sustain and build a community project. However, it looks like that didn't work out due to the low number of contributors compared with the work needed to be done. This must have left a hefty burden on the lives of those who were actively involved.

The problem when you end up doing all the work while others benefit from it without doing their share is very frustrating as I'm sure we can all agree. We've all been in the situation at work where a colleage does not pull their weight. Imagine sacrficing hours, weeks, months, years of work for the benefit of others while you recieve little reward. Time is the most valuable resource we have. Time away from paid work to buy that new family home, time away from your children, time away from your wife, your friends, etc, etc.

Sure, OSVDB did have a commercial arm, "it was a business!" I hear you cry. Of course it made money, maybe even as a non-profit? (I'm not entirely sure of the details). But there are costs of running the servers, backups, legal issues, accounting, other business costs. Who should pay for all that? It needs to make money to be even slghtly sustainable. Without money the lights go out.

The point we're missing here is, sure it was a business, maybe not a great one, but most of us still got immense value from OSVDB for free (gratis). You at some point in your career probably got some value from OSVDB and you paid nothing back in return. Apart from my, I shouldn't probably even mention small contribution, I never paid anything to read, reference or search OSVDB's public web database. Not only did this information hold vendors to account, it was a huge and largely accurate database of vulnerabilities that anyone could read, references and search, for absolutly nothing (gratis).

Oh, but OSVDB did not allow you to take all that data they had worked years for to add value to your own bussiness or your own personal needs for free (gratis)? Why should they? What do they owe the vast majority of you? Just because they give something away for free (gratis) doesn't mean you can have the socks of their feet.

Some may not realise how much OSVDB influenced and was used within the industry, here are some examples of other tools referencing OSVDB data, adding value to those tools and ultimatly the end users:

Nessus:

<p align="center"><img src="http://i.imgur.com/ysR4avq.png" alt="Nessus OSVDB" /></p>

ExploitDB:

<p align="center"><img src="http://i.imgur.com/UDpQzqz.png" alt="ExploitDB OSVDB" /></p>

WPVULNDB & WPScan:

<p align="center"><img src="http://i.imgur.com/eXNF5ID.png" alt="WPVULNDB OSVDB" /></p>

Nikto:

<p align="center"><img src="http://i.imgur.com/KfSiPl8.png" alt="Nikto OSVDB" /></p>
