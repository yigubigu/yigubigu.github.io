
---
date: 2018-1-23 09:50:47+00:00
layout: post
title: 'Mysql Global Variable'
categories: 技术
tags:  Mysql MaxConnection
---

max connection 是mysql的global 变量， 可以查看变量
```
SHOW WARNINGS;
show variables like "max_connections";
```

如果要设置max connections, 修改 mysqld.cnf
```
sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
```
Add 
```
max_connections=1000
```

max connection变量受到系统的open_files_limit 限制，因为是service，可以修改sysctl 变量来increase open files。如果

```
sudo vi /etc/sysctl.conf
```
Add

```
fs.file-max=34166
```




