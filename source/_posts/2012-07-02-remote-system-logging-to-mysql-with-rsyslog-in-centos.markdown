---
comments: true
date: 2012-07-02 16:26:00
layout: post
slug: remote-system-logging-to-mysql-with-rsyslog-in-centos
title: Remote system logging to Mysql with Rsyslog in Centos 5.8
wordpress_id: 35
categories:
- Technology
---

Gathering information message is important on Data Center, in some situations you’ll want to store all entries of logfiles on another server. If a server crashes or gets hacked it will be able to trace through  logfiles from your machine. this is can be accomplished by using centralized log server that receive messages from another hosts.  A syslog facility can receive messages from Unix/Linux hosts but also network devices and windows hosts.

In this post, I want to explain step installation of Rsyslog, and Centralized log using MySQL Database. And using LogAnalyzer web interface, for graphical view and administrative.

Step Installation:

**1. First we need to install the following packages:**

`# yum install rsyslog rsyslog-mysql mysql-server php-mysql php-gd httpd mod_ssl`

**2. Configure rsyslog, mysqld, and httpd to run on startup:**

`#  chkconfig --add rsyslog
#  chkconfig --add mysqld
#  chkconfig --add httpd
#  chkconfig rsyslog on
#  chkconfig httpd on
#  chkconfig mysqld on
#  service rsyslog start
#  service mysqld start
#  service httpd start`

**3.  Configure RSyslog with MySQL Database Connection
**

Assuming for example:
user: root
password: sql password
host: localhost
db to create: Rsyslogdb
RSyslog-mysql database installation path: /usr/share/doc/rsyslog-mysql-2.0.0/createDB.sql

Create database:
`# mysql –u root –psqlpassword
mysql> CREATE DATABASE Rsyslogdb;`

Export rsyslog database table:
`# mysql –u root –psqlpassword Rsyslogdb < /usr/share/doc/rsyslog-mysql-2.0.0/createDB.sql`

Setup MySQL permission (must be same with /etc/rsyslog.conf and /path/to/loganalyzer/config.php)
`# mysql –u root –psqlpassword
mysql> GRANT ALL ON Rsyslogdb.* TO ‘root’@’localhost’ IDENTIFIED BY 'sqlpassword';`

**4. Configure RSyslog**

edit rsyslog configuration file
`vi /etc/rsyslog.conf`

add this line below:
`$ModLoad ommysql
$ModLoad imuxsock
$ModLoad imklog
$Modload imudp
$UDPServerRun 514
$Modload imtcp
$InputTCPServerRun 514
## Optional
#$UDPServerAddress 0.0.0.0
## Optional
#$RepeatedMsgReduction ()
$template dbFormat,"insert into SystemEvents (Message, Facility,FromHost, Priority, DeviceReportedTime, ReceivedAt, InfoUnitID, SysLogTag) values ('%msg%', %syslogfacility%, '%HOSTNAME%',%syslogpriority%, '%timereported:::date-mysql%', '%timegenerated:::date-mysql%', %iut%, '%syslogtag%')",sql
*.*       : ommysql:localhost,Ryslog,root,sqlpassword
*.info;mail.none;authpriv.none;cron.none            /var/log/messages
authpriv.*                                          /var/log/secure
mail.*                                              /var/log/maillog
cron.*                                              /var/log/cron
*.emerg                                             *
uucp,news.crit                                      /var/log/spooler
local7.*                                             /var/log/boot.log`

**5. Restarting rsyslog service:**
`# service rsyslog restart`

**6. Centralized Syslog Server**
Edit file:  /etc/sysconfig/rsyslog  (add this line)
`# vi /etc/sysconfig/rsyslog
SYSLOGD_OPTIONS="-c3"`

**7. Log Analyzer Installation**
Download the latest installation :
[http://loganalyzer.adiscon.com/downloads](http://loganalyzer.adiscon.com/downloads)

`# cd /tmp
# wget [http://download.adiscon.com/loganalyzer/loganalyzer-3.0.6.tar.gz](http://download.adiscon.com/loganalyzer/loganalyzer-3.0.6.tar.gz)
# tar -zxvf loganalyzer-3.0.6.tar.gz
# cd loganalyzer-3.0.6/src/
# mkdir /var/www/html/Rsyslog
# cp –R * /var/www/html/Rsyslog
# cp ../contrib/configure.sh /var/www/html/
# chmod +x configure.sh
# ./configure.sh`

After you execute configuration.sh files, it will create an empty config.php that used for Log Analyzer Configuration.

Open your favorite web browser and navigate into your homepage (i.e: [http://localhost](http://localhost/)), then fill in and follow the Log Analyzer configuration steps to complete. From here RSyslog can be displayed on Show Events tab, choose MySQL Native to load your syslog messages on this machine into your RSyslog database on MySQL.

[
](http://gembuls.files.wordpress.com/2011/02/rsyslog1.jpg)Done!
