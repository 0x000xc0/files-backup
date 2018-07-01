---
title: CSS 进阶四 背景
date: 2018-06-29 16:50:43
tags: CSS
---
# 一 背景/图片
## 1 颜色
`background-color`
```
background-color:transparent;  /* 直接设置值的名字 */

background-color:rgb(255,255,0);
/* background-color:rgba(255,255,0,0.5)  a 为透明度，0-1 的浮点数 */
```

## 2 添加
`background-image`
可以同时使用多张图片，后使用的图片在下面的图层。
背景颜色在背景图片下面。
```
background-image:url(pic.jpg),url(pic2.jpg);
background-image:url(http://www.163.com/pic.jpg)
```

## 3 平铺方式
`background-repeat`
space 会留空，round 在平铺时会伸缩，这两种都不会把图截断。
可以写两个值，中间空格隔开表示一个 x 轴的，一个 y 轴的。
可以对多个图片设置，用逗号隔开，不设置的则和前一个图片的设置相同。
![背景图片平铺方式](图1.PNG)

## 4 附着方式
`background-attachment`
```
background-attachment:fixed;  /* 当页面的其余部分滚动时，背景图像不会移动。 */
/* background-attachment:scroll; 默认值,背景图像会随着页面其余部分的滚动而移动。 */
```

## 5 位置
`background-position`
可以是文字值（left,center,right,top,bottom），百分比，也可以是具体位置。
```
background-position:top right;  /* background-position:200px 200px; */
```

- 四个值时的情况：
![四个值](图2.PNG)

- 通过使用负值只显示一部分图片：
![负值只显示一部分](图3.PNG)

## 6 渐变
1. 线性渐变 inear-gradient()
`linear-gradient()`
位置可以为角度,十二点钟向顺时针偏移 `background-image:linear-gradient(45deg,red,blue)`
颜色后加空格加百分比可调整颜色区域。
![线性渐变](图4.PNG)

2. 径向渐变 radial-gradient()
`radial-gradient()`
![径向渐变](图5.PNG)

3. 渐变重复
```
repeating-linear-gradient()
repeating-radial-gradient()
```

## 7 以盒模型区域基准
`background-origin`
默认为 padding-box。
![背景图片所在区域](图6.PNG)

## 8 背景图片盒模型裁剪
`background-clip`
设置的值为保留的部分。可选值有 border-box，padding-box，content-box。

## 9 图片大小
cover 为充满容器，contain 为尽可能大但不超出容器。
![图片大小](图7.PNG)

# 二 综合使用
![综合使用](图8.PNG)