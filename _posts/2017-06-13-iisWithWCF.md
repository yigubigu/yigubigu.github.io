---
date: 2017-06-13 17:22:47+00:00
layout: post
title: 'dotnet'
categories: 文档
tags:  iis-wcf
---

#1 安装IIS
"Control Panel" -> "启用或关闭Windows功能"

![](../assets/iis-install.png)

Dotnet Advandced Feature

![](../assets/dotnet-advanced.png)


#2 配置IIS

##2.1 Create Site

Control Panel-> 管理工具 -> "Internet Information Services (IIS)管理器"

#2.2 网站绑定要支持net.tcp

![](../assets/website-port.png) 
#2.3 应用需启用net.tcp支持

![](../assets/app-enable-net.tcp.png) 


