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
<p>[code]<br />
wp.getUsersBlogs<br />
wp.newPost<br />
wp.editPost<br />
wp.deletePost<br />
wp.getPost<br />
wp.getPosts<br />
wp.newTerm<br />
wp.editTerm<br />
wp.deleteTerm<br />
wp.getTerm<br />
wp.getTerms<br />
wp.getTaxonomy<br />
wp.getTaxonomies<br />
wp.getUser<br />
wp.getUsers<br />
wp.getProfile<br />
wp.editProfile<br />
wp.getPage<br />
wp.getPages<br />
wp.newPage<br />
wp.deletePage<br />
wp.editPage<br />
wp.getPageList<br />
wp.getAuthors<br />
wp.getCategories<br />
wp.getTags<br />
wp.newCategory<br />
wp.deleteCategory<br />
wp.suggestCategories<br />
wp.uploadFile<br />
wp.getCommentCount<br />
wp.getPostStatusList<br />
wp.getPageStatusList<br />
wp.getPageTemplates<br />
wp.getOptions<br />
wp.setOptions<br />
wp.getComment<br />
wp.getComments<br />
wp.deleteComment<br />
wp.editComment<br />
wp.newComment<br />
wp.getCommentStatusList<br />
wp.getMediaItem<br />
wp.getMediaLibrary<br />
wp.getPostFormats<br />
wp.getPostType<br />
wp.getPostTypes<br />
wp.getRevisions<br />
wp.restoreRevision<br />
blogger.getUsersBlogs<br />
blogger.getUserInfo<br />
blogger.getPost<br />
blogger.getRecentPosts<br />
blogger.newPost<br />
blogger.editPost<br />
blogger.deletePost<br />
metaWeblog.newPost<br />
metaWeblog.editPost<br />
metaWeblog.getPost<br />
metaWeblog.getRecentPosts<br />
metaWeblog.getCategories<br />
metaWeblog.newMediaObject<br />
metaWeblog.deletePost<br />
metaWeblog.getUsersBlogs<br />
mt.getCategoryList<br />
mt.getRecentPostTitles<br />
mt.getPostCategories<br />
mt.setPostCategories<br />
mt.supportedMethods<br />
mt.supportedTextFilters<br />
mt.getTrackbackPings<br />
mt.publishPost<br />
pingback.ping<br />
pingback.extensions.getPingbacks<br />
demo.sayHello<br />
demo.addTwoNumbers<br />
system.getCapabilities # Incutio XML-RPC Library call - added 17.06.2013<br />
system.listMethods # Incutio XML-RPC Library call - added 17.06.2013<br />
system.multicall # Incutio XML-RPC Library call - added 17.06.2013<br />
[/code]</p>
<p>As you can see from the above list there are a whole host of different things you can do via the API. Creating blog posts, requesting information about the blog's settings and even uploading media! Most of these require authentication and use the same authorisation mechanisms as the GUI. The three I found not to require authentication were pingback.ping, demo.sayHello and demo.addTwoNumbers (there are probably others).  </p>
<p>A typical API request body looks like the following:</p>
<p>[code]<br />
&lt;?xml version=&quot;1.0&quot; encoding=&quot;iso-8859-1&quot;?&gt;<br />
&lt;methodCall&gt;<br />
  &lt;methodName&gt;demo.sayHello&lt;/methodName&gt;<br />
  &lt;params&gt;<br />
   &lt;param&gt;&lt;/param&gt;<br />
  &lt;/params&gt;<br />
&lt;/methodCall&gt;<br />
[/code]</p>
<p>The xmlrpc.php file needs the valid XML sent to it as a POST request. The easiest way to do this in Linux is to use <a href="http://curl.haxx.se/" target="_blank">cURL</a>. The following command will send the XML contained within the 'demo.sayHello.txt' file as a POST request to the remote WordPress API:</p>
<p>[code]<br />
curl --data @demo.sayHello.txt http://www.example.com/xmlrpc.php<br />
[/code]</p>
<p>Which should return a response that looks like this:</p>
<p>[code]<br />
&lt;?xml version=&quot;1.0&quot; encoding=&quot;UTF-8&quot;?&gt;<br />
&lt;methodResponse&gt;<br />
  &lt;params&gt;<br />
    &lt;param&gt;<br />
      &lt;value&gt;<br />
      &lt;string&gt;Hello!&lt;/string&gt;<br />
      &lt;/value&gt;<br />
    &lt;/param&gt;<br />
  &lt;/params&gt;<br />
&lt;/methodResponse&gt;<br />
[/code]</p>
<p>Simple, eh?</p>
<p>Here are a few other WordPress API calls:</p>
<p>demo.addTwoNumbers<br />
[code]<br />
&lt;?xml version=&quot;1.0&quot; encoding=&quot;iso-8859-1&quot;?&gt;<br />
&lt;methodCall&gt;<br />
  &lt;methodName&gt;demo.addTwoNumbers&lt;/methodName&gt;<br />
  &lt;params&gt;<br />
   &lt;param&gt;&lt;value&gt;2.0E+72&lt;/value&gt;&lt;/param&gt;<br />
   &lt;param&gt;&lt;value&gt;2.0E+72&lt;/value&gt;&lt;/param&gt;<br />
  &lt;/params&gt;<br />
&lt;/methodCall&gt;<br />
[/code]</p>
<p>pingback.ping<br />
[code]<br />
&lt;?xml version=&quot;1.0&quot; encoding=&quot;iso-8859-1&quot;?&gt;<br />
&lt;methodCall&gt;<br />
  &lt;methodName&gt;pingback.ping&lt;/methodName&gt;<br />
  &lt;params&gt;<br />
   &lt;param&gt;&lt;value&gt;&lt;string&gt;http://www.example.com/index.php?p=71&lt;/string&gt;&lt;/value&gt;&lt;/param&gt;<br />
   &lt;param&gt;&lt;value&gt;&lt;string&gt;http://www.example2.com/index.php?p=72&lt;/string&gt;&lt;/value&gt;&lt;/param&gt;<br />
  &lt;/params&gt;<br />
&lt;/methodCall&gt;<br />
[/code]</p>
<p>wp.getPost<br />
[code]<br />
&lt;?xml version=&quot;1.0&quot; encoding=&quot;iso-8859-1&quot;?&gt;<br />
&lt;methodCall&gt;<br />
  &lt;methodName&gt;wp.getPost&lt;/methodName&gt;<br />
  &lt;params&gt;<br />
   &lt;param&gt;&lt;value&gt;1&lt;/value&gt;&lt;/param&gt;<br />
   &lt;param&gt;&lt;value&gt;username&lt;/value&gt;&lt;/param&gt;<br />
   &lt;param&gt;&lt;value&gt;password&lt;/value&gt;&lt;/param&gt;<br />
   &lt;param&gt;&lt;value&gt;72&lt;/value&gt;&lt;/param&gt;<br />
  &lt;/params&gt;<br />
&lt;/methodCall&gt;<br />
[/code]</p>
<p>wp.getUsers<br />
[code]<br />
&lt;?xml version=&quot;1.0&quot; encoding=&quot;iso-8859-1&quot;?&gt;<br />
&lt;methodCall&gt;<br />
  &lt;methodName&gt;wp.getUsers&lt;/methodName&gt;<br />
  &lt;params&gt;<br />
   &lt;param&gt;&lt;value&gt;1&lt;/value&gt;&lt;/param&gt;<br />
   &lt;param&gt;&lt;value&gt;username&lt;/value&gt;&lt;/param&gt;<br />
   &lt;param&gt;&lt;value&gt;password&lt;/value&gt;&lt;/param&gt;<br />
  &lt;/params&gt;<br />
&lt;/methodCall&gt;<br />
[/code]</p>
<p>There you are, something to get you started playing around with the WordPress API. If you find out how to turn the damn thing off let me know! :)</p>
<p>EDIT ---</p>
<p>After reading this post long time WPScan contributor (<a href="https://twitter.com/_FireFart_" target="_blank">@_FireFart_</a>) wrote a port scanner using a remote WordPress API! - <a href="https://github.com/FireFart/WordpressPingbackPortScanner" target="_blank">https://github.com/FireFart/WordpressPingbackPortScanner</a></p>
<p>EDIT: 06.01.2013 00:55</p>
<p>An even more serious issue has been identified with WordPress's XMLRPC API. ONsec research lab have found that the pingback API is vulnerable to 'SSRF' (Server Side Request Forgery): <a href="http://lab.onsec.ru/2013/01/wordpress-xmlrpc-pingback-additional.html" target="_blank">http://lab.onsec.ru/2013/01/wordpress-xmlrpc-pingback-additional.html</a></p>
