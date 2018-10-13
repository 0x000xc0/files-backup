---
title: 双系统原理与安装（Windows、Deepin）
date: 2018-10-13 21:53:00
tags: 记录小结
---
# 双系统原理
[参考资料](https://wenku.baidu.com/view/a153663583c4bb4cf6ecd101.html?from=search)

1. 操作系统启动过程（双系统）：先执行 BIOS 程序去找硬盘；执行硬盘第一个扇区中 MBR 中的引导代码（boot loader 开机管理程序，其功能直接载入操作系统，提供不同开机选项，转交其他 loader）；MBR 中的 引导代码去执行用来引导 Linux 的 boot loader。

- 双系统 Linux 大致启动过程：BIOS > MBR（boot loader）> Grub > 装载 Linux 操作系统。
- Windows 大致启动过程：BIOS > MBR（boot loader）> 装载 Windows 操作系统。
- Windows 启动具体过程：BIOS > MBR > DPT > pbr > Bootmgr > bcd > Winload.exe > 内核加载 > 整个 Windows。

2. 分区：一块硬盘进行高级格式化（逻辑分区），方便管理。（低级格式化为分磁道扇区）。主流分区机制为 MBR、GPT 两种。分区个数取决于分区表所能存储的描述磁盘分区的情况。

MBR：最多 4 个主分区，或者 3 个主分区加 1 个扩展分区，扩展分区中的逻辑分区可分多个。由磁盘操作系统对硬盘进行初始化时产生的。
![MBR 结构](图1.PNG)

GPT：一个较新的分区机制，解决了 MBR 很多缺点。向后兼容 MBR，必须在 UEFI 硬件上使用，必须为 64 位系统，Mac、Linux 都支持 GPT 分区格式。

3. Linux 分区：
/ 根分区、swap 交换分区。
可以给根分区加密保证物理安全，会丧失性能；可以给引导加密码（可进入单用户模式清除 root 密码）。

# Windows 与 Deepin 双系统安装
> Deepin 官方文档：[文档](https://wiki.deepin.org/wiki/%E5%8E%9F%E7%94%9F%E5%AE%89%E8%A3%85#.E5.A4.9A.E7.A1.AC.E7.9B.98.E6.97.B6.E5.AE.89.E8.A3.85_deepin_.E5.87.BA.E7.8E.B0.E7.9A.84.E6.97.A0.E6.B3.95.E5.BC.95.E5.AF.BC.E7.9A.84.E9.97.AE.E9.A2.98)
安装教程 1 不需要设置引导：[文档](https://jingyan.baidu.com/article/17bd8e524527a985ab2bb82e.html)
安装教程 2 需设置引导：[文档](https://bbs.deepin.org/forum.php?mod=viewthread&tid=158334&extra=)

1. 注意：
- 一般先安装 Windows，后装 Linux，安装 Linux 会自动配置好引导，反过来 Windows 比较霸道会覆盖掉 Linux 的引导。
- 最好用 MBR 去引导 GRUB，以免反过来在删除 Linux 后（由于 GRUB 被删除）出问题,U 盘安装方法会导致反过来。（用 EasyBCD 配置，添加条目，调整 Windows 引导、GRUB 顺序，MbrFix.exe 将 GRUB 覆盖掉。[参考教程](https://www.cnblogs.com/sikewang/p/4609527.html)；删除 Linux 导致 windows 进入不了，也可以进入 PE 系统用 diskgenius 重建 MBR 解决。）
- 用 EasyBCD 备份好引导文件。

2. 安装过程：Wubi 安装最简单稳妥；U 盘安装其次简单；不用 U 盘比较复杂和 Wubi 一样稳妥。

- U 盘安装：Windows 下准备好划分出一定的磁盘空间；用 UltraISO 解压出其中的 deepin-boot-maker.exe，用它来制作 U 盘映像；设置 BIOS 启动顺序等其他配置；安装 Linux 后重启；进入 Windows 用 EasyBCD 配置好引导问题（如果无法进入 Linux 的话需此步，U 盘安装是 Grub 引导 MBR，可用 EasyBCD 重新设置顺序[参考教程](https://www.cnblogs.com/sikewang/p/4609527.html)）。
- 不用 U 盘（参见安装教程 2）：Windows 下准备好划分出一定的磁盘空间；用 EasyBCD 配置好引导问题；重启电脑，就可以找到新添加的 NeoGrub 启动项，选中它启动 live 版本 deepin 安装。
- Wubi 安装：不需要考虑引导，如支持 Wubi 安装。如同 Windows 操作系统里的其他软件一样安装卸载 Linux。

3. 补充引导问题解决方法（EasyBCD 使用）：[参考 1](https://bbs.deepin.org/forum.php?mod=viewthread&tid=158334&extra=)、[参考 2](https://www.cnblogs.com/bluestorm/p/3310941.html) 


