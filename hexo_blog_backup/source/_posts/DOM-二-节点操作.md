---
title: DOM 二 节点操作
date: 2018-07-27 19:44:09
tags: DOM
---
# 一 获取节点
## 1 获取方法
1. 通过节点关系（父子关系，兄弟关系）获取节点可维护性差。

2. 通过接口获取节点：
`<p id="Id" class="ClassName"></p>`
- getElementById
- getElementByTagName
- getElementByClassName
- querySelector/All

## 2 各接口使用
![示例](图1.PNG)
1. getElementById：
```
element=document.getElementById(id)
```

2. getElementByTagName:
```
collection=element.getElementByTagName(tagName)

collection=element.getElementByTagName("*")  //获取指定元素所有后代元素。
```

3. getElementByClassName：
```
collection=element.getElementByClassName(className)
```

4. querySelector/All:
其返回的值是静态的。
```
var users=document.querySelector("#users")  //选择第一个 id 为 users 的节点。
users.querySelectorAll(".user")  //选择所有类名为 user 的节点。
```

## 3 IE 兼容
![IE 兼容](图2.PNG)

## 4 小结
![小结](图3.PNG)

# 二 创建节点
示例：
![创建节点示例](图4.PNG)

```
element=document.createElement(tagName)

var li=document.creatElement("li")
```

# 三 修改节点
element.textContent 节点及其后代节点的文本内容。
element.innerText 节点及其后代节点的文本内容,不规范，ff 不支持。
```
var a=document.createElement("a");
a.innerText="Xiaoming";
```

# 四 插入节点
1. appendChild:
追加一个节点。
```
var achild=element.appendChild(achild);
```
![追加一个节点](图5.PNG)

2. insertBefore:
在指定节点(referenceChild)前插入一个节点(achild)。
```
var achild=element.insertBefore(achild,referenceChild);

ul.insertBefore(li,ul.firstChild);
```

3. 创建，修改，插入，设置属性：
![创建，修改，插入，设置属性](图6.PNG)

# 五 删除节点
```
child=element.removeChild(child)

var user2=users.getElementByClassName('user')[1];  //先获取准备删除的节点。
user2.parentNode.removeChild(user2);  //删除获取到的节点。
```

# 六 innerHTML 
修改某节点的 HTML。可以直接创建插入节点，批量删除节点。

1. 示例：
先追加一个空 li 节点，后向里加内容。
![修改某节点的 HTML](图7.PNG)

2. 问题：
![问题](图8.PNG)
直接插入整个 HTML 代码会刷新页面，可能导致之前的效果失效。
也可能导致内存泄漏，安全问题。