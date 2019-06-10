---
date: 2019-6-10 18:50:47+00:00
layout: post
title: linux
categories: shell
tags:  shell
---

# How to rename file under a folder in batch

```
 for file in *.pic; do mv "$file" "${file%.pic}.jpeg";done
```
