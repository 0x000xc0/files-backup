---
title: WordPress 与 Hexo 搭建的博客相互迁移问题
date: 2019-01-02 17:55:31
tags: 记录小结
---
>参考：
1、 [Hexo文档：WordPress转到Hexo](https://hexo.io/zh-cn/docs/migration.html)
2、 [Hexo数据导入到WordPress博客方法](https://sobaigu.com/hexo-to-wordpress.html)
3、 [从hexo迁移回wordpress,并进行wordpress优化、编辑器等](http://www.lizenghai.com/archives/117.html)

# 一 谈谈两者异同
- 使用 Hexo 搭建博客，可以使用免费的 GitHub Pages 服务，使用 Markdown 写博客，然后 git 提交。缺点是需要在本地部署环境，如果跨平台写博客比较麻烦。
- 使用 WordPress 搭建博客更快更简单，部署在云服务器上，跨设备平台写博客，并且有手机客户端在手机上写博客，可视化设置也简单。

# 二 WordPress 迁移到 Hexo
1. 安装 hexo-migrator-wordpress 插件：`npm install hexo-migrator-wordpress --save`

2. WordPress 仪表盘中导出数据，“Tools” -> “Export” -> “WordPress”。[参考文档](https://en.support.wordpress.com/export/)。

3. 执行命令 `hexo migrate wordpress <source>`，source 可以是 WordPress 导出的文件路径或网址。

4. 注意，此插件并不完美，在处理 WordPress 的分类方面存在问题，需手动检查 markdown 文件。

# 三 Hexo 迁移到 WordPress
1. Hexo 输出 xml：
- 安装 hexo-generator-feed 插件：`npm install hexo-generator-feed --save`
- 在 `_config.yml` 文件中添加内容：
```
feed:
  type: rss2
  path: rss2.xml
  limit: false
  hub:
```
- 重启 Hexo server，访问 localhost/rss2.xml，保存该文件或者直接 hexo g，然后去 public 目录找这个文件。

2. WordPress 安装相关插件，导入 rss2.xml

3. 因为不是定制的导入程序，导入 WordPress 后分类将会消失。可能需要自己修改导入程序。