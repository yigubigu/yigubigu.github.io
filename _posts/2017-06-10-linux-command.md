---
date: 2017-06-10 10:50:47+00:00
layout: post
title: 'Linux Commad'
categories: 文档
tags:  Linux Command
---

#1 file
````
file DB_LINK.sql 
````

output
````
DB_LINK.sql: ASCII text, with CRLF line terminators

````

#2 iconv
````
iconv -f cp936 -t utf-8 DB_LINK.sql -o DB_LINK_utf-8.sql
````

#3 dos2unix

convert dos fromat to unix format
sudo apt-get install dos2unix -y

#4 convert all files into anoter format under current folder
````
for file in *.sql; do
    iconv -f cp936 -t utf-8 "$file" -o "${file%}"
done
````


