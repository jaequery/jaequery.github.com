---
comments: true
date: 2012-08-28 04:51:00
layout: post
slug: log-all-root-commands
title: log all root commands
wordpress_id: 27
categories:
- Technology
---

PROMPT_COMMAND='history -a >(tee -a ~/.bash_history | logger -t "$USER[$$] $SSH_CONNECTION")'




add this to /root/.bashrc and it will log all to syslog/rsyslog messages
