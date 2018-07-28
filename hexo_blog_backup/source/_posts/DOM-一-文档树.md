---
title: DOM 一 文档树
date: 2018-07-22 21:06:24
tags: DOM
---
1. 概念：
![DOM](图1.PNG)
用文档对象来描述 HTML，DOM 是一系列 API 规范。
在浏览器中由 JS 来实现这些规范并调用它。

2. DOM 包括：
- DOM Core
- DOM HTML
- DOM Style
- DOM Event

3. HTML 转为 DOM 树：
![HTML 转为 DOM 树](图2.PNG)

4. 节点遍历：
![节点遍历](图3.PNG)
以 p 标签为节点，
firstChild 是 hello；
lastChild 是 img 标签；
previousSibling 为 null；
nextSibling 为 div 标签。

5. 节点类型：
![节点类型](图4.PNG)

6. 元素遍历：
与节点遍历类似，只是去除了文本节点。
（需要兼容的做法：节点遍历 + 节点判断 = 元素节点遍历）
![元素遍历](图5.PNG)