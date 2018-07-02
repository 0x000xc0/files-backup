---
title: JavaScript 基础三 面向对象与事件处理
date: 2018-06-19 11:23:18
tags: JavaScript
---
# 一 对象
对象是 JavaScript 的一种复合数据类型（一个属性集合），把很多数据集合在一个变量中。
JavaScript 不像其他 OOP 语言有类的概念。

1. 创建对象：
```
var o = new Object();

var ciclr = {x:0,y:0,tadius:2};  // var 对象 = {属性:值,...};
```

2. 访问对象属性：
```
var book = new Object();
book.title = "XXXX";

book.chapter1 = new Object();
book.chapter1.title = "XXX";  //动态加属性。
```

3. 删除对象属性：
```
delete book.chapter1;

book.chapter1 = null;
```

# 二 遍历对象属性
```
for(var x in o)
{
	alert(x+"为"+o[x]);
}  
// o 为创建的对象；x 为属性；o[x] 为属性值。
```

# 三 构造函数
不直接制造对象；通过 this 来定义；没有 return。
```
function Rect(w,h)
{
	this.width = w;
	this.height = h;
	this.area = function()
	{
		return this.width * this.height;
	};
}

var r = new Rect(5,10);
alert(r.area());
```

# 四 原型对象
1. 对象的 prototype 属性指定了它的原型对象，可以用点运算符直接读它的原型对象的属性；
当写这个属性时才在它自己内部产生实际的属性。
（赋新的值才会有自己的，否则使用原型中的值）
```
function Person()
{
	Person.prototype.name = "Mike";
	Person.prototype.job = "Software Engineer";
	Person.prototype.sayName = function()
	{
		alter(this.name);
	};
}

var person1 = new Person(;)
```

2. 组合原型和构造方法:
让一部分不共享，一部分共享。
```
function Person(name,age,job)
{
	this.name = name;
	this.age = age;
	this.job = job;
	this.friends = ["Allen","Jhon"];
}
Person.prototype = {
	constructor : Person,
	sayName : function()
	{
		alert(this.name);
	}
};
```

# 五 浏览器中的 JS
浏览器的全局对象是 window；所有全局变量实际上是 window 的成员。
```
var answer = 12;
alert(window.answer);
```

# 六 事件处理器
1. 例：
```
<p onMouseOver="alert('hi');">
```

2. body 事件：
```
onLoad  // 页面装载完成，显示前要执行的事件。
onUnload  // 关掉之前的事件。
```

3. 简单对话框：
- alert：一个参数，显示警告框的信息；无返回值。
- confirm：一个参数。显示提示框的信息；按确定返回 true，按取消返回 false。
- prompt：两个参数，显示提示输入框的信息，用于显示输入框的默认值；返回用户输入的值，取消返回 null。   

4. 状态栏：
status
```
<p onMouseOver="status='XXX'; onMouseOut="status='';"></p>
```

5. 定时器：
setInterval() //时间间隔。参数为执行的动作，时间。
```
<body onLoad="setInterval('update()',1000);"></body>
```
