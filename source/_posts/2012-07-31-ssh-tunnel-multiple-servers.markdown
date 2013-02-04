---
comments: true
date: 2012-07-31 02:44:23
layout: post
slug: ssh-tunnel-multiple-servers
title: ssh tunnel multiple servers
wordpress_id: 33
categories:
- Technology
---

i have a bastion server i need to connect to access other servers.  
this pose some problems when i require a need to access a web-gui within the internal servers, such as ASL admin gui or other control panels, etc …




here is a simple way to forward a port from my target server to my localhost specified port:




ssh -t -t -L8081:localhost:10000 mvriel@a.server.example.com 'ssh -L10000:localhost:80 mvriel@b.server.example.com' 




now when i point my browser to http://localhost:8081, i am viewing the port 80 from server b.
