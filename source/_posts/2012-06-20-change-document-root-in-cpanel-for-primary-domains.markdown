---
comments: true
date: 2012-06-20 22:51:23
layout: post
slug: change-document-root-in-cpanel-for-primary-domains
title: Change document root in cpanel for primary domains
wordpress_id: 38
categories:
- Technology
---

So I needed to change document root of one of my accounts in cpanel.




I know I can do this for add-on and subdomains but I couldn't find out how for account's primary domain.




So here's what I found:  
 




Changing Primary domains




For changing the main/primary domain, you will need to have root SSH access and be able to locate and edit the following file (replacing your user & domain info):




/var/cpanel/userdata/USERNAME/DOMAIN.COM




1. Once you have opened the file, look for the following line:




documentroot: /home/USERNAME/public_html




2. Modify the location according to your needs. Save it and exit.




3. Rebuild the Apache conf and restart Apache:







/scripts/rebuildhttpd.conf  
service httpd restart







The change will be immediate. Simply clear your browser cache and force refresh the page!
