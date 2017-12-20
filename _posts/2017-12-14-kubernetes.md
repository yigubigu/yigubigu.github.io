---
date: 2017-12-20 10:50:47+00:00
layout: post
title: 'Kuberneters Tch'
categories: 技术
tags:  Kuberneters Network DNS
---

# 1. 如何测试
[how to verify dns work or not] (https://kubernetes.io/docs/tasks/administer-cluster/dns-custom-nameservers/)

# 2. 如何修改dns
在腾讯云容器服务上添加自定义dns服务器操作步骤

*1 将kube-dns的yaml文件保存下来
```
kubectl get deployment kube-dns -n kube-system -o yaml > kubedns.yaml
```

*2 修改kubedns.yaml文件，找到kube-dnsmasq-amd64的镜像位置，在其启动参数中做修改,原来的参数如下：
- args: - --cache-size=500 - --no-resolv - --server=127.0.0.1#10053 - --log-facility=-
如果这个时候要添加2个外部的dns服务器，对应的yaml文件修改如下，修改内容就是加了两个--server的启动参数:
- args: - --cache-size=500 - --no-resolv - --server=127.0.0.1#10053 - --server=/internal.thekelleys.org.uk/192.168.1.1 - --server=/google.com/192.168.2.1 - --log-facility=-
如果这时需要添加主机名和IP的对应关系，可以通过添加--address参数实现：
- args: - --cache-size=500 - --no-resolv - --server=127.0.0.1#10053 - --address=/www.test1.com/192.168.10.2 - --server=/www.test2.com/192.168.10.3 - --log-facility=-

*3 使用修改后的yaml文件执行kubectl apply使配置生效
```
kubectl apply -f kubedns.yaml
```

4、验证添加的自定义dns服务器是否在容器里生效，验证方法有很多种，可以通过在服务里使用dig或nslookup命令来看；也可以直接通过某个依赖于该自定义dns的应用服务来验证。