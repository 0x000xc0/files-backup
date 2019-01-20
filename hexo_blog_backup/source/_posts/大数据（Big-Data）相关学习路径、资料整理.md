---
title: 大数据（Big Data）相关学习路径、资料整理
date: 2019-01-08 19:31:55
tags: 知识图谱与方法论
---
> 参考：
1、 [如何进入大数据领域，学习路线是什么？](https://www.zhihu.com/question/35942305)
2、 [怎样进行大数据的入门级学习？](https://www.zhihu.com/question/24761255/answer/59803163)
3、 [如何快速成为数据分析师？](https://www.zhihu.com/question/29265587/answer/44010658)
4、 [极客时间：从0开始学大数据](https://time.geekbang.org/column/intro/133?utm_term=zeusNMTT8&utm_source=website&utm_medium=oschina&utm_campaign=133-onsell&utm_content=oschina5)
5、 [BI转数据挖掘，我的脱产学习路](https://zhuanlan.zhihu.com/p/32454374)
6、 [知乎：数据挖掘](https://www.zhihu.com/search?type=content&q=%E6%95%B0%E6%8D%AE%E6%8C%96%E6%8E%98)

# 一 概述
- 大致方向：
大数据工程师、数据分析师、大数据科学家、其他。

- 随着近些年大数据技术的发展，以 Hadoop、Spark 为代表的大数据开源项目早已迭代成熟，构建起生态化系统。与此对应，不论是开发者还是企业，关注点也已经从技术的演进转向如何更好地应用大数据，去支撑业务和云计算、人工智能的深度融合。

# 二 补充资料
- [实验楼-路径：大数据工程师](https://www.shiyanlou.com/paths/2)
- [大数据工程师必备技能图谱](https://github.com/TeamStuQ/skill-map/blob/master/data/designbyStuQ/png-BigData-by-StuQ.png)
- [Hadoop 家族技能图谱](https://github.com/TeamStuQ/skill-map/blob/master/data/designbyStuQ/png-Hadoop-by-StuQ.png)

# 三 学习路径
## 0 极速了解大数据
> 参考：
1、 [极客时间：从0开始学大数据](https://time.geekbang.org/column/intro/133?utm_term=zeusNMTT8&utm_source=website&utm_medium=oschina&utm_campaign=133-onsell&utm_content=oschina5)
2、 [BI转数据挖掘，我的脱产学习路](https://zhuanlan.zhihu.com/p/32454374)

- ![BI转数据挖掘，我的脱产学习路](图0.PNG)

- ![极速了解大数据](图1.PNG)

## 1 入门指南
1. 知识图谱：
- [数据库 SQL 教程](https://www.w3cschool.cn/sql/)。
- Python/R 语言基础。
- Linux 基础。
- Excel/Tableau 数据分析软件。
- [哈里斯堡社区大学公开课：统计学入门](http://open.163.com/special/opencourse/statistics.html)。
- [数据挖掘 18 大算法实现以及其他相关经典 DM 算法](https://github.com/linyiqun/DataMiningAlgorithm)。

2. 工具：
- PyCharm
- anaconda
- Jupyter Notebook/Jupyter Lab

3. 参赛平台：
kaggle、阿里巴巴天池、kesci、datacastle、biendata、datafountain 等。

## 2 学习路线
> 参考：
1、 [如何进入大数据领域，学习路线是什么？](https://www.zhihu.com/question/35942305)

- 入门知识
- Java 基础；补充：Java 高级（《深入理解Java虚拟机》、《Java高并发实战》）。
- Scala 基础；补充：《快学 Scala》。
- Hadoop 技术模块；补充：董西成的书、《HBase 权威指南》、《Hive开发指南》。
- Hadoop 项目实战。
- Spark 技术模块；补充：《Spark 快速大数据分析》。
- 大数据项目实战。

## 3 参考经验小结
1. 必须技能 10 条:
- Java高级（虚拟机、并发）
- Linux 基本操作
- Hadoop（此处为侠义概念单指 HDFS + MapReduce + Yarn）
- HBase（JavaAPI 操作 + Phoenix ）
- Hive（Hql 基本操作和原理理解）
- Kafka 
- Storm
- Scala 需要
- Python
- Spark (Core + sparksql + Spark streaming ）

2. 高阶技能 6 条:
- 机器学习算法以及 mahout 库加 MLlib
- R 语言
- Lambda 架构
- Kappa 架构
- Kylin
- Aluxio