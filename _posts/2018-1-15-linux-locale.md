
---
date: 2018-1-15 09:50:47+00:00
layout: post
title: 'Linux Locale'
categories: 技术
tags:  Linux
---

```
sudo locale-gen "en_US.UTF-8"
sudo dpkg-reconfigure locales
sudo vim /etc/default/locale
```
Add at the end of file
```
LC_ALL="en_US.UTF-8"
```
