---
title: 更加自动化的部署 Hexo 博客
date: 2019-01-10 17:03:32
tags: 记录小结
---
> 参考：
1、 [使用 netlify 托管静态网站](https://einverne.github.io/post/2018/03/netlify-to-host-static-website.html)
2、 [Hexo+Netlify快速搭建个人博客](https://blog.csdn.net/salsamaniac/article/details/81026739)
3、 [Github上搭建Hexo如何跨电脑写作部署方便?](https://segmentfault.com/q/1010000004593371)
4、 [快速搭建Hexo博客+webhook自动部署+全站HTTPS](https://www.jianshu.com/p/c5724c8d9e4c)
5、 [使用Travis CI持续部署Hexo博客](https://www.jianshu.com/p/5691815b81b6)

# 一 概述
## 1 三种方法
- 方法一，GitHub 仓库的 GitHub Pages：
不需要云服务器，但要本地搭建环境本地，本地生成博客内容（生成 public 文件夹中的文件），然后将此文件夹内容 git 到仓库。

- 方法二，GitHub（私有）仓库 + Netlify：
不需要云服务器，但要本地搭建环境，然后将除 public 文件夹的内容 git 到仓库即可（Netlify 从仓库中读文件帮你生成，然后部署在 Netlify 的服务器）。

- 方法三，GitHub（私有）仓库 + travis-ci + webhook：
需要自己购买云服务器。只需要本地写 Markdown 博文，然后 git 到仓库即可（云服务器搭建 Hexo、Web 服务环境；自动从仓库拉 Markdown 博文，然后生成后部署）。

- 小结：
三种方法依次更加自动化。
如果想完全自动化（并有自己的 VPS 和域名），最优选第三种方法；
否则选第一种方法；
第二种方法缺点在于只有 Netlify 提供给你的随机域名。

## 2 方法的差异
1. GitHub（私有）仓库 + Netlify：
微软收购了 GitHub 后，于这两天提供了 GitHub 私有仓库免费的服务。具体 plan 参见 [链接](https://github.com/pricing)。
Netlify 是一家专注于提供静态网站托管服务的公司；所以将博客内容存在 GitHub 私有仓库，然后用 Netlify 的服务提供服务器，来搭建自己的博客或静态网站，会提供一个域名，或绑定自己的域名。
这样即方便，也免去了自己购买维护云服务器的成本。

2. GitHub（私有）仓库 + travis-ci + webhook：
每次在本地更新了博客，push 到 github 上，还要去 VPS 再 git pull 一下，很麻烦，配置好 webhooks 就可以在 github 有 push 操作时，VPS 自动更新并部署博客。

## 3 一些概念
- Netlify 是一家专注于提供静态网站托管服务的公司，通过自己的内容分发网络，将提前建立好的静态页面呈献给访客，节约了加载的时间。 提供 CI 服务，能够将托管 GitHub，GitLab 等网站上的 Jekyll，Hexo，Hugo 等静态网站。能够绑定自定义域名，支持 SSL 证书。支持自动构建。 Netlify 会在每一次提交 commit 时自动编译部署静态网站。

- 一些静态网站生成器：Jekyll、Hugo、Gatsby、Hexo 等。

- 静态博客站点页面都是静态页面，访问时无需查询数据库。速度快、更安全。

# 二 详细步骤
## 1 方法二
参考：[Hexo+Netlify快速搭建个人博客](https://blog.csdn.net/salsamaniac/article/details/81026739)。

## 2 方法三
暂时未实践。