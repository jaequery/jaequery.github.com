---
comments: true
date: 2012-08-31 21:01:57
layout: post
slug: tcpdump-capture-packets-while-connected-on-ssh
title: tcpdump capture packets while connected on SSH
wordpress_id: 23
categories:
- Technology
---

tcpdump by default will listen and output everything, including your current SSH session, which means you'll get a lot of junk!




so do this to ignore all ssh connections to filter them out




tcpdump -i any -s 0 not port ssh
