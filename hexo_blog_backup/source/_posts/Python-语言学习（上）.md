---
title: Python 语言学习（上）
date: 2018-09-03 17:40:56
tags: Python
---
> 参考课程：[课程地址](http://www.icourse163.org/course/HIT-1001616002?tid=1002164016)

# 一 概述
1. 使用的 IDE 为 PyCharm，其基本使用教程：[基本使用教程](https://blog.csdn.net/zhusongziye/article/details/79069233)

2. 验证正确安装及配置环境变量：
命令 `python`
![验证正确安装及配置环境变量](图0.PNG)

3. 行注释用 `#`，块注释用 `"""` 包裹。
![注释](图1.PNG)

4. 命令行下运行程序：进入文件所在目录，命令 `python test.py` 。
命令行无需创建文件，立即看到运行结果，适用于语句功能测试；脚本可反复运行，易于编辑，适用于编写大型程序。

# 二 Python 基础概念
## 1 对象和类型
1. 五种基本数据类型：
- 字符串 str：用单引号或双引号表示。
- 整数 int：如 21，025，0x15
- 浮点数 float
- 布尔型 bool：true false 两个值。
- 复数：如 1+1j

2. 查看数据类型函数： `type()`

## 2 运算符与表达式
1. 算术运算符：
- ![算术运算符](图2.PNG)

- 自动类型转换：bool -> int -> float -> complex
布尔值 true 为 1，false 为 0

- 使用其他运算：
引入模块（实现一定功能的脚本集合） `import module_name` ，
查看模块内容 `dir(module_name)` ,
查看帮助 `help(math.sin)` ,
使用其运算，如 `math.sin(100)` `math.pi` 。

2. 关系运算符：
![关系运算](图3.PNG)

3. 逻辑运算符：
![逻辑运算符](图4.PNG)

4. 运算符优先级：
![运算符优先级](图5.PNG)

## 3 变量与简单 I/O
1. 变量：
用来绑定一个对象的标识符。`变量名=对象（数值，表达式等）`

![标识符命名规则](图6.PNG)

2. 简单 I/O，输入：
输入函数 input，读取键盘输入，所有输入作为字符串看待。`input([prompt])` ，可选填提示。
```python
r = float(input('Enter r:'))
area = (math.pi ** 2) * r
print(area)
```
3. 简单 I/O，输出：
`print()` ，将对象值输出到控制台上，多个值用逗号隔开。
如 `print('area of the circle is:', area)` ，其输出结果为 `area of the circle is: 49.34802200544679`

# 三 程序控制结构
## 1 选择结构
1. 单分支结构：
- if 语句：
```
if 条件:
	语句块
其余语句	
```

- if-else 语句：
```
if 条件:
	语句块
else:
	语句块
```

- if 嵌套：
```
if 条件:
	if 条件:
	语句块
```

2. 多分支结构：
```
if 条件:
	语句块
elif 条件:
	语句块
elif 条件:
	语句块
elif 条件:
	语句块
else:
	语句块		
```

## 2 循环结构
1. while 循环：
```
while 条件:
	语句块
```

2. for 循环：
遍历对象 object 中的每个元素，并赋值给 anElement。
```
for anElement in object:
	语句块

例 1+2+3+...+10：
s = 0
for i in range(11)
	s = s + i
print('sum is:',s)
```

# 四 函数与递归函数
## 1 函数
1. 概念：完成特定功能的语句组，作为一个单位使用。

2. 函数定义与调用：
```
定义：
def 函数名(参数):
	语句块

调用：
函数名(实参)
```

3. 变量作用域：局部变量修改并不改变全局变量，若想在函数体内对全局变量修改需添加关键字 global `global x = 2` 。

4. 占位符 `pass` ，用来暂时占据位置。

## 2 递归函数
斐波那契额数列：
```
def fib(n):
	if n == 1 or n == 2:
		return 1
	else:
		return fib(n-1) + fib(n-2)
```