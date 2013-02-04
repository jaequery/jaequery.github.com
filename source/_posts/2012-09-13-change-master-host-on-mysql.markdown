---
comments: true
date: 2012-09-13 20:24:31
layout: post
slug: change-master-host-on-mysql
title: change master host on mysql
wordpress_id: 20
categories:
- Technology
---

CHANGE MASTER TO MASTER_HOST='db0.local', MASTER_USER='xxx', MASTER_PASSWORD='xxx', MASTER_LOG_FILE='mysql-bin.000003', MASTER_LOG_POS=628;
