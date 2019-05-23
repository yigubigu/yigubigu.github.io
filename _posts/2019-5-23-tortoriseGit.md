---
date: 2019-5-23 18:50:47+00:00
layout: post
title: TortoiseGit 
categories: Tech
tags:  Tool
---
# TortoiseGit密钥的配置


TortoiseGit使用扩展名为ppk的密钥，而不是ssh-keygen生成的rsa密钥。也就是说使用ssh-keygen -t rsa -C "yourname@yourcompany.com"产生的密钥在TortoiseGit中不能用。而基于github的开发必须要用到rsa密钥，因此需要用到TortoiseGit的putty key generator工具来生成既适用于github的rsa密钥也适用于TortoiseGit的ppk密钥，配置步骤如下：

* 1 运行TortoiseGit开始菜单中的Puttygen程序
* 2 Click "Load" button to load an existing private key file
* 3 Load the ssh-keygen生产的rsa 私钥，如 c:\users\abc\.ssh\id_rsa
* 4 点击“Save private key”按钮,将生成的key保存为适用于TortoiseGit的私钥（扩展名为.ppk）
* 5 运行TortoiseGit开始菜单中的Pageant程序，程序启动后将自动停靠在任务栏中，双击该图标，弹出key管理列表
* 6 点击“Add Key”按钮，将第4步保存的ppk私钥添加进来，关闭对话框即可
