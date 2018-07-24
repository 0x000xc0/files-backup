---
title: JavaScript 进阶五 闭包
date: 2018-07-22 20:50:56
tags: JavaScript
---
[闭包参考文档](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Closures)
[闭包概念参考博文 1](http://web.jobbole.com/94343/)
[闭包概念参考博文 2](https://www.cnblogs.com/qieguo/p/5457040.html)

> 闭包就是能够读取其他函数内部变量的函数。例如在javascript中，只有函数内部的子函数才能读取局部变量，所以闭包可以理解成“定义在一个函数内部的函数“。在本质上，闭包是将函数内部和函数外部连接起来的桥梁。

> 闭包就是一个函数引用另外一个函数的变量，因为变量被引用着所以不会被回收，因此可以用来封装一个私有变量。他就像一个静态私有变量一样。

> 函数带()才是执行函数！ 单纯的一句 var f = function() { alert('Hi'); }; 是不会弹窗的，后面接一句 f(); 才会执行函数内部的代码。

1. 闭包概念：
![闭包概念](图1.PNG)

2. 闭包作用-保存变量现场
![保存变量现场](图2.PNG)

3. 闭包作用-封装
![封装](图3.PNG)