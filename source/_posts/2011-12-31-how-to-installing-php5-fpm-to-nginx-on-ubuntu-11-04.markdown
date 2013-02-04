---
comments: true
date: 2011-12-31 05:06:37
layout: post
slug: how-to-installing-php5-fpm-to-nginx-on-ubuntu-11-04
title: 'HOW TO: Installing PHP5-FPM to nginx on ubuntu 11.04'
wordpress_id: 47
categories:
- Technology
---

Nginx by default does not include the setup necessary for PHP.  For that, we will need to configure the php5-fpm package.  We will first discuss that package, and then discuss configuring nginx to work with php5-fpm.  Note that the actions done in this HOW-TO will most likely need superuser rights, either via the use of sudo or by the use of the superuser account.




## php5-fpm




  1. We need to install php5-fpm and its dependencies.  The version from the Ubuntu repositories will work well:

    
    sudo apt-get install php5-fpm





  2. We will begin by editing the php.ini file.  Open the php.ini file in the current directory with your favorite editor (I prefer using nano, but you’re free to use vim, emacs, or any other editor you like, as long as its run as superuser with sudo):

    
    sudo nano /etc/php5/fpm/pool.d/www.conf





  3. We will be configuring the php5-fpm process to use a socket.  This will allow for nginx to more easily communicate with the php5-fpm process to serve the PHP content to the Internet.  Inside the [www.conf](http://www.conf) file, look for the line starting with:

    
    listen =




and replace that line so it instead says:



    
    listen = /var/run/php5-fpm.sock




This tells the php5-fpm process to only listen for incoming PHP processing requests in the socket file located in the /var/run/ directory.





  4. Restart the php5-fpm service:

    
    sudo service php5-fpm restart






If all was configured correctly, then the php5-fpm service should have restarted without any errors.  On to configuring your nginx site for working with PHP.




## nginx Site Configuration




NOTE!  There are different steps you will need to take in order to get PHP on nginx working if you want to use SSL!  _Those steps are not covered in this HOW-TO, but may be covered in a future HOW-TO, so keep an eye on this blog!_




We will now begin setting up your nginx site config file for using PHP.  This is the sample config file from the initial Configuring nginx HOW-TO on this blog, using foobar.com as the domain name.  Your domain name will be different:



    
    server {
            server_name localhost;
            root /var/www/;
    
            index index.html index.htm /index.htm;
    
            location / {
                    try_files $uri $uri/ =404;
            }
    }




As you can tell, this doesn’t include anything about PHP. It only talks about HTML, and the basic server configuration. We will now modify this to include the information necessary to allow the processing of PHP.




  1. Navigate to the location of your site’s configuration file.  If you followed the HOW-TO on this site, then the file will be located in /etc/nginx/sites-available/.


  2. Open the configuration file for your site.


  3. Add the following to the server block, and then save the file:

    
    location ~ .php$ {
            fastcgi_split_path_info ^(.+.php)(/.+)$;
            include fastcgi_params;
            fastcgi_pass unix:/var/run/php5-fpm.sock;
    }




This will add the necessary parameters in order to process the PHP files and serve them correctly.





  4. Restart the nginx service: sudo service nginx restart


  5. In wherever you stated in the “root” statement in your site’s config, create a file called phpinfo.php, containing the following:

    
    <?php phpinfo();




and then open the page in your Internet browser (in the example config, the site would be [http://foobar.com/phpinfo.php](http://foobar.com/phpinfo.php))





  6. If you configured PHP correctly, a page containing various information regarding PHP and your web server should be displayed.  If this is the case, then congratulations, PHP has been successfully configured for your site.  You can now remove the phpinfo.php page (it is not advised to keep that page, as it contains some information which can put your server at risk).  If you did not configure PHP correctly, you will instead be prompted with either a blank page or a download prompt.  If this is the case, make sure you followed the steps in this HOW-TO correctly.


