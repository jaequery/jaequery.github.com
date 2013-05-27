---
comments: true
date: 2012-10-06 18:34:57
layout: post
slug: see-whats-using-up-your-server
title: see whats using up your server
wordpress_id: 10
categories:
- Technology
---

see which connections are connected to you sorted by:
```
netstat -pant | grep :80 | awk '{ print $5}' | cut -d: -f1 | sort | uniq -c | sort -n
```

see which process are eating up your server:
```
ps -eo pmem,pcpu,pid,user,rss,vsize,args | { head -1 ; sort -k 1 -r -n ; } | head -10
```
