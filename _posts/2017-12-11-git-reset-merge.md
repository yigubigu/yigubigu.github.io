---
date: 2017-12-11 09:50:47+00:00
layout: post
title: 'git reset merge'
categories: 技术
tags:  git 
---

[git reset merge] (http://www.cnblogs.com/qinbb/p/5972308.html)


# 1. git命令在提交代码前，没有pull拉最新的代码，因此再次提交出现了冲突

error: You have not concluded your merge (MERGE_HEAD exists).
hint: Please, commit your changes before merging.
fatal: Exiting because of unfinished merge.


解决方法如下两种：

## 1.1. 保留你本地的修改

git merge --abort
git reset --merge

合并后记得一定要提交这个本地的合并（add-->commit-->push-->pull）

然后在获取线上仓库

git pull

## 1.2. down下线上代码版本,抛弃本地的修改

不建议这样做,但是如果你本地修改不大,或者自己有一份备份留存,可以直接用线上最新版本覆盖到本地
git fetch --all

git reset --hard origin/master

git fetch

# 2. 从git远程仓库中pull最新的代码，出现如下错误：Please commit your changes or stash them before you merge

解决方法如下：(git stash 可用来暂存当前正在进行的工作， 比如想pull 最新代码， 又不想加新commit， 或者另外一种情况，为了fix 一个紧急的bug,  先stash, 使返回到自己上一个commit, 改完bug之后再stash pop, 继续原来的工作。)

1: git stash //暂存代码

2: git pull  分支名//从远程仓库拉取最新代码

3: git stash pop //合并代码到本地仓库  此时代码是将暂存的代码和远程仓库的代码合并，如下图

4：这时候需要手动修改合并所需的代码即可。

5：git stash clear//需要清空git栈执行该命令


git stash: 备份当前的工作区的内容，从最近的一次提交中读取相关内容，让工作区保证和上次提交的内容一致。同时，将当前的工作区内容保存到Git栈中。
git stash pop: 从Git栈中读取最近一次保存的内容，恢复工作区的相关内容。由于可能存在多个Stash的内容，所以用栈来管理，pop会从最近的一个stash中读取内容并恢复。
git stash list: 显示Git栈内的所有备份，可以利用这个列表来决定从那个地方恢复。
git stash clear: 清空Git栈。此时使用gitg等图形化工具会发现，原来stash的哪些节点都消失了 

git push 报错，如下：