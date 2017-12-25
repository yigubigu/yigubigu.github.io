---
date: 2017-12-22 09:50:47+00:00
layout: post
title: 'Linux Pefformance'
categories: 技术
tags:  Linux Performance
---

# 1. Sysctl Parameter
```
sudo sysctl -w net.ipv4.tcp_max_syn_backlog=10240

```
# 2. /etc/sysctl.conf文件

/etc/sysctl.conf是一个允许你改变正在运行中的Linux系统的接口。它包含一些TCP/IP堆栈和虚拟内存系统的高级选项，
可用来控制Linux网络配置，由于/proc/sys/net目录内容的临时性，建议把TCPIP参数的修改添加到/etc/sysctl.conf文件, 然后保存文件，
使用命令“/sbin/sysctl –p”使之立即生效。具体修改方案参照上文：

net.core.somaxconn

# 3. sysctl parameter

![](../assets/linux-performance-1.jpg)