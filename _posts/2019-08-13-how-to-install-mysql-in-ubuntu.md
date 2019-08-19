---
layout: post
title: "How to Install MySQL in Ubuntu"
create: 2019-08-13
update: 2019-08-13
categories: blog
tags: [Ubuntu]
description: "How to Install MySQL in Ubuntu"
---

```
install:

sudo apt-get update
sudo apt-get install mysql-server
sudo mysql_secure_installation

Other command:

apt-get install default-jdk
tar -zxvf apache-tomcat-9.0.12.tar.gz


rc.local for ubuntu-18.04:
nano /etc/systemd/system/rc-local.service
{
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
}


nano /etc/rc.local
{
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
    echo "测试脚本执行成功" > /usr/local/test.log
    exit 0
}
chmod 755 /etc/rc.local
sudo systemctl enable rc-local

```


`mysql允许远程连接:`

mysql -uroot -p

use mysql;

GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '$password'

flush privileges;

exit;

service mysql restart



`Git`
## 删除包括历史
git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch 文件相对路径' --prune-empty --tag-name-filter cat -- --all
## 同步到远程
git push origin master --force