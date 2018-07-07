---
title: JavaScript 进阶一 概述
date: 2018-07-05 17:47:40
tags: JavaScript
---
# 一 简介
## 1 浏览器中的 JavaScript
![浏览器中的 JS](图1.PNG)

## 2 JavaScript 引入
- 内嵌代码
```
<body>
	<script type="text/javascript">
		document.write("hello world");
	</script>
</body>
```

- 外联文件
```
<body>
	<script type="text/javascript" src="demo.js"></script>
</body>

demo.js 文件名的文件
document.write("hello world");
```

## 3 JavaScript 调试
参考文档：[Firefox Developer Tools 调试器](https://developer.mozilla.org/zh-CN/docs/Tools/Debugger)

# 二 基本语法
 1. 变量标识符命名要求：
字母，下划线，美元符号开头。
由字母，下划线，美元符号，数字组成。

2. 关键字和保留字：
![关键字和保留字](图2.PNG)

3. JavaScript 大小写敏感。

4. 严格模式:
![严格模式](图3.PNG)
![严格模式2](图4.PNG)

6. 注释:
单行注释用 `//`
多行注释用 `/* */`

# 三 类型系统
## 1 基本类型
宿主对象是浏览器为完善 js 运行环境提供的对象（DOM）；
浏览器扩展对象是各个浏览器厂商提供的对象（BOM）。
![基本类型](图5.PNG)

1. 标准类型：
![标准类型](图6.PNG)

- 原始类型与引用类型区别：
应用类型只在栈中保存个地址，指向堆中的具体变量与值；
复制时原始类型在栈中复制了一份，而引用类型栈内存两个变量指向同一个堆中的值（修改会相互影响）。

- undefined：
![undefined](图7.PNG)
undefined -> boolean 为 false；
undefined -> number 为 NaN；
undefined -> string 为 "undefined"。

- Null：
null 表示对象不存在。
null -> boolean 为 false；
null -> number 为 0；
null -> string 为 "null"。

- boolean：
条件语句导致系统执行的隐式转换，字面量或变量定义 `var a =true;`。
布尔值 true -> number 为 1；布尔值 true -> string 为 "null"。
布尔值 false -> number 为 0；布尔值 false -> string 为 "false"。

- string：
由单引号或双引号括起来的字符序列。
空字符串 `""` 转为 boolean 为 false；其他转为 boolean 全为 true。

- number：
![number](图8.PNG)

- object：
Object 是一组属性的集合。
任何 object 值转换为
-> boolean 为 true；
-> number 为 NaN；
-> string 为 "[object Object]"

## 2 类型识别
![类型识别](图9.PNG)
提高稳定性，减少错误。

1. typeof：
![typeof](图10.PNG)

2. Object.prototype.toSting：
![Object.prototype.toSting](图11.PNG)

3. constructor：
![constructor](图12.PNG)

4. instanceof：
![instanceof](图13.PNG)