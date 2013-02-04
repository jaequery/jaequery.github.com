---
comments: true
date: 2012-10-08 23:00:24
layout: post
slug: disable-apache-get-requests-logging
title: disable apache GET requests logging
wordpress_id: 9
categories:
- Technology
---

If you are working for PCI compliance, you may have run into situations as to where you need to disable all GET request logging.




This is due to the fact that some merchants might accidentally submit their card processing over GET, in which, the server will be logging all card numbers and other valuable information in clear text.




So to do that:




SetEnvIf Request_Method "GET" dontlog  
CustomLog "/var/log/httpd/site.com.ssl.request.log" combined env=!dontlog 
