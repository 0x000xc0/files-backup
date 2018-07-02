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