---
title: 信息收集（Information Gathering）相关笔记
date: 2018-12-26 19:02:53
tags: 信息安全
---
# 一 补充：Kali Linux 工具分类简介
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

# 二 信息搜集之道经验整理
> 此部分为链接博文的整理小结。
参考：
[我的信息搜集之道](https://www.freebuf.com/articles/web/190403.html)

![信息搜集之道经验整理](图1.PNG)

## 1 首先（域名）
1. whois：
国际域名可以设置隐私保护，国内.cn 等域名是不可以设置隐私保护。
- [站长工具](http://whois.chinaz.com/)
- [微步](https://x.threatbook.cn/)
- Linux whois 命令
- 其他工具

2. 子域名：
- layer 子域名挖掘机，[下载地址](https://www.webshell.cc/6384.html)
- [Lcy 在线子域名爆破工具](https://phpinfo.me/domain/)
- subDomainsBrute 子域名爆破工具，[下载地址](https://github.com/lijiejie/subDomainsBrute)
- 搜索引擎语法，site:xxx.com

3. 备案信息:
国内 ICP 备案信息查询、公安部备案信息查询；国外无需备案。
- [ICP 备案信息查询](http://www.miitbeian.gov.cn/icp/publish/query/icpMemoInfo_showPage.action#)
- [公安部备案信息查询](http://www.beian.gov.cn/portal/recordQuery)

## 2 其次（服务器）
1. DNS 信息：
- Kali（host、dig 命令）
- Windows（nslookup 命令）
- 在线工具：[全球 DNS 搜索引擎](https://dnsdb.io/zh-cn/)，[tool.chinaz](http://tool.chinaz.com/dns/)，[tool.lu](https://tool.lu/dns/)

2. 端口服务：
- Nmap 扫描

3. 真实 IP：
- 二级域名法（一般网站不会所有的二级域名放 CDN）
- 多地 ping，[ping.chinaz](http://ping.chinaz.com/)。IP 不一样，则目标网站肯定使用了 CDN。
- nslookup 法。找国外的比较偏僻的 DNS 解析服务器进行 DNS 查询，大部分 CDN 提供商只针对国内市场，而对国外市场几乎是不做 CDN。
- 通过查看邮件原文来确定 IP 地址。
- RSS 订阅法，同邮件法原理。
- 查看域名历史解析记录，[netcraft.com](https://toolbar.netcraft.com/site_report)，使用 CDN 前的 IP。
- 利用网站漏洞（XSS、命令执行、SSRF、php 探针、phpinfo 页面等）。

## 3 然后（网站程序）
1. 网站架构：
- 操作系统：Nmap、wappalyzer 插件、[云奚](http://www.yunsee.cn/)。
- 中间件信息：wappalyzer 插件、[云奚](http://www.yunsee.cn/)。
- 数据库：wappalyzer 插件、[云奚](http://www.yunsee.cn/)。
- 编程语言：wappalyzer 插件、[云奚](http://www.yunsee.cn/)。

2. 敏感目录及敏感信息、源码泄露（搜索引擎+工具）：
- 御剑 
- 搜索引擎（见 Google 搜索语法）
- BBscan，[Github 项目地址](https://github.com/lijiejie/BBScan)
- GSIL，[Github 项目地址](https://github.com/FeeiCN/GSIL)
- 社交平台（QQ 群、文库、求职网）

3. 脆弱系统（网络空间）：
[博文：Web 大数据工具](https://marlous.github.io/2018/12/09/%E4%BF%A1%E6%81%AF%E5%AE%89%E5%85%A8%E3%80%81CTF%20%E5%85%A5%E9%97%A8%E4%B8%8E%E5%AD%A6%E4%B9%A0%E6%96%B9%E6%B3%95%E7%AC%94%E8%AE%B0%EF%BC%88%E6%8C%81%E7%BB%AD%E6%9B%B4%E6%96%B0%EF%BC%89/#5-Web-%E5%A4%A7%E6%95%B0%E6%8D%AE)
- Shodan 
- FOFA 
- Zoomeye

4. 旁站查询：
- [站长之家在线工具获取旁站](http://s.tool.chinaz.com/same)
- k8 旁站查询

5. C 段查询:
- 北极熊扫描器，[下载地址](http://www.xitongzhijia.net/soft/71774.html)
- Nmap

6. 指纹信息：
通过识别目标网站所使用的 CMS 信息，可以帮助我们进一步了解渗透测试环境。
```
指定路径下指定名称的js文件或代码。

指定路径下指定名称的css文件或代码。

<title> 中的内容，有些程序标题中会带有程序标识。

meta 标记中带程序标识
<meta name=”description”/>
<meta name=”keywords”/>、
<meta name=”generator”/>
<meta name=”author”/>
<meta name=”copyright”/>

display:none 中的版权信息。

页面底部版权信息，关键字 © Powered by 等。

readme.txt、License.txt、help.txt 等文件。

指定路径下指定图片文件，如一些小的图标文件，后台登录页面中的图标文件等，一般管理员不会修改它们。

注释掉的 html 代码中 <!–

http 头的 X-Powered-By 中的值，有的应用程序框架会在此值输出。

cookie 中的关键字。

robots.txt 文件中的关键字。

404 页面。

302 返回时的旗标。
```

- wappalyzer 插件
- [云奚](http://www.yunsee.cn/)
- whatweb 工具

7. 探测 WAF：
WAF 识别大多基于 Headers 头信息。通过发送恶意的内容，对比响应，寻找数据包被拦截、拒绝或者检测到的标识。

- 手工（提交恶意数据） 
- 工具（WAFW00F、Nmap）

## 4 最后（企业方面）
- [天眼查](https://www.tianyancha.com/)
- [启信宝](https://www.qixin.com/)
- [企业信用信息公示系统](http://www.gsxt.gov.cn/index.html)