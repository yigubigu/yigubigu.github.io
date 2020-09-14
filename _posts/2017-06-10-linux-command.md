---
date: 2017-06-10 10:50:47+00:00
layout: post
title: 'Linux Commad'
categories: 技术
tags:  Linux Command
---

# 1. file
````
file DB_LINK.sql 
````

output
````
DB_LINK.sql: ASCII text, with CRLF line terminators

````

# 2. iconv
````
iconv -f cp936 -t utf-8 DB_LINK.sql -o DB_LINK_utf-8.sql
````

# 3. dos2unix

convert dos fromat to unix format
sudo apt-get install dos2unix -y

# 4. convert all files into anoter format under current folder
````
for file in *.sql; do
    iconv -f cp936 -t utf-8 "$file" -o "${file%}"
done
````


# 5. Background 

Before running the command, you can append & to the command line to run in the background:

```
long-running-command &

```

After starting a command, you can press CtrlZ to suspend it, and then bg to put it in the background:
```
long-running-command
[Ctrl+Z]
bg
```


# 6. Port 
netstat
netstat -tunlp 用于显示 tcp，udp 的端口和进程等相关情况。

netstat 查看端口占用语法格式：

```
netstat -tunlp | grep 端口号
```

- -t (tcp) 仅显示tcp相关选项
- -u (udp)仅显示udp相关选项
- -n 拒绝显示别名，能显示数字的全部转化为数字
- -l 仅列出在Listen(监听)的服务状态
- -p 显示建立相关链接的程序名


# 6. Search text content
```
find . -name "*.c" -print | xargs grep "main"
```

# 7. Seearch process

```
PID=$(ps -ef | grep tos.jar | grep -v grep | awk '{ print $2 }')
if [ -z "$PID" ]
then
    echo Application is already stopped
else
    echo kill $PID
    kill -9 $PID
fi

```

# 8 show process details

```
ps -p {pid} -lF
```

```
/proc/{PID} 
```

#9 信息摘要

```
sha256sum file.zip > file.sha256

sha256sum -c file.sha256  (注意：摘要的文件名与被校验的文件名要一致)

```
