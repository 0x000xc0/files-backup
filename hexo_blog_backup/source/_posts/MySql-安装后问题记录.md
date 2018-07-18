---
title: MySql 安装后问题记录
date: 2018-07-18 18:15:59
tags: 记录小结
---
之前安装过 MySql，系统还原后重新安装后出现的一些问题。
此次安装时选择安装了所有组件。

1. MySQL Notifier 为辅助工具；MySQL Workbench 为可视化工具。

2. ？ 使用 MySQL 5.7 Command Line Client，打开后出现一条警告：
![警告](图1.PNG)

3. 打开服务，忘记打开服务会在输完密码后闪退。
![打开服务](图2.PNG)

通过 cmd 或 MySQL 5.7 Command Line Client 使用。也可以用可视化工具。
![使用 MySql 1](图3.PNG)
![使用 MySql 2](图4.PNG)

4. 配置环境变量
（安装时没选择自动配置环境变量，为方便现手动配置。）

此电脑（右键）-> 属性 -> 高级系统设置 -> 环境变量。

找到环境变量中的 Path，然后对其编辑，添加 C:\Program Files\MySQL\MySQL Server 5.7\bin，非 Win 10 需要加在前面并加上英文分号。