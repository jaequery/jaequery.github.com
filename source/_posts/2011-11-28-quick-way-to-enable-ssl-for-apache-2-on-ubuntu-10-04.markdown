---
comments: true
date: 2011-11-28 17:09:48
layout: post
slug: quick-way-to-enable-ssl-for-apache-2-on-ubuntu-10-04
title: Quick way to enable SSL for Apache 2 on ubuntu 10.04+
wordpress_id: 50
categories:
- Technology
---

**Here is a real simple and a quick way of enabling SSL for your apache server on ubuntu 10.04+**




sudo apt-get install libapache2-mod-auth-mysql  
sudo a2enmod auth_mysql  
sudo /etc/init.d/apache2 restart  
sudo a2dismod auth_mysql  
sudo a2enmod ssl  
sudo a2ensite default-ssl  
sudo /etc/init.d/apache2 restart




#optional: nano ports (disable 80)
