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
点击右上角的绿色三角形可以运行应用，当看到下面的截图并跳出浏览器时，项目就运行成功了
![img](/img/2020-03-24-idea-start.png)
当代码有更改时，如果要更新正在运行的项目，你仍然可以点击那个按钮，只不过现在它是一个半圆形的刷新箭头，当跳出Update 'example'框时，可以选择Redeploy来最快的应用更改
![img](/img/2020-03-24-idea-start-1.png)
接下来是配置要部署的内容了，进入`Deployment`点击右侧的+号，点击`Artifact...`就可以生成一个默认的未压缩的可用于部署的应用，Application Context是应用的路径，这里我们设置位example，所以到时候可以通过 <http://localhost:8080/example/> 访问应用
![img](/img/2020-03-24-idea-add-conf-6.png)
![img](/img/2020-03-24-idea-add-conf-7.png)

接下来是打包应用的步骤
项目右键点击`Open Module Settings`
![img](/img/2020-03-24-idea-pack.png)
我们看到这里已经有了之前创建的exploded_war，现在我们要新建以这个exploded_war打包的配置，点击+号
![img](/img/2020-03-24-idea-pack-1.png)
选择`Web Application: Archive`,`For 'example:war exploded'`就可以了，我们可以把Name改成example，这样生成的war文件的文件名就是example.war了
![img](/img/2020-03-24-idea-pack-2.png)
要编译新的应用是，只需要点击`Build`, `Buile Artifacts...`,点击Build或Rebuild就行了，example.war会出现在out文件夹中，把example.war文件放入Tomcat的webapps文件夹下，Tomcat默认会自动解压和部署，并且当文件夹下的example.war更新时，应用也会相应的更新
![img](/img/2020-03-24-idea-pack-3.png)
![img](/img/2020-03-24-idea-pack-4.png)
![img](/img/2020-03-24-idea-pack-5.png)
