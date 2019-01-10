---
title: DevOps 与 CI/CD 的概念
date: 2018-10-31 15:48:25
tags: 软件工程
---
> 参考：
1、 [一文收录16张DevOps ”拍照神图” ](https://mp.weixin.qq.com/s/wCFM6Ln-iG_G-Um8cad0aA)
2、 [如何理解持续集成、持续交付、持续部署？](https://www.zhihu.com/question/23444990/answer/89426003)
3、 [什么是DevOps？阿里专家为你来解读](https://zhuanlan.zhihu.com/p/26600598)
4、 [给 DevOps 初学者的入门指南](https://zhuanlan.zhihu.com/p/22638204)
5、 [一点都不高大上，手把手教你使用Travis CI实现持续部署](https://zhuanlan.zhihu.com/p/25066056)
6、 [理想化的DevOps流程](https://zhuanlan.zhihu.com/p/31849745)
7、 [腾讯云 DevOps 解决方案](https://cloud.tencent.com/solution/devops)
8、 [自动化打包（持续集成+持续交付+持续部署）](https://www.jianshu.com/p/319bb7d9c250)
9、 [jenkins持续集成原理](https://blog.csdn.net/gc_cg/article/details/68064156)

# 一 概述工作流
整个软件工程从提出需求到最终交付的流程。

## 1 传统工作流
- PD(Demond) ->[ DEV(Coding) -> SCM(Build) -> QA(Test) -> OPS(Deploy) ]-> Release
- PD 提出需求 ->[ 开发者根据需求写代码 -> SCM 拿着代码去打包 -> QA 测试 -> 运维进行上线部署 ]

## 2 DevOps 工作流
DevOps 即更好的优化开发、测试、运维的流程；开发运维一体化，通过高度自动化工具与流程来使得软件构建、测试、发布更加快捷、频繁和可靠。
同时，CI/CD（持续集成/持续部署）可看作传统工作流的增强版；DevOps 可看作是 CI/CD 的增强版。
![DevOps 工作流概述](图1.PNG)
![DevOps 工作流具体](图2.PNG)

## 3 敏捷开发、DevOps、CI/CD 关系
所处的软件生命周期不同。
![敏捷开发、DevOps、CI/CD 关系](图2-1.PNG)

## 4 一些 DevOps 相关服务
- 微软的 App Center
- CircleCI
- Netlify

## 5 自动化打包
引起各种奇怪问题的原因有很多，比如开发环境比较复杂不干净，IDE 的 bug，提交前有一些必要的检查需要做，但是开发时因为各种原因没做，这些机械重复的事情我们可以找一个工具来帮我们完成，而且这个工具跑在一个专门的服务器上，该服务器环境相对干净，可以运行一些自动化操作，而自动编译，代码检查，测试等环节，那么这种东西，就是持续集成。

- 持续集成：
频繁地（一天多次）将代码集成到主干。
要求：一个自动构建过程，包括自动编译、分发、部署和测试等；一个代码存储库，即需要版本控制软件来保障代码的可维护性，同时作为构建过程的素材库；一个持续集成服务器。

- 持续交付：
频繁地将软件的新版本，交付给测试和用户，以供测试和评审。

- 持续部署：
是持续交付的下一步，指的是代码通过以后，自动部署到生产环境。

# 二 DevOps 的技术栈与工具链
> 参考：
1、 [给 DevOps 初学者的入门指南](https://zhuanlan.zhihu.com/p/22638204)

1. 图解工具链：
![图解工具链](图2-2.PNG)

2. 工具链列表：
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
