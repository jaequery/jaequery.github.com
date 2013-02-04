---
comments: true
date: 2012-08-16 15:41:06
layout: post
slug: warning-rsyslogd-is-running-in-compatibility-mode
title: 'WARNING: rsyslogd is running in compatibility mode. Automatically generated
  config directives may interfer with your rsyslog.conf settings. We suggest upgrading
  your config and adding -c3 as the first rsyslogd option.'
wordpress_id: 28
categories:
- Technology
---

If you are getting the error:




WARNING: rsyslogd is running in compatibility mode. Automatically generated config directives may interfer with your rsyslog.conf settings. We suggest upgrading your config and adding -c3 as the first rsyslogd option.




when starting up your rsyslog, do this:




edit /etc/sysconfig/syslog




and add -c5 in your options like this:




SYSLOGD_OPTIONS="-c5 -m 0"
