
---
date: 2018-7-16 09:50:47+00:00
layout: post
title: 'android sdk'
categories: 技术 
tags:  android
---

# Install SDK

## Download and Unzip SDK Tools
```
Download sdk-tools-linux-4333796.zip
unz
ip sdk-tools-linux-4333796.zip -d /usr/local/android/ 
```
## Set Env
```
ENV ANDROID_HOME=/usr/local/android
ENV PATH $ANDROID_HOME/tools/bin:$PATH
```

## Install Build Tools and Platforms
```
yes | sdkmanager  "build-tools;26.0.0"   --no_https --proxy=http --proxy_host=192.168.111.54 --proxy_port=8123 
```
## Install  Platforms
```
yes | sdkmanager  "platforms;android-23"   --no_https --proxy=http --proxy_host=192.168.111.54 --proxy_port=8123
```
## Install NDK
yes | sdkmanager "ndk-bundle" --no_https --proxy=http --proxy_host=192.168.111.54 --proxy_port=8123


