---
comments: true
date: 2012-09-28 03:45:00
layout: post
slug: rotate-outgoing-ip-in-postfix
title: rotate outgoing ip in postfix
wordpress_id: 16
categories:
- Technology
---

Here is a script I wrote for a friend who needed to update his outgoing IP on his postfix server and rotate them once every minute: /root/crons/rotate_postfix_ip.sh and add it to your cronjob to run every minute and you are set!



    
    #!/bin/bash
    ips=("64.250.120.128" "64.250.121.241" "64.250.121.242")
    length=${#ips[@]}
    pos=`cat current.txt`
    oldip=${ips[$pos - 1]}
    if [ "$length" -eq "$pos" ] ; then
        echo "limit reached"
        pos=1
    else
        echo "increment!"
        (( pos++ ))
    fi
    
    echo "$pos" > current.txt
    
    newip=${ips[$pos - 1]}
    echo "prev: $oldip"
    echo "new: $newip"
    
    sed -ie "s/smtp_bind_address=$oldip/smtp_bind_address=$newip/g" /etc/postfix/main.cf > /dev/null
    service postfix reload
    
    
    
