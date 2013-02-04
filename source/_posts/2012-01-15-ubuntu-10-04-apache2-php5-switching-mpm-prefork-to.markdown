---
comments: true
date: 2012-01-15 01:08:00
layout: post
slug: ubuntu-10-04-apache2-php5-switching-mpm-prefork-to
title: ubuntu 10.04 apache2 + php5 - switching mpm-prefork to mpm-worker how to guide
wordpress_id: 46
categories:
- Technology
---

I am running an online service that gets about 500k hits/day. It's a new service I started up beginning of december last year but growing at an incredible rate so I never had time to properly lay out a scalable infrastructure. Up until now, I was running it on a single dedicated server but noticed it was starting to take a toll on the server and didn't want to affect the other sites on the server (load avg 1.5+) so I decided to move it to Rackspace cloud.  
  
So I set up the instances:  
- 1 haproxy load balancer (256 mb)  
- 1 memcache (256 mb)  
- 3 apache (1 gig)  
- 1 nginx (1 gig)  
- 1 mysql master (1 gig)  
- 1 mysql slave (1 gig)




I'd have imagine this would be enough to handle this much traffic but my app servers kept swapping time to time. There was no way I was going to spin up even more apache servers as I know this will cost me more than double what I used to pay for the dedicated server which was holding up just fine.




First thing I did was move over from apache to nginx using php5-fpm. It works fine as a single dedicated instance but when it is routed off of haproxy, it was giving me some strange errors. Since I didn't have much time to tinker with it, I decided to try something I always heard about but never tried before, Apache MPM-WORKER.




So after googling around, I found a really nifty tutorial (can't remember where I got this from) which only took me like 2 minutes to go from apache mpm-prefork to mpm-worker. And as soon as I changed to it, I saw my load drop dramatically and I even went from 3 apache's to just 1 apache and still holding up well. 




So I highly recommend those of you looking to go to nginx or trying to scale their apache, take a jab at trying out the apache mpm-worker w/ php5 fcgi. It works flawlessly. I'd say it works just as well as nginx + php5 fpm.




------




When you install lamp on Ubuntu 10.04 , apache comes by default as mpm-prefork.  
But you will want to instead use mpm-worker, as it will use less memory and be more efficient. 




To use the “worker” MPM with PHP, do the following:




**Step 1. **Stop the apache2 daemon




`sudo /etc/init.d/apache2 stop`




**Step 2.  **Uninstall _apache2-mpm-prefork_




`sudo aptitude remove apache2-mpm-prefork`




**Step 3.**  Install _apache2-mpm-worker_ and _apache2-threaded-dev_




`sudo aptitude install apache2-mpm-worker apache2-threaded-dev`




**Step 4.** Enable _CGI_ and _mod_actions_ (may already be enabled)




`sudo a2enmod cgid``2``sudo a2enmod actions`




**Step 5.**  Create a file in _/etc/apache2/conf.d_ with the following content (I called mine php5-cgi.conf):




`<IfModule mod_actions.c>``2``        ``Action application/x-httpd-php /cgi-bin/php5``3``</IfModule>`




**Step 6.**  Start the apache2 daemon




`sudo /etc/init.d/apache2 start`
