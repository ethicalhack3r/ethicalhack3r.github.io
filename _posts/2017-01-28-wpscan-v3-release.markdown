---
layout: post
status: publish
published: true
title: WPScan Version 3.0 BETA Release
excerpt: "Yesterday, January 28th 2017, members of the WPScan Team released WPScan version 3.0. WPScan is a black box WordPress Vulnerability Scanner written in Ruby which was released in 2011 for Penetration Testers. WPScan 3.0 is not just another release. It was re-written from the ground up by a WPScan team member, Erwan."
---

# WPScan Version 3.0 BETA Release

Yesterday, January 28th 2017, members of the WPScan Team released WPScan version 3.0.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">WPScan v3 BETA Released!!! <a href="https://t.co/eUSWg15iHC">https://t.co/eUSWg15iHC</a> (complete rewrite, new repo, ++functionality) Feedback welcome!</p>&mdash; WPScan (@_WPScan_) <a href="https://twitter.com/_WPScan_/status/824996933391499266">January 27, 2017</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

WPScan is a black box WordPress Vulnerability Scanner written in Ruby which was released in 2011 for Penetration Testers.

[WPScan 3.0](https://github.com/wpscanteam/wpscan-v3/) is not just another release. It was re-written from the ground up by a WPScan team member, [Erwan](https://twitter.com/erwan_lr). Erwan made his first commits to a private Git repository on April 19th 2015, and worked on it throughout the rest of 2015. It was pretty much release ready at the beginning of 2016.

![WPScan v3 Commit History](http://i.imgur.com/z6HDPiM.png)

We did not release WPScan v3 at that time because we were planning on first releasing a commercial Software as a Service (SaaS) product using the new codebase. After the SaaS was operational we planned on releasing WPScan v3 to the public. However, due to everyone in the WPScan Team  having full time jobs, and having to maintain the other aspects of the WPScan project, we were unable to complete the SaaS product in the time we wanted. But, we still desperately wanted to get the new WPScan codebase out there.

The main reasons why WPScan was completely rewritten was to be able to release WPScan as a Ruby gem, to support machine readable output, such as JSON, and to make it more modular.

## CMS Scanner Framework

Also created by Erwan, WPScan now uses a [CMS Scanner Framework](https://github.com/wpscanteam/CMSScanner) which handles a lot of the core scanning logic. The CMS Scanner Framework will allow for other scanners to be created for other CMSs.

WordPress has the largest market share in Content Management Systems (CMSs) by far. Looking at [some statistics](https://w3techs.com/technologies/history_overview/content_management) it has more than half of the CMS market share. Followed by Joomla, Drupal and Magento.

The new CMS Scanner Framework opens up the opportunity to create WPScan-esk scanners for these other CMSs. We are not working on creating another CMS scanner at the moment, nor currently have any plans to. So the opportunity is there if anyone wants to give it a shot.

## New Features

### Machine Readable Output

With the release of WPScan version 3.0 we now have machine readable output in JSON format. This was a [much requested feature](https://github.com/wpscanteam/wpscan/issues/198) by our users for obvious reasons. It makes WPScan more automateable and easier to integrate with other software.

### Ruby Gem

WPScan is now a [Ruby gem](https://rubygems.org/gems/wpscan). It will be easier for our users to install (`gem install wpscan`), easier to distribute and easier to include in other Ruby software projects via Gemfiles.

### Detection Modes

You can now choose from three different detection modes. Aggressive mode will send more requests and carry out additional checks which will detect more issues. Passive mode will not do any forced browsing, lessening the load on the target server and is less likely to be identified by IDS/IPS systems. Mixed mode is the default mode which uses a mixture of both aggressive and passive. If the target server you are scanning is not stable or has an IDS/IPS enabled, you are best choosing the Passive mode. If it is a stable server you could start with the mixed mode. If that does not find any good results, you could then try with the Aggressive mode.

### Configuration Files

All of WPScan's options can now be configured with configuration files. This will make it easier for users to create their own preferred defaults. Checkout the CLI help information for all the available command line flags.

### More Verbose Output

WPScan v3 detects a lot more useful information which will be output.

### More

There are tons of other improvements throughout WPScan v3. Everything was rewritten with the lessons learned over the +5 years of working on the project. Exit codes are now more in line with industry standards. The way we manage and store the vulnerability data. It should also be much easier to add your own checks.

## License

WPScan v3 was released under the same license as the WPScan v2 branch, the [WPScan Public License](https://github.com/wpscanteam/wpscan-v3/blob/master/LICENSE). This is not an Open Source license. The license allows for individuals to use WPScan free of charge. If you're a pentester (our intended users), or want to scan your own personal WordPress blog (also our intended users) then WPScan is free of charge. If you want to sell WPScan as a service, or use it to give your business a commercial advantage over your competitors, or to attract new clients, or keep existing ones. Then you will need to purchase a commercial license. Refer to the license for the full legalities. You can also contact us if you have any questions.

Please note that the CMS Scanner Framework is released under a separate license with [different conditions](https://github.com/wpscanteam/CMSScanner/blob/master/LICENSE).

## Road Ahead

WPScan v3 has been released under the "BETA" tag to reflect that it has not yes been tested by the masses. Although it does have extensive unit tests and has been used in the real world. We're hoping that user feedback over the next few weeks and months will help mold WPScan v3 into its final form. Once it makes sense to do so, we will start to deprecate the WPScan v2 branch. So for now, both versions will be supported. Although the v2 branch will most likely just receive small bug fixes, whereas v3 will receive bigger bug fixes and new features.
