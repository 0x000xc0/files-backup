---
title: 双系统使用和工作环境（Linux）初始化
date: 2018-10-14 20:38:30
tags: 记录小结
---
# 一 双系统使用
双系统工作环境（Windows 10 与 Deepin Linux）；Windows 10 环境为主，Deepin Linux 环境为辅。

Deepin Linux 使用 Win 下磁盘存储的目录及文件（Deepin Linux 单工作环境则把存储的目录及文件放在 /home/user 的 Document 文件夹下）。

# 二 工作环境（Linux）初始化
## 1 需要安装的最基本软件
- 蓝牙相关：blueZ、blueman
- openssh-server
- samba 共享相关：sambaclient、cifs-utils

## 2 需要的最基本配置
- 新安装的系统没给 root 设置密码会切换用户失败。`sudo passwd root` 给 root 设置密码，后 `su` 提升权限为 root 用户（`su - root` 切换为全新的 root 用户）。

- 由于网络原因，可能需要更换源。推荐清华大学镜像（如 Ubuntu 的）：https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/

- 更新源与更新软件：`apt-get update`、`apt-get upgrade`

- 配置 SSH 相关：
```
ssh localhost 查看是否安装了 SSH；

没安装用 apt-get install openssh-server 安装；

允许 root 用户远程登陆 vi /etc/ssh/sshd_config 加入一行 PermitRootLogin yes 并注释掉不用密码登陆；

将 SSH 加入开机自启，打开 /etc/rc.local 文件，在 exit 0 语句前加入
/etc/init.d/ssh start；

开启服务与查看状态用 service ssh start、ps -s | grep ssh；

使用命令 ip addr 查看 ip 地址，用 Termius 填入相关信息后登陆。
```

- 蓝牙连接键盘：
```
sudo service bluetooth start
bluetoothctl
power on
agent on
default-agent
scan on
pair [yourDeviceMAC] # 记得输入完授权码后回车。 
```

- 配置文件共享（samba）相关：
```
可能要修复破损的依赖关系 apt-get -f install；

安装 sambaclient 等 sudo apt-get install smbclient、apt-get install cifs-utils；

然后将此文件夹挂载到虚拟机中，先在 /mnt 目录下创建挂载文件夹 mkdir sharecode；

挂载命令 mount -t cifs //192.168.50.114/secode /mnt/sharecode/ -o username=mo,password=12345，不行加上 ,vers=2.0。

自动挂载，在文件 /etc/rc.local 添加 mount -t cifs //192.168.50.114/secode /mnt/sharecode/ -o username=mo,password=12345,vers=2.0

卸载 umount /mnt/sharecode
```