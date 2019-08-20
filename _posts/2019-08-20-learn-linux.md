---
layout: post
title: "Learn Linux (Ubuntu 18.04 as Example)"
create: 2019-08-13
update: 2019-08-20
categories: blog
tags: [Ubuntu]
description: "Learn Linux"
---


`update and upgrade`
```
sudo apt-get update
sudo apt-get upgrade
```

`change passowrd for user ubuntu`
```
sudo passwd ubuntu
```

`download file`
```
wget https://dl.google.com/dl/android/studio/ide-zips/3.4.2.0/android-studio-ide-183.5692245-windows.zip
```

`install mysql`
```
sudo apt-get install mysql-server
sudo mysql_secure_installation
```

`unpack tar.gz`
```
tar -zxvf apache-tomcat-9.0.12.tar.gz
```

`rc.local for Ubuntu-18.04`

```
sudo nano /etc/systemd/system/rc-local.service

内容：

[Unit]
Description=/etc/rc.local Compatibility
ConditionPathExists=/etc/rc.local

[Service]
Type=forking
ExecStart=/etc/rc.local start
TimeoutSec=0
StandardOutput=tty
RemainAfterExit=yes
SysVStartPriority=99

[Install]
WantedBy=multi-user.target


sudo nano /etc/rc.local

内容：

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

TODO()

exit 0

sudo chmod 755 /etc/rc.local
sudo systemctl enable rc-local
```