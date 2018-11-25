---
title: PHP 调试环境程序集成包之 phpstudy 与本地 MySQL 使用
date: 2018-11-25 18:14:42
tags: 记录小结
---
# 一 问题描述
- 集成程序包与自己搭建环境之间的关系问题。
- phpStudy 是一个 PHP 调试环境的程序集成包，Apache + PHP + MySQL + phpMyAdmin + ZendOptimizer，一次性安装，无须配置即可使用，是非常方便、好用的 PHP 调试环境，该程序不仅包括 PHP 调试环境，还包括了开发工具、开发手册等。
- 本地已经安装了 MySQL5.7，那么如何通过 phpstudy 来用数据库 Web 图形工具 phpMyAdmin 来管理两个 MySQL（本地安装好的、phpstudy 自带的）呢？

# 二 使用
1. 首先了解概况：
- phpstudy 使用教程，[教程视频](http://www.php.cn/course/639.html)。点击运行后查看是否安装成功，在其他选项菜单 -> php 探针，打开页面在其中检测（MySQL 默认用户名密码为 root）。
- 通过任务管理器快速了解 phpstudy 运行的程序。在其他选项菜单 -> 服务管理器，启动或停止某个服务。
![phpstudy 运行的程序](图1.PNG)

2. 为了使两个 MySQL 服务都能正常使用，可以修改其中一个的端口号，这里修改的是 phpstudy 自带的，改为 3307。注意，使用 phpMyAdmin 来管理两个数据库时，因为配置不同，需要对其进行配置后才能使用。配置在 `phpStudy\PHPTutorial\WWW\phpMyAdmin\libraries\config.default.php`，[配置教程](http://www.php.cn/php-weizijiaocheng-383120.html)。
![修改自带的 MySQL 端口号](图2.PNG)
![修改 phpMyAdmin 配置的 MySQL 端口号](图3.PNG)

3. 使用本地之前安装的 MySQL5.7，启动服务。修改 phpMyAdmin 配置，其端口号为默认的 3306，即可通过 phpMyAdmin 管理本地之前安装的 MySQL5.7。

4. 如果之前安装了 MySQL5.7，后又安装了 phpstudy，但是不想用以前的 MySQL5.7。
- 这时需将原来的数据转移到 phpstudy 下的 MySQL 中。`C:\ProgramData\MySQL\MySQL Server 5.7\Data` 中的文件复制到 `D:\phpStudy\PHPTutorial\MySQL\data`。
- 如果因为 MySQL 版本问题导致无法正常使用的话，直接将 MySQL 程序换掉。`C:\Program Files\MySQL\MySQL Server 5.7` 中的文件复制到 `D:\phpStudy\PHPTutorial\MySQL`，注意保留 data 文件夹，phpstudy 中的 MySQL 内文件包含程序本身和 data（数据库中的数据）。