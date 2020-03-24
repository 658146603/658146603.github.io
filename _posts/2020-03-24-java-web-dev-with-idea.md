---
layout: post
title: "Windows搭建本地Java Web开发环境(IDEA)以及部署"
create: 2020-03-24
update: 2020-03-24
categories: blog
tags: [JAVA]
description: "Windows搭建本地Java Web开发环境(IDEA)以及部署"
---

## Windows搭建本地Java Web开发环境(IDEA)以及部署

### `准备工作`

- idea 2019.3.4
- Jdk 7及以上版本
- Tomcat 7及以上版本(推荐tar.gz的压缩包)

### `Tomcat`

[官网下载Tomcat](https://tomcat.apache.org/)
![img](/img/2020-03-24-tomcat-download.png)
解压到一个目录(最好不含空格或中文的路径)
![img](/img/2020-03-24-tomcat-directory.png)
我们可以用bin/catalina.bat 或 bin/catalina.sh来开关Tomcat

```bat
# 开启
PS C:\dev\apache-tomcat-9.0.12\bin> .\catalina.bat start
Using CATALINA_BASE:   "C:\dev\apache-tomcat-9.0.12"
Using CATALINA_HOME:   "C:\dev\apache-tomcat-9.0.12"
Using CATALINA_TMPDIR: "C:\dev\apache-tomcat-9.0.12\temp"
Using JRE_HOME:        "C:\Program Files\Java\jdk1.8.0_131"
Using CLASSPATH:       "C:\dev\apache-tomcat-9.0.12\bin\bootstrap.jar;C:\dev\apache-tomcat-9.0.12\bin\tomcat-juli.jar"

# 关闭
PS C:\dev\apache-tomcat-9.0.12\bin> .\catalina.bat stop
Using CATALINA_BASE:   "C:\dev\apache-tomcat-9.0.12"
Using CATALINA_HOME:   "C:\dev\apache-tomcat-9.0.12"
Using CATALINA_TMPDIR: "C:\dev\apache-tomcat-9.0.12\temp"
Using JRE_HOME:        "C:\Program Files\Java\jdk1.8.0_131"
Using CLASSPATH:       "C:\dev\apache-tomcat-9.0.12\bin\bootstrap.jar;C:\dev\apache-tomcat-9.0.12\bin\tomcat-juli.jar"
```

我们可以看见Tomcat下有webapps目录，我们写的应用可以部署在这里

### `使用IDEA提高开发效率`

打开IDEA我们可以看见下面的起始页面
点击`Create New Page`新建项目
![img](/img/2020-03-24-idea-start-page.png)
进入`Java Enterprice`选择`Web Application`
![img](/img/2020-03-24-idea-new-project.png)
输入项目名称和路径
![img](/img/2020-03-24-idea-new-project-1.png)
新建项目完毕
![img](/img/2020-03-24-idea-new-project-2.png)
到这一步我们就完成了项目的创建，接下来是部署和运行项目的环节
点击右上角的`Add Configuration`新增配置
![img](/img/2020-03-24-idea-add-conf.png)
点击左上角的+号并选择(Tomcat Server, Local)来新建一个本地的部署配置
![img](/img/2020-03-24-idea-add-conf-1.png)
因为是第一次配置，我们需要配置Tomcat目录，点击Application Server的Configure新增一个Tomcat目录
![img](/img/2020-03-24-idea-add-conf-2.png)
![img](/img/2020-03-24-idea-add-conf-3.png)
这里的URL是我们点击运行项目后IDEA自动打开浏览器URL，HTTP Port则是IDEA里的Tomcat需要监听的端口
![img](/img/2020-03-24-idea-add-conf-4.png)
![img](/img/2020-03-24-idea-add-conf-5.png)
接下来是配置要部署的内容了，进入`Deployment`点击右侧的+号，点击`Artifact...`就可以生成一个默认的未压缩的可用于部署的应用
Application Context是应用的路径，这里我们设置位example，所以到时候可以通过 <http://localhost:8080/example/> 访问应用
![img](/img/2020-03-24-idea-add-conf-6.png)
![img](/img/2020-03-24-idea-add-conf-7.png)
