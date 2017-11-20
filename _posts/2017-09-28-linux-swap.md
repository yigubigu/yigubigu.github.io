---
date: 2017-09-28 09:50:47+00:00
layout: post
title: 'linux swap'
categories: 技术
tags:  linux swap
---
[Linux Swap](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)

```
 832  sudo swapon -s
  833  free -m
  834  sudo swapon -s
  835  df -h
  836  sudo swapon -s
  837  ls -lh /swapfile
  838  sudo dd if=/dev/zero of=/swapfile bs=1G count=4
  839  top
  840  sudo fallocate -l 4G /swapfile
  841  ls -lh /swapfile
  842  sudo chmod 600 /swapfile
  843  ls -lh /swapfile
  844  sudo mkswap /swapfile
  845  sudo swapon /swapfile
  846  sudo swapon -s
  847  free -m
  848  sudo vi /etc/fstab
  849  docker ps
```
