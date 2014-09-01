---
layout: post
status: publish
published: true
title: Concrete5 5.5.2.1 Multiple Authenticated Cross-Site Scripting (XSS)
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "# Exploit Title: Concrete5 5.5.2.1 Multiple Authenticated Cross-Site Scripting
  (XSS)\r\n# Date: 2012-08-25\r\n# Author: Ryan 'ethicalhack3r' Dewhurst (www.ethicalhack3r.co.uk)\r\n#
  Software Link: http://sourceforge.net/projects/concretecms/files/concrete5/5.5.2.1/\r\n#
  Version: 5.5.2.1\r\n\r\n1.Vulnerability Description\r\n\r\nMultiple authenticated
  Cross-Site Scripting (XSS) vulnerabilities were identified within Concrete5 version
  5.5.2.1. Also reported were some cookie security improvements. The first Concrete5
  advisory can be found here [1].\r\n\r\n2.Software Description\r\n\r\nCMS made for
  Marketing but built for Geeks, concrete5 [0] is a content management system that
  is free and open source.\r\n\r\n3. Vulnerability Information\r\n\r\n"
wordpress_id: 16847
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16847
date: '2012-08-25 10:05:16 +0100'
date_gmt: '2012-08-25 09:05:16 +0100'
---
<p># Exploit Title: Concrete5 5.5.2.1 Multiple Authenticated Cross-Site Scripting (XSS)<br />
# Date: 2012-08-25<br />
# Author: Ryan 'ethicalhack3r' Dewhurst (www.ethicalhack3r.co.uk)<br />
# Software Link: http://sourceforge.net/projects/concretecms/files/concrete5/5.5.2.1/<br />
# Version: 5.5.2.1</p>
<p>1.Vulnerability Description</p>
<p>Multiple authenticated Cross-Site Scripting (XSS) vulnerabilities were identified within Concrete5 version 5.5.2.1. Also reported were some cookie security improvements. The first Concrete5 advisory can be found here [1].</p>
<p>2.Software Description</p>
<p>CMS made for Marketing but built for Geeks, concrete5 [0] is a content management system that is free and open source.</p>
<p>3. Vulnerability Information</p>
<p><a id="more"></a><a id="more-16847"></a></p>
<p>3.1 Cross-Site Scripting (XSS)</p>
<p>Page: index.php/tools/required/files/customize_search_columns<br />
Parameters: searchInstance<br />
Method: GET</p>
<p>Page: index.php/tools/required/files/save_search<br />
Parameters: ccm-submit-button, searchInstance<br />
Method: POST</p>
<p>Page: index.php/tools/required/files/search_results<br />
Parameters: numResults, searchInstance & searchType<br />
Method: GET</p>
<p>Page: index.php/tools/required/sitemap_search_selector.php<br />
Parameters: cID, sitemap_select_mode<br />
Method: GET</p>
<p>Page: index.php/tools/required/users/search_dialog<br />
Parameters: mode<br />
Method: GET</p>
<p>Page: index.php/tools/required/users/search_results<br />
Parameters: mode, numResults & searchType<br />
Method: GET</p>
<p>3.2 Cookie Security</p>
<p>Current cookie name/value: CONCRETE5=6amek9tk8549gisbhsqcpi0ku6;<br />
path=/concrete5.5.2.1/</p>
<p>The 'httpOnly' and 'secure' flags should be set as well as an expiry time/date.</p>
<p>4.Vulnerability Timeline</p>
<p>2012-07-24 – Reported to vendor<br />
2012-07-24 – Vendor acknowledged<br />
2012-08-25 – Vulnerability Disclosed</p>
<p>5.References</p>
<p>[0] http://www.concrete5.org/<br />
[1] http://www.ethicalhack3r.co.uk/security/concrete5/</p>
