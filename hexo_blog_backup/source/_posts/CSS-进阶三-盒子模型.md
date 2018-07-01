---
title: CSS 进阶三 盒子模型
date: 2018-06-28 18:39:58
tags: CSS
---
# 一 概念
![盒子模型1](图1.PNG)
![盒子模型2](图2.PNG)

- 具体设置方法：
![设置方法](图3.PNG)

- 设置值的缩写：
![缩写](图4.PNG)

# 二 具体使用
## 1 margin
- margin 合并：
会取两个 margin 中大的值。
![margin 合并](图5.PNG)

- margin 的 auto 值巧用：
利用 auto 值来水平居中。
![auto 值](图6.PNG)

## 2 border
- 边框 border：
![边框 border](图7.PNG)

- 圆角边框 border-radius：
![圆角边框 border-radius](图8.PNG)

用 `/` 来分割水平半径和垂直半径。当水平垂直都是 50% 时为一个正圆 `border-radius:50%` 。
![水平半径和垂直半径](图9.PNG)

## 3 盒子设置
- 溢出设置 overflow：
当盒子内内容容纳不下时设置该怎样显示。
![overflow](图10.PNG)

- 指定宽高 box-sizing：
指定宽高代表的含义。
![box-sizing](图11.PNG)

- 盒子阴影 box-shadow：
模糊半径为 3px，则向内 1.5px，向外 1.5px。
![box-shadow](图12.PNG)

- 多种阴影：
![多种阴影](图13.PNG)

- 轮廓 outline：
用来描绘轮廓，类似与 border。
![轮廓 outline](图14.PNG)