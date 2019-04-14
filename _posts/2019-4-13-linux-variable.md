---
date: 2019-4-13 18:50:47+00:00
layout: post
title: 'Linux Variable'
categories: Tech
tags:  Linux
---

# 1. Install for Single User

* Check if JAVA_HOME is already set 

````
echo $JAVA_HOME
````

If response is empty, then JAVA_HOME is not set.

* Set Variable

```
vi ~/.bashrc OR vi ~/.bash_profile
```

Add 
```
export JAVA_HOME=/usr/java/jre1.6.0_04
```
Save file

* Reload profile 

source ~/.bashrc OR source ~/.bash_profile



# 2 Install for all users 

Login as root or execute commands with sudo

Execute command
```
Execute: vi /etc/bashrc OR vi /etc/profile
```
Add 
```
export JAVA_HOME=/usr/java/jre1.6.0_04
```
Save file