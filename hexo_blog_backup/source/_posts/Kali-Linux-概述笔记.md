---
title: Kali Linux 概述笔记
date: 2019-01-01 01:36:49
tags: Kali
---

# 一 关于 Kali Linux 的学习资料
1. 文档书籍：
- Kali Linux 官方文档，[链接](https://www.kali.org/kali-linux-documentation/)
- kali linux 工具相关：[工具使用说明书链接](https://tools.kali.org/tools-listing)，[补充：Kali 工具页面链接](https://tools.kali.org/)，[kali 工具列表中文解释](https://blog.csdn.net/jayjaydream/article/details/82945384)
- 《Kali Linux大揭秘：深入掌握渗透测试平台》，[豆瓣读书链接](https://book.douban.com/subject/30309211/)
- Kali 渗透测试（大学霸），[链接](http://www.daxueba.net/?page_id=2108)
- Kali Linux web 渗透测试经典视频，[链接](https://www.bilibili.com/video/av23312845?from=search&seid=1344609958529235591)
- [GitHub：Awesome Penetration Testing](https://github.com/enaqx/awesome-pentest)
- [GitHub：Kali Linux工具文档翻译计划](https://github.com/Jack-Liang/kalitools)
- [GitHub：开始学习 Kali Linux](https://github.com/tiancode/learn-hacking)

2. 资源：
- [PentestBox：Windows 平台下预配置的便携式开源渗透测试环境](https://pentestbox.org/zh/)

# 二 Kali Linux 工具分类简介
- Information Gathering（信息收集）
- Vulnerability Analysis（漏洞分析）
- Web Applications Analysis（Web 程序分析）
- Database Assessment（数据库评估）
- Password Attacks（密码攻击）
- Wireless Attacks（无线攻击）
- Reverse Engineering（逆向工程）
- Exploitation Tools（漏洞利用工具集）
- Sniffing & Spoofing（嗅探/欺骗）
- Post Exploitation（权限维持）
- Forensics Tools（数字取证）
- Reporting Tools（报告工具集）
- Social Engineering Tools（社会工程学工具）
- System Services（系统服务）

# 三 各工具功能概述
## 1 Information Gathering（信息收集）
1. dmitry：
- 参考文档：
[DMitry Package Description](https://tools.kali.org/information-gathering/dmitry)；[DMitry 介绍](https://github.com/Marlous/kalitools/blob/master/Information%20Gathering/DMitry.md)。
- 简介：
DMitry(Deepmagic Information Gathering Tools 深度信息收集工具)是一个linux下用C语言写的工具。它能够尽可能的获取指定主机目标的信息。基础功能是获取目标的子域名，Email地址，运行时间相关信息，tcp端口，whois信息等等。
- 评价等：
whois 查询/子域名收集/端口扫描；whois并不简单明了，子域名和邮箱依赖google，端口扫描速度一般。

2. dnmap：
- 参考文档：
[dnmap Package Description](https://tools.kali.org/information-gathering/dnmap)；[dnmap 介绍](https://github.com/Marlous/kalitools/blob/master/Information%20Gathering/dnmap.md)。
- 简介：
dnmap（distributed nmap）是一款基于nmap的分布式扫描工具，它能够用一个集群来对另外一个大型集群网络进行扫描。 dnmap采用的是客户端/服务器体系结构，服务端主要是用来分发任务和汇总扫描状态，客户端主要用来执行扫描任务和记录自身的扫描状态。 该工具主要用于你想一个大型集群网络进行扫描，你自己拥有一个集群（肉鸡）的资源或者你的小伙伴想帮你的情况。
- 评价等：
用于组建分布式 nmap，dnmap_server 为服务端；dnmap_client为客户端，用起来并不是那么方便，不是实在不行不是很必要。

## 2 Vulnerability Analysis（漏洞分析）