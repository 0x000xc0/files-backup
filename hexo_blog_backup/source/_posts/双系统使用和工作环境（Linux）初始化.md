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
Ubuntu 下启用 root 登陆，`sudo gedit /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf`,添加 `greeter-show-manual-login=true` 保存；然后 `gedit /root/.profile` 将文件末尾一句 mesg n 更改为
`tty -s && mesg n`。

- 更改 Grub 默认启动顺序，找到 Grub 配置文件（位置可能不同 Ubuntu 在 `/etc/default/grub`，CentOS 在 `/etc/grub.conf`）；GRUB_DEFAULT=0 设置（大同小异） ，如在选择界面查看为 N，则改为 N-1；设置完 `update-grub` 重新生成启动配置文件。

- Grub 加密：CentOS 下，生成 md5 值 `grub-md5-crypt`（旧版本），在 `/etc/grub.conf` 中添加 `password --md5 生成的md5值`；新版本 Ubuntu 下，生成密码 `grub-mkpasswd-pbkdf2`，在 `/etc/grub.d/00_header` 中添加用户名和密码，[参考教程](https://help.ubuntu.com/community/Grub2/Passwords)。

- 可以再对 BIOS 加密，增强安全性。Grub 加密后仍然何以通过从 U 盘或光盘启动，进入救援模式将 Grub 配置文件中的加密配置删除。

- 设置对硬盘全盘加密，以防硬盘窃取保障安全性，或防止 BIOS 主板上电池放电后设置的密码被清除。

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
安装：（Ubuntu）
可能要修复破损的依赖关系 apt-get -f install；
安装 sambaclient 等 sudo apt-get install smbclient、apt-get install cifs-utils；
或安装 samba（共享自己的文件夹）。

使用其他共享文件夹：
1、然后将此文件夹挂载到虚拟机中，先在 /mnt 目录下创建挂载文件夹 mkdir sharecode；
2、挂载命令 mount -t cifs //192.168.50.114/secode /mnt/sharecode/ -o username=mo,password=12345，不行加上 ,vers=2.0。
3、自动挂载，在文件 /etc/rc.local 添加 mount -t cifs //192.168.50.114/secode /mnt/sharecode/ -o username=mo,password=12345,vers=2.0
4、卸载 umount /mnt/sharecode

共享自己的文件夹:
安装 samba：安装；配置共享文件夹（注意服务和操作系统对文件夹权限问题）；可以添加用户后设置对应的 samba 用户授权（用户需密码才能访问），注意禁止其登陆操作系统只使用 samba 服务。
```