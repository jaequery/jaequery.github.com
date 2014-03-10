---
layout: post
title: "percona sql-mode causing 'incorrect integer value for column' errors"
date: 2013-06-12 15:51
comments: true
categories:
---

When I switched one of my client's db server to another newer environment, it caused theier site to fail.
It was a strange problem because everything was the same environment from the other server, from versions/configs of apache, php, mysql (Percona), etc and they all checked out fine.

The underlying problem was narrowed down to the fact there were some sql queries in the scripts that passed in empty strings on an integer column. This is due to the fact sql-mode had STRICT_TRANS_TABLES enabled.
I've never seen a case where this was enabled by default and this was the first time it ever occurred to me.

So to resolve it, I tried editing the my.cnf and explicitly setting to:

```
sql-mode = ''
```

But this didn't seem to take any effect whatsoever. When I set it manually within the mysql console using, it worked:

```
SET @@global.sql_mode= '';
```

This made me realize that /etc/my.cnf is not being read! To my surprise, Percona actually installs /usr/my.cnf (a big major WTF moment!) in their recent 5.6 release which had this:

```
# For advice on how to change settings please see
# http://dev.mysql.com/doc/refman/5.6/en/server-configuration-defaults.html

[mysqld]

# Remove leading # and set to the amount of RAM for the most important data
# cache in MySQL. Start at 70% of total RAM for dedicated server, else 10%.
# innodb_buffer_pool_size = 128M

# Remove leading # to turn on a very important data integrity option: logging
# changes to the binary log between backups.
# log_bin

# These are commonly set, remove the # and set as required.
# basedir = .....
# datadir = .....
# port = .....
# server_id = .....
# socket = .....

# Remove leading # to set options mainly useful for reporting servers.
# The server defaults are faster for transactions and fast SELECTs.
# Adjust sizes as needed, experiment to find the optimal values.
# join_buffer_size = 128M
# sort_buffer_size = 2M
# read_rnd_buffer_size = 2M

sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES
```

So solution was to just remove that file /usr/my.cnf and let /etc/my.cnf take over.

It's all good now but seriously, /usr/my.cnf? Is /usr/local/my.cnf next in line in the future? (shaking my head)