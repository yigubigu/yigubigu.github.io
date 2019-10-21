---
date: 2019-6-10 18:50:47+00:00
layout: post
title: Windows Virtual Machine Setting
categories: virtual machine
tags:  windows 
---

# Create new virtual machine
## Create new virtual machine
 Do not specify disk

## Copy base image to new virtual machine
Copy from browser 

## Attach the copied file to new virutla machine 
Change configuration from UI to attach existing disk 

## Run systemprepare command
go to command line
go to c:\windows\system32\sysprep, and execute sysprep.exe

[Sysprep](https://www.sysgeek.cn/windows-10-sysprep/)

# Control Panel

## Enable remote access
Control Panel -> System and Security -> System -> Allow remote access

## Find IP

Command line -> ipconfig
## Turn Offline Windows Firewall

Control Panel -> System and Security -> Windows Firewall

Note: remote access is also blocked by Windows Firewall default

## Change computer name
Control Panel -> System and Security ->System -> See name of this computer

## Turn off windows update
Control Panel -> System and Security -> Windows update

## Update Esxi config

Update the virtual machine name to attach IP.


## Check remote computer name by IP
```
nbtstat -a 192.168.109.104
```

## Check network 
```
tracert 192.168.109.104
```

## Check remote computer ip by name 
```
nslookup qa-wp-web
ping -4 qa-wp-app
```

## Firwaall

```
New-NetFirewallRule -Protocol TCP -LocalPort 22 -Direction Inbound -Action Allow -DisplayName SSH
```
