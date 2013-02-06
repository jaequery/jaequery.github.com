---
layout: post
title: "A strong iptables ruleset for running websites"
date: 2013-02-05 22:55
comments: true
categories: security
---

Here is a simple quick rule to get you secure for most running websites. But it is extremely strict as it only allows HTTP (port 80) from the internet.

Save this into a file (e.g; ~/iptables.hardened)

	*filter
	:INPUT ACCEPT [0:0]
	:FORWARD DROP [0:0]
	:OUTPUT ACCEPT [0:0]
	-A INPUT -i lo -j ACCEPT
	-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
	-A INPUT -m state --state INVALID -j DROP
	-A INPUT -p icmp -m icmp --icmp-type any -j ACCEPT
	-A INPUT -p tcp --dport 80 -j ACCEPT
	-A INPUT -p tcp -s x.x.x.x/32 --dport 22 -j ACCEPT
	-A INPUT -p tcp -s x.x.x.x/32 --dport 3306 -j ACCEPT
	-A INPUT -p tcp --dport 0:1024 -m state --state NEW -m limit --limit 5/s -j LOG
	-A INPUT -j DROP
	COMMIT

Then test it by:
     iptables-restore < ~/iptables.hardened

Note) If you are paranoid and don't want to risk yourself from locking out of the machine, just make sure to add a cronjob to stop iptables every minute.
Something like:
`*/5 * * * * /etc/init.d/iptables stop`

Once you are satisfied, save it to your /etc/sysconfig/iptables to make it permanent.
