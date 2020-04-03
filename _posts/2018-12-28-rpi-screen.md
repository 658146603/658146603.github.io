---
layout: post
title: "[树莓派]树莓派屏幕配置"
create: 2018-12-28
update: 2018-12-28
categories: blog
tags: [Raspberry Pi]
description: "树莓派屏幕配置"
---

触摸屏使用方式：

 1. 烧录自己想要的系统

 2. 保证网络连接正常

 3. 将LCD屏与树莓派开发板正确连接

 4. 将网盘驱动拷贝到树莓派上（使用ssh或者使用U盘介质挂载）

 5. 解压文件并开始安装。

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

hdmi_mode 设置屏幕分辨率

    当hdmi_group=1 (CEA)时,下列值有效
    hdmi_mode=1    VGA
    hdmi_mode=2    480p  60Hz
    hdmi_mode=3    480p  60Hz  H
    hdmi_mode=4    720p  60Hz
    hdmi_mode=5    1080i 60Hz
    hdmi_mode=6    480i  60Hz
    hdmi_mode=7    480i  60Hz  H
    hdmi_mode=8    240p  60Hz
    hdmi_mode=9    240p  60Hz  H
    hdmi_mode=10   480i  60Hz  4x
    hdmi_mode=11   480i  60Hz  4x H
    hdmi_mode=12   240p  60Hz  4x
    hdmi_mode=13   240p  60Hz  4x H
    hdmi_mode=14   480p  60Hz  2x
    hdmi_mode=15   480p  60Hz  2x H
    hdmi_mode=16   1080p 60Hz
    hdmi_mode=17   576p  50Hz
    hdmi_mode=18   576p  50Hz  H
    hdmi_mode=19   720p  50Hz
    hdmi_mode=20   1080i 50Hz
    hdmi_mode=21   576i  50Hz
    hdmi_mode=22   576i  50Hz  H
    hdmi_mode=23   288p  50Hz
    hdmi_mode=24   288p  50Hz  H
    hdmi_mode=25   576i  50Hz  4x
    hdmi_mode=26   576i  50Hz  4x H
    hdmi_mode=27   288p  50Hz  4x
    hdmi_mode=28   288p  50Hz  4x H
    hdmi_mode=29   576p  50Hz  2x
    hdmi_mode=30   576p  50Hz  2x H
    hdmi_mode=31   1080p 50Hz
    hdmi_mode=32   1080p 24Hz
    hdmi_mode=33   1080p 25Hz
    hdmi_mode=34   1080p 30Hz
    hdmi_mode=35   480p  60Hz  4x
    hdmi_mode=36   480p  60Hz  4xH
    hdmi_mode=37   576p  50Hz  4x
    hdmi_mode=38   576p  50Hz  4x H
    hdmi_mode=39   1080i 50Hz  reduced blanking
    hdmi_mode=40   1080i 100Hz
    hdmi_mode=41   720p  100Hz
    hdmi_mode=42   576p  100Hz
    hdmi_mode=43   576p  100Hz H
    hdmi_mode=44   576i  100Hz
    hdmi_mode=45   576i  100Hz H
    hdmi_mode=46   1080i 120Hz
    hdmi_mode=47   720p  120Hz
    hdmi_mode=48   480p  120Hz
    hdmi_mode=49   480p  120Hz H
    hdmi_mode=50   480i  120Hz
    hdmi_mode=51   480i  120Hz H
    hdmi_mode=52   576p  200Hz
    hdmi_mode=53   576p  200Hz H
    hdmi_mode=54   576i  200Hz
    hdmi_mode=55   576i  200Hz H
    hdmi_mode=56   480p  240Hz
    hdmi_mode=57   480p  240Hz H
    hdmi_mode=58   480i  240Hz
    hdmi_mode=59   480i  240Hz H
    H表示16:9比例(正常是4:3).
    2x表示双倍像素(即更高的像素时脉, 每个像素重复两次)
    4x表示四倍像素(即更高的像素时脉, 每个像素重复四次)

 

    当hdmi_group=2 (DMT)时,下列值有效警告: 像素时脉是有限制的, 最高支持的模式是1920x1200 @60Hz with reduced blanking.
    hdmi_mode=1    640x350   85Hz
    hdmi_mode=2    640x400   85Hz
    hdmi_mode=3    720x400   85Hz
    hdmi_mode=4    640x480   60Hz
    hdmi_mode=5    640x480   72Hz
    hdmi_mode=6    640x480   75Hz
    hdmi_mode=7    640x480   85Hz
    hdmi_mode=8    800x600   56Hz
    hdmi_mode=9    800x600   60Hz
    hdmi_mode=10   800x600   72Hz
    hdmi_mode=11   800x600   75Hz
    hdmi_mode=12   800x600   85Hz
    hdmi_mode=13   800x600   120Hz
    hdmi_mode=14   848x480   60Hz
    hdmi_mode=15   1024x768  43Hz  DO NOT USE
    hdmi_mode=16   1024x768  60Hz
    hdmi_mode=17   1024x768  70Hz
    hdmi_mode=18   1024x768  75Hz
    hdmi_mode=19   1024x768  85Hz
    hdmi_mode=20   1024x768  120Hz
    hdmi_mode=21   1152x864  75Hz
    hdmi_mode=22   1280x768        reduced blanking
    hdmi_mode=23   1280x768  60Hz
    hdmi_mode=24   1280x768  75Hz
    hdmi_mode=25   1280x768  85Hz
    hdmi_mode=26   1280x768  120Hz reduced blanking
    hdmi_mode=27   1280x800        reduced blanking
    hdmi_mode=28   1280x800  60Hz
    hdmi_mode=29   1280x800  75Hz
    hdmi_mode=30   1280x800  85Hz
    hdmi_mode=31   1280x800  120Hz reduced blanking
    hdmi_mode=32   1280x960  60Hz
    hdmi_mode=33   1280x960  85Hz
    hdmi_mode=34   1280x960  120Hz reduced blanking
    hdmi_mode=35   1280x1024 60Hz
    hdmi_mode=36   1280x1024 75Hz
    hdmi_mode=37   1280x1024 85Hz
    hdmi_mode=38   1280x1024 120Hz reduced blanking
    hdmi_mode=39   1360x768  60Hz
    hdmi_mode=40   1360x768  120Hz reduced blanking
    hdmi_mode=41   1400x1050       reduced blanking
    hdmi_mode=42   1400x1050 60Hz
    hdmi_mode=43   1400x1050 75Hz
    hdmi_mode=44   1400x1050 85Hz
    hdmi_mode=45   1400x1050 120Hz reduced blanking
    hdmi_mode=46   1440x900        reduced blanking
    hdmi_mode=47   1440x900  60Hz
    hdmi_mode=48   1440x900  75Hz
    hdmi_mode=49   1440x900  85Hz
    hdmi_mode=50   1440x900  120Hz reduced blanking
    hdmi_mode=51   1600x1200 60Hz
    hdmi_mode=52   1600x1200 65Hz
    hdmi_mode=53   1600x1200 70Hz
    hdmi_mode=54   1600x1200 75Hz
    hdmi_mode=55   1600x1200 85Hz
    hdmi_mode=56   1600x1200 120Hz reduced blanking
    hdmi_mode=57   1680x1050       reduced blanking
    hdmi_mode=58   1680x1050 60Hz
    hdmi_mode=59   1680x1050 75Hz
    hdmi_mode=60   1680x1050 85Hz
    hdmi_mode=61   1680x1050 120Hz reduced blanking
    hdmi_mode=62   1792x1344 60Hz
    hdmi_mode=63   1792x1344 75Hz
    hdmi_mode=64   1792x1344 120Hz reduced blanking
    hdmi_mode=65   1856x1392 60Hz
    hdmi_mode=66   1856x1392 75Hz
    hdmi_mode=67   1856x1392 120Hz reduced blanking
    hdmi_mode=68   1920x1200       reduced blanking
    hdmi_mode=69   1920x1200 60Hz
    hdmi_mode=70   1920x1200 75Hz
    hdmi_mode=71   1920x1200 85Hz
    hdmi_mode=72   1920x1200 120Hz reduced blanking
    hdmi_mode=73   1920x1440 60Hz
    hdmi_mode=74   1920x1440 75Hz
    hdmi_mode=75   1920x1440 120Hz reduced blanking
    hdmi_mode=76   2560x1600       reduced blanking
    hdmi_mode=77   2560x1600 60Hz
    hdmi_mode=78   2560x1600 75Hz
    hdmi_mode=79   2560x1600 85Hz
    hdmi_mode=80   2560x1600 120Hz reduced blanking
    hdmi_mode=81   1366x768  60Hz
    hdmi_mode=82   1080p     60Hz
    hdmi_mode=83   1600x900        reduced blanking
    hdmi_mode=84   2048x1152       reduced blanking
    hdmi_mode=85   720p      60Hz
    hdmi_mode=86   1366x768        reduced blanking

