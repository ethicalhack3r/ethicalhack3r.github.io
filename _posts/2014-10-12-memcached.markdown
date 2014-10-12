---
layout: post
status: publish
published: true
title: Memcached
excerpt: "Last week I came across a service on the Internet running on TCP port 11211, Memcached's default port. I had heard of Memcached before but I probably only knew it was some kind of database system, that was the extent of my familiarity with it.
\r\n\r\n
I quickly learnt that connecting to Memcached does not require authentication. Authentication can be implmented but even then Memcached's own documentation says it should not be fully trusted."
---

##What is Memcached?

> Free & open source, high-performance, distributed memory object caching system, generic in nature, but intended for use in speeding up dynamic web applications by alleviating database load.

> Memcached is an in-memory key-value store for small chunks of arbitrary data (strings, objects) from results of database calls, API calls, or page rendering.

> Memcached is simple yet powerful. Its simple design promotes quick deployment, ease of development, and solves many problems facing large data caches. Its API is available for most popular languages.

> At heart it is a simple Key/Value store.

http://memcached.org/

## Background

Last week I came across a service on the Internet running on TCP port 11211, Memcached's default port. I had heard of Memcached before but I probably only knew it was some kind of database system, that was the extent of my familiarity with it.

I quickly learnt that connecting to Memcached does not require authentication. Authentication can be implmented but even then Memcached's own documentation says it should not be fully trusted. 

> Using SASL authentication here helps, but should not be totally trusted.

[https://code.google.com/p/memcached/wiki/NewConfiguringServer#Networking](https://code.google.com/p/memcached/wiki/NewConfiguringServer#Networking)

## Give me the data!

I have a database server which I can connect to (you can use Telnet) without any authentication, great! Give me the data!

Now here lies the problem, Memcached is a Key/Value store. To get any data from the key's values I need to know the key name first and the key name can be any string. I was also told that there was no way to get the key names from a Memcached server.

### Stats

I found a Ruby Gem called [dalli](https://github.com/mperham/dalli) which is a Memchaced client and started to play around with the API, one interesting Memchaced call is the ```stats``` one.

Here is some example output when the ```stats``` command is executed on a remote Memcached server:

```
[*] pid: 1020
[*] uptime: 14903707
[*] time: 1413105644
[*] version: 1.4.4
[*] pointer_size: 64
[*] rusage_user: 286.130501
[*] rusage_system: 319.259465
[*] curr_connections: 10
[*] total_connections: 46
[*] connection_structures: 13
[*] cmd_get: 38617
[*] cmd_set: 38630
[*] cmd_flush: 0
[*] get_hits: 1
[*] get_misses: 38616
[*] delete_misses: 0
[*] delete_hits: 0
[*] incr_misses: 0
[*] incr_hits: 0
[*] decr_misses: 0
[*] decr_hits: 0
[*] cas_misses: 0
[*] cas_hits: 0
[*] cas_badval: 0
[*] auth_cmds: 0
[*] auth_errors: 0
[*] bytes_read: 30650122
[*] bytes_written: 26375254
[*] limit_maxbytes: 67108864
[*] accepting_conns: 1
[*] listen_disabled_num: 0
[*] threads: 4
[*] conn_yields: 0
[*] bytes: 600555
[*] curr_items: 1541
[*] total_items: 38617
[*] evictions: 0
```

I've seen this data fluctuate in terms of content, sometimes you get more stat information and others less. There's some interesting data here but nothing to help get any key names.

### Cachedump

After some googleing I came across a [blog post](http://www.darkcoding.net/software/memcached-list-all-keys/) which outlines a method to extract some of the key names.

The method to extract the key names outlined in the blog post uses the ```stats cachedump``` command and passing a 'slab id' and a keys limit.

The full command would look something like this:

```
stats cachedump 3 100
```

Where ```3``` is the slab id and ```100``` is the maximum number of keys to return. Slabs are a way Memcached handles its internal memory rather than storing the key/values individually.

### Slabs

So to return the key names we first need the slab ids. Luckily for us some slab ids are retrned when issueing the ```stats items``` command.

The output of this command looks like this (borrowed from the previous [blog post](http://www.darkcoding.net/software/memcached-list-all-keys/)):

```
STAT items:3:number 1
STAT items:3:age 498
STAT items:22:number 1
STAT items:22:age 498
END
```

The number after ```items:``` is a slab id, we can easily extract the slab ids with the following regex ```^items:(\d*):```.

Now we have some slab ids we can use ```cachedump``` do get the key name and once we have the key name we can extract the key value. Unfortunatly the [dalli](https://github.com/mperham/dalli) gem doesn't have an API call for ```cachedump```, however, this can be done easily over Telnet or the like.

### Values (the meat!)

To get the key value I just used the [dalli](https://github.com/mperham/dalli) gem's ```get(key_name)``` API call. I did come across some interesting data but most of the time no data was returned. I guess it depends on how frequently the Memcached server is used.

## The Script

To automate the data extraction from a Memcached server I wrote the following script - [https://github.com/ethicalhack3r/my-scripts/blob/master/memcached_client.rb](https://github.com/ethicalhack3r/my-scripts/blob/master/memcached_client.rb) - which uses a mixture of the [dalli](https://github.com/mperham/dalli) Gem and Telnet to extract the data.

Using [massscan](https://github.com/robertdavidgraham/masscan) I scanned some net blocks for TCP port 11211 to see how popular Memcached was and how how frequently it was listening over the Internet despite Memcached's own documentation advising against this.

> So you must not expose memcached directly to the internet, or otherwise any untrusted users.

[https://code.google.com/p/memcached/wiki/NewConfiguringServer#Networking](https://code.google.com/p/memcached/wiki/NewConfiguringServer#Networking)

Memcached were nice enough to tell us who the biggest users of the software are:

- LiveJournal
- Wikipedia
- Flickr
- Bebo
- Twitter
- Typepad
- Yellowbot
- Youtube
- WordPress.com
- Craigslist
- Mixi

[http://memcached.org/](http://memcached.org/)

## Conclusion

After all this I came across a [blog post](http://www.sensepost.com/blog/4873.html) by SensePost who did all of this back in 2010. They even wrote a tool called ```go-derper``` which I havn't had the chance to try yet. My Google Fu must have been weak when I first came across the Memcached server on the Internet. Nevertheless I learned a little about Memcached and will be prepared next time I come across it. Hopefully you learned a little about it too.

There was no Metasploit module to extract data from a Memcached server, maybe this is something I can do in future if I get the time or someone else can do if they're interested. Metaploit did have a [DoS exploit](https://github.com/rapid7/metasploit-framework/blob/master/modules/auxiliary/dos/misc/memcached.rb) (CVE-2011-4971) for Memcached though.
