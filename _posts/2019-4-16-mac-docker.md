---
date: 2019-4-16 18:50:47+00:00
layout: post
title: 'Mac Docker'
categories: Tech
tags:  docker 
---

# 1. Issue: docker no space left on device

[mac docker issue](https://forums.docker.com/t/no-space-left-on-device-error/10894)

```
sudo rm -rf ~/Library/Containers/com.docker.docker/Data/com.docker.driver.amd64-linux
```
Then restart docker

