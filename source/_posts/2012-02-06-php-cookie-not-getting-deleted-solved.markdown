---
comments: true
date: 2012-02-06 05:39:59
layout: post
slug: php-cookie-not-getting-deleted-solved
title: PHP Cookie not getting deleted [Solved]
wordpress_id: 45
categories:
- Technology
---

This one was a bit of a hair puller but finally found out why I could not reset a cookie.  
All the stuffs online tells you to use:




setcookie('yourcookie', ", time() - 86400);




Well apparently this fails for most web apps.




What will work however is this:




setcookie('yourcookie', ", time() - 86400, '/');




The reason being is that I am setting my cookie initially from /auth/login. So this means my cookie will only live inside /auth path. But by setting '/' to reset it, it tells it to reset for all the sub folders in the site.
