---
layout: post
title: "Percona Toolkit (Maatkit) - Check integrity of the master/slave replication"
date: 2013-05-30 16:18
comments: true
categories:
---



### INSTALL

First install Percona Toolkit if you haven't already.

```
wget percona.com/get/percona-toolkit.tar.gz
wget percona.com/get/percona-toolkit.rpm
wget percona.com/get/percona-toolkit.deb
```

### Start checksum

From master:

```
pt-table-checksum -uuser -ppwd
```
