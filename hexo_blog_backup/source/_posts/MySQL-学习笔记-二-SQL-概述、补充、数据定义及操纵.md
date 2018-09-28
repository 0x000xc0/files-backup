---
title: MySQL 学习笔记 二 SQL 概述、补充、数据定义及操纵
date: 2018-09-05 17:35:01
tags: 数据库
---
> 需要的预备知识：《数据库系统概论（基础篇）》中的绪论及关系数据库这两部分内容（组成、三级模式和二层映像、关系数据结构及关系的完整性、关系代数）。
以下为 MySQL 语法为主，与 SQL 中会有不同之处，不同处会指出。

# 一 SQL 概述
1. SQL 语言集数据定义语言（DDL）、数据操纵语言（DML）、数据控制语言（DCL）功能于一体。

2. SQL 功能及其作用对象：
数据定义，数据操作见本博文，数据控制见本系列第四篇博文（安全性），数据查询见本系列第三篇博文。
![SQL 功能及其作用对象](图1.PNG)

3. 内容小结：三个层次。定义、操作、控制、查询；索引、表、视图；增、删、改。

# 二 补充
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

2. 主键约束：
- PRIMARY KEY 主码，自动设为 NOT NULL，UNIQUE。
- FOREIGN KEY 外码。
- UNIQUE 确保非主码列值不重复，可以为空。
- NOT NULL 该属性不为空。

3. 外键约束的参照操作：
![外键约束的参照操作](图2.PNG)

4. 列级约束与表级约束：
对一个数据列的约束，为列级约束，列定义时或定义后声明。
对多个数据列的约束，为表级约束，只能定义后声明。

# 三 数据定义
## 1 模式定义
注：MySQL 中创建 scheme 和创建 database 相同。
1. 定义： `CREATE DATABASE <数据库名>;`
2. 修改：用图形界面修改。或 `ALTER DATABASE ...;`
3. 删除： `DROP DATABASE <数据库名>;`

> 补充： 关于 SQL 的定义与删除。
1. 定义： `CREATE SCHEME <模式名> AUTHORIZATION <用户名>` ,可在下面加表、视图、授权定义子句。
2. 删除：`DROP SCHEME <模式名> <CASCADE|RESTRICT>` ，CASCADE 级联，全部删除；RESTRICT 限制，若有对象拒绝删除。

## 2 表定义
注：创建完 database 需要 `use 数据库名;` ;名称可不加单引号；结尾一定要双引号。

1. 定义： `CREATE TABLE table_name (column_name column_type,...);`
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
2. 修改（列与约束）：
```
ALTER TABLE table_name
ADD <新列名> <数据类型> [完整型约束] [FIRST|AFTER 列名],
ADD [CONSTRAINT 约束名] <完整型约束>(列名) [ON DELETE 外键约束参照操作],

ALTER <列名> <数据类型>,
ALTER <列名> <SET DEFAULT 值|DROP DEFAULT>,
CHANGE <原列名> <现列名> <类型>,

DROP <列名|完整型性约束名>,
DROP <PRIMARY KEY|FOREIGN KEY(列名)|KEY 列名>；
```
```
NOT NULL 约束的添加，删除：(其他约束也可用 MODIFY)
ALTER TABLE table_name MODIFY <列名> <数据类型> NOT NULL;

ALTER TABLE table_name MODIFY <列名> <数据类型>;
```

3. 删除：`DROP TABLE <表名> [外键约束参照操作];`

## 3 视图定义
视图是从一个或几个基本表或视图导出的表，只存放定义，不存放数据。
1. 定义：
AS 后面是子查询。
`[WITH [CASCADED|LOCAL] CHECK OPTION]` 决定了是否允许更新数据记录不再满足视图的条件。local 只要满足本视图的条件就可以更新,cascaded 必须满足所有针对该视图的所有视图的条件才可以更新，默认是 cascaded。
```
CREATE VIEW <视图名>(列1，列2...)
AS [SELECT 表名.列1,表名.列2...) FROM 表名]
[WITH [CASCADED|LOCAL] CHECK OPTION]; 

例：
CREATE VIEW student_view(id,name)
AS SELECT student.s_id,student.s_name
FROM student;
```

2. 修改：
```
CREATE OR REPLACE VIEW <视图名>(列1，列2...)
AS [SELECT 表名.列1,表名.列2...) FROM 表名]
[WITH [CASCADED|LOCAL] CHECK OPTION];
```

3. 删除：
该视图还导出其他视图可级联删除。
```
DROP VIEW <视图名> [CASCADE];
```

## 4 索引定义
通过 BTREE、HASH 算法来建立索引（对某列等），加快查询速度。

1. 定义：
如果是 CHAR，VARCHAR 类型，length 可以小于字段实际长度；如果是 BLOB 和 TEXT 类型，必须指定 length。
`[UNIQUE|CLUSTER]` 前者指每个索引值对应唯一数据记录，后者指索引项顺序与表中物理顺序一致。
```
CREATE [UNIQUE|CLUSTER] INDEX <索引名> ON <表名>(<列名>(长度));
或
ALTER TABLE <表名> ADD INDEX <索引名>(<列名>(长度));
```

2. 删除：
```
DROP INDEX <索引名>;
```

# 三 数据操纵
## 1 表、视图操纵
1. 增：
```
对特定列赋值：
INSERT 
INTO <表名> (<列 1>,...)
VALUES (<常量 1>,...);

使用子查询：用 SET。
INSERT 
INTO <表名> (<列 1>,...)
SET <子查询>；

对所有列赋值：必须对所有列赋值，可以用 NULL 或 DEFAULT 为值。
INSERT
<表名>
VALUES (<常量 1>,...);
```

2. 改：
```
UPDATE <表名>
SET <列名>=<表达式>,...
WHERE <条件>；
```

3. 删：
```
DELETE FROM <表名>
WHERE <条件>;
```

4. 表补充：
通常可以先分组再排序。
GROUP BY：对结果分组，`GROUP BY <列名> [ASC|DESC]` (升序，降序)。
ORDER BY：对结果分组，`ORDER BY <列名> [ASC|DESC]` (升序，降序)。
HAVING：分组的条件，`HAVING <条件>`
LIMIT：限制返回的数量，`LIMIT 开始位置 条数` ，从头开始可不写开始位置。

5. 视图特点：[参考博文](https://blog.csdn.net/dyushuo6230/article/details/80413082)
视图的可更新性和视图中查询的定义有关系，以下类型的视图是不可更新的。
- 包含一下关键字的 sql 语句：聚合函数（sum,min,max,count 等）,distinct,group by,having,union 或者 union all。
- 常亮视图。
- select中包含子查询。
- jion。
- from 一个不能更新的视图。
- where 句子的子查询引用了 from 句子中的表。