---
title: 多操作系统安装与引导原理（Windows、Deepin）
date: 2018-10-14 03:53:00
tags: 记录小结
---
# 一 双系统原理
[参考资料](https://wenku.baidu.com/view/a153663583c4bb4cf6ecd101.html?from=search)

1. 操作系统启动过程：

双系统，Grub 来引导：
- Linux 大致启动过程：BIOS > MBR > Grub > 装载 Linux 操作系统。
- Windows 大致启动过程：BIOS > MBR > Grub > BOOTMGR > 装载 Windows 操作系统。

双系统，BOOTMGR 来引导：
- Linux 大致启动过程：BIOS > MBR > BOOTMGR > Grub > 装载 Linux 操作系统。
- Windows 大致启动过程：BIOS > MBR > BOOTMGR > 装载 Windows 操作系统。

解释：
先执行 BIOS 程序去找硬盘；
执行硬盘第一个扇区中 MBR 中的引导代码 boot loader（boot loader 为开机管理程序，Windows 的是 BOOTMGR，Linux 的是 Grub，其功能有三点：直接载入操作系统，提供不同开机选项，转交其他 loader）；
引导操作系统。

补充：
Grub 装在 MBR，即用 Grub 引导（Win 下安装 Linux 的默认方式，会自动修复 Win 的引导问题）；装在其它地方即用 Windows 的来引导的话，需要用 EasyBCD 来设置添加 Linux 的启动项。

2. 分区：
- 一块硬盘进行高级格式化（逻辑分区），方便管理。（低级格式化为分磁道扇区）。主流分区机制为 MBR、GPT 两种。分区个数取决于分区表所能存储的描述磁盘分区的情况。

- 两种模式：BIOS + MBR 或 UEFI + GPT。

- MBR：最多 4 个主分区，或者 3 个主分区加 1 个扩展分区，扩展分区中的逻辑分区可分多个。由磁盘操作系统对硬盘进行初始化时产生的。
![MBR 结构](图1.PNG)

- GPT：一个较新的分区机制，解决了 MBR 很多缺点。向后兼容 MBR，必须在 UEFI 硬件上使用，必须为 64 位系统，Mac、Linux 都支持 GPT 分区格式。

3. Linux 分区：
- / 根分区、swap 交换分区。
- 可以给根分区加密保证物理安全，会丧失性能；可以给引导加密码（可进入单用户模式清除 root 密码）。

# 二 Windows 与 Deepin 双系统安装
> Deepin 官方文档：[文档](https://wiki.deepin.org/wiki/%E5%8E%9F%E7%94%9F%E5%AE%89%E8%A3%85#.E5.A4.9A.E7.A1.AC.E7.9B.98.E6.97.B6.E5.AE.89.E8.A3.85_deepin_.E5.87.BA.E7.8E.B0.E7.9A.84.E6.97.A0.E6.B3.95.E5.BC.95.E5.AF.BC.E7.9A.84.E9.97.AE.E9.A2.98)
安装教程 1 不需要设置引导：[文档](https://jingyan.baidu.com/article/17bd8e524527a985ab2bb82e.html)
安装教程 2 需设置引导：[文档](https://bbs.deepin.org/forum.php?mod=viewthread&tid=158334&extra=)

1. 注意：
- 安装 Linux 时会选择 Grub 安装位置。往 MBR 上装，往 Linux 系统所在的分区的第一个扇区里装。本文是前者，一般前者不会出问题。
- 一般先安装 Windows，后装 Linux，安装 Linux 会自动配置好引导，反过来 Windows 比较霸道会覆盖掉 Linux 的引导。
- Grub 开机启动管理软件更加方便进行多操作系统引导。
- 可用 EasyBCD 备份好引导文件。
- 可以用 Grub 引导；或用 BOOTMGR 引导。

2. 安装过程：Wubi 安装最简单稳妥；U 盘安装；不用 U 盘安装。
- U 盘安装（用 Grub 引导）：Windows 下准备好划分出一定的磁盘空间；用 UltraISO 解压出其中的 deepin-boot-maker.exe，用它来制作 U 盘映像；设置 BIOS 启动顺序等其他配置；安装 Linux 后重启；进入 Windows 用 EasyBCD 配置好引导问题（如果无法进入 Linux 的话需此步）。
- 不用 U 盘（用 BOOTMGR 引导）：（参见安装教程 2）Windows 下准备好划分出一定的磁盘空间；用 EasyBCD 配置好引导问题；重启电脑，就可以找到新添加的 NeoGrub 启动项，选中它启动 live 版本 deepin 安装。
- Wubi 安装：不需要考虑引导，如支持 Wubi 安装。如同 Windows 操作系统里的其他软件一样安装卸载 Linux。

3. 补充：用 U 盘安装后，改为用 BOOTMGR 引导。[启动引导设置、用 BOOTMGR 引导参考文章](https://bbs.deepin.org/forum.php?mod=viewthread&tid=44261)
- 进入 windows，可以设置当前引导为 Bootmgr（已经是的不用），也就是主引导记录 MBR 设置为：Windows NT 6.x MBR，分区引导记录为：BOOTMGR 引导程序，通过用 EasyBCD 和 BOOTICE 都可以。
- 使用 EasyBCD，添加 Linux 启动项。

4. 补充：卸载 Linux。
用 U 盘安装，下次不想使用 Linux 前，用 PE 恢复 MBR 引导（如第三点）或用 EasyUEFI 删除其启动项（前 BIOS + MBR，后 UEFI + GPT 情况），然后进 Windows 删除其分区。参考：[Windows 下卸载](https://wiki.deepin.org/wiki/%E7%B3%BB%E7%BB%9F%E5%8D%B8%E8%BD%BD)

# 三 引导修复及卸载问题
> [参考博文](https://blog.csdn.net/s_gy_zetrov/article/details/51958484)
> [启动引导设置、用 BOOTMGR 引导参考文章](https://bbs.deepin.org/forum.php?mod=viewthread&tid=44261)

## 1 概述
Linux 引导出问题：用 Linux 的 U 盘挂载上 Linux 所在分区，安装 Grub（会自动配置好 Windows 的启动项）；
Windows 引导出问题或两个都出问题：（用 Grub 引导的方式）用 PE 先修复 MBR，后安装 Grub，和配置 Grub 中的 Windows 引导。

## 2 具体实践
1. U 盘 PE 恢复 MBR 引导：
使用 U 启动盘（老毛桃 PE）进入 PE，用 NTBOOTautofix 修复 MBR；然后用 DiskGenius，选择 C 盘，分区 > 激活当前分区 > 保存更改。
删除 Linux 导致 windows 进入不了，也可以使用此方法。

2. U 盘 Linux 系统挂载安装 Grub：
```
# 创建挂载目录
sudo mkdir -p /mnt/temp

# 挂载分区
mount /dev/sda5 /mnt/temp

# 重装 Grub
grub2-install --root-directory=/mnt/temp /dev/sda

# 使生效
sudo apt-get update
```

3. Grub 中添加操作系统启动项：
[自定义菜单项 menuentry 构建参考](https://wenku.baidu.com/view/fcaf77bf960590c69ec37680.html)
多操作系统添加启动项前，可先备份 grub.cfg，要想办法搞清楚每个系统安装位置，可在 Linux 下查看；UUID 查看命令 `sudo blkid`。

可编辑的 Grub 2 配置文件主要包括 /etc/default/grub、和 /etc/grub.d/ 下的各文件。
自定义菜单项一般存放在 /etc/grub.d/40_custom 文件中。编辑完运行 `update-grub` 命令。 

- 构建 menuentry 中的主要项:
```
menuentry "显示的操作系统名" {
	insmod part_msdos
	insmod ntfs            # 文件系统类型。
    set root='hd0,msdos1'  # hd0 为第几块硬盘，1 为第几个分区。
    search --no-floppy --fs-uuid --set=root 7E58BCF758BCAF71   # 磁盘用 UUID 来标记，更精确。
    chainloader +1
}
```

- grub.cfg 中的模板：
```
menuentry 'Deepin 15.7 GNU/Linux' --class deepin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f179bdda-0718-4b4c-8408-4b06f5483456' {
	load_video
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos3'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  f179bdda-0718-4b4c-8408-4b06f5483456
	else
	  search --no-floppy --fs-uuid --set=root f179bdda-0718-4b4c-8408-4b06f5483456
	fi
	linux	/boot/vmlinuz-4.15.0-29deepin-generic root=UUID=f179bdda-0718-4b4c-8408-4b06f5483456 ro  splash quiet
	initrd	/boot/initrd.img-4.15.0-29deepin-generic
}


menuentry 'Windows 10 (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-7E58BCF758BCAF71' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  7E58BCF758BCAF71
	else
	  search --no-floppy --fs-uuid --set=root 7E58BCF758BCAF71
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
```

# 四 小结
BIOS + MBR 模式。

- 搞清楚 MBR 的开机管理程序（boot loader）是 Grub 还是 BOOTMGR；谁调用谁进入第二个操作系统。
开机管理程序是谁，就在谁添加另一个被调用的启动项（是 Grub，会自动设置好；是 BOOTMGR，需要手动进 Win 添加 Linux 启动项）。

- 搞清楚哪个操作系统没法启动，然后修复，详情见第三部分。

# 五 补充：安装多个 Linux 操作系统
> [参考文档](https://wenku.baidu.com/view/2f10944f69eae009581bec21.html)

- Windows 下安装第二个操作系统 Linux 时，会选择 Grub 安装位置。往 MBR 上装，往 Linux 系统所在的分区的第一个扇区里装。一般安装在 MBR。

- MBR 是各个系统的必争之地，尤其是 Windows 一旦重装, MBR 记录就被覆盖, GRUB 也会不见。先后安装两个 Linux，其 Grub 都往 MBR 上装，留下的只会是后来者。需要进入最后安装的 Linux，修改配置 Grub 文件，添加前面安装的操作系统的启动项。

