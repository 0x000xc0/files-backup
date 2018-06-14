---
title: HTML 常用标签
date: 2018-06-12 13:54:19
tags: HTML
---
# 概念
HTML 文档基本构成：标签，属性，元素。

Head 放置一些辅助元素（主要为样式表 `<style></style>`；JavaScript 脚本 `<script><script>`）。
Body 放置网页主体内容。

注释在 HTML,CSS,JavaScript 中的区别：
HTML中 `<!--   -->` ，
CSS中 `/*   */` ，
JavaScript 单行 `//`   多行 `/*   */` 。

使用小于号，大于号，引号等需要使用参考字符，以 `&` 开始，以 `;` 结束。如 1<2 写成 `1&lt;` 。


# 基础格式
使用 `<hgroup>` 标签对网页或区段（section）的标题进行组合，逻辑上为一体：
```
<hgroup>
 <h1>Welcome to my WWF</h1>
 <h2>For a living planet</h2>
</hgroup>
```

上标，下标
```
a<sup>2</sup>+b<sub>0</sub>
```

加粗
```
<b></b>
```
 
斜体
```
<i></i>
```

缩小
```
<small></small>
```

删除
```
<del></del>
```

增加的
```
<ins></ins>
```

过时的不提倡使用
```
<s></s>
```

高亮
```
<mark></mark>
```

定义
```
<dfn>define</dfn>
```

代码片段
```
<code>code代码</code>

<samp>samp例子代码</samp>
```

用户输入
```
<kbd>kbd用户输入</kbd>
```

变量
```
<var>变量</var>
```

引用
```
<cite>cite引用</cite>
```

地址
```
<address>Rm401 XK West</address>
```

引用
```
<q>：引用的是小段文字；

<blockquote>：引用的是大段的内容块。
```

预格式化不做处理
```
<pre></pre>
```

水平线
```
<hr>
```

缩写，鼠标停留有注释
```
<abbr="中华人民共和国">PRC</abbr>
```

# 深入格式
## 列表与图片
有序列表,start 属性为从几开始。
```
<ol start=2>
	<li>ABC</li>
	<li>ABC</li>
</ol>
```

无序列表
```
<ul>
	<li>ABC</li>
	<li>ABC</li>
</ul>
```

定义列表
```
<dl>
	<dt>词条</dt>
	<dd>词条的解释</dd>
</dl>
```

插入图片，`./` 表示当前目录,同目录可直接写文件夹；`../` 表示上一级目录。从当前位置去找目的位置。
```
<img src="example.jpg" width="50%" height="50%" alt="另选的。装在中，失败时显示的文字">
```

窗口插入另一个页面
```
<iframe src="http://www.163.com"></iframe>
```

## 超链接
target 属性有：`_blank` `_self` `_top`(在整个窗口中打开)
```
<a href="">XXX</a>
```

页面内链接
```
<a href="#here">XXX</a> <!--here 为某个标签的 id值-->
<a href="you.html#here">XXX</a>
```

图片定位链接。
将图片隐射到地图，地图中再划分区域（区域中属性有形状，坐标，链接）。
```
<img src="example.jpg" width="200" height="200" usemap="#map">

<map name="map">
	<area shape="rect" coords="0,0,50,50" href="">
	<area shape="circle" coords="75,75,25" href="">
</map>
```

## 表格
标题，行，表头&列组成。
```
<table border="1">
	<caption>这是一个表格</caption>
	<thead>
	<tr>
		<th>OS</th>
		<th>Chinese?</th>
		<th>French</th>
	</tr>
	</thead>
	<tbody>
	<tr>
		<td>iOS 10</td>
		<td>YES</td>
		<td>YES</td>
	</tr>
	</tbody>
	<tfoot>
	<tr>
		<td colspan="3">列延展3个格子</td> <!--rowspan 为行延展，行合并-->
	</tr>
	</tfoot>
</table>
```
```
<thead>用来包裹表格表头行</thead>
<tbody>用来包裹表格 body 部分行</tbody>
<tfoot>用来包裹表格 foot 行</tfoot>
```
