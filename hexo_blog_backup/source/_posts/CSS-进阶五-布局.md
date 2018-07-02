---
title: CSS 进阶五 布局
date: 2018-07-01 16:25:12
tags: CSS
---
# 一 display
display 属性用来设置元素的显示方式（元素的大小和位置）。
![display](图1.PNG)

- none 值：设置元素不显示。`display:none` 和 `visibility:hidden` 区别在于后者隐藏但会占据位置。

- block 值：
![block](图2.PNG)

- inline 值：
![inline](图3.PNG)

- inline-block 值：
![inline-block](图4.PNG)

# 二 position
可用于弹出的登陆框。（元素叠加）
## 1 定位位置
![position](图5.PNG)

- top/right/bottom/left：
![值含义](图6.PNG)

- z-index:0
`z-index` 是 z 轴上的位置，默认为 0，大的值会覆盖掉小的。
注意父元素的属性（z-index 栈）。

## 2 定位方式
![定位方式](图7.PNG)

- relative：仍在文档流中（会占位），参照物为元素本身。常作为绝对定位元素的参照物（其父元素设置成相对定位）。

- absolute：脱离文档流（相当于浮上来了），宽度默认为内容宽度，参照物为第一个祖先/根元素。

- fixed：脱离文档流，宽度默认为内容宽度，参照物为窗口。

## 3 遮罩
用于登陆框后遮罩整个页面。
```
<div class="mask"></div>

.mask{position:fixed;top:0;left:0;z-index:999;width:100%;height:100%}
```

# 三 float
## 1 float 概念
![float](图8.PNG)
- 脱离文档流，宽度默认为内容宽度，向指定方向一直移动。

- float 的元素在同一文档流中。

- float 元素半脱离文档流（对后续的元素，脱离文档流；对内容，在文档流中）。
![半脱离文档流](图9.PNG)
注：文字没有被遮住（文字是内容），但有一部分被覆盖了。

## 2 clear，清除浮动
> 父级元素内部的子元素是浮动的。脱离文档流性质导致父级元素无法被撑开。此时要使用到 clear 属性。
![示例](图10.PNG)
[clear 属性使用参考博文](https://www.jianshu.com/p/9d6a6fc3e398)

clear 属性规定元素的哪一侧不允许其他浮动元素。
![clear](图11.PNG)

- 使用空白元素达到效果（现在不常用）。

- 使用 clearfix 达到效果：
利用元素半脱离文档流性质（对内容，在文档流中），用 CSS 伪类添加个内容并设置为不可见。
```
/* 父元素使用此 CSS */
.clearfix:after {
	content: ".";
	display: block;
	clear: both;

	height: 0;
	overflow:hidden;
	visibility: hidden;
}

.clearfix{zoom:1;}  /* IE 不支持需要添加此代码 */
```

## 3 两列布局示例
![两列布局示例](图12.PNG)

# 四 flex 弹性布局
## 1 概念
- 一个元素是弹性布局的，则称此元素为 flex container，为弹性容器。
它有两个直接子元素，成为弹性元素。其子元素排列方式如图（主轴，辅轴）。
![flex 弹性布局](图13.PNG)

- 创建弹性容器：`display:flex` 。
弹性容器中的子元素并不都是弹性元素，只有弹性容器中直接的在文档流中的子元素才是弹性元素。

## 2 flex 方向
- flex-direction：
![flex-direction](图14.PNG)

- flex-wrap：
不换行，换行，反向换行。
![flex-wrap](图15.PNG)

- flex-flow：
一次设置两个属性。
![flex-flow](图16.PNG)

- order 排列顺序属性：
默认为 0,order 是相对值，通过大小确定顺序。
![order](图17.PNG)

## 3 flex 弹性
- flex-basis：
默认为主方向的宽/高。
![flex-basis](图18.PNG)

- flex-grow：
![flex-grow](图19.PNG)

- flex-shrink：
与 flex-grow 正好相反，不同之处在于它分配的是负值（超出容器部分），这样原来的子元素会变小。
![flex-shrink](图20.PNG)

- 综合缩写：
![综合缩写](图21.PNG)

## 4 flex 对齐
- justify-content：
设置主轴上的对齐方式。
![justify-content](图22.PNG)

- align-items：
设置辅轴上的对齐方式。
![align-items](图23.PNG)

- align-self：
对容器内单个子元素设置辅轴上的对齐方式。
![align-self](图24.PNG)

- align-content：
容器内有多行，对行设置对齐方式。
![align-content](图25.PNG)

## 5 综合运用
![综合运用](图26.PNG)