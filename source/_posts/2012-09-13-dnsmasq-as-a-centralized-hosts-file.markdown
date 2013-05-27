---
comments: true
date: 2012-09-13 23:24:49
layout: post
slug: dnsmasq-as-a-centralized-hosts-file
title: dnsmasq as a centralized hosts file
wordpress_id: 19
categories:
- Technology
---

if you are like me and like things where you can get setup in a quick pinch, you'll like dnsmasq.
have you ever had a time where you had multiple servers and have wondered why we can't just easily have a central hosts file so they are all synchronized?
well look no further. dnsmasq, is that, and more.
install dnsmasq on centos 5.8 is as easy as:
```
yum install dnsmasq -y
```
that's it, you just now need to start it up: service dnsmasq start, and point your other server's /etc/resolv.conf to your dnsmasq server.

note) if you are on openvz, make sure you set user=root in /etc/dnsmasq.conf, otherwise it won't let you start the service.
