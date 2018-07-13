---
title: JavaScript 进阶二 内置对象
date: 2018-07-07 17:38:44
tags: JavaScript
---
# 一 简介
![简介](图1.PNG)
![内容](图2.PNG)
以下“常用方法”指“常用的原型方法”。

# 二 Object
1. 概念：
![Object](图3.PNG)

2. 常用方法：
- Object.create
![Object.create](图4.PNG)

- Object.prototype.toString
![Object.prototype.toString](图5.PNG)

- Object.prototype.hasOwnProperty
判断一个属性是自身属性，还是原型链上的属性。
![Object.prototype.hasOwnProperty](图6.PNG)

# 三 String、Number、Boolean
## 1 Boolean
1. 概念：
![Boolean](图7.PNG)

2. 其他类型向布尔型转换：
![其他类型向布尔型转换](图8.PNG)

## 2 String
1. 概念：
![String](图9.PNG)

2. 常用方法：
- String.prototype.indexOf
![String.prototype.indexOf](图10.PNG)

- String.prototype.replace
![String.prototype.replace](图11.PNG)

- String.prototype.split
![String.prototype.split](图12.PNG)

## 3 Number
1. 概念：
![Number](图13.PNG)

2. 常用方法：
- Number.prototype.toFixed
![Number.prototype.toFixed](图14.PNG)

# 四 Array
1. 概念：
![Array](图15.PNG)

2. 常用方法：
- Array.prototype.splice
![Array.prototype.splice](图16.PNG)

- Array.prototype.forEach
![Array.prototype.forEach](图17.PNG)

# 五 Function
1. 概念：
- ![Function](图18.PNG)

- 自定义对象构造器：
![自定义对象构造器](图19.PNG)

2. 常用方法：
- Function.prototype.apply
![Function.prototype.apply](图20.PNG)

- Function.prototype.bind
通过把返回值赋给变量 circlemove，然后用 setTimeout 函数让点推迟一定时间移动。 
![Function.prototype.bind](图21.PNG)

3. 子类构造器：
![子类构造器](图22.PNG)

4. 函数调用的三种方式：
- ()
- apply，call 。指定函数调用者和参数。

5. 函数参数特点：
形参个数不一定等于实参个数。
值传递。
通过参数类型检查实现函数重载。

6. arguments
arguments 对象是在函数执行时函数内部生成的。
![arguments](图23.PNG)

7. 值传递：
![值传递](图24.PNG)

# 六 RegExp、Date、Error
## 1 RegExp
1. 概念：
![RegExp](图25.PNG)

2. 常用方法：
- RegExp.protorype.test
![RegExp.protorype.test](图26.PNG)

## 2 Date
1. 概念：
![Date](图27.PNG)

## 3 Error
N/A

# 七 Math、JSON
## 1 Math
1. 概念：
![Math](图28.PNG)

2. 常用方法：
- Math.floor
![Math.floor](图29.PNG)

- Math.random
![Math.random](图30.PNG)

## 2 JSON
1. 概念：
![JSON](图31.PNG)

2. 常用方法：
- JSON.stringify
![JSON.stringify](图32.PNG)

- JSON.parse
![JSON.parse](图33.PNG)

# 八 全局对象
1. 概念：
![全局对象](图34.PNG)

2. 几个重要的属性和方法：
- NaN
![NaN](图35.PNG)

- parseInt
![parseInt](图36.PNG)

- eval
示例代码，将字符串转成 JSON 对象。
通常不建议使用此函数。
![eval](图37.PNG)

- encodedURIComponent
![encodedURIComponent](图38.PNG)
