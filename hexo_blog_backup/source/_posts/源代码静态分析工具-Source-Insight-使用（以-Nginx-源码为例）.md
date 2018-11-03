---
title: 源代码静态分析工具 Source Insight 使用（以 Nginx 源码为例）
date: 2018-11-02 20:06:18
tags: 软件工程
---
> 参考：
[Source Insight 导入项目](https://jingyan.baidu.com/article/db55b609a8c6104ba30a2f88.html)
[Source Insight 入门教程](https://blog.csdn.net/it1988888/article/details/8026930)
[Source Insight 4.0 的基本使用方法](https://blog.csdn.net/Cheatscat/article/details/79709616)
[C 语言中 .h 和 .c 文件解析](https://www.cnblogs.com/laojie4321/archive/2012/03/30/2425015.html)
[C 程序怎样组织更有结构性](https://blog.csdn.net/heybeaman/article/details/80227111)
[C 语言头文件组织与包含原则](https://www.cnblogs.com/clover-toeic/archive/2014/05/14/3728026.html)

1. 分析源代码及其结构，下载安装使用源代码静态分析工具 Source Insight。

2. 以分析 Nginx 源代码为例，先 clone 源代码。

3. 了解 Nginx 项目目录结构：
> 参考：[Nginx 项目目录结构参考](http://tengine.taobao.org/book/chapter_09.html)

```
.
├── auto            自动检测系统环境以及编译相关的脚本
│   ├── cc          关于编译器相关的编译选项的检测脚本
│   ├── lib         nginx编译所需要的一些库的检测脚本
│   ├── os          与平台相关的一些系统参数与系统调用相关的检测
│   └── types       与数据类型相关的一些辅助脚本
├── conf            存放默认配置文件，在make install后，会拷贝到安装目录中去
├── contrib         存放一些实用工具，如geo配置生成工具（geo2nginx.pl）
├── html            存放默认的网页文件，在make install后，会拷贝到安装目录中去
├── man             nginx的man手册
└── src             存放nginx的源代码
    ├── core        nginx的核心源代码，包括常用数据结构的定义，以及nginx初始化运行的核心代码如main函数
    ├── event       对系统事件处理机制的封装，以及定时器的实现相关代码
    │   └── modules 不同事件处理方式的模块化，如select、poll、epoll、kqueue等
    ├── http        nginx作为http服务器相关的代码
    │   └── modules 包含http的各种功能模块
    ├── mail        nginx作为邮件代理服务器相关的代码
    ├── misc        一些辅助代码，测试c++头的兼容性，以及对google_perftools的支持
    └── os          主要是对各种不同体系统结构所提供的系统函数的封装，对外提供统一的系统调用接口
```

4. 注：C 的文件组织
- 一般都在头件中进行宏、类型（typedef、struct、union、menu）、数据和函数的声明；而在 C 文件中去进行变量定义，函数实现。或头文件只向外提供接口。
- 需要注意的是 C++ 与 C 语言的多文件并不相同，c++ 头文件中一般放的是类的定义。
- 避免重复定义，开头加上：双下划线多用于警告提示。
```
#ifndef _NGINX_H_INCLUDED_
#define _NGINX_H_INCLUDED_
```

5. Source Insight 添加其它功能窗口与工作界面：
![添加其它功能窗口](图1.PNG)
![工作界面](图2.PNG)

6. 功能窗口简介：
从左到右，从上到下的顺序（3 + 4 个）。

- 符号窗口：
显示的是文档窗口的代码结构，宏、函数声明、结构体、函数等。
![符号窗口](图3.PNG)

- 文档窗口：
显示当前项目窗口中选择的文件。

- 项目窗口：
当前要分析的项目文件。
![项目窗口](图4.PNG)

- 上下文窗口：
这个窗口一般配合关联窗口使用，单机关联窗口的某一项，可以自动在上下文窗口显示该项的上下文，双击上下文内容，则可以在文档窗口打开上下文。
![上下文窗口](图5.PNG)

- 关联窗口：
显示文档中的符号在哪些地方进行了引用。如哪些地方调用了函数，或该函数调用了哪些函数等。关联窗口可以有好多个。（选择后右键查看关联，calls and callers 查看调用与被调用关系。）
![关联窗口](图6.PNG)

- 代码片段窗口：
可以自定义一些代码片段，使用时直接插入即可。

- 粘贴窗口：相当于是定义了好多的粘贴板，一个剪辑相当于一个粘贴板。