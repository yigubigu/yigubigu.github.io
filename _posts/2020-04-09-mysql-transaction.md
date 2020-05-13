---
date: 2019-12-15
layout: post
title:   mysql transaction level
categories: Tech
tags:  mysql
---
access访问日志
tomcat中默认是有access访问日志的，用于记录访问者的IP，不过在spring boot中这个日志默认是关闭的。如果你的服务器结构中有nginx类的http服务器，access日志应该是在nginx中配置的。而tomcat这样的后台服务器只需要记录后台日志，不需要管access日志。如果想在spring boot中打开access日志，可以在application.properties中配置


#配置tomcat工作目录，为当前分区的tomcat目录
server.tomcat.basedir=/tomcat
#开启accesslog，会记录到上面的目录下
server.tomcat.accesslog.enabled=true
