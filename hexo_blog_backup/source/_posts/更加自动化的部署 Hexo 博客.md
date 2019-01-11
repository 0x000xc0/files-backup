---
title: 更加自动化的部署 Hexo 博客
date: 2019-01-10 17:03:32
tags: 记录小结
---
> 参考：
1、 [使用 netlify 托管静态网站](https://einverne.github.io/post/2018/03/netlify-to-host-static-website.html)
2、 [Hexo+Netlify快速搭建个人博客](https://blog.csdn.net/salsamaniac/article/details/81026739)
3、 [A Step-by-Step Guide: Hexo on Netlify](https://www.netlify.com/blog/2015/10/26/a-step-by-step-guide-hexo-on-netlify/)
4、 [Github上搭建Hexo如何跨电脑写作部署方便?](https://segmentfault.com/q/1010000004593371)
5、 [快速搭建Hexo博客+webhook自动部署+全站HTTPS](https://www.jianshu.com/p/c5724c8d9e4c)
6、 [使用Travis CI持续部署Hexo博客](https://www.jianshu.com/p/5691815b81b6)
7、 [使用 Travis 自动部署 Hexo 到 Github 与 自己的服务器](https://segmentfault.com/a/1190000009054888)
8、 [手把手教你使用Travis CI自动部署你的Hexo博客到Github上](https://blog.csdn.net/woblog/article/details/51319364)
9、 [使用 CircleCI 2.0 进行持续集成/持续部署](https://www.jianshu.com/p/36af6af74dfc)

# 一 概述
## 1 四种方法
- 方法一，GitHub 仓库的 GitHub Pages：
不需要云服务器，但要本地搭建环境，本地生成博客内容（生成 public 文件夹中的文件），然后将此文件夹内容 git 到仓库（hexo g 命令自动部署）。

- 方法二，GitHub（私有）仓库 + Netlify：
不需要云服务器，但要本地搭建环境，然后将除 public 文件夹的内容 git 到仓库即可（Netlify 从仓库中读文件帮你生成，然后部署在 Netlify 的服务器）。

- 方法三，GitHub 仓库 + travis-ci/CircleCI：
不需要云服务器，但要本地搭建环境，然后将除 public 文件夹的内容 git 到仓库（GitHub Pages 的仓库开两个分支）即可；CI 服务只是帮你使用源文件来构建和部署到 GitHub Pages 或自己的服务器。类似方法二。

- 方法四，GitHub（私有）仓库 + webhook + VPS：
需要自己购买云服务器。只需要本地写 Markdown 博文，然后 git 到仓库即可（云服务器搭建 Hexo、Web 服务环境；触发 webhook，VPS 自动从仓库拉 Markdown 博文，然后在 VPS 上生成、部署）。

## 2 方法小结
- 方法一、方法二和三、方法四，依次更加自动化。

- 如果想完全自动化（并有自己的 VPS 和域名），最优选第四种方法，方法四相当于触发 webhook 后在自己的 VPS 上完成了 travis-ci/CircleCI 提供的构建和部署服务，并且可以不需要在本地搭建 Hexo 环境。

- 否则选第一种方法。

- 第二和三种方法缺点在于仅仅只是帮你构建部署而已。环境还要依赖本地搭建的，和用批处理差别不是很大，只是省了十几秒构建部署时间。

## 3 方法的差异
1. GitHub（私有）仓库 + Netlify：
微软收购了 GitHub 后，于这两天提供了 GitHub 私有仓库免费的服务。具体 plan 参见 [链接](https://github.com/pricing)。
Netlify 是一家专注于提供静态网站托管服务的公司；所以将博客内容存在 GitHub 私有仓库，然后用 Netlify 的服务提供服务器，来搭建自己的博客或静态网站，会提供一个域名，或绑定自己的域名。
这样即方便，也免去了自己购买维护云服务器的成本。

2. GitHub（私有）仓库 + webhook + VPS：
每次在本地更新了博客，push 到 github 上，还要去 VPS 再 git pull 一下，很麻烦，配置好 webhooks 就可以在 github 有 push 操作时，VPS 自动更新并部署博客。

## 4 一些概念
- Netlify 是一家专注于提供静态网站托管服务的公司，通过自己的内容分发网络，将提前建立好的静态页面呈献给访客，节约了加载的时间。 提供 CI 服务，能够将托管 GitHub，GitLab 等网站上的 Jekyll，Hexo，Hugo 等静态网站。能够绑定自定义域名，支持 SSL 证书。支持自动构建。 Netlify 会在每一次提交 commit 时自动编译部署静态网站。

- 一些静态网站生成器：Jekyll、Hugo、Gatsby、Hexo 等。

- 静态博客站点页面都是静态页面，访问时无需查询数据库。速度快、更安全。

# 二 详细步骤
## 1 方法一
见博文《Hexo 踩坑记》。

## 2 方法二
参考：[Hexo+Netlify快速搭建个人博客](https://blog.csdn.net/salsamaniac/article/details/81026739)。

## 3 方法三
参考：[使用 Travis 自动部署 Hexo 到 Github 与 自己的服务器](https://segmentfault.com/a/1190000009054888)。

## 4 方法四
参考：[快速搭建Hexo博客+webhook自动部署+全站HTTPS](https://www.jianshu.com/p/c5724c8d9e4c)。