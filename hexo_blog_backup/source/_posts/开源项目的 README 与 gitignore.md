---
title: 开源项目的 README 与 gitignore
date: 2018-09-22 20:58:06
tags: 软件工程
---
# 一 README 通用模板
> README 介绍 1：[参考文章](https://zhuanlan.zhihu.com/p/29136209)
README 介绍 2：[参考文章](https://python.freelycode.com/contribution/detail/482)
为 README 添加徽章：[参考博文](https://shikieiki.github.io/2017/03/01/%E4%B8%BA%E4%BD%A0%E7%9A%84Github%E7%94%9F%E6%88%90%E6%BC%82%E4%BA%AE%E7%9A%84%E5%BE%BD%E7%AB%A0%E5%92%8C%E8%BF%9B%E5%BA%A6%E6%9D%A1/)
生成徽章的服务：https://shields.io/#/

内容清单：
```
[icon]

# Name

[Badges]

## Introduction - 介绍
### Summary - 概要
### Features - 特性

## Requirements - 必要条件
环境，对所有项目，和所有子模块和库的描述。

## Configuration - 配置
配置信息。

## Installation - 安装
如何安装。

## Usage - 用法
用法。

## Development - 开发
关于怎样开发的文档信息。（API 等。）

## Changelog - 更新日志
一个简短的历史记录（更改，替换或者其他）。

## FAQ - 常见问题
常见问题。

## Support - 支持
### Dos - 文档
更多文档。
### Contact - 联系
其他联系信息（电子邮件地址，网站，公司名称，地址等）。
提交bug，功能要求，提交补丁，加入邮件列表，得到通知，或加入用户或开发开发区群的介绍。

## Authors and acknowledgment - 贡献者和感谢
作者列表和鸣谢。

## License - 版权信息
版权和许可信息（或阅读许可证）、法律声明。
```

# 二 关于 gitignore
>  Git 忽略文件：[参考博文](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013758404317281e54b6f5375640abbb11e67be4cd49e0000)

将不需要上传的文件写在 .gitignore 文件中。

1. GitHub 上提供的配置文件可以直接使用：https://github.com/github/gitignore

2. 一个工程项目中需要忽略的文件：
- 忽略操作系统自动生成的文件。
- 忽略编译生成的中间文件、可执行文件等。
- 忽略你自己的带有敏感信息的配置文件。

3. .gitignore 文件具体格式：
[参考博文](https://www.jianshu.com/p/e56ab8ca6243)
Git 对于 .gitignore 配置文件是按行（从上到下）进行规则匹配的，这意味着如果前面的规则匹配的范围更大，则后面的规则将不会生效。

- 以斜杠 `/` 开头表示目录；
- 以星号 `*` 通配多个字符；
- 以问号 `?` 通配单个字符；
- 以方括号 `[]` 包含单个字符的匹配列表；
- 以叹号 `!` 表示不忽略(跟踪)匹配到的文件或目录；

4. .gitignore 文件写法：
- 忽略目录（按目录名忽略，所有整个名字的都忽略）：`documentname/*` （或不加星号。）
- 忽略指定目录下所有文件：`/documentname/*`
- 仅忽略当前目录下的文件，不包含子目录：`/documentname`
- 反选，在最前面加 `!`
- 只管理某个文件夹下的某个文件：`/mtk/*`，`!/mtk/one.txt`。