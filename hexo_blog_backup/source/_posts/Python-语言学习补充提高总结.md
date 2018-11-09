---
title: Python 语言学习补充提高总结
date: 2018-11-09 20:19:34
tags: Python
---
# 一 数据类型
## 1 数据类型


## 2 集合数据类型补充
1. 定义和元组相同，但用大括号 `{}`。如 `s = {"a","b","c"} 或 s = set("abc")`，set() 中的值可以是一个列表，即把列表中的值遍历放入集合中，集合可以用来去重。
集合是无值的字典，集合与元组区别在于：元组无序、不可变；集合无序、可变、不重复。

2. 方法：
```
s.add("abc")  # 增加一项，作为整体添加
s.update("abc")  # 增加多项，拆分为个体添加
s.update(["abc"，"hello", "world"])  # 增加多项
s.pop()  # 随机删除
s.remove(要删除的值)  # 指定删除，元素不存在会报错
s.discrad(要删除的值) # 指定删除，元素不存在不报错
s.issubset(XXX)  # 判断 s 是不是 XXX 的子集，返回 True，False
s.issuperset(XXX)  # 判断 s 是不是 XXX 的父集
s.isdisjoint(XXX)  # 判断是不是相交
s = forzenset("hello")  # 将集合变为不可变的集合（元组）
```

3. 集合关系运算：
- 求交集：`a_s & b_s`，`a_s.intersection(b_s)`。
- 求并集：`a_s | b_s`，`a_s.union(b_s)`。
- 求差集：`a_s - b_s`，`a_s.difference(b_s)`。
- 交叉补集（除去相同部分剩下的）：`a_s ^ b_s`，`a_s.symmetric_difference(b_s)`。

4. 补充：
对列表去重：names 为一个列表。`names = list(set(names))`。

# 二 文件操作


# 三 函数