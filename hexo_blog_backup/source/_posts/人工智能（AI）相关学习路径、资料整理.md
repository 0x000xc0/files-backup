---
title: 人工智能（AI）相关学习路径、资料整理
date: 2019-01-08 16:45:13
tags: 知识图谱与方法论
---
> 参考：
1、 [如何用3个月零基础入门「机器学习」？](https://zhuanlan.zhihu.com/p/29704017)
2、 [非计算机专业学生如何转行 AI，并找到算法 offer？](https://www.zhihu.com/question/265041005)
3、 [从入门到高阶，读懂机器学习需要哪些数学知识（附网盘）](https://zhuanlan.zhihu.com/p/36018667)
4、 [【学界】一文读懂机器学习需要哪些数学知识(附全套优秀课程的网盘链接资源)](https://zhuanlan.zhihu.com/p/33999430)
5、 [奔走相告！亚马逊内部机器学习课程现向大众免费开放](https://zhuanlan.zhihu.com/p/51011016)
6、 [从基础概念到数学公式，这是一份520页的机器学习笔记（图文并茂）](https://zhuanlan.zhihu.com/p/36287950)
7、 [学习机器学习过程中都走过哪些弯路，怎样避免走弯路？](https://www.zhihu.com/question/265000993/answer/288147789)
8、 [普通程序员如何正确学习人工智能方向的知识？](https://www.zhihu.com/question/51039416/answer/126821822)
9、 [如何自学人工智能？](https://www.zhihu.com/question/21277368/answer/550671387)

# 一 概述
- 不要把深度学习作为入门第一课，建议从经典机器学习开始入手。
- 不要过度收集材料，机器学习的资料有很大的时效性。
- 选择符合自己风格的材料，进行 T 字形阅读。
- 如果在读，优先进实验室，再去找实习，最后一条路是好好刷 GPA。
- 学好英语，至少打下阅读和听力的基础。
- 不要试图掌握所有的相关数学知识再开始学习。

# 二 补充资料
- [PracticalAI 从零开始学习人工智能（重实践）](https://github.com/GokuMohandas/practicalAI/)。
- [Interpretable Machine Learning](https://christophm.github.io/interpretable-ml-book/index.html)。
- [从基础概念到数学公式，机器学习笔记](https://pan.baidu.com/s/1tNXYQNadAsDGfPvuuj7_Tw#list/path=%2F)。
- [深度学习500问](https://github.com/scutan90/DeepLearning-500-questions)。
- [机器学习技能图谱](https://github.com/TeamStuQ/skill-map/blob/master/data/designbyStuQ/png-MachineLearning-by-StuQ.png)。
- [哥伦比亚大学研究生详细吴恩达《机器学习》笔记](https://wei2624.github.io/machine%20learning/Machine-Learning-Notes/)。
- 读懂机器学习需要哪些数学知识，[备用连接 1：密码: yzkx](https://pan.baidu.com/s/1rEoidASC51_gDMcLpi1wxQ)，[备用连接 2：密码: i7mn](https://pan.baidu.com/s/1PCkS--EpbOaQ7LD8HGlBfQ)。
- [实验楼-路径：机器学习工程师](https://www.shiyanlou.com/paths/20)
- [AWS Machine Learning 学习课程](https://aws.amazon.com/cn/training/learning-paths/machine-learning/)。
- [极客时间：人工智能基础课](https://time.geekbang.org/column/intro/62)。
- [Kaggle 挑战赛/练习](https://www.kaggle.com/)。

# 三 详细学习路径
## 0 极速了解人工智能
> 参考：
1、 [极客时间：人工智能基础课](https://time.geekbang.org/column/intro/62)

![极速了解人工智能](图1.PNG)

## 1 基础入门（3-6 个月）
- [吴恩达 Cousera 机器学习课程](https://www.coursera.org/learn/machine-learning)。
- 《Python 机器学习》、《Hands-On Machine Learning with Scikit-Learn and TensorFlow》、[《Introduction to Statistical Learning with R》](http://www-bcf.usc.edu/~gareth/ISL/ISLR%20First%20Printing.pdf)。
- 周志华《机器学习》，作为参考书。

## 2 进阶学习（3-6 个月）
- Kaggle 挑战赛/练习，[链接](https://www.kaggle.com/)。
- Sklearn 文档学习。

## 3 深度学习（3-6 个月，可选）
- [吴恩达深度学习课程](https://mooc.study.163.com/smartSpec/detail/1001319001.htm)。
- Deep Learning - by Ian GoodFellow，[链接](https://github.com/exacity/deeplearningbook-chinese)。

## 4 深入研究
- 周志华老师的《机器学习》、李航老师的《统计学习基础》、《Elements of Statistical Learning》。
- 订阅 Arxiv，关注机器学习的顶级会议，如 ICML/NIPS/KDD 等。

# 四 需要的数学知识
> 参考：
1、 [从入门到高阶，读懂机器学习需要哪些数学知识（附网盘）](https://zhuanlan.zhihu.com/p/36018667)

## 1 入门基础
- 微积分（求导，极限，极值）。
- 线性代数（矩阵表示、矩阵运算、特征根、特征向量），（主成分分析（PCA）、奇异值分解（SVD）、矩阵的特征分解、LU 分解、QR 分解、对称矩阵、正交化和正交归一化、矩阵运算、投影、特征值和特征向量、向量空间和范数（Norms））。
- C/C++/Python.
- 算法（算法复杂度）。
- 矩阵求导。

## 2 中级教程
- 概率论+统计（很多数据分析建模基于统计模型）、统计推断、随机过程。
- 线性规划 + 凸优化（或者只学一门叫 Numerical optimization，统计、机器学习到最后就是求解一个优化问题）、非线性规划等。
- 数值计算、数值线代等。

## 3 高阶课程
- 略。