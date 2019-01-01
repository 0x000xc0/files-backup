---
title: 使用 WordPress 在云服务器快速建站
date: 2019-01-01 15:06:27
tags: 记录小结
---
> 阿里云可以直接使用 WordPress，本博文教程使用虚拟机（Ubuntu）当作 ECS 云服务器，从零开始建站。

> 参考：
1、 [WordPress 官方中文文档](https://codex.wordpress.org/zh-cn:Main_Page)
2、 [阿里云服务器使用教程，新手上云必备功课](https://yq.aliyun.com/articles/680675?spm=a2c4e.11155472.0.0.ffd460c7YeHPNs)
3、 [建站零基础入门（阿里云）](https://help.aliyun.com/document_detail/63819.html?spm=a2c4g.11186623.6.874.57c74cc1dj0fps)
4、 [手动建站方式汇总（阿里云）](https://help.aliyun.com/document_detail/57160.html?spm=a2c4g.11186623.6.876.434f68110P5L7q)
5、 [域名注册流程](https://help.aliyun.com/document_detail/54068.html?spm=a2c4g.11186623.2.34.e56523c7sxHfK4#concept-x22-3rv-12b)
6、 [首次备案](https://help.aliyun.com/knowledge_detail/36922.html#concept-ghz-3rl-zdb)，（国内 CN 等域名需要备案。）
7、 [设置域名解析](https://help.aliyun.com/document_detail/29716.html?spm=a2c4g.11186623.2.37.e56523c7sxHfK4)

# 一 环境搭建
1. 首先设置虚拟机的环境（LAMP）：
- 使用 SSH 客户端链接虚拟机。
- 查看 WordPress 环境要求，[参考文档](https://wordpress.org/about/requirements/)。
- 搭建环境，参考：[LAMP一键安装包](https://lamp.sh/install.html)。

2. 启动服务：
- MySQL：`/etc/init.d/mysqld (start|stop|restart|status)`
- Apache：`/etc/init.d/httpd (start|stop|restart|status)`