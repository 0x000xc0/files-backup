---
title: Win 10 安装 Kali 子系统（WSL）
date: 2018-10-26 02:51:28
tags: 记录小结
---
# 一 WSL 概念
“Windows Subsystem for Linux（WSL）是一个为在 Windows 10上能够原生运行 Linux 二进制可执行文件（ELF 格式）的兼容层。WSL 提供了一个微软开发的 Linux 兼容内核接口。”

# 二 安装子系统 Kali
- 在控制面板 -> 程序 -> 程序和功能 -> 开启或关闭 Windows 功能 -> 打钩 “适用于 Linux 的 Windows 子系统”。

- PowerShell 作为管理员并运行：
```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

- Windows App 商店安装 Kali Linux。

# 三 安装使用 GUI
1. 给子系统 Kali 安装图形界面：
```
wget https://kali.sh/xfce4.sh

sudo sh xfce4.sh   # 等待漫长的安装过程。
```

2. 启动 xrdp 服务：
`sudo /etc/init.d/xrdp start`，会显示服务监听的端口号。

3. 登陆 Kali：
使用 Windows 的远程桌面连接。
地址：`127.0.0.1:3390`。

4. 停止 xfce 会话，返回使用 CMD：
在图形界面点击 log out；
CMD 命令 `sudo /etc/init.d/xrdp stop`。

# 四 补充
开启 SSH，自启动：
```
修改 sshd 配置文件：
vi /etc/ssh/sshd_config
去掉允许授权登陆前的注释；加上 PermitRootLogin yes。

开机自启动：
update-rc.d ssh enable
```