---
title: Hexo 博客迁移重新部署
date: 2018-07-16 17:30:32
tags: 记录小结
---
> 把原来的博客重新迁移至新的计算机部署或恢复。
[参考博文](https://www.jianshu.com/p/ca87dd7b9e00)

# 一 备份
备份以下几个文件：
```
scaffolds（文章模版）
source（博客文章） 
themes（主题）
.gitignore（限定在 push 时那些文件可以忽略）
_config.yml（站点配置文件）
package.json（安装包的名称）

.ssh（密钥文件） // 可选，此文件不备份的话，如果新环境没配置 Git，在配置时需要重新生成新的密钥。
```

# 二 配置环境，安装 Hexo
1. 配置环境：
安装 Node.js 和 Git,配置 Git。若已安装略过此步。

2. 安装 Hexo：
在命令行 cmd 下操作。
```
进入新的博客文件夹目录下；

npm install -g hexo //安装 Hexo。

hexo init //初始化 Hexo。

npm install //安装依赖包。
```
3. 把备份的几个文件复制粘贴到博客文件夹，替换掉新的。

4. 安装自己博客需要的插件：
每个人需要的插件可能会不同，如图除红线外的全是默认安装好的插件，安装除默认外的插件。
需要安装哪些插件对比备份的 package.json 查看。

我的博客需要安装的：
```
npm install hexo-deployer-git --save

npm install hexo-asset-image --save
```
![package.json](图1.PNG)

# 三 生成并部署博客
```
git init //初始化本地仓库。

hexo g

hexo d
```