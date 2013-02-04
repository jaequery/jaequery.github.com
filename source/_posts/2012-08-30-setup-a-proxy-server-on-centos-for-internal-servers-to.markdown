---
comments: true
date: 2012-08-30 18:19:00
layout: post
slug: setup-a-proxy-server-on-centos-for-internal-servers-to
title: setup a proxy server on Centos for internal servers to use
wordpress_id: 25
categories:
- Technology
---

### setting up a proxy server that does, DNS, http/https




# [setup bind on proxy server]




yum install bind -y




# create /etc/named.conf, replace 1.1.1.0 with your LAN servers ip range:




options {




        listen-on port 53 { 127.0.0.1; 1.1.1.0/24; };




        listen-on-v6 port 53 { ::1; };




        directory       "/var/named";




        dump-file       "/var/named/data/cache_dump.db";




        statistics-file "/var/named/data/named_stats.txt";




        memstatistics-file "/var/named/data/named_mem_stats.txt";




        allow-query     { localhost; 1.1.1.0/24; };




        allow-query-cache { localhost; 1.1.1.0/24; };




};




logging {




        channel default_debug {




                file "data/named.run";




                severity dynamic;




        };




};




view localhost_resolver {




        match-clients      { localhost; 1.1.1.0/24; };




        match-destinations { localhost; 1.1.1.0/24; };




        recursion yes;




        include "/etc/named.rfc1912.zones";




};




# restart bind




chkconfig named on




service named restart




# [setup squid on proxy server]




yum install squid -y




chkconfig squid on




# modify /etc/squid.conf




# uncomment these two lines and set the IPs you wish to grant access to




acl our_networks src 1.1.1.0/24




http_access allow our_networks




# restart squid




service squid start




# [now setup client servers to use proxy server]




# easiest way is to add this line to your /etc/bashrc




http_proxy="http://proxyserver:3128"  
ftp_proxy="http://proxyserver:3128"  




export http_proxy  
export ftp_proxy  




# re-login 




………..







that's it. now all your internal/private servers can access the internet.
