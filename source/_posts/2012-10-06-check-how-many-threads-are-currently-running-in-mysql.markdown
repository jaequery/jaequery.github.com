---
comments: true
date: 2012-10-06 07:05:36
layout: post
slug: check-how-many-threads-are-currently-running-in-mysql
title: check how many threads are currently running in mysql
wordpress_id: 11
categories:
- Technology
---

mysqladmin ext -i1 | grep Threads_running
