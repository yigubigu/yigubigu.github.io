---
date: 2017-06-19 09:50:47+00:00
layout: post
title: 'Linux 网络配置'
categories: 文档
tags:  Linux, network
---

#1 Ip Config
cat /etc/network/interfaces

#2 Restart Network Service 
Ubuntu Linux user use sudo command with above Debian Linux command:
````
# sudo /etc/init.d/networking restart
````

To start Linux network service:
````
# sudo /etc/init.d/networking start
````

To stop Linux network service:
````
# sudo /etc/init.d/networking stop
````
