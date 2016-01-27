---
layout: post
title: "Octopress搭建静态博客网站"
date: 2015-09-11 11:32:38 +0800
comments: true
categories: [Octopress]
tags: [octopress,博客搭建，seo]
keywords: seo, octopress, analytics, 博客搭建
description: Octopress搭建静态博客网站
---

###导语

>[Octopress](http://octopress.org/)是一个基于 Jekyll 的静态博客站点生成系统，它很大程度上简化了用 Jekyll 搭建博客的过程。  

###一、[Octopress](http://octopress.org/)的优势

命令行操作 纯文本写 博客定制性高 纯静态 版本化管理 迁移成本低 简洁的Ruby框架 [Markdown](http://www.markdown.cn/#overview)语法
<!-- more --> 

###二、搭建[Octopress](http://octopress.org/)博客需要了解的知识

* [Ruby](http://www.Mmyton.com)(其实会几个命令即可，后续会讲到)
* [Markdown](http://www.markdown.cn/#overview)语法
* [Github](http://www.github.com/)(部署博客用，会简单使用即可）
* [Git](http://www.Mmyton.com)(会一些简单的Git命令)

###三、准备工作

系统：本机系统是window8 64位，window7以上均可。下载以下软件<br/>
[Git](http://pan.baidu.com/s/1hrxiHdM) &nbsp;&nbsp;&nbsp;[Ruby](http://pan.baidu.com/s/1skr0Ewl)&nbsp;&nbsp;&nbsp;[DevKit](http://pan.baidu.com/s/1sjSymqL)&nbsp;&nbsp;&nbsp;[Python](http://www.python.org/ftp/python/2.7.5/python-2.7.5.msi)&nbsp;&nbsp;&nbsp;[Awesomium](http://pan.baidu.com/s/1ZExrw)&nbsp;&nbsp;&nbsp;[Markdownpad](http://pan.baidu.com/s/1skjZdPr)

* Git:版本管理工具，将代码托管到GitHub
* Ruby+DevKit：生成静态网页
* MarkdownPad：Window下Markdown语法编辑器
* Awesomium：实现MarkdownPad实时预览功能

###四、配置环境
####1.安装Git<br/>
  window下安装[Git](http://pan.baidu.com/s/1hrxiHdM)很简单，跟安装软件一样，一路next即可。安装好后在桌面点击右键,右键菜单中将包括以下几个选项：  
  {% img /images/1.jpg 150 150 %}  
  在进行接下去的配置之前，需要一个[Github](http://www.github.com/)账号，到相应的官网申请个[Github](http://www.github.com/)账号即可，记得验证注册时所用的邮箱。
  完成注册后，开始配置[Git](http://pan.baidu.com/s/1hrxiHdM)全局用户信息。单击桌面右键，在右键菜单中选择Git Bash。此时将跳出如下页面：  
  {% img /images/7.jpg 300 400 %}  
  在Git Bash中输入如下命令：  
```      
git config --global user.name "这里是你的Github账号" 
```   
  按回车结束，接着继续输入：  
```      
  git config --global user.email "这里是你的注册邮箱" 
```   
  同样按回车结束，接下开始设置与[Github](http://www.github.com/)进行数据交互的密钥(默认保存在C:\Users\Mmyton\.ssh下，其中Mmyton是我们本机的用户名)，在Git Bash输入如下命令：  
```  
  ssh-keygen -t rsa -C "这里是你的注册邮箱"   
``` 
  一直按回车直到结束即可（如果你是第一次输入上面这个命令，则在没输入命令之前，你在C:\Users\Mmyton下看不到.ssh文件夹），此时找到我们生成的密钥：  
  {% img /images/8.jpg 300 400 %}  
  打开id_rsa.pub,全选复制。浏览器打开你的[Github](http://www.github.com/)账号：点击右上角的头像：  
  {% img /images/9.png 100 100 %} {% img /images/10.jpg 400 400 %}    
  点击Add key即可。然后回到Git Bash验证我们的设置是否可行，输入如下命令,回车：  
```
  ssh -T git@github.com
```   
{% img /images/11.jpg 500 500 %}  
  如果出现以上画面，恭喜配置正确。  
####2.安装Ruby<br/>
  [Ruby](http://pan.baidu.com/s/1skr0Ewl)的安装也是一路next，不过有一个地方需要注意下：  
  {% img /images/6.jpg 300 400 %}       
####3.解压DevKit  
  解压[DevKit](http://pan.baidu.com/s/1sjSymqL)到和[Ruby](http://pan.baidu.com/s/1skr0Ewl)安装的同一盘下，如c盘，把安装路径改为C:\DevKit,然后解压即可，解压完后（为了把[Ruby](http://pan.baidu.com/s/1skr0Ewl)和[DevKit](http://pan.baidu.com/s/1sjSymqL)关联起来）进入到Devkit目录下，右键单击空白处，选择Git Bash，输入如下命令：  
```
ruby dk.rb init
```  
  回车，接着继续输入：   
```  
ruby dk.rb install
```  
{% img /images/12.jpg 500 500 %}  
出现如上画面表示配置成功。  
####4.安装Octopress以及安装依赖项
在桌面上单击右键选择Git Bash，输入如下命令：
```
git clone git://github.com/imathis/octopress.git octopress
cd octopress
```  
然后继续输入命令：  
```
gem install bundler
```  
由于国内网的问题，这个安装命令一般都会出错，所以我需要修改软件源，淘宝提供了很方便的软件源，只需按照如下命令修改默认软件源并移除之前的软件源即可：  
添加软件源      
```
gem sources -a http://ruby.taobao.org
```  
移除软件源      
```
gem sources -r http://rubygems.org
```  
接着修改[Octopress](http://octopress.org/)下的Gemfile文件：  
```  
source "https://rubygems.org"
```  
修改为     
```
source "https://ruby.taobao.org"(网上其他的攻略写的软件源有误)
```  
保存即可接着就可以安装bundler和bundler中的软件包  
```
gem install bundler
bundle install	
```
现在终于可以安装[Octopress](http://octopress.org/)的默认主题：
```
rake install
```
####5.生成并预览[Octopress](http://octopress.org/)博客
```
rake generate
rake preview
```
浏览器输入http://localhost:4000 	即可看到如下画面：  
{% img /images/2.png 500 500 %} 
      

  


