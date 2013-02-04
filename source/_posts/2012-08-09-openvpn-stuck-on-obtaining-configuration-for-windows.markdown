---
comments: true
date: 2012-08-09 16:31:35
layout: post
slug: openvpn-stuck-on-obtaining-configuration-for-windows
title: openvpn stuck on obtaining configuration for windows
wordpress_id: 31
categories:
- Technology
---

So i been using openvpn to connect to our internal servers.  
I noticed that some of my other co-workers had issue connecting to the VPN, they would get stuck on the screen saying:




"Obtaining configuration"




This was odd to me and I couldn't reproduce this so I thought something was wrong with their PC.




But just today, I too had this same behaviour and I was locked out. I decided to wonder if this was a VPN client issue and I tested on my Mac via TunnelBlick, and it was able to connect fine.




So I knew the problem was with the openVPN client software and decided to look for an alternative, I wish there was a TunnelBlick for Windows but Mac only.




I stumbled across Sparklab's Viscosity VPN client. I installed via free trial and I was able to connect!




[[http://www.thesparklabs.com/viscosity/](http://www.thesparklabs.com/viscosity/)](http://www.thesparklabs.com/viscosity/)




I hate to pay for it but it seems at the moment, I don't have a choice. It's only $9 lifetime, fairly cheap.




Anyhow, problem solved.
