---
date: 2017-08-25 09:50:47+00:00
layout: post
title: 'Linux Public Key ssh '
categories: 文档
tags:  'Linux'
---

使用一种被称为"公私钥"认证的方式来进行ssh登录. "公私钥"认证方式简单的解释:首先在客户端上创建一对公私钥 （公钥文件：~/.ssh/id_rsa.pub； 私钥文件：~/.ssh/id_rsa）
然后把公钥放到服务器上（~/.ssh/authorized_keys）, 自己保留好私钥.在使用ssh登录时,ssh程序会发送私钥去和服务器上的公钥做匹配.如果匹配成功就可以登录了

#1本地 

先要在本地生成一个 rsa 的公共key .然后 copy 到远程你要认证的服务器创建 key
ssh-keygen -t rsa
这里会提示输入密码，（这个密码与与远程ssh登入密码无关）

#2 将公钥文件复制到authorized_keys

cat id_rsa.pub >> ~/.ssh/authorized_keys

#3 Nnable public key login

需要检查sshd服务的Pubkey认证功能是否默认打开
/etc/ssh/sshd_config

```
PubkeyAuthentication yes           
```

#4 Disable password login

```
PasswordAuthentication no
```

如果修改后记的要重起你的ssh服务,用ssh –v来显示详细的登陆过程.

#5 Restart SSH
sudo service ssh restart 

