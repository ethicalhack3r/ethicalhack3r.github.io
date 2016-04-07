---
layout: post
status: publish
published: false
title: OSVDB Gone
excerpt: ""
---

<p align="center"><img src="http://i.imgur.com/ffTzX2e.jpg" alt="OSVDB" /></p>

On April 5th the Open Sourced Vulnerability Database (OSVDB) announced that they were [shutting down](https://blog.osvdb.org/2016/04/05/osvdb-fin/).

For me, the writing was on the wall when OSVDB implemented CloudFlare's DDoS protection which makes you wait 5 seconds on a loading screen before you are able to access the site. It was not so much the waiting that alluded to the potential ending of OSVDB, it was that OSVDB's Google PageRank was taking a battering. So much that searching for terms such as "OSVDB $somid" would not result in a osvdb.org hit on Google's front page.

On Twitter most people have had good things to say about the legacy of OSVDB. I want to point out the value I believe OSDVB provided to the community and to myself. My perspective is biased as I help build and run [WPVULNDB](https://wpvulndb.com), a WordPress Vulnerability Database. This may give me some unique insight, even if only slightly.

One thing people like to point out is that OSVDB wasn't Open Source. I have used and contributed (ever so slightly) to OSVDB when it was still named the 'Open Source Vulnerability Database'. From memory, the name changed a few years ago, and along with the name change OSVDB stopped taking open contributions, restricted their API and stopped distributing their database dump freely.

OSVDB's initial idea must have been that a lot of the community would chip in with the workload to help sustain and build a community project.It looks like that didn't work out due to the low number of contributors compared with the work needed. This must have left a burden on the lives of those who were involved.

The problem when you end up doing all the work while others benefit without doing their share is frustrating, as I'm sure we can all agree. We've all been in the situation at work where a colleague does not pull their weight. Imagine sacrificing hours, weeks, months, years of work for the benefit of others while you receive little reward.

Time is the most valuable resource we have. Time away from paid work to buy that new family home, time away from your children, time away from your wife, your friends, etc, etc. Time away from your life.

OSVDB did have a commercial arm, "it was a business!" I hear you cry. There are costs that come with running a vulnerability database.  Running the servers, backups, potential legal issues, accounting and other business costs. Without money the lights go out. Most of us still got immense value from OSVDB for free (gratis). Apart from my menial contribution I never paid anything to read, reference or search OSVDB's public database.

OSVDB did not allow you to take all their data to add value to your own business or your own personal needs for free (gratis)? Just because they give something away for free doesn't mean you are entitled to everything they own.

Here are some examples of other tools currently referencing OSVDB data, adding value to those tools and ultimately the end users:

Nessus:

<img src="http://i.imgur.com/ysR4avq.png" alt="Nessus OSVDB" />

ExploitDB:

<img src="http://i.imgur.com/UDpQzqz.png" alt="ExploitDB OSVDB" />

WPVULNDB & WPScan:

<img src="http://i.imgur.com/eXNF5ID.png" alt="WPVULNDB OSVDB" />

Nikto:

<img src="http://i.imgur.com/KfSiPl8.png" alt="Nikto OSVDB" />

The OSVDB references from these tools will most likely dissapear over the next weeks and months. We have already started that process on WPVULNDB.
