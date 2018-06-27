---
title: CSS 进阶一 选择器
date: 2018-06-26 16:39:50
tags: CSS
---
# 简介
1. CSS 全称为层叠样式表。用来呈现页面的表现。

2. CSS 发展史：
![CSS 发展史](图1.PNG)

3. 添加 CSS 的三种方式:
- 内联：
```
<p style="background-color:yellow;"></p>
```

- 嵌入式：
```
<style type="text/css"></style>
```

- 外部式：
```
<link rel="stylesheet" type="text/css" href="">
```

4. 语法：
由选择器，属性声明构成。
```
选择器{
	属性:值;
	属性2:值2;
	... /* 属性声明 */
}
```

5. 浏览器私有属性：
![浏览器私有属性](图2.PNG) 

6. @ 规则：
![规则](图3.PNG)
@media 用来做响应式布局。
@keyframes 用来描述一些 CSS 动画的中间步骤。
@font-face 用来引入外部字体。

# 选择器
## 简单选择器
选择器：通过选择器表达式来选中一系列元素。
可以将各种选择器进行组合。`img[src$=jpg]{属性声明;}`
### 标签选择器
```
p{color:blue;}
```

### 类选择器
```
.stress{font-weight:bold;}  /* 区分大小写 */
<p class="stress"></p>
```

### id 选择器
```
#foot{font-weight:bold;}  /* id 只出现一次 */
<p class="foot"></p>
```

### 通配符选择器
```
*{属性声明;}
```

### 属性选择器
```
[属性]{属性声明;}

[type=button]{属性声明;}
<input type="button" value="按钮">

[class~=sports]{属性声明;}
<h2 class="title sports"></h2>
<p class="sports"></p>

...
```

### 伪类选择器
- 链接：
```
a:link{属性声明;}
a:visited{属性声明;}  /* 访问过的链接 */
a:hover{属性声明;}  /* 鼠标移上去显示的样式 */
a:active{属性声明;}  /* 鼠标点击上去显示的样式 */
<a href="www.baidu.com"></a>
```

- input 类型：
```
input:enabled{属性声明;}
input:disabled{属性声明;}
input:checked{属性声明;}
```

- 列表：
```
li:first-child{属性声明;}  /* 列表的第一个子元素 */
li:last-child{属性声明;}
li:nth-child(even){属性声明;}  /* even odd 3n+1 */
li:nth-last-child{属性声明;}
li:only-child{属性声明;}  /* 选中只有一个子元素的 */
```

- 定义列表:
```
dd:first-of-type{属性声明;}  /* 选中第一个 dd 类型的元素 */
dd:last-of-type{属性声明;}
dd:nth-of-type(even){属性声明;}  /* even odd 3n+1 */
dd:nth-last-of-type(even){属性声明;}
```

- 其他标签：
```
span:only-of-type{属性声明;}  /* 好几个 span 标签，选中第一个 span 标签 */
```

- 其他不常用的：
```
:empty  /* 选中没有子元素的标签 */
:root  /* 选中根标签 <html></html> */
```

## 其它选择器
### 伪元素选择器
```
::first-letter{color:red}  /* 第一个字符为红色 */
::first-line{属性声明;}
::before{content:"在某元素内容前面插入的内容"}
::after{content:"在某元素内容后插入的内容"}
<p>伪元素选择器</p>

::selection{属性声明;}  /* 被选中的内容显示出的样式 */
```

### 组合选择器
```
<div class="main">
	<h1></h1>
	<div>
		<h1></h1>
		<p></p>
	</div>
</div>
```
- 后代选择器:
```
.main h1{属性声明;}  /* 选中 main 下的内容 */
```

- 子选择器:
```
.main>h1{属性声明;}  /* 选中 main 下的 h1 */
```

- 兄弟选择器:
```
<div>
	<h2></h2>
	<p>段落一</p>
	<p>段落二</p>
</div>

h2+p{属性声明;}  /* 只选中段落一的 p 标签 */
h2~p{属性声明;}  /* 选中 h2 后的若干个段落 */
```

### 选择器分组
```
h1,h2,h3{属性声明;}  /* 将多个相同的写成一组 */ 
```

## 继承，优先，层叠
### 继承
```
body{font-family:"Microsoft Yahei";}  
/* 可以使所有子元素都应用雅黑字体，一些属性可以自动继承。 */
```

### 优先与层叠
![优先](图4.PNG)
1. 值越大优先级越高，若相同则层叠。
a：1000
b：100
c：10
d：1

2. 改变优先级三个方法：
改变先后顺序；提升选择器优先级（用组合起来的来提升）；!important（直接加在属性声明的值的后面）如 `.tip{color:blue !important;}` 。