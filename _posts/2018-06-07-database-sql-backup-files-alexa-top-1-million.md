---
layout: post
status: publish
published: true
title: Database Dumps and the Alexa Top 1 Million
excerpt: "Out of the 852,301 (85%) of sites that we were able to check, we identified that 736 (0.086%) of them were exposing their database export files publicly with the same name as their domain. This may not seem like a lot, but when you consider the impact of the database contents being exposed to malicious actors, it is a considerable risk to the affected individual sites, and their users.

The sites affected included 11 worldwide government websites, a lot of porn sites, 2 small banks, 5 educational institutions and a lot of other random websites, such as personal sites, anime sites, etc.

Out of the 736 affected sites, 290 (39%) of them, were running WordPress."
---

### Introduction

While at WordCamp Irun recently there was a talk on [WP-CLI](https://wp-cli.org/), which is a command line interface for WordPress. One of WP-CLI's functionalities is to export the database to a file. Fortunately, by default the exported file name is random enough to make it difficult to brute force, if, for example, someone exported the file to a publicly accessible location on their Web server.

However, the WP-CLI export database command does allow users to specify an output file name. And this gave us an idea.

How many people export their database to a publicly accessible location with a predictable file name?

In our experience, developers often name their application's database with the same name as their domain name. So, for example, if my application's domain name was ```superawesomeapp.com```, it is possible that the database for this application is named ```superawesomeapp```. Which makes it also possible that if the database was exported, the file name may be the same as the database name, ```superawesomeapp.sql```.

There are also other possible common database export file names, such as ```backup.sql```, ```database.sql```, ```database.backup```, ```dump.sql```, etc. However, these file names are most likely already searched for by automated web scanning tools. In fact, [Nikto](https://github.com/sullo/nikto) already includes most of these file name checks, and more. But it is less likely that automated web scanning tools check for the case we discussed, naming the database export file name the same name as the database, which is likely to be the same name as the domain name.

This could result in very sensitive information being left publicly accessible, even after an application security assessment has been conducted. Databases often contain IP addresses, payment data, personal user information, passwords, usernames, and a lot more. Leaving this data exposed would result in a breach of [The EU General Data Protection Regulation (GDPR)](https://www.eugdpr.org/).

### Gathering Data

With this in mind, we wanted to prove our hypothesis. How many people actually exported their database to a publicly accessible location on their web server, using the same name as their domain name?

We have done research using the [Alexa Top 1 Million Global sites](https://www.alexa.com/topsites) list in the past, [Zone Transfers on The Alexa Top 1 Million](https://blog.dewhurstsecurity.com/2013/08/03/zone-transfers-on-the-alexa-top-1-million.html) and [Zone Transfers on The Alexa Top 1 Million Part 2](https://blog.dewhurstsecurity.com/2013/08/08/zone-transfers-on-the-alexa-top-1-million-part-2.html), to create better subdomain brute forcing lists.

We decided to use the Alexa Top 1 Million websites list to check how many of them had the exported database ```.sql``` file in their root web server directories.

### The Results

After spending a couple of days writing and testing a script that was fast enough, and accurate enough, we ran the script against the Alexa Top 1 Million sites list. The script took the website name, extracted the domain, appended ```.sql```, and then queried the site for the file.

We used the ```Range``` HTTP request header to request only the first 3MB of the file, to search for a string to identify the file was a database output file. None of the files were stored to disk and the server used was destroyed after the research was conducted.

The script took just under 10 hours to complete, 107,922 of the script's requests timedout due to the site not responding quick enough, and 39,777 of the sites did not respond at all when sending a request. That's a total of 147,699 sites, about 15%, out of the 1 million sites that we were unable to check.

Out of the 852,301 (85%) of sites that we were able to check, we identified that 736 (0.086%) of them were exposing their database export files publicly with the same name as their domain. This may not seem like a lot, but when you consider the impact of the database contents being exposed to malicious actors, it is a considerable risk to the affected individual sites, and their users.

The sites affected included 11 worldwide government websites, a lot of porn sites, 2 small banks, 5 educational institutions and a lot of other random websites, such as personal sites, anime sites, etc.

Out of the 736 affected sites, 290 (39%) of them, were running WordPress.

### Disclosure

For the affected government websites, we contacted the affected countries Computer Emergency Response Team (CERT), who were all very responsive and contacted people within their respective government departments to have the files removed from the web servers.

We attempted to contact some of the affected sites manually, some of which were quite high up in the Alexa rankings, however, we only received a response from one of them, who removed the file from their site.

This leaves the vast majority of the 736 sites still affected.

### Tools

We decided that this issue was serious enough to implement checks for the database output files with the same file name as the domain name, into various tools that we use on a regular basis. This will ensure that every time we conduct a test for one of out clients, we check for this issue. It also means that others will benefit from this check too, if they use the same tools against their own websites, or within penetration tests.

#### Nikto

For the Nikto tool, adding the check was as trivial as adding the ```.sql``` extension to similar already existing checks.

[https://github.com/sullo/nikto/pull/542/commits/513c647d7f7490580edc66c22525dcdf36dfeef3](https://github.com/sullo/nikto/pull/542/commits/513c647d7f7490580edc66c22525dcdf36dfeef3)

#### WPScan

WPScan version 2 (master branch) now checks for the ```superawesomeapp.sql``` and other ```.sql``` backup files.

[https://github.com/wpscanteam/wpscan/commit/0e73774bd9f6d13c8194e44b9b799d3e5dd089ca](https://github.com/wpscanteam/wpscan/commit/0e73774bd9f6d13c8194e44b9b799d3e5dd089ca)

### Conclusions

Do not export database dumps/backups to publicly accessible places on your web server. When you create database exports ensure the file name is long, complex and random, so that it can not be guessed.