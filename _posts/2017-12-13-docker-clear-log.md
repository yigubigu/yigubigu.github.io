---
date: 2017-12-13 09:50:47+00:00
layout: post
title: 'Docker Clear Log '
categories: 技术
tags:  docker log
---

```
sudo sh -c "truncate -s 0 /var/lib/docker/containers/*/*-json.log"
```
