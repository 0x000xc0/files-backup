---
title: MySQL 学习笔记 一 介绍与安装
date: 2018-09-17 22:32:14
tags: 数据库
---
> 课程视频：
《与 MySQL 的零距离接触》 https://www.imooc.com/learn/122
数据库系统概论（基础篇）：http://www.icourse163.org/course/RUC-488001
数据库系统概论（高级篇）：http://www.icourse163.org/course/RUC-1001655006
MySQL 官方文档：https://dev.mysql.com/doc/

# 一 MySQL 介绍
## 1 MySQL 组件介绍
开发者默认安装类型下的组件和插件，都在安装目录下。

1. 相关软件产品：
![相关软件产品](图0.PNG)
- MySQL Server：MySQL Server.
- MySQL Workbench：The GUI application to develop for and manage the database server.
- MySQL Visual Studio Plugin：To work with the MySQL Server from Visual studio.
- MySQL Connectors：Connector/Net, Java, C/C++, OBDC and others.
- Examples and tutorials：To help you get started with your development.
- Documentation：Allows you to read the documentation offline.

2. 相关组件：
![相关组件](图1.PNG)
- MySQL Server：MySQL 服务程序。
- MySQL Notifier：一个启动和停止mysql服务的程序。
- Connector：用来连接相关。
- MySQL Documents：一些类似于帮助文件的的东西。
- MySQL Examples and Samples：一些数据库案例，可以不要。

## 2 配置文件
旧版本配置文件在安装目录下。
MySQL 5.7 的配置文件在 `C:\ProgramData\MySQL\MySQL Server 5.7\my.ini` ，可在 MySQL Workbench 中默认的数据库中查看。
![MySQL 5.7 的配置文件查看](图2.PNG)

# 二 MySQL 安装
1. 注意：MySQL 5.7 版本与之前版本存在一些不同。
- MySQL 5.7 安装目录下 `C:\Program Files\MySQL\MySQL Server 5.7\bin` 中没有配置向导程序。
- MySQL 旧版安装类型：典型安装、完全安装、定制安装。MySQL 5.7 改成了：开发者默认、只安装 MySQL 服务、只安装 MySQL 客户端、全部安装、手动选择。

2. 安装教程：[参考博文](https://blog.csdn.net/hebbely/article/details/52370179)