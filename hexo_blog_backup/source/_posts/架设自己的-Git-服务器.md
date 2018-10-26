---
title: 架设自己的 Git 服务器
date: 2018-10-17 20:04:43
tags: 版本控制
---
> 参考文档：[Git 文档](https://git-scm.com/book/zh/v1/%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8A%E7%9A%84-Git-%E5%8D%8F%E8%AE%AE)

# 一 搭建服务器
> [参考文章](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137583770360579bc4b458f044ce7afed3df579123eca000)

远程仓库与本地仓库概念完全相同。

- 安装 git：`sudo apt-get install git`

- 可以创建一个用来运行 git 服务的用户：`sudo adduser git`

- 将需要登陆的用户公钥（id_rsa.pub 文件）导入 `/home/git/.ssh/authorized_keys`，一行一个。

- 新建一个文件夹作为仓库，服务器上的通常都以 .git 结尾，在此文件夹内命令：
```
# 创建一个裸仓库
sudo git init --bare example.git

# 修改仓库 example.git 目录所属用户为 git，用户组为 git。
sudo chown -R git:git example.git
```

- 创建的 git 用户不允许登陆 shell：修改 `/etc/passwd`
```
将
git:x:1001:1001:,,,:/home/git:/bin/bash

改为
git:x:1001:1001:,,,:/home/git:/usr/bin/git-shell
```

- 补充：克隆仓库 `git clone git@server:/srv/example.git`。

# 二 公钥管理、权限控制
> 可以使用 Gitosis。
[官方文档](https://git-scm.com/book/en/v1/Git-on-the-Server-Gitosis)
Gitosis 使用指南参考：[参考博文](https://www.jianshu.com/p/2ebd208975cd)

Gitosis 是一套用来管理 authorized_keys 文件和实现简单连接限制的脚本。
管理一个特殊的 Git 仓库，在这个特殊仓库内做好相应的设定，然后推送到服务器上，Gitosis 就会随之改变运行策略。