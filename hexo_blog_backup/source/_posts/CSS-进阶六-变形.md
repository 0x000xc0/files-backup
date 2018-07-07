---
title: CSS 进阶六 变形
date: 2018-07-02 17:39:35
tags: CSS
---
# 一 2D 变形
## 1 transform 属性
none 为不做变换，其他可使用为下方法。
其中平移，缩放，倾斜都可以有 x，y 轴。
```
<body style="transform:rotate(180deg);">  /*  将网页旋转 180 度 */
```

- 旋转
`rotate() 方法`
正值为顺时针，负值为逆时针。如 `transform:rotate(120deg);`

- 平移
`translate() 方法`
![translate](图1.PNG)

- 缩放
`scale() 方法`
以中心点为原点。
![scale](图2.PNG)

- 倾斜
`skew() 方法`
向 x 轴倾斜，逆时针；向 y 轴倾斜，顺时钟。两个都向第四象限。
负值则相反。
![skew](图3.PNG)

- 综合运用
注意：多个方法之间用空格隔开；多个方法顺序不同结果可能会不同。
![综合运用](图4.PNG)

## 2 transform-origin 属性
设置坐标轴的原点相对于容器的位置。
默认为 `transform-origin:50% 50%` ；可以为三个值，分别代表 x，y，z 轴。
![transform-origin](图5.PNG)

# 二 3D 变形
## 1 perspective 属性
none 为不做透视；也可以为数值表示眼睛到物体的距离（数值越小越近，透视效果越明显）。
当为元素定义 perspective 属性时，其子元素会获得透视效果，而不是元素本身。
```
<pre style="transform:rotateY(45deg);"></pre>
/* 不加透视会看上去像是宽度发生变化。 */
```

![perspective](图6.PNG)

## 2 perspective-origin 属性
设置 3D 元素的基点位置（视觉位置角度），默认为 50% 50%。
![perspective-origin](图7.PNG)

## 3 transform 属性下的 3D 方法
- 3D 移动：
`translate3d() 方法`
![translate3d](图8.PNG)

- 3D 缩放：
`scale3d() 方法`
![scale3d](图9.PNG)

- 3D 旋转：
`rotate3d() 方法`
以某个轴为轴心旋转。
![rotate3d](图10.PNG)

## 4 transform-style 属性
有两个值，flat 为扁平化，preserve-3d 为保留 3D 空间。
![transform-style](图11.PNG)

## 5 backface-visibility 属性
![backface-visibility](图12.PNG)