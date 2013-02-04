---
comments: true
date: 2011-10-14 04:18:00
layout: post
slug: zend-view-renderer-ugh
title: Zend View Renderer ... ugh
wordpress_id: 60
categories:
- Technology
---

I just have to say, Zend View Renderer is like the magic of all magic methods. 




It's such a PITA to understand what the heck it does.




I just want to simply override the view script to another view script. I know there is one for switching view script folder path, but what about the script file?




ViewRenderer == FAIL




And no, render() doesn't do jack for me even though it attempts to look for it. I don't know, it's just too magical.




***update***




So I had to use $this->_helper->viewRenderer('form'); instead of $tihs->view->render('form');




I hate tricky naming conventions like this.
