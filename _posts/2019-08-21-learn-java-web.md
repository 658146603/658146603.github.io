---
layout: post
title: "Learn JavaWeb Development"
create: 2019-08-21
update: 2019-08-26
categories: blog
tags: [JavaWeb]
description: "Note for Development"
---

## Windows 下开发 JavaWeb 的教程

### 1. 准备步骤
- 安装 JDK 并配置环境变量
- [安装 IDEA](https://www.jetbrains.com/idea/)
- [下载 Tomcat](http://tomcat.apache.org/)

### 2. 创建项目

首先在idea的创建项目引导页选择JavaEE中的Spring













### 环境变量配置 for Windows 10

`JAVA_HOME`
```
...
```
`CLASSPATH`
``` 
.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
```
`Path`
```
%JAVA_HOME%\bin && %JAVA_HOME%\jre\bin
```
`create jre`
```
bin\jlink.exe --module-path jmods --add-modules java.desktop --output jre
```
