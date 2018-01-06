
---
date: 2018-1-6 09:50:47+00:00
layout: post
title: 'Linux Sudo NoPassword'
categories: 技术
tags:  Linux
---

```
sudo visudo
```
And add a line like:

```
alct ALL=(ALL) NOPASSWD: ALL
```
At the end.

