---
date: 2017-06-19 09:50:47+00:00
layout: post
title: '用户帐号管理'
categories: 文档
tags:  Linux
---

# 1 帐号系统概述
# 1.1 用户账户

超级用户：root，默认的超级用户帐号，拥有至高无上的权限，一般系统安装的时候会设置管理员账号，管理员本身是普通用户，可以通过在命令前添加sudo关键字把执行权限提升为root；

普通用户：由管理员创建，拥有权限受到限制，一般在自己家目录权限最高；

程序用户：安装应用的时候，添加一些特定低权限账户，不允许登录到系统，仅用于特定应用。
## 1.2 组帐号

基本组：每一个用户帐号至少属于一个组，这个组为这个用户的基本组

附加组：如果用户帐号包涵基本组同时还包括其它的组，这些组为这个用户的附加组
## 1.3 UID、GID

UID：用户标识号
GID：组标识号

# 2 用户帐号

## 2.1 /etc/passwd
保存用户名称、用户家目录、登录shell，使用“：”分隔配置字段，所有用户可以访问，只有root可以修改。

````
vagrant@vagrant-ubuntu-trusty-64:~$ head /etc/passwd         //查看文件的前面10行内容
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
vagrant@vagrant-ubuntu-trusty-64:~$ 
````

注意：

* 第一字段：用户帐号名称
* 第二字段：密码（经过加密的）、占位符号x
* 第三字段：UID
* 第四字段：GID
* 第五字段：全名
* 第六字段：家目录
* 第七字段：登录shell

## 2.2 /etc/shadow
密码，帐号有效期，只用root可以读取信息，不许直接修改。

````
vagrant@vagrant-ubuntu-trusty-64:~$ sudo head /etc/shadow
[sudo] password for liu: 
root:!:16969:0:99999:7:::
daemon:*:16289:0:99999:7:::
bin:*:16289:0:99999:7:::
sys:*:16289:0:99999:7:::
sync:*:16289:0:99999:7:::
games:*:16289:0:99999:7:::
man:*:16289:0:99999:7:::
lp:*:16289:0:99999:7:::
mail:*:16289:0:99999:7:::
news:*:16289:0:99999:7:::
vagrant@vagrant-ubuntu-trusty-64:~$ 
````

注意：

* 第一字段：用户帐号名称
* 第二字段：MD5加密的密码信息
* 第三字段：........

## 2.3 命令
### 2.3.1 useradd
````
vagrant@vagrant-ubuntu-trusty-64:~$ sudo useradd test_usr     //添加用户test_usr
vagrant@vagrant-ubuntu-trusty-64:~$ tail -1 /etc/passwd       //查看文件最后一行
test_usr:x:1001:1001::/home/test_usr:/bin/sh
vagrant@vagrant-ubuntu-trusty-64:~$ sudo tail -1 /etc/shadow
test_usr:!:17013:0:99999:7:::
vagrant@vagrant-ubuntu-trusty-64:~$ tail -1 /etc/group
test_usr:x:1001:
vagrant@vagrant-ubuntu-trusty-64:~$ sudo tail -1 /etc/gshadow
test_usr:!::
vagrant@vagrant-ubuntu-trusty-64:~$ 
````

### 2.3.2  passwd
````
vagrant@vagrant-ubuntu-trusty-64:~$ sudo passwd test_usr         //修改用户密码
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
vagrant@vagrant-ubuntu-trusty-64:~$ sudo tail -1 /etc/shadow    //经过加密后的用户密码
test_usr:$6$oqADA8ut$6JrHpOaaT2pOUmemYisfkJdFaSgL.FhG0mFJb/yrf6Lizz73iB2l8cFxUQCTgh996LYgjWmi5yJC5ckD3Pzar0:17013:0:99999:7:::
vagrant@vagrant-ubuntu-trusty-64:~$ 
````

### 2.3.3 usermod
````
例：修改用户test_usr的UID
vagrant@vagrant-ubuntu-trusty-64:~$ id test_usr               
uid=1001(test_usr) gid=1001(test_usr) groups=1001(test_usr)
vagrant@vagrant-ubuntu-trusty-64:~$ usermod -u 1010 test_usr  //liu没有权限修改test_usr
usermod: cannot lock /etc/passwd; try again later.
vagrant@vagrant-ubuntu-trusty-64:~$ sudo usermod -u 1010 test_usr //修改test_usr的uid为1010
vagrant@vagrant-ubuntu-trusty-64:~$ id test_usr
uid=1010(test_usr) gid=1001(test_usr) groups=1001(test_usr)
vagrant@vagrant-ubuntu-trusty-64:~$ 
````

### 2.3.4 userdel
````
vagrant@vagrant-ubuntu-trusty-64:~$ userdel -r test_usr    //liu用户没有权限删除
userdel: cannot lock /etc/passwd; try again later.
vagrant@vagrant-ubuntu-trusty-64:~$ sudo userdel -r test_usr//删除用户
userdel: test_usr home directory (/home/test_usr) not found
vagrant@vagrant-ubuntu-trusty-64:~$ id test_usr
id: test_usr: No such user
vagrant@vagrant-ubuntu-trusty-64:~$ 
````

## 2.4 用户帐号初始配置文件
家目录下：

* bash_profile：每次登录执行
* bashrc：每次加载bash执行（包含登录）
* bash_logout：用户每次退出登录执行

# 3 组帐号管理
#3.1 组帐号文件
#3.1.1 /etc/group：保存组帐号名称、GID、组成员等

````
vagrant@vagrant-ubuntu-trusty-64:~$ sudo tail  /etc/group
avahi-autoipd:x:117:
avahi:x:118:
pulse:x:119:
pulse-access:x:120:
utempter:x:121:
rtkit:x:122:
saned:x:123:
````

#3.1.2 /etc/gshadow 保存组帐号的加密密码
````
vagrant@vagrant-ubuntu-trusty-64:~$ sudo tail /etc/gshadow
avahi-autoipd:!::
avahi:!::
pulse:!::
pulse-access:!::
utempter:!::
rtkit:!::
saned:!::
liu:!::
sambashare:!::liu
test_usr:!::
vagrant@vagrant-ubuntu-trusty-64:~$
````

#3.2 命令
#3.2.1 groupadd 添加一个组帐号


#3.2.2 groupwd 设置组帐号密码


#3.2.3 groups 查看用户属于哪个组

groups   用户名

#3.3.3 who,w 查看当前登录到本机的用户帐号详细信息
````
who 
w
````

#3.3.4 users 查看用户帐号详细信息





