---
title: Python 爬虫 一 前奏
date: 2018-09-10 19:41:03
tags: 网络爬虫
---
# 一 Requests 库入门
Python 的一个第三方库。

1. Requests 库安装：
管理员权限命令行 `pip install requests` 。

注：
pip 程序在 Python 安装的路径下 `x:\Python xx\Scripts` ；Python 第三方库路径 `x:\Python xx\Lib\site-packages` 。
用 IDE 要搞清楚其用的 Python 是安装在那里的，若命令行正确安装而 IDE 中无法使用，要检查项目设置中使用的 Project Interpreter。
可以用命令行安装库，也可以在 IDE 的菜单设置中安装库。

Pychram 安装库示例：
![Pychram 安装库示例](图1.PNG)

# 二 Requests 库七个主要方法
- 主要方法为 `requests.request()` ，其他六个方法是这个方法的延伸。

- Requests 库的七个主要方法：
![Requests 库的七个主要方法](图2.PNG)

## 1 get() 方法
`r = requests.get(url)`

1. 对象方法属性：
- 结构： Response 对象（被赋值变量） = Request 对象

- Response 对象属性：
![Response 对象属性](图3.PNG)

- Requests 库的异常：
![Requests 库的异常](图4.PNG)

2. 流程：
- 基本流程：先判断 r.status_code 是否为 200，是则成功，不是则失败。

- 爬取网页的通用代码框架：让爬取更稳定可靠。
![爬取网页的通用代码框架](图5.PNG)
