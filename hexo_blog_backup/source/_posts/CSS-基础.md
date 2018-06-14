---
title: CSS 基础
date: 2018-06-13 21:31:23
tags: CSS
---
# 概念
HTML 表达结构（它是什么，意义），CSS 表达样式。
内容/结构和样式分离的。（CSS 出现前，HTML 既表示结构也表示样式。）

# 添加 CSS 的三种方式
1.内联
```
<p style="background-color:yellow;"></p>
```

2.嵌入式
```
<style type="text/css"></style>
```

3.外部式
```
<link rel="stylesheet" type="text/css" href="">
```

# 简单样式
关于颜色。（前端取色软件推荐：ColorPic 等）
```
background-color:transparent;  <!-- 直接设置值的名字 -->

background-color:rgb(255,255,0);  <!-- background-color:rgba(255,255,0,0.5)  a 为透明度，0-1 的浮点数 -->

background-image:url(pic.jpg);  <!-- background-image:url(http://www.163.com/pic.jpg) -->
```

图片背景
```
background-image:url(pic.jpg);
background-repeat:no-repeat;  <!-- background-repeat:repeat-x / repeat-y; -->
background-position:top right;  <!-- background-position:200px 200px; -->
background-attachment:fixed;  <!-- background-attachment:scroll; 默认为滚动 -->
```

# 基础样式
## 文本样式
文字修饰与空格处理
```
text-transform:uppercase;  <!-- 文本转换 -->
text-decoration:underline overline line-through;  <!-- 文本装饰 -->
white-space:pre;  <!-- 留白处理方式 -->
```

字体
```
font-family:hei,times,serif;
<!-- font-family 可以有多个备选字体（字体分为五个大类，具体字体名称） -->
```

文字修饰
```
font-style:italic;  <!-- 斜体 -->
font-variant:small-caps;  <!-- 小号大写字母 -->
font-weight:bold;  <!-- 加粗或细。也可用不同值，不同浏览器可能不同 100～900 --> 
font-size:0.5em;  <!-- 1em 为默认大小的字 -->
```

文字效果
```
text-shadow:3px 5px 5px rgba(0,255,0,0.5);  
<!-- 在 x 右方向上与本体延伸多少，y 下方向上延伸多少，延伸范围，颜色。/负值则为向左，上，可以多组组合起来用逗号隔开。 -->

outline-color:red;outline-style:solid;  <!-- 边框 -->
outline-width:2  <!-- 可以为数值，也可以为提供的样式。 -->
```

## 段落样式
段落缩进
```
text-indent:2em;  <!-- 首行缩进 2 个字符。 -->
padding：2em;  <!-- 每行缩进 2 个字符。 -->
```

间距与对齐
```
line-height:2em;  <!-- 行高行间距,也可用数值倍数如 1.5。 -->
text-align:right  <!-- 对齐方式，left,right,center,justify 两端对齐。 -->
word-spacing:10px;  <!-- 英文单词间间距。 -->
letter-spacing:10px;  <!-- 字符间的间距。 -->
```
