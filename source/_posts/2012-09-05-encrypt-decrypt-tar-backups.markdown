---
comments: true
date: 2012-09-05 22:43:11
layout: post
slug: encrypt-decrypt-tar-backups
title: encrypt / decrypt tar backups
wordpress_id: 22
categories:
- Technology
---

This command will compress the directory *todays_backup* into the compressed file *todays_backup.tar.gz*:
```bash
tar -zcf todays_backup.tar.gz todays_backup
```

To decompress it use the following command:
```bash
tar -zxf todays_backup.tar.gz
```

Now to the fun part. Let’s look at how we can add a basic level of encryption to the process we used above. To compress the directory *todays_backup* with protection do the following:
```bash
tar -zcf – todays_backup|openssl des3 -salt -k yourpassword | dd of=todays_backup.des3
```

Replace *yourpassword* with a password of your own. Keep the password to yourself, and keep it carefully. The above command will generate a file called *todays_backup.des3*. This file can only be decompressed using this password.

To extract your protected archive *todays_backup.des3* use the following command:
```bash
dd if= todays_backup.des3 |openssl des3 -d -k yourpassword |tar zxf -
```

Make note of the trailing *-* at the end. It is not a typo, but a requirement for this command to work. Replace *yourpassword* with the password you used while encrypting the file. Executing the above command will extract the compressed file *todays_backup.des3* into a directory *todays_backup*. Use this encryption with care. As I said earlier, the only way you can retrieve your data once secured is by using the password, so do not lose this password under any circumstances.
