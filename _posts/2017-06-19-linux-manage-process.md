---
date: 2017-06-19 09:50:47+00:00
layout: post
title: 'Linux manage process'
categories: 文档
tags:  Linux
---

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