---
layout: post
title: "[树莓派]树莓派屏幕配置"
create: 2018-12-28
update: 2018-12-28
categories: blog
tags: [Raspberry Pi]
description: "树莓派屏幕配置"
---


使用方式：

a.快捷的方式，使用网盘（35_HDMI_Normal）或者网站

里面的编译好的文件直接烧录到sd卡。

b.使用网盘里的驱动。

 1.烧录自己想要的系统

 2.保证网络连接正常

 3.将LCD屏与树莓派开发板正确连接

 4.将网盘驱动拷贝到树莓派上（使用ssh或者使用U盘介质挂载）

 5.解压文件并开始安装。

    修改权限        sudo chmod 777 LCD_show_35hdmi.tar.gz

    解压文件        tar -xzvf LCD_show_35hdmi.tar.gz

    跳入文件夹      cd  LCD_show_35hdmi

    先升级更新系统(可选)    sudo apt-get update

    备份数据（可选）        sudo ./LCD_backup

    安装驱动 

    分辨率为480*320         sudo ./LCD35_480*320

    分辨率为720*480         sudo ./LCD35_720*480

    分辨率为810*540         sudo ./LCD35_810*540

    稍等一段时间系统就会安装驱动并自动重新启动

    如果想重新使用安装之前系统的话，可以使用 sudo ./LCD_restore   

    注意：当你更新系统使用之前，必须使用一下这个命令 sudo apt-mark hold raspberrypi-kernel(锁住内核及驱动不被改变)sudo apt-mark hold raspberrypi-bootloader(锁定分辨率不改变)

    然后使用一下命令，
    sudo apt-get update 
    sudo apt-get upgrade

    sudo  apt-get  dist-upgrade  (不推荐此命令升级，更新是最新的，但是可能是不安全的否则可能重启以后会失败)

引脚定义：

1   ----> NC

2   ----> 5v

3   ----> NC

4   ----> 5V

19 ----> MOSI

20 ----> GND

21 ----> MISO

22 ----> TP_IRQ

23 ----> SCLK

24 ----> TP_CS

25 ----> GND

26 ----> NC

Others are NC