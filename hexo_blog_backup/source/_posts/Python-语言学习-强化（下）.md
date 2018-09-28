---
title: Python 语言学习 强化（下）
date: 2018-09-28 17:00:23
tags: Python
---
# 一 程序开发
## 1 程序设计
1. IPO 模式：
输入，处理，输出。

2. 自顶向下求解问题：
将一个大问题，分解为许多小问题，最后把这些解决的小问题汇总。
![自顶向下设计思想](图1.PNG)
例：![自顶向下设计思想 例](图2.PNG)

3. 自底向上测试问题：
从底层模块开始一个个测试。
通过调用库函数方法，将 `import matchsim` 加载到交互环境对函数测试。

## 2 软件开发方法
1. 内容：程序、数据、文档。

2. 软件开发生命周期：
![软件开发生命周期](图3.PNG)

3. 敏捷开发：
拆分为多个相互联系、独立运行的小项目。软件一直除余可使用的状态。迭代增量开发。
![敏捷开发过程 1](图4.PNG) ![敏捷开发过程 2](图5.PNG)

## 3 面向过程\对象的程序设计
1. 面向过程程序设计：
![面向过程程序设计](图6.PNG)

2. 面向对象程序设计：
内容：对象、状态、行为。（类、属性、方法。）
特点：封装（属性和方法相对独立）、多态（同一函数名启用不同方法）、继承（提升代码复用程度）。

实列：（创建类、对象、属性、方法）
![实列 类定义 1](图7.PNG)
![实列 类定义 2](图8.PNG)
![实列 建立方法](图9.PNG)

# 二 Python 之面向对象
1. Python 官方库索引与安装：
PyPI https://pypi.python.org/

![python 库安装](图10.PNG)
![pip 子命令](图11.PNG)

2. 查看文档：`python -m pydoc -p 端口号` ，然后在浏览器中查看。

3. OS 编程：
目录文件的操作（OS 库）:
不安装 python 环境运行 py 文件，OS 库是自带的库，处理操作系统相关问题。
```
os.getcwd() 获得当前工作目录
os.listdir(path) 返回指定目录下的所有文件和目录名
os.remove() 删除一个文件
os.removedirs(path) 删除多个目录
os.chdir(path) 更改当前目录到指定目录
os.mkdir(path) 新建一个目录
os.rmdir(name) 删除一个目录
os.rename(src, dst) 更改文

Os.path 处理操作系统目录的一个子库
Os.path.isfile() 检验路径是否是一个文件
Os.path.isdir() 判断是否是文件夹
Os.path.exists() 判断路径是否存在
Os.path.split() 返回一个路径的目录名和文件名
os.path.splitext() 分离扩展名
Os.path.dirname 获得路径名
Os.path.basename() 获得文件名
Os.path.getsize() 获得文件大小
Os.path.join(path, name) 返回绝对路径

os.walk(path)用于遍历一个目录，返回一个三元组
root, dirs, files = os.walk(path)
其中，root 是字符串，dirs 和 files 是列表类型，表示 root 
中的所有目录和所有文件
```

程序定时执行（sched 库）：
sched 库用来进行任务调度。
```
s = sched.scheduler() 用来创建一个调度任务。
当需要对一个任务进行时间调度时，用这个库
s.enter(delay, priority, action, argument=()) 创建一个调度事件，argument 中是 action() 的参数部分。

scheduler.run() 运行调度任务中的全部调度事件
scheduler.cancel(event) 取消某个调度事件
```

可执行程序的转换（py2exe 库）：
Windows 平台下，转为 exe 程序，在没有 python 环境下运行。
```
为目标 py 程序写一个发布脚本 setup.py，然后在命令行运行该脚本。
生成的两个目录其中 _pycache_ 为过程文件可删除，dist 目录可整体拷贝到其他系统使用。

setup.py 脚本代码：
from distutils.core import setup
import py2exe

setup(console=['目标文件.py'])
```

4. Office 编程：
需要的库：
xlwt 库，生成 excel 表单，pip 安装；Xlrd 库，读入并处理 excel 表单，pip 安装。
Python-docx 库，创建并更新 word 文件，pip 安装；其 lxml 依赖库用 wheel 安装。
Python-pptx 库，创建并更新 powerpoint 文件，pip 安装。

# 三 交互式图形编程

# 四 数学库使用基础