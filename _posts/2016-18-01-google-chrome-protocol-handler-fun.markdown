---
layout: post
status: publish
published: false
title: Google Chrome Protocol Handler Fun
excerpt: "Certificate Pinning is an extra layer of security that is used by applications to ensure that the certificate provided by the remote server is the one which is expected.
\r\n\r\n
By including the remote server’s x509 certificate or public key within the application, it is possible to compare the locally stored certificate or key with the one provided by the remote server.
\r\n\r\n
If you have been unable to intercept (Man-in-the-Middle) the application’s HTTPS traffic, after taking the necessary steps, this is probably due to the application using Certificate Pinning."
---

You're probably all familiar of the custom protocol handlers browsers use for various things such as ```chrome://settings/``` and ```chrome://credits/```. I was using a Chrome app (extention) the other day that suggested I copy and pasted ```chrome://restart``` in to my browser address bar to restart Chrome. This got me thinking about the ```chrome``` protocol handler, what other ones are there and how they might they be able to be used for a bit of fun.

The first obvious bit of fun we could have is if someone clicked on a HTML link to ```chrome://restart``` and have their browser restart, losing all of their open tabs. This is so obvious that Chrome do not allow this to happen by default and you will see the following error in the browser console ```Not allowed to load local resource: chrome://restart/```.

So I thought about setting ```chrome://restart``` as the browser's startup page, the idea being that Chrome would just restart itself everytime the browser is opened. This kind of worked, but Chrome only restarted itself the once and then stopped, not much fun.






