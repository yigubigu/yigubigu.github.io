
---
date: 2018-3-27 09:50:47+00:00
layout: post
title: 'Linux Locale'
categories: 技术
tags:  Linux  
---

# Locale Issue

## Command Line
```
export LC_ALL="en_US.UTF-8"

```


## Config file

/etc/default/locale

```
LC_CTYPE="en_US.UTF-8"
LC_ALL="en_US.UTF-8"
LANG="en_US.UTF-8"
```