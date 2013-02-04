---
comments: true
date: 2012-08-15 18:48:00
layout: post
slug: creating-a-vnc-tunnel-using-freenx
title: creating a VNC tunnel using freeNX
wordpress_id: 30
categories:
- Technology
---

I found a pretty cool VNC alternative, which I think surpasses all other solutions out there.




Installation is very easy too!




on centos:




yum groupinstall "X Window System" "KDE (K Desktop Environment)"  
yum install nx freenx  
nxserver --start




Now nx server is installed and should be awaiting connections!




Download the NX Client for Windows/Mac (for macs, i think you have to use something else)




Now on password, click "choose key". Copy and paste this on to that textarea:




cat /var/lib/nxserver/home/.ssh/client.id_dsa.key




Once done, put in your server hostname info, etc.. and you should be able to connect.
