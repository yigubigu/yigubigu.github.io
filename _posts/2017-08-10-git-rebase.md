---
date: 2017-08-10 21:50:47+00:00
layout: post
title: 'git rebase'
categories: 技术
tags:  git rebase
---

当远程服务器有人check in，本地也有check in, 如果执行git pull,就会产生一个git merge, like: 'Merge branch 'master' of git.xxxx/tmp1'。
如何避免这个merge 呢？
git pull --base 而不是git pull。
这个可以让服务器上的commit 在本地先一步一步的执行，然后再把我们的改动apply上去。
注意，如果有冲突，会导致当前的代码留在某一个commit，需要手工解决冲突，然后commit。 


[git rebase](http://kernowsoul.com/blog/2012/06/20/4-ways-to-avoid-merge-commits-in-git/)
