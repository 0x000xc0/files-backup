---
title: MySQL 学习笔记 二 SQL 功能及其对象
date: 2018-09-18 17:35:01
tags: 数据库
---
> 需要的预备知识：《数据库系统概论（基础篇）》中的绪论及关系数据库这两部分内容（组成、三级模式和二层映像、关系数据结构及关系的完整性、关系代数）。
以下为 MySQL 语法为主，与 SQL 中会有不同之处，不同处会指出。

# 一 SQL 概述
1. SQL 语言集数据定义语言（DDL）、数据操纵语言（DML）、数据控制语言（DCL）功能于一体。

2. SQL 功能及其作用对象：
![SQL 功能及其作用对象](图1.PNG)

# 二 数据定义
## 补充
1. 数据类型：

PART 整型
- TINYINT 占 1 字节。
- SMALLINT 占 2 字节。
- MEDIUMINT 占 3 字节。
- INT 占 4 字节。
- BIGINT 占 8 字节。

PART 浮点型
- FLOAT[(总位数，小数点后位数)]
- DOUBLE[(总位数，小数点后位数)]

PART 字符型
- CHAR(字节数) 字节数 0 到 255。
- VARCHAR(字节数) 字节数为 0 到 65536。
- TINYTEXT 约 2^8。
- TEXT 约 2^16。
- MEDIUMTEXT 约 2^24。
- LONGTEXT 约 2^32。
- ENUM('value1','value2',...) 枚举，最多 65535个值。
- SET('value1','value2',...) 集合，最多 64 个成员。

PART 日期时间型
- YEAR
- TIME
- DATE 范围为 1000 年 1 月 1 日到 9999 年 12 月 31 日。
- DATETIME 范围为 1000 年 1 月 1 日 0 点到 9999 年 12 月 31 日 23 点 59 分 59 秒。
- TIMESTAMP 范围为 1970 年 1 月 1 日 0 点到 2037 年中的一个值。

2. 约束：
- PRIMARY KEY 主码，自动设为 NOT NULL，UNIQUE。
- FOREIGN KEY 外码。
- UNIQUE 确保非主码列值不重复，可以为空。
- NOT NULL 该属性不为空。

## 1 模式定义
1. MySQL:
注：MySQL 中创建 scheme 和创建 database 相同。
- 定义： `CREATE DATABASE <数据库名>;`
- 修改：用图形界面修改。或 `ALTER DATABASE ...;`
- 删除： `DROP DATABASE <数据库名>;`

2. SQL：
- 定义： `CREATE SCHEME <模式名> AUTHORIZATION <用户名>` ,可在下面加表、视图、授权定义子句。
- 删除：`DROP SCHEME <模式名> <CASCADE|RESTRICT>` ，CASCADE 级联，全部删除；RESTRICT 限制，若有对象拒绝删除。

## 2 表定义
注：创建完 database 需要 `use 数据库名;` ;名称可不加单引号；结尾一定要双引号。
1. MySQL:
- 定义： `CREATE TABLE table_name (column_name column_type,...);`
```
例：
CREATE TABLE IF NOT EXISTS student(
s_id int,
c_id int,
s_name char(10),
s_gender char(2),
s_age tinyint,
PRIMARY KEY(s_id),
FOREIGN KEY(c_id) REFERENCES course(c_id)
);
```
- 修改：


## 3 视图定义

## 4 索引定义

# 三 数据操纵
## 1 表操纵

# 四 数据控制

# 五 数据查询
表和视图的查询相同。