---
date: 2017-12-13 09:50:47+00:00
layout: post
title: 'Linux Memory'
categories: 技术
tags:  Linux
---

5 commands to check memory usage on Linux

# 1. Memory Usage


On linux, there are commands for almost everything, because the gui might not be always available. When working on servers only shell access is available and everything has to be done from these commands. So today we shall be checking the commands that can be used to check memory usage on a linux system. Memory include RAM and swap.


# 2. Free command
The free command is the most simple and easy to use command to check memory usage on linux. Here is a quick example
The m option displays all data in MBs. The total os 7976 MB is the total amount of RAM installed on the system, that is 8GB. The used column shows the amount of RAM that has been used by linux, in this case around 6.4 GB. The output is pretty self explanatory. The catch over here is the cached and buffers column. The second line tells that 4.6 GB is free. This is the free memory in first line added with the buffers and cached amount of memory.

Linux has the habit of caching lots of things for faster performance, so that memory can be freed and used if needed.
The last line is the swap memory, which in this case is lying entirely free.

```
free -m
```

# 3. /proc/meminfo

The next way to check memory usage is to read the /proc/meminfo file. Know that the /proc file system does not contain real files. They are rather virtual files that contain dynamic information about the kernel and the system.
```
cat /proc/meminfo
```

# 4. vmstat
The vmstat command with the s option, lays out the memory usage statistics much like the proc command. Here is an example

```
vmstat -s
```


# 5. Top
The top command is generally used to check memory and cpu usage per process. However it also reports total memory usage and can be used to monitor the total RAM usage. The header on output has the required information. Here is a sample output

Check the KiB Mem and KiB Swap lines on the header. They indicate total, used and free amounts of the memory. The buffer and cache information is present here too, like the free command.

# 6. Htop
Similar to the top command, the htop command also shows memory usage along with various other details.



# 7. RAM Information

To find out hardware information about the installed RAM, use the demidecode command. It reports lots of information about the installed RAM memory.

```
sudo dmidecode -t 17
# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0015, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0014
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: J1MY
        Bank Locator: CHAN A DIMM 0
        Type: DDR2
        Type Detail: Synchronous
        Speed: 667 MHz
        Manufacturer: 0xFF00000000000000
        Serial Number: 0xFFFFFFFF
        Asset Tag: Unknown
        Part Number: 0x524D32474235383443412D36344643FFFFFF
```		



