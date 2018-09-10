---
title: GitBook 使用小结
date: 2018-08-09 18:58:36
tags: 记录小结
---
> 此小结是使用 GUI 的小结，不使用命令行。
GitBook 的使用和 GitHub 的使用非常相似，其客户端为 GitBook Editor。
以下用制作一本书从零到发布到 GitBook 全过程为例介绍怎样使用 GitBook。
我的 GitBook 主页：https://legacy.gitbook.com/@marlous

# 一 准备
1. 注册 GitBook，安装 GitBook Editor 并登陆。

2. 可以直接使用网页版创建并发布；可以在本地创建并在网页版创建后使用 Git HTTPS 将本地与远程仓库关联；可以远端创建后直接在 GitBook Editor 客户端中打开。
![网页版创建](图0.PNG)
![Git HTTPS](图1.PNG)

3. 注：title 下的路径即为本书面向公共的访问路径（直接访问本书内容）。本地客户端和网页版均无法输入中文的书名（title），在网页版的书主页设置中可更改为中文书名。
![更改为中文书名](图2.PNG)

# 二 使用
1. 在编辑中右上角 Publish 为发布。
![Publish 发布](图3.PNG)

2. 若发布失败可在书主页的 UPDATES 中按哈希选择重新发布。
![Restart this build](图4.PNG)