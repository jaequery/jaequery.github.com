---
comments: true
date: 2012-08-30 21:49:00
layout: post
slug: allow-only-certain-sites-with-squid
title: allow only certain sites with squid
wordpress_id: 24
categories:
- Technology
---

first create /etc/squid/allowed-sites




add the list of domains you wish to allow, for instance:




.yahoo.com  
.softlayer.com




now edit /etc/squid/squid.conf and modify as follows (remember to place these just before "http_access deny all":




acl allowed_network src 1.1.1.0/24  
acl allowed_sites dstdomain "/etc/squid/allowed-sites"  
http_access allow allowed_network allowed_sites  
http_access deny allowed_network !allowed_sites




now save and reload squid
