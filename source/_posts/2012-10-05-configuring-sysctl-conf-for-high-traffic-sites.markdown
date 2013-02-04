---
comments: true
date: 2012-10-05 19:07:00
layout: post
slug: configuring-sysctl-conf-for-high-traffic-sites
title: configuring sysctl.conf for high traffic sites (150k+/min)
wordpress_id: 12
categories:
- Technology
---

edit /etc/sysctl.conf

     #net.ipv4.netfilter.ip_conntrack_max = 300000 # for centos 5  
     net.netfilter.nf_conntrack_max = 300000 # for centos 6
     net.ipv4.tcp_max_syn_backlog = 10240
     net.core.netdev_max_backlog = 4000
     kernel.panic = 10
     net.ipv4.tcp_slow_start_after_idle=0
     net.ipv4.tcp_tw_reuse = 1
     net.ipv4.ip_local_port_range = 1024 65023
     net.ipv4.tcp_max_syn_backlog = 10240
     net.ipv4.tcp_max_tw_buckets = 400000
     net.ipv4.tcp_max_orphans = 60000
     net.ipv4.tcp_synack_retries = 3
     net.core.somaxconn = 10000

##### also look into considering increasing ulimit
ulimit -n 30000
ulimit -u 50000










now save then type sysctl -p to reload changes
