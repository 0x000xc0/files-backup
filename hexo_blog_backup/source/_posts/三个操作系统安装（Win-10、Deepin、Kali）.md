---
title: 三个操作系统安装（Win 10、Deepin、Kali）
date: 2018-10-28 04:51:21
tags: 记录小结
---
# 一 安装第一个 Linux 系统
- 此篇均为 BIOS 传统模式 + MBR，非 UEFI + GPT。
查看 BIOS 模式：
![查看 BIOS 模式](图1.PNG)

- 已存在 Windows 10，在 Windows 下准备好划分出一定的磁盘空间（用分区魔术师切割并转为主分区。一开始就准备装两个 Linux 的话，直接划两个分区出来。）；用 UltraISO 解压出其中的 deepin-boot-maker.exe，用它来制作 U 盘映像；设置 BIOS 启动顺序等其他配置，安装即可（引导会自动设置好）。Deepin 安装成功。

# 二 安装第二个 Linux 系统
- 先进入 Deeppin，为以防万一和备份一些信息（一般不会有问题，可略过）：
备份 gurb.cfg，查看备份分区情况和 UUID（硬盘分区唯一识别符）。
![分区情况](图2.PNG)
![UUID](图3.PNG)

- 使用 Win32DiskImager-0.9.5（用其它软件写入可能会数据写入出错）将 Kali 镜像写入准备好的 U 盘，注意路径及文件名用英文。

- 用分区魔术师切割一部分空间并转为主分区（之前没预留空间的情况），并重启。
![分区魔术师切割](图4.PNG)
![分区魔术师转为主分区](图5.PNG)

- 重启后因为分区的变化导致 Grub 引导找不到位置而无法正常启动（最好之前预留好空闲分区），进入 grub rescue：
```
# 查看各分区文件系统类型，确定哪个是 Deepin 系统安装位置，文件系统为 ext。
ls
ls (hdx,msdosy)    # x，y 为数字，参见 ls 命令后显示的分区情况。

# 如果之前安装 Linux 时没有分 /boot 分区：
ls (hdx,msdosy)/boot/grub
set root=(hdx,msdosy)
set prefix=(hdx,msdosy)/boot/grub
insmod normal
normal

# 如果之前安装 Linux 时分出了 /boot 分区：
ls (hdx,msdosy)/grub
set root=(hdx,msdosy)
set prefix=(hdx,msdosy)/grub
insmod normal
normal

# 回车进入 Linux，命令行输入命令：
sudo update-grub
sudo grub-install /dev/sda
```

- 重启进入 Windows 查看，准备好的空闲分区也已成功：
![空闲分区状态](图6.PNG)

- 重启用 U 盘安装第二个 Linux 操作系统 Kali，完成（Grub 会自动识别并完成引导的配置）。