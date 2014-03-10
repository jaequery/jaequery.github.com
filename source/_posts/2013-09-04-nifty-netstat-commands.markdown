---
layout: post
title: "nifty netstat commands"
date: 2013-09-04 23:38
comments: true
categories:
---

Try the following commands to determine if you have a lot of connections coming from one address or if you are under a distributed attack.

```
netstat -nt | cut -c 40- | cut -d: -f1 | sort | uniq -c | sort -n
netstat -nt | cut -d: -f2 | sort | uniq -c | sort -n
```

If you have high numbers from a few IP addresses it will be easier to limit the connections. You can then add deny rules or rate-limit rules to iptables to limit access from these addresses.

If you are under attack you may want to get your ISP involved as they can limit connections before they reach you.