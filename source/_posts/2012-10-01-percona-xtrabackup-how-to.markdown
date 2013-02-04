---
comments: true
date: 2012-10-01 21:32:05
layout: post
slug: percona-xtrabackup-how-to
title: percona xtrabackup how to
wordpress_id: 15
categories:
- Technology
---

to create a backup:




innobackupex --user=root --password=xxx .




this should create a folder in timestamp, i.e; 2012-09-01_11-11-11




innobackupex --apply-log 2012-09-01_11-11-11




this keeps backup in sync, so make sure to apply this, always.
