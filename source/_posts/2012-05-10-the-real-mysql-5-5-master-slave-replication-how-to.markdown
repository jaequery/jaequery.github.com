---
comments: true
date: 2012-05-10 23:40:38
layout: post
slug: the-real-mysql-5-5-master-slave-replication-how-to
title: the REAL mysql 5.5 master slave replication how-to
wordpress_id: 41
categories:
- Technology
---

so i spent about half a day trying to get a simple mysql 5.5 master to slave replication going. mainly because 5.5 seems to have changed in how replication works, compared to the previous versions, so all the tutorials on google, didn't work for me.




after trying out literally 5 different tutorials with no luck, i went to the trusted mysql's documentation (i should do that more often), and i was able to follow their directions and finish replication in under 3 mins. o_O




so here's the deal:




first go here [[http://dev.mysql.com/doc/refman/5.5/en/replication-howto.html](http://dev.mysql.com/doc/refman/5.5/en/replication-howto.html)](http://dev.mysql.com/doc/refman/5.5/en/replication-howto.html) , follow exactly what they tell you to do step by step.




but since you are here, i'll go ahead and list out the steps below:




### 1) Setup the Master




1) edit my.cnf (from a default my.cnf) and make sure you have these





[mysqld]  
log-bin=mysql-bin  
server-id=1




and now restart mysql




2) from mysql console




- add slave user:  
grant replication slave ON *.* TO 'slave'@'%' IDENTIFIED BY 'test';




flush privileges; (not sure if it's needed anymore but do it anyway for good measures)




- lock writes




flush tables with read lock ;




- get your log file and log position (save these since you'll need it later for slave setup)




show master status;





### 2) Setup the Slave




1) edit my.cnf




[mysqld]  
server-id=2




that's all you need. restart mysql




2) load master's database dump (optional), apparently you need to use mysql cli to load data, you can't do "load data from master" anymore as it's deprecated.




3) put in your master server and log details:




CHANGE MASTER TO MASTER_HOST='ServerIP/FQDN', MASTER_USER='slave', MASTER_PASSWORD='test', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=98;




*Replace mysql-bin.0000001 and master_log_pos with what you got from "show master status" from Master server




4) start slave;




5) check if everything is cool by doing:




show slave statusG;




You should see stuffs like:




mysql> show slave statusG;




*************************** 1. row ***************************




               Slave_IO_State: Waiting for master to send event




                  Master_Host: mysql1




                  Master_User: slave_user




                  Master_Port: 3306




                Connect_Retry: 60




              Master_Log_File: mysql-bin.000005




          Read_Master_Log_Pos: 10383




if not something went wrong




### Almost done




1) go back to master server mysql console and unlock the tables




unlock tables;




### Done
