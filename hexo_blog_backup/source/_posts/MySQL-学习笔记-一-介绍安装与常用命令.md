---
title: MySQL 学习笔记 一 介绍安装与常用命令
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

## 3 服务启动与停止
1. 启动命令 `net start mysql` （注意服务名是否无效，在服务中看正确的服务名，为 mysql57，拒绝访问用管理员。）;

2. 关闭服务 `net stop mysql` 。

## 4 登陆与退出
1. 登陆：`mysql 参数` ，如 `mysql -uroot -p -P3306 -h127.0.0.1` 
参数：![登陆参数](图3.PNG)

2. 退出：`exit 或 quit 或 \q`

## 5 修改提示符
参数：![提示符参数](图4.PNG)
- 连接时通过参数指定：`mysql -uroot -p --prompt 提示符`
- 连接上后：`prompt 提示符`

## 6 MySQL 常用命令及语句规范
1. 常用命令：[参考博文](https://www.cnblogs.com/wanghetao/p/3806888.html)

PART 1
- 显示当前服务器版本 `SELECT VERSION();`
- 显示当前日期时间 `SELECT NOW();`
- 显示当前用户 `SELECT USER();`

PART 2
- 列出所有数据库 `SHOW DATABASES;`
- 切换数据库 `USE '数据库名';`
- 列出所有表 `SHOW TABLES;`
- 显示数据表结构 `DESCRIBE 表名;`
- 删除数据库，数据表 `DROP DATABASE 数据库名;` 和 `DROP TABLE 数据表名;`

PART 3
- 未进入修改密码 `mysqladmin -u用户名 -p旧密码 password 新密码`
- 进入后修改密码 `UPDATE mysql.user SET password=PASSWORD('新密码') WHERE User='root';` ，刷新 `FLUSH PRIVILEGES;`

PART 4
- 创建用户并授权 `GRANT SELECT ON 数据库.* TO 用户名@登录主机 IDENTIFIED BY "密码";`
- 撤销授权 `REVOKE ALL ON *.* FROM user@localhost;` ，刷新 `FLUSH PRIVILEGES;`
- 显示所有用户 `SELECT user,host FROM mysql.user;`
- 删除用户 `DELETE FROM user WHERE User='test' AND Host='localhost';` ，刷新 `FLUSH PRIVILEGES;` ，删除 `DROP DATABASE 该用户数据库名;`

2. 语句规范：
- 关键字与函数名全部大写。
- 数据库、表、字段名称全部小写。
- SQL 语句全部以分号结尾。

# 二 MySQL 安装
1. 注意：MySQL 5.7 版本与之前版本存在一些不同。
- MySQL 5.7 安装目录下 `C:\Program Files\MySQL\MySQL Server 5.7\bin` 中没有配置向导程序。
- MySQL 旧版安装类型：典型安装、完全安装、定制安装。MySQL 5.7 改成了：开发者默认、只安装 MySQL 服务、只安装 MySQL 客户端、全部安装、手动选择。

2. 安装教程：[参考博文](https://blog.csdn.net/hebbely/article/details/52370179)