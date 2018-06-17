---
title: JavaScript 基础
date: 2018-06-15 18:26:34
tags: JavaScript
---
# 概念
JavaScript 是一种可以在浏览器中运行的脚本语言。
用来实现用户数据交互，数据处理。

JavaScript 不仅可以应用在浏览器，也可应用于服务器，桌面应用（需要 Node.js 这个 JS 运行环境）。跨平台性好。

为了与 HTML 区分，JS 使用单引号包裹参数（也支持双引号）,变量不需要用引号。

变量命名规则：字母，数字，下划线。开头不能出现数字，不能出现关键字。

变量赋值：
```
var out = "Hello";
document.write(out);  /* 写到 HTML，注意：HTML 中键入多个空格键，但最终也只显示一个空格间隙。 */
```

# 计算
JS 中变量是没有类型的，但值是有类型的。

JS 中定义了四种原始数据类型：number，string，boolean，undefined。

# 判断
字符串比较大小与首字母顺序相关，首字母相同则比较下一个字母。
`document.write("Hello > "Hello")` 为 false。

# 循环
while 循环：
先判断（条件为 true 则循环），后执行。

do-while 循环：
先执行，后判断（条件为 true 则循环）。

for 循环：
for ( init; condition; step ){}

break 与 continue：
break 离开此循环。
continue 不执行接下来的语句，执行下一次循环。

# 函数
## 定义函数
`function fun_name(){}` 或 `function fun_name(a,b){}`

## 有返回值的函数
```
function max(a,b){return a>b?a:b;}
function print(s){document.write(s);}

print(max(2,5));
```

## 函数变量
将函数定义成一个对象。
```
var f = new Function("x","y","return x*y");  /* 函数也可以当成参数进行传递。 */
等价于
function f(x,y){return x*y;}
```

## 变量空间
定义在函数外的变量，作用域为整个 HTML 页面。
定义在函数内的变量，作用域为函数内部。

注意：函数内变量只在函数内部起作用（与函数外变量相同也只使用函数内定义的）。JS 只有函数内外这两种作用域，没有更小的作用域了（如更小的语句块内）。

# 数组
用来存放一些数据，特别是每个数据通过索引来访问。

## 几种定义数组方式
```
var score = new Array();  /* 通过索引赋值。score[0] = "hello"; */
var score = new Array(size);
var score = new Array(d1,d2,d3,...,dn);  /* 如果只有一个数字，则表示 size 意思。 */
var score = [d1,d2,...,dn];
```

## 数组的定义
score.length 为占据的空间。如原数组有三个值，现对第五号索引赋值，则长度为 6。
可以通过修改数组长度来抛弃某处之后的值。
score.length 永远比最后一个下标大 1。可向后追加。

## 转换数组为字符串
```
alert(score.toString());
alert(score.valueOf());

alert(score);

alert(score.join(","));
```

## 关于数组的一些操作
堆栈操作：
```
var colors = new Array();
var count = colors.push("red","green");
alert(count);

var item = colors.pop();
alert(item);
```

队列操作：
```
var colors = new Array();
var count = colors.push("red","green");
alert(count);

var item = colors.shift();
alert(item);
```

排序操作
```
var values = [0,4,2,8,5];
values.sort();
alert(values);

var values = [1,2,3,4,5];
values.reverse();  //反转。
alert(values);  //5,4,3,2,1
```
