---
title: Java 语言学习（上）
date: 2018-08-08 22:05:17
tags: Java
---
# 一 概述
1. Java 的三个体系：
JavaSE（J2SE)(Java2 Platform Standard Edition，java 平台标准版）
JavaEE (J2EE)(Java 2 Platform,Enterprise Edition，java 平台企业版)
JavaME (J2ME)(Java 2 Platform Micro Edition，java 平台微型版)

SE 桌面程序开发；EE 适合网络服务的开发；ME 适合小规模的嵌入式开发。

2. 环境变量配置：
（Windows 10 安装 jdk1.8.0_172）
下载 JDK 安装。
新建变量名为 `JAVA_HOME` ，值为 `C:\Program Files\Java\jdk1.8.0_172` （JDK 的安装目录）。
新建变量名为 `CLASSPATH` ，值为 `.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar` 。
已有的变量名 `path` ，值为 `%JAVA_HOME%\bin` 和 `%JAVA_HOME%\jre\bin`。

3. 验证成功配置和安装：
命令行分别输入 `java -version` 和 `javac -version` 。
![验证成功](图1.PNG)