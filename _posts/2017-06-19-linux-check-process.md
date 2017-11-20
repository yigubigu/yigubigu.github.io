---
date: 2017-06-19 09:50:47+00:00
layout: post
title: 'Linux 查看process'
categories: 技术
tags:  Linux
---

## 静态
### ps / ps aux
当前的进程

### pstree
当前的进程树

### pgrep
ps | grep


## 动态

### top
* p - 按cpu排序
* m - 按memory排序
* k - kill process


# 1启动

### 1.1前台
man ls
### 1.2后台
man ls &

# 2前后台
## 查看后台
jobs -l
## 把后台放到前台
fg 

# 3终止
## by Id
kill 
## by Proce Name 
man ls &
killall  -9 man