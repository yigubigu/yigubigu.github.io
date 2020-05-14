---
date: 2020-5-14
layout: post
title:   Manage Jenkins ssh for git 
categories: Tech
tags:  Jenkins
---

以前在jenkins中配置ssh key，好像很麻烦，内心一直很抗拒，一般都是用username/passowrd 模式。这次用git.code.tencent.com,没有用户名/密码了，被迫使用ssh key。重新试了一下，发现非常简单。

# Generate ssh key
```
ssh-keygen -t rsa
```

# Add ssh public key in git account 
```
cat ~/.ssh/id_rsa.pub
```

# Add ssh private key into jenkins 

```
cat ~/.ssh/id_rsa
```

Go to jenkins home ->凭据 -> 全局  -> 添加凭据 

选择类型 SSH Username with private key

Input username just as your like, input Private key from clipboard

# Create task to verify credentials 
