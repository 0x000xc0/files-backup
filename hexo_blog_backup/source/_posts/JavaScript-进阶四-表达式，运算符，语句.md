---
title: JavaScript 进阶四 表达式，运算符，语句
date: 2018-07-13 18:01:57
tags: JavaScript
---
# 一 表达式
js 短语，解释器可以执行并生成一个值。

# 二 运算符
![运算符](图1.PNG)

1. 关系运算：
- ===
判断类型（主要是原始类型）和值是否相等。
![关系运算 1](图2.PNG)

- ==
判断对象或值是否相等。（会类型转换）
![关系运算 2](图3.PNG)

例外规则：
![例外规则](图4.PNG)

3. 逻辑运算：
- ！
取反。

- &&
并。（注意短路）

- ||
或。（注意短路）

4. 运算符优先级：
![运算符优先级](图5.PNG)

# 三 语句
## 1 条件控制语句
- if else

- switch：
与 C 语言不同在于，case 后可以跟字符串或是表达式，不仅仅是数字或单个字符。

## 2 循环控制语句
- while

- do while

- for

- for/in
遍历对象属性。
```
for(var key in object)
	{
		console.log(key + ":" + object[key]);
	}

/*  
type:benz
color:black
id:12345
*/
```

避免遍历方法的情况：
![避免遍历方法](图6.PNG)

## 3 异常处理语句
`try/catch/finally  throw`
[参考博文 1](https://www.cnblogs.com/knightsu/p/7114914.html)
[参考博文 2](https://www.cnblogs.com/foodoir/p/5720752.html)

- try块：负责捕获异常，一旦try中发现异常，程序的控制权将被移交给catch块中的异常处理程序。

- catch块：如何处理？比如发出警告：提示、检查配置、网络连接，记录错误等。执行完catch块之后程序跳出catch块，继续执行后面的代码。(多个 catch 块处理的异常类,要按照先 catch 子类后 catch 父类的处理方式，因为会就近处理异常,由上自下。)

- finally：最终执行的代码，用于关闭和释放资源。

```
try{
//一些会抛出的异常
}

catch（e）{
//第一个catch
//处理该异常的代码块
}

catch（e）{
//第二个catch，可以有多个catch
//处理该异常的代码块
}

finally{
//最终要执行的代码
} 
```

例子：
```
<script type="text/javascript">
　　try{
　　　　var n = error; //人为引发一个错误，error 未定义就使用
　　}
　　catch(e){
　　　　alert((e.number&0xFFFF) + "号错误：" + e.description); //错误处理：仅输出错误信息
　　}
</script>
```

## 4 with 语句
通常不建议使用。可能会导致执行性能下降。
![with 语句](图7.PNG)

例子：
![例子](图8.PNG)