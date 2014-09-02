---
layout: post
status: publish
published: true
title: Introduction to the WordPress XML-RPC API
author:
  display_name: ethicalhack3r
  login: ethicalhack3r
  email: ryandewhurst@gmail.com
  url: ''
author_login: ethicalhack3r
author_email: ryandewhurst@gmail.com
excerpt: "WordPress 3.5 was recently released which now comes with the WordPress API
  \"always enabled\". Personally I think this adds unnecessary risk by increasing
  the attack surface. How many WordPress user's actually use the API? I would put
  my money on it being a very small fraction, either way I'm sure the WordPress Core
  Development team had good reason to enable the API by default. After spending 5
  minutes looking for where to turn the API off in WordPress 3.5 I gave up. Huh, I'll
  have another look sometime soon.\r\n\r\nI've had a play with the API in the past,
  however, I've always found it hard to get going as the information on how to interact
  with the API is a bit sparse. Having played with it for an hour or so this evening
  I thought I'd share some of the information on how to get started (as well as a
  self reminder ;).\r\n\r\nThe latest API calls can be found on WordPress's Codex
  <a href=\"http://codex.wordpress.org/XML-RPC_WordPress_API\" target=\"_blank\">here</a>.
  It doesn't list all available calls, to find these let's extract them from the 'wp-includes/class-wp-xmlrpc-server.php'
  file.\r\n\r\n"
wordpress_id: 16894
wordpress_url: http://www.ethicalhack3r.co.uk/?p=16894
date: '2012-12-11 19:27:10 +0000'
date_gmt: '2012-12-11 19:27:10 +0000'
---
<p>WordPress 3.5 was recently released which now comes with the WordPress API "always enabled". Personally I think this adds unnecessary risk by increasing the attack surface. How many WordPress user's actually use the API? I would put my money on it being a very small fraction, either way I'm sure the WordPress Core Development team had good reason to enable the API by default. After spending 5 minutes looking for where to turn the API off in WordPress 3.5 I gave up. Huh, I'll have another look sometime soon.</p>
<p>I've had a play with the API in the past, however, I've always found it hard to get going as the information on how to interact with the API is a bit sparse. Having played with it for an hour or so this evening I thought I'd share some of the information on how to get started (as well as a self reminder ;).</p>
<p>The latest API calls can be found on WordPress's Codex <a href="http://codex.wordpress.org/XML-RPC_WordPress_API" target="_blank">here</a>. It doesn't list all available calls, to find these let's extract them from the 'wp-includes/class-wp-xmlrpc-server.php' file.</p>
<p><a id="more"></a><a id="more-16894"></a></p>
<p>{% highlight text %}
wp.getUsersBlogs
wp.newPost
wp.editPost
wp.deletePost
wp.getPost
wp.getPosts
wp.newTerm
wp.editTerm
wp.deleteTerm
wp.getTerm
wp.getTerms
wp.getTaxonomy
wp.getTaxonomies
wp.getUser
wp.getUsers
wp.getProfile
wp.editProfile
wp.getPage
wp.getPages
wp.newPage
wp.deletePage
wp.editPage
wp.getPageList
wp.getAuthors
wp.getCategories
wp.getTags
wp.newCategory
wp.deleteCategory
wp.suggestCategories
wp.uploadFile
wp.getCommentCount
wp.getPostStatusList
wp.getPageStatusList
wp.getPageTemplates
wp.getOptions
wp.setOptions
wp.getComment
wp.getComments
wp.deleteComment
wp.editComment
wp.newComment
wp.getCommentStatusList
wp.getMediaItem
wp.getMediaLibrary
wp.getPostFormats
wp.getPostType
wp.getPostTypes
wp.getRevisions
wp.restoreRevision
blogger.getUsersBlogs
blogger.getUserInfo
blogger.getPost
blogger.getRecentPosts
blogger.newPost
blogger.editPost
blogger.deletePost
metaWeblog.newPost
metaWeblog.editPost
metaWeblog.getPost
metaWeblog.getRecentPosts
metaWeblog.getCategories
metaWeblog.newMediaObject
metaWeblog.deletePost
metaWeblog.getUsersBlogs
mt.getCategoryList
mt.getRecentPostTitles
mt.getPostCategories
mt.setPostCategories
mt.supportedMethods
mt.supportedTextFilters
mt.getTrackbackPings
mt.publishPost
pingback.ping
pingback.extensions.getPingbacks
demo.sayHello
demo.addTwoNumbers
system.getCapabilities # Incutio XML-RPC Library call - added 17.06.2013
system.listMethods # Incutio XML-RPC Library call - added 17.06.2013
system.multicall # Incutio XML-RPC Library call - added 17.06.2013
{% endhighlight %}</p>
<p>As you can see from the above list there are a whole host of different things you can do via the API. Creating blog posts, requesting information about the blog's settings and even uploading media! Most of these require authentication and use the same authorisation mechanisms as the GUI. The three I found not to require authentication were pingback.ping, demo.sayHello and demo.addTwoNumbers (there are probably others).  </p>
<p>A typical API request body looks like the following:</p>
<p>{% highlight xml %}
<?xml version="1.0" encoding="iso-8859-1"?>
<methodCall>
  <methodName>demo.sayHello</methodName>
  <params>
   <param></param>
  </params>
</methodCall>
{% endhighlight %}</p>
<p>The xmlrpc.php file needs the valid XML sent to it as a POST request. The easiest way to do this in Linux is to use <a href="http://curl.haxx.se/" target="_blank">cURL</a>. The following command will send the XML contained within the 'demo.sayHello.txt' file as a POST request to the remote WordPress API:</p>
<p>{% highlight text %}
curl --data @demo.sayHello.txt http://www.example.com/xmlrpc.php
{% endhighlight %}</p>
<p>Which should return a response that looks like this:</p>
<p>{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<methodResponse>
  <params>
    <param>
      <value>
      <string>Hello!</string>
      </value>
    </param>
  </params>
</methodResponse>
{% endhighlight %}</p>
<p>Simple, eh?</p>
<p>Here are a few other WordPress API calls:</p>
<p>demo.addTwoNumbers<br />
{% highlight xml %}
<?xml version="1.0" encoding="iso-8859-1"?>
<methodCall>
  <methodName>demo.addTwoNumbers</methodName>
  <params>
   <param><value>2.0E+72</value></param>
   <param><value>2.0E+72</value></param>
  </params>
</methodCall>
{% endhighlight %}</p>
<p>pingback.ping<br />
{% highlight xml %}
<?xml version="1.0" encoding="iso-8859-1"?>
<methodCall>
  <methodName>pingback.ping</methodName>
  <params>
   <param><value><string>http://www.example.com/index.php?p=71</string></value></param>
   <param><value><string>http://www.example2.com/index.php?p=72</string></value></param>
  </params>
</methodCall>
{% endhighlight %}</p>
<p>wp.getPost<br />
{% highlight xml %}
<?xml version="1.0" encoding="iso-8859-1"?>
<methodCall>
  <methodName>wp.getPost</methodName>
  <params>
   <param><value>1</value></param>
   <param><value>username</value></param>
   <param><value>password</value></param>
   <param><value>72</value></param>
  </params>
</methodCall>
{% endhighlight %}</p>
<p>wp.getUsers<br />
{% highlight xml %}
<?xml version="1.0" encoding="iso-8859-1"?>
<methodCall>
  <methodName>wp.getUsers</methodName>
  <params>
   <param><value>1</value></param>
   <param><value>username</value></param>
   <param><value>password</value></param>
  </params>
</methodCall>
{% endhighlight %}</p>
<p>There you are, something to get you started playing around with the WordPress API. If you find out how to turn the damn thing off let me know! :)</p>
<p>EDIT ---</p>
<p>After reading this post long time WPScan contributor (<a href="https://twitter.com/_FireFart_" target="_blank">@_FireFart_</a>) wrote a port scanner using a remote WordPress API! - <a href="https://github.com/FireFart/WordpressPingbackPortScanner" target="_blank">https://github.com/FireFart/WordpressPingbackPortScanner</a></p>
<p>EDIT: 06.01.2013 00:55</p>
<p>An even more serious issue has been identified with WordPress's XMLRPC API. ONsec research lab have found that the pingback API is vulnerable to 'SSRF' (Server Side Request Forgery): <a href="http://lab.onsec.ru/2013/01/wordpress-xmlrpc-pingback-additional.html" target="_blank">http://lab.onsec.ru/2013/01/wordpress-xmlrpc-pingback-additional.html</a></p>
