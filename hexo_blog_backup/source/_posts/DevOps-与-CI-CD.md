---
title: DevOps 与 CI/CD
date: 2018-10-31 15:48:25
tags: 软件工程
---
> 参考：
[如何理解持续集成、持续交付、持续部署？](https://www.zhihu.com/question/23444990/answer/89426003)
[什么是DevOps？阿里专家为你来解读](https://zhuanlan.zhihu.com/p/26600598)
[给 DevOps 初学者的入门指南](https://zhuanlan.zhihu.com/p/22638204)
[一点都不高大上，手把手教你使用Travis CI实现持续部署](https://zhuanlan.zhihu.com/p/25066056)
[理想化的DevOps流程](https://zhuanlan.zhihu.com/p/31849745)
[腾讯云 DevOps 解决方案](https://cloud.tencent.com/solution/devops)

# 一 概述工作流
整个软件工程从提出需求到最终交付的流程。

1. 传统工作流：
- PD(Demond) ->[ DEV(Coding) -> SCM(Build) -> QA(Test) -> OPS(Deploy) ]-> Release
- PD 提出需求 ->[ 开发者根据需求写代码 -> SCM 拿着代码去打包 -> QA 测试 -> 运维进行上线部署 ]

2. DevOps 工作流：
DevOps 即更好的优化开发、测试、运维的流程；开发运维一体化，通过高度自动化工具与流程来使得软件构建、测试、发布更加快捷、频繁和可靠。
同时，CI/CD（持续集成/持续部署）可看作传统工作流的增强版；DevOps 可看作是 CI/CD 的增强版。
![DevOps 工作流概述](图1.PNG)
![DevOps 工作流具体](图2.PNG)

# 二 DevOps 的技术栈与工具链
> [参考](https://zhuanlan.zhihu.com/p/22638204)

- 版本控制&协作开发：GitHub、GitLab、BitBucket、SubVersion、Coding、Bazaar
- 自动化构建和测试: Apache Ant、Maven 、Selenium、PyUnit、QUnit、JMeter、Gradle、PHPUnit
- 持续集成&交付:Jenkins、Capistrano、BuildBot、Fabric、Tinderbox、Travis CI、flow.ci Continuum、LuntBuild、CruiseControl、Integrity、Gump、Go
- 容器平台: Docker、Rocket、Ubuntu（LXC）、第三方厂商如（AWS/阿里云）
- 配置管理：Chef、Puppet、CFengine、Bash、Rudder、Powershell、RunDeck、Saltstack、Ansible
- 微服务平台：OpenShift、Cloud Foundry、Kubernetes、Mesosphere
- 服务开通：Puppet、Docker Swarm、Vagrant、Powershell、OpenStack Heat
- 日志管理：Logstash、CollectD、StatsD
- 监控，警告&分析：Nagios、Ganglia、Sensu、zabbix、ICINGA、Graphite、Kibana

# 三 DevOps 知识图谱
> 参见 GitHub 项目 developer-roadmap：[链接](https://github.com/kamranahmedse/developer-roadmap)

![DevOps 知识图谱](图3.PNG)

# 四 打造自己的 DevOps
> [持续集成实践参考](https://www.cnblogs.com/Leo_wl/p/4728745.html)
[flow.ci + Github + Slack 一步步搭建 Python 自动化持续集成](https://www.jianshu.com/p/67286ee91252)
[持续部署实践参考](https://zhuanlan.zhihu.com/p/25066056)
