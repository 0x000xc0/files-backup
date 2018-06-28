---
title: CSS 进阶二 文本
date: 2018-06-28 16:53:32
tags: CSS
---
# 字体
## 字体大小 font-size
![font-size](图1.PNG)
1em = 12px，百分比也以 12px 为基准。1em 取决于 px 设置的大小。

## 字体 font-family
![font-family1](图2.PNG)
![font-family2](图3.PNG)

## 加粗 font-weight
![font-weight](图4.PNG)

## 斜体 font-style
![font-style](图5.PNG)
![line-height](图6.PNG)
数值为数字则直接继承，数值为百分比则先计算再继承。

## 多属性缩写
![多属性缩写](图7.PNG)

## 文字颜色 color
![文字颜色](图8.PNG)
rgba() 中 a 为透明度。0 为全透明，1 为不透明。

# 对齐方式
## 对齐方式 text-align
![text-align](图9.PNG)
justify 为两端对齐。

## 垂直对齐 vertical-align
![vertical-align](图10.PNG)
百分比以行高为参照向上偏移。

## 首行缩进 text-indent
![text-indent](图11.PNG)
百分比以容器宽度为参照。

# 格式处理
## white-space
设置如何处理元素内的空白。
![white-space](图12.PNG)

## 长单词自动换行 word-wrap
![word-wrap](图13.PNG)
设置为 break-word

## 任意字母间换行 word-break
![word-break](图14.PNG)

# 文字修饰
## 文字阴影 text-shadow
![text-shadow](图15.PNG)
三个 px 参数：x 轴偏移，y 轴偏移，模糊半径。

## 文字加线 text-decoration
![text-decoration](图16.PNG)

# 高级设置
## 长文本省略 text-overflow
让长文本不显示全，后面只显示三个省略。注意要配合两个属性使用。
![text-overflow](图17.PNG)

## 定义鼠标图形 cursor
可用于将文本通过 CSS 做成按钮。
![cursor](图18.PNG)
可以是一个图片，为图片时可多用一个做备份用（以防图片不可用）；
auto 为自动变换；
default 为箭头；
none 为消失；
help 为问号；
pointer 为手形状；
zoom-in 为放大镜；
move 在移动一些元素时可以使用。

## 强制继承值 inherit
当值为 inherit 时可强制继承父元素的值。
![inherit](图19.PNG)