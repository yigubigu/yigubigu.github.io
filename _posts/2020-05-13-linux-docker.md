---
date: 2019-12-15
layout: post
title:   Linux  
categories: Tech
tags:  Linux
---

* How to show groups of
```
cat /etc/groups

```
* Add current user to given group

```
sudo gpasswd -a $USER docker     #将登陆用户加入到docker用户组中
newgrp docker     #更新用户组
```

