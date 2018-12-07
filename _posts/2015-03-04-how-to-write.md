---
layout: post
title: 这是一篇博客文章模板
date: 2015-3-04
categories: blog
tags: [标签一,标签二]
description: 文章金句。
---

#### 在Github上新建一个Repository

1.如果没有github账户，则[创建一个github账户](https://github.com/join)，如有跳过这一步。
2.

#### 配置自己的账户

1.从根文件夹打开**_config.yml**，会看到下列信息，按照提示修改。

```yml
# Site settings
title: 博客名字 # 你的博客名字，可以定义修订
header-img: "img/green.jpg"
tagline: "cn"  
description: "这是我的博客"  # 一句话描述你的博客
baseurl: ""
url: "http://cnfeat"  # 此处填写你的博客地址 

# About/contact
owner: 
  name: "作者名字" # 填写作者信息：名字
  email: X@gmail.com # 填写作者信息：邮箱
  bio: "你的博客描述" # 填写作者信息：博客描述

# Data
gavatar: img/favicon.png # 浏览器地址栏小图标，可自定义更改
favicon: img/favicon.png # 浏览器地址栏小图标，可自定义更改

douban_username:  # 你的豆瓣id
twitter_username: 
github_username: 
facebook_username: 
weibo_username: 
zhihu_username: 

# Build settings  
# use Github Flavored Markdown !important  
# document: http://jekyllrb.com/docs/configuration/#kramdown  
markdown: kramdown
highlighter: rouge
permalink: pretty
paginate: 8
exclude: ["less","node_modules","Gruntfile.js","package.json","README.md"]

# http://en.wikipedia.org/wiki/List_of_tz_database_time_zones
timezone: Asia/Shanghai

# Defaults for posts
defaults:
  -
    scope: 
      path: ""
      type: "posts"
    values:
      layout: "post"
      author: "你的名字" # 你的名字
      header-img: "img/green.jpg" # We don't want posts without a header image, that whould mean white on white

# Comments 
comments :
  provider : disqus # 使用 disqus 评论模块，读者翻墙才能看见
  duoshuo :
    short_name :  # 填写你的 disqus id
  disqus :
      short_name :  # 填写你的 disqus id

# Analytics and webmaster tools stuff goes here
google_analytics:  # 填写你  google_analytics id
google_verify:
# https://ssl.bing.com/webmaster/configure/verify/ownership Option 2 content= goes here
bing_verify:

# Links to include in footer navigation
```