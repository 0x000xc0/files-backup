---
title: Hexo 踩坑记
date: 2018-06-12 03:33:30
tags: 记录小结
---
# 一 安装
配置环境，安装 hexo，初始化，安装一些依赖包。完成基础配置，无论换不换主题，按照文档也不会有太大问题。（此文使用的是 Anisina 主题，[主题文档教程](https://haojen.github.io/2017/05/09/Anisina-%E4%B8%AD%E6%96%87%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B/)）

# 二 问题一之博文插入图片
1. 博文插入图片配置：[参考博文](http://etrd.org/2017/01/23/hexo%E4%B8%AD%E5%AE%8C%E7%BE%8E%E6%8F%92%E5%85%A5%E6%9C%AC%E5%9C%B0%E5%9B%BE%E7%89%87/)
Hexo的配置文件_config.yml，设置为 `post_asset_folder: true` ；

2. 安装图片路径转换的插件，`npm install https://github.com/CodeFalling/hexo-asset-image --save` ，其插件存放于 `\node_modules\hexo-asset-image` 

3. 注意图片与 html 页面同目录引入图片的 Markdown 格式为 `![图1 改导航栏生成路径代码](图1.PNG)`，路径怎么写要看最后生成的静态博客目录结构。

# 三 问题二之导航菜单添加
坑来了。（非默认主题）
1. 在配置 works 导航栏时，用命令 `hexo new page “works”` 中因为 “work” 。在 source 文件夹下对应的 index.md 记得设置 layout 为 works，用对应的模版进行渲染。具体见 themes 文件夹对应主题的模版文件（layout 文件夹）。

2. 在配置 about 导航栏时，先将 themes 中对应主题的 about 模版内容改成自己的，然后 `hexo new page “about”`，改 layout。最后 `hexo clear && hexo generate && hexo deploy`，结束。

# 四 问题三之导航菜单文件夹小大写
在配置 about 导航栏时遇到的问题，开始 new page 用的大写，导致生成了 ABOUT 文件夹，于是无法打开此页连接（模版中代码其生成的链接为小写，将对应代码改成小写也可以正常使用）。
![图1 改导航栏生成路径代码](图1.PNG)

强迫症为保持一致还是删掉重建导航页。不知道是第一次错误的大写导致后来删掉后依然生成的是大写文件夹，还是 win 下文件夹大小写不敏感原因（总之 push 上去 GitHub 显示大写文件夹，本地为小写），反复删除生成重新 push，GitHub 上依然是大写文件夹，git 设置大小写不敏感也无济于事。这是个大坑啊。

解决方案：将关于 about 文件夹删掉，手动在博客根目录 source 文件夹创建 about 文件夹，并手动创建 index.md 并将 layout 设置为 about，清理生成部署，完成！

# 五 遗留问题（重新部署后已解决）
问题：部署后只有 about 导航页用 PC 和手机蜂窝数据正常打开，手机连 Wi-Fi 就打不开，是 CDN 问题么，之后几小时又带不开了，唯独此页间歇性抽风，但换成蜂窝数据就能打开…