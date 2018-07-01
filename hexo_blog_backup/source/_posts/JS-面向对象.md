---
title: JS 面向对象
date: 2018-06-21 19:18:43
tags: JavaScript
---
# 一 面向对象概念
1. 程序设计方法：
面向过程：以过程为中心，自顶向下逐步细化。看成一系列函数的调用。
面向对象：对象作为基本单元，程序分解为数据和相关操作。

2. 概念和特性：
概念：对象，类，属性，方法。
特性：继承，封装，多态。

# 二 constructor 对象构造器
1. 概念：
```
var o = new Array();  // var 对象 = 对象构造器; 
```

2. 使用函数来构造自定义的构造器：
```
function Student(name,class,score)
{
	this.name = name;
	this.class = class;
	this.score = score;
	this.changeScore = function(score)  // 函数类型的属性即方法。
	{
		this.score = score;
	};
}

var student1 = new Student('Amy','2','98');
```

3. 注意：如果构造函数有返回值 `return{}` 则得到的是一个空对象，undefined。

# 三 this
1. 全局环境中的 this：
```
var a = 10;
alert(this.a);
```
this 指向全局对象（在浏览器中是 window 对象，其他环境不同）。

2. constructor 中的 this：
指将要创建出来的新的对象。

3. 函数中的 this：
```
function Person(name,age)
{
	this.name = name;
	this.age = age;
	this.sayHello = function()
	{
		alert('hello,'+this.name);  // 指向函数调用者 p1。
	}
}

var p1 = new Person('lily','20');
p1.sayHello();
```

4. `var o = new Function('alert(this)');` 中的 this：
和全局中的 this 一样，指全局对象。

5. eval() 中的 this:
`eval('alert(this)');` 指代调用上下文中的 this。

6. 小结：
![this 小结](图1.PNG)

7. apply 和 call：
改变其他构造函数中方法的 this 指代，改为参数中的对象。
```
point.move(1,1);  // 其他对象方法

point.move.call(circle,1,1);  // 想使用其他对象的方法
point.move.apply(circle,[1,1]);
```

# 四 原型继承
prototype，让创建的对象共享一个原型的值，不浪费空间（生成多个占用不同空间的值）。
```
function Teacher(){
	this.course = [];
}	
Teacher.prototype = {
	job: 'teacher',
	setName: function(name){
		this.name = name;
	},
	addCourse: function(course){
		this.course.push(course);
	}
}
```

# 五 原型链
## 1 属性查找
在对象本身中找，没有则去其原型中找，没有再去 Object.prototype 中查找。
![属性查找](图2.PNG)

## 2 属性修改
永远只修改对象本身的属性，不管名字来源于对象本身还是其原型。
和原型上的属性相同只会在对象本身上创建一个属性，想修改原型的属性值必须用 `Teacher.prototype.job = 'XXX';`

## 3 属性删除
1. 与修改类似，删除只能删除对象本身的属性，无法删除原型的属性。
```
delete teacher1.job;
//删除对象 teacher1 上的 job 属性。如果这时访问该属性会去原型找到。
```

2. 用 `techer1.hasOwnProperty('job');` 来判断其属性是否来自它本身（true）还是其原型(flase)。

3. ES5 中的原型继承：
直接从原型中创建一个对象，`Object.create(proto[,propertiesObject])` 。
eg. `var teacher2 = Object.create(teacher);` 

# 六 应用
## 1 全局变量
1. 全局变量的三种定义：
- 在最外面定义 `var test = 'some value';`
- window.变量名字 `window.test = 'some value';`
- 在程序内内直接给一个变量赋值，但不用 var 定义。
后两种定义在 window 对象上，可以用 delete 删除。

2. 其他两种全局变量情况：
![全局变量情况](图3.PNG)

## 2 封装
1. 信息隐藏：
![信息隐藏](图4.PNG)

2. Java 中的封装权限：
![Java 中的封装权限](图5.PNG)

3. JavaScript 中的封装：
![JavaScript 中的封装](图6.PNG)

## 3 继承
1. 原型继承：
类继承。
![原型继承](图7.PNG)

2. 原型继承结构：
![原型继承结构](图8.PNG)