---
comments: true
date: 2012-08-16 15:39:38
layout: post
slug: dev-xvc0-no-such-file-or-directory
title: '/dev/xvc0: No such file or directory'
wordpress_id: 29
categories:
- Technology
---

So I been getting a lot of these errors lately.




It's due to some legacy XEN images. Here's how to get rid of it:




edit /etc/inittab




find the line, co:2345:respawn:/sbin/agetty xvc0 9600 vt100-nav




and comment it out, like so:




#co:2345:respawn:/sbin/agetty xvc0 9600 vt100-nav
