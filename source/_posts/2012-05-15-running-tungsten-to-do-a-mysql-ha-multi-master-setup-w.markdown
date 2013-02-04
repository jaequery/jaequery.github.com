---
comments: true
date: 2012-05-15 23:23:00
layout: post
slug: running-tungsten-to-do-a-mysql-ha-multi-master-setup-w
title: Running tungsten to do a mysql HA multi-master setup w/ HAProxy
wordpress_id: 40
categories:
- Technology
---

### setup of tungsten on centos 5.8




1) copy private key of root to other mysql servers




sudo su -




ssh-keygen




cd ~/.ssh




ssh-copy-id -i id_rsa.pub root@procdb1  
 




2) install libraries




yum install ruby ruby-libs   
 




3) install java




download and install the rpm [http://www.oracle.com/technetwork/java/javase/downloads/jre-7u4-download-1591157.html](http://www.oracle.com/technetwork/java/javase/downloads/jre-7u4-download-1591157.html)




  
4) add this to my.cnf and restart mysql




### tungsten ###  
server-id                               =       1 #set to 2 on other  
log-bin                                 =       mysql-bin  
innodb_flush_log_at_trx_commit          =       2  
sync_binlog                             =       0  
max_allowed_packet                      =       48m  
# number of servers  
auto_increment_increment                =       2  
# set this to 1, set to 2 on other  
auto_increment_offset                   =       1  
 




5) create super account 'tungsten' on all mysql servers




grant all privileges on *.* to tungsten IDENTIFIED BY 'xxx' with grant option;




6) download tungsten replicator




wget [http://tungsten-replicator.googlecode.com/files/tungsten-replicator-2.0.5.tar.gz](http://tungsten-replicator.googlecode.com/files/tungsten-replicator-2.0.5.tar.gz)




7) create setup-multimaster.sh and run it




#! /bin/bash




TUNGSTEN_HOME=/opt/replication




TUNGSTEN_TOOLS=tools




MASTER_USER=tungsten




MASTER_PW=xxxx




MASTER1=procdb0 #change to the hostname of your db




SERVICE1=$MASTER1




  
MASTER2=procdb1 #change to the hostname of your db




SERVICE2=$MASTER2




echo 'setting up installer for '$MASTER1




./tools/tungsten-installer 




    --master-slave 




    --master-host=$MASTER1 




    --datasource-user=$MASTER_USER 




    --datasource-password=$MASTER_PW 




    --service-name=$SERVICE1 




    --home-directory=$TUNGSTEN_HOME 




    --cluster-hosts=$MASTER1 




    --start-and-report




echo 'setting up installer for '$MASTER2




./tools/tungsten-installer 




    --master-slave 




    --master-host=$MASTER2 




    --datasource-user=$MASTER_USER 




    --datasource-password=$MASTER_PW 




    --service-name=$SERVICE2 




    --home-directory=$TUNGSTEN_HOME 




    --cluster-hosts=$MASTER2 




    --start-and-report




8) create configure-multimaster.sh and run it




#! /bin/bash




TUNGSTEN_HOME=/opt/replication




TUNGSTEN_TOOLS=/opt/replication/tungsten/tools




MASTER1=procdb0 #change to the hostname of your db




SERVICE1=$MASTER1




MASTER2=procdb1 #change to the hostname of your db




SERVICE2=$MASTER2




echo 'configure services for '$MASTER1




$TUNGSTEN_TOOLS/configure-service 




   --host $MASTER1 




   -C -q 




   --local-service-name=$SERVICE1 




   --role=slave 




   --service-type=remote 




   --datasource=$MASTER1 




   --master-thl-host=$MASTER2 




   --svc-start $SERVICE2




echo 'configure services for '$MASTER2




$TUNGSTEN_TOOLS/configure-service 




  --host $MASTER2 




  -C -q 




  --local-service-name=$SERVICE2 




  --role=slave 




  --service-type=remote 




  --datasource=$MASTER2 




  --master-thl-host=$MASTER1 




  --svc-start $SERVICE1




9) All done, check if they are running  
  
/opt/replication/tungsten/tungsten-replicator/bin/trepctl services  
this should list two blocks of texts if everything is working correctly    




11) to stop or start replication, do:




/opt/replication/tungsten/tungsten-replicator/bin/replicator stop




/opt/replication/tungsten/tungsten-replicator/bin/replicator start




when server goes down or is rebooted, make sure to start the replicator as it's not turned on automatically like mysql daemon. this to ensure you can just double check your data.







### configure haproxy for mysql multi-master




12) setup haproxy







have heartbeat installed and make sure you've got a virtual ip for your db servers.







add these to the end of your /etc/haproxy/haproxy.cfg:










listen mysql-cluster




        bind x.x.y.y:3306 #virtual ip




        mode tcp




        balance roundrobin




        option tcpka




        option httpchk




        option mysql-check user root







        server procdb0 x.x.x.x:3306 check #db ip




        server procdb1 x.x.x.y:3306 check #db ip2






