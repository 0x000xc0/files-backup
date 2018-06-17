---
title: Git Tips
date: 2018-06-13 00:46:09
tags: Git
---
# 本地仓库与远程已存在仓库同步
三种情况：
本地存在仓库，远程没有。//可将本地 push 到远程。
远程存在仓库，本地没有。//可将远程仓库 clone 到本地。
本地已存在仓库，远程已存在仓库做关联。//先将两仓库关联，将远程仓库内容 pull 到本地，解决冲突合并后 push 到远程仓库。

第三种:
1.先将两仓库关联，命令 `git remote add origin [远程仓库地址]` 。

2.将远程仓库内容 pull 到本地，`命令 git pull origin master` 。

3.解决问题后推送，命令 `git push -u origin master` 。

注意：出现电子邮箱设置为 private 而无法 push，则可参考如下：
github 网站电子邮件设置中这一选项不打勾。
![图1 电子邮箱设置](图1.png)

# 更改仓库用户名邮箱
见图，以及链接 [主题文档教程](https://help.github.com/articles/setting-your-commit-email-address-in-git/)
![图2 电子邮箱设置](图2.png)

# SSH 与 Public Key
用 SSH 和 Github 服务器链接，如链接不上，注意本机 Public Key 是否有问题，若有问题可生成新的 Public Key。

在 git bash 中使用命令 `ssh-keygen -t rsa` 生成。
![图2 生成Public Key](图3.png)

Id_rsa.pub 内容编辑器打开复制粘贴到 Github 网站。
![图4 添加Public Key](图4.png)

用命令 `ssh -T git@github.com` 验证是否成功。