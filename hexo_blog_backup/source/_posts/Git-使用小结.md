---
title: Git 使用小结
date: 2018-06-13 00:43:46
tags: Git
---
# 概述 Github flow
1.创建一个新分支。
同一时刻多个想法，创建分支来进行管理。

2.添加新版本。
不断做新功能出来。

3.开启一个 pull request
发起对做的各个版本的讨论，代码审核。

4.合并分支，然后部署。
大家审核了 pull request并通过测试，后合并到主分支上。

# 具体核心流程
教程：[参考教程](http://blog.jobbole.com/76867/)
![图1 具体流程](图1.png)
master 分支作为中央仓库主分支，并且功能分支不是从 master 分支上拉出新分支，而是使用 develop 分支作为父分支。

一旦 develop 分支上有了做一次发布（或者说快到了既定的发布日）的足够功能，就从 develop 分支上 fork 一个发布分支，即 release。新建的分支用于开始发布循环，所以从这个时间点开始之后新的功能不能再加到这个分支上,这个分支只应该做 Bug 修复、文档生成和其它面向发布任务。一旦对外发布的工作都完成了，发布分支合并到 master 分支并分配一个版本号打好Tag。另外，这些从新建发布分支以来的做的修改要合并回 develop 分支。

预发布分支命名: release-

维护分支或说是热修复（hotfix）分支用于生成快速给产品发布版本（production releases）打补丁，这是唯一可以直接从 master 分支 fork 出来的分支。修复完成，修改应该马上合并回 master 分支和 develop 分支（当前的发布分支），master 分支应该用新的版本号打好Tag。

# Pull Request 完整流程图
![图1 Pull Request 完整流程图](图2.png)