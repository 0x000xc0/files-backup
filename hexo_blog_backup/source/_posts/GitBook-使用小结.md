---
title: GitBook 使用小结
date: 2018-08-09 18:58:36
tags: 记录小结
---
> 网页版使用教程：[参考博文](https://www.jianshu.com/p/4731abc562e7)
本地 GUI 使用教程：[参考博文](https://blog.csdn.net/duanbiren123/article/details/80190489)
本地命令行使用及生成 PDF 教程：[参考博文](https://www.jianshu.com/p/09a1cac0a0d0)
本地编译成 PDF 或其他格式：[参考博文](https://www.jianshu.com/p/d8286217b401)

# 一 网站与客户端生成
## 1 准备
1. 注册 GitBook，安装 GitBook Editor 并登陆。

2. 可以直接使用网页版创建并发布；可以在本地创建并在网页版创建后使用 Git HTTPS 将本地与远程仓库关联；可以远端创建后直接在 GitBook Editor 客户端中打开。
![网页版创建](图0.PNG)
![Git HTTPS](图1.PNG)

3. 注：title 下的路径即为本书面向公共的访问路径（直接访问本书内容）。本地客户端和网页版均无法输入中文的书名（title），在网页版的书主页设置中可更改为中文书名。
![更改为中文书名](图2.PNG)

## 2 使用
1. 在编辑中右上角 Publish 为发布。
![Publish 发布](图3.PNG)

2. 若发布失败可在书主页的 UPDATES 中按哈希选择重新发布。
![Restart this build](图4.PNG)

# 二 本地编译生成
## 1 安装、更新与卸载
- 安装环境：Node.js

- 安装 GitBook：`npm install -g gitbook-cli`

- 检查是否安装成功：`gitbook -V`

- 更新 GitBook：`gitbook update`

- 卸载 GitBook：`npm uninstall -g gitbook`

- 安装 GitBook Editor，用于图形化编辑文档。

- 安装 Calibre：用于生成 PDF（用到此软件的 ebook-convert）。配置环境变量，Calibre 安装目录，（Windows 下会自动配置好）。

## 2 编译
用 GitBook Editor 编写完成后。

- 命令行进入该书目录，Windows 下默认为 `C:\Users\UserX\GitBook\Library\Import\XXX`

- 预览测试：`gitbook serve`，浏览器打开 `http://localhost:4000`（control + c 停止）。

- 生成 PDF：`gitbook pdf`