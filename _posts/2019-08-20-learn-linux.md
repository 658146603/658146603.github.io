---
layout: post
title: "Learn Linux (Ubuntu 18.04 as Example)"
create: 2019-08-20
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

```shell
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

`Windows Terminal 添加Ubuntu-18.04选项卡`
```
{
    "acrylicOpacity" : 0.5,
    "closeOnExit" : true,
    "colorScheme" : "Campbell",
    "commandline" : "wsl.exe -d Ubuntu-18.04",
    "cursorColor" : "#FFFFFF",
    "cursorShape" : "bar",
    "fontFace" : "Consolas",
    "fontSize" : 10,
    "guid" : "{c6eaf9f4-32a7-5fdc-b5cf-066e8a4b1e40}",
    "historySize" : 9001,
    "icon" : "ms-appx:///ProfileIcons/{9acb9455-ca41-5af7-950f-6bca1bc9722f}.png",
    "name" : "Ubuntu-18.04",
    "padding" : "0, 0, 0, 0",
    "snapOnInput" : true,
    "useAcrylic" : false
}
```


## 换源
```shell
sudo nano /etc/apt/sources.list
```
```
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
```
```shell
sudo apt-get update
```

## frp
```
wget https://github.com/fatedier/frp/releases/download/v0.29.1/frp_0.29.1_linux_amd64.tar.gz

# frps.ini
[common]
bind_addr = 0.0.0.0
bind_port = 7000
vhost_http_port = 8000
vhost_https_port = 8001
dashboard_port = 7500
privilege_token = 123456
dashboard_user = ubuntu
dashboard_pwd = 123
log_file = ./frps.log
log_level = info
log_max_days = 3
max_pool_count = 5
authentication_timeout = 900
tcp_mux = true

# frpc.ini
[common]
server_addr = 服务器IP地址
server_port = 7000
privilege_token = 123456

log_file = ./frpc.log
log_level = info
log_max_days = 3
pool_count = 5
tcp_mux = true

[ssh]
type = tcp
local_ip = 127.0.0.1
local_port = 22
remote_port = 2200

[web]
type = http
local_port = 80
custom_domains = 服务器IP地址或服务器的域名（仔细填写，这是连接的主要方式）

# start
sudo ./frps -c frps.ini
sudo ./frpc -c frpc.ini

```

## nginx显示文件目录
```conf
http{
    # add lines below
    autoindex on;
    autoindex_exact_size off;
    autoindex_localtime on;
}
```