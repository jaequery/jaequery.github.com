---
comments: true
date: 2011-11-22 17:57:00
layout: post
slug: take-and-capture-screenshots-of-any-webpage-using-php
title: Take and capture screenshots of any webpage using PHP & Ubuntu
wordpress_id: 51
categories:
- Technology
---

### An Open Source screenshot capture script using PHP and Ubuntu




For those looking to take screenshots of webpages, I just released a couple scripts to Github that can help you out.




This works on using CutyCapt (qt webkit) and the Xvfb (headless X11).




**To get started:**




  1. Install dependencies


  2. [[https://github.com/jaequery/cutycapt-installer-script-on-ubuntu](https://github.com/jaequery/cutycapt-installer-script-on-ubuntu)](https://github.com/jaequery/cutycapt-installer-script-on-ubuntu)


  3. Get the php script


  4. [[https://github.com/jaequery/php-site-screenshot](https://github.com/jaequery/php-site-screenshot)](https://github.com/jaequery/php-site-screenshot)



**Next, you need to configure the script capture.php:**




// lib path  
$xvfb_path = '/usr/bin';  
$cutycapt_path = "/home/user/scripts/cutycapt/CutyCapt";




// capture settings  
$screen = '1280x1024x24';  
$output_path = '/home/user/www/images/capture.png';  
$url = $_GET['url']; // set it however you want  
//$url = 'http://www.yahoo.com'; // set it manually




**Change them accordingly and you are done**




To get you started, here is a simple usage: http://localhost/capture.php?url=http://www.google.com




Hope this is useful to someone.
