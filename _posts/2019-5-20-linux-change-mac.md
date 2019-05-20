---
date: 2019-4-26 18:50:47+00:00
layout: post
title: Linux Change Mac
categories: Tech
tags:  Linux
---
# Find the HWaddr to be changed

```
ifcofnig
```
The output looks like below. In the below, the "enp1s0" is the Mac driver name we want to change.

```
br-7cfd0e9c73bf Link encap:Ethernet  HWaddr 02:42:2a:e5:35:1b
          inet addr:172.21.0.1  Bcast:172.21.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

br-beed478b426d Link encap:Ethernet  HWaddr 02:42:b9:1c:ac:c7
          inet addr:172.18.0.1  Bcast:172.18.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

br-e3092e796f34 Link encap:Ethernet  HWaddr 02:42:1d:31:06:1b
          inet addr:172.19.0.1  Bcast:172.19.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

docker0   Link encap:Ethernet  HWaddr 02:42:b5:27:7c:09
          inet addr:172.17.0.1  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp1s0    Link encap:Ethernet  HWaddr 02:43:b7:c9:f1:c0
          inet addr:192.168.109.98  Bcast:192.168.109.255  Mask:255.255.255.0
          inet6 addr: fe80::43fb:8d78:ad2d:2635/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:111054 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22412879 (22.4 MB)  TX bytes:188768 (188.7 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:931 errors:0 dropped:0 overruns:0 frame:0
          TX packets:931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:83409 (83.4 KB)  TX bytes:83409 (83.4 KB)

```

# Change enp1s0 HWddrr 

```
sudo /sbin/ifconfig enp1s0 down
sudo /sbin/ifconfig  enp1s0 hw ether 02:43:b7:c9:f1:c0
sudo /sbin/ifconfig enp1s0 up
```
