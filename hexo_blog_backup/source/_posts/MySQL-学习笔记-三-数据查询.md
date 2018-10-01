---
title: MySQL 学习笔记 三 数据查询
date: 2018-09-10 20:20:16
tags: 数据库
---
# 一 数据查询
一般格式：
DISTINCT 为去掉重复列。
HAVING 为满足条件才输出。
```
SELECT [ALL|DISTINCT] <目标列表达式>,... 
FROM <表名或视图名>,...
WHERE <条件表达式>
GROUP BY <列名> HAVING <条件表达式>
ORDER BY <列名> [ASC|DESC];
```

## 1 单表查询（仅涉及一个表）
<目标列表达式> 可以为 * 星号、可以为算术表达式、字符串常量、函数等（原来没有的列会新增显示出来）。
如 `SELECT sname,"year of birthday",2004-sage,LOWER(sdept)`

1. 常用查询条件（WHERE）：
![常用查询条件](图1.PNG)

2. 确定集合：查找属性值属于指定集合的元组。
`WHERE sdept IN("CS","MA")`

3. 字符匹配：
`[NOT] LIKE "<匹配串>" [ESCAPE "<换码字符>"]` ；
任意长度字符用 `%` ,单个字符用 `_` ；
查询内容中有百分号或下划线须在前加 `\` 转义，并加上 `ESCAPE 转义符号` 。

例：查询 cname 列以 DB_ 开头，倒数第三个字符为 i 的情况，`WHERE cname LIKE "DB\_%I__" ESCAPE "\"` 。

4. 多重条件：
用 AND、OR 来联结多个查询条件。

5. 聚合函数：
```
COUNT([DISTINCT|ALL] *) 统计元组个数
COUNT([DISTINCT|ALL] <列名>) 统计列中值的个数
SUM([DISTINCT|ALL] <列名>) 计算一列值的总和
AVG([DISTINCT|ALL] <列名>) 一列平均值
MAX([DISTINCT|ALL] <列名>) 一列中最大值
MIN([DISTINCT|ALL] <列名>) 一列中最小值
```

## 2 连接查询
条件中使用等于号的为等值连接，其他为非等值连接；
连接中列名类型必须是可比的；
列属性名唯一可省略表名；
去掉重复列为自然连接。

1. 等值与非等值连接：
```
例：
SELECT student.sno,sname,cno
FROM student,course
WHERE student.sno=course.cno;
```

2. 自身连接：
把自身虚拟为两张表操作。

```
例：
SELECT <虚拟表名1.列名1>,<虚拟表名2.列名2>
FROM <表名> <虚拟表名1>,<表名> <虚拟表名2>
WHERE <虚拟表名1.列名1> = <虚拟表名2.列名2>;
```

3. 外连接：
保留属性为空的元组。
LEFT OUT JOIN 为保留左表值（表名1）。
USING(列名) 为去掉该列重复值。
```
SELECT <列>,...
FROM <表名1>
LEFT OUT JOIN <表名2> ON (条件);
```

4. 复合条件：
多个条件用 AND 连接。

## 3 嵌套查询
一个 SELECT-FROM-WHERE 为一个查询块，将查询块嵌套在另一个查询块 WHERE 子句或 HAVING 短语条件中查询。

1. 带有 IN 谓词的子查询：
```
SELECT <列名>,...
FROM <表名>
WHERE <列名> IN
(一个查询块);
```

2. 带有比较运算符的子查询：
```
SELECT <列名>,...
FROM <表名>
WHERE <列名> >=
(一个查询块);
```

3. 带有 ANY、SOME、ALL 谓词的子查询：

4. 带有 EXIXTS 谓词的子查询：


## 4 集合查询
将多个查询块结果进行集合操作。
并：UNION、交：INTERSECT、差：EXCEPT。

```
查询块1
UNION
查询块2
```