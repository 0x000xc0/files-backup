---
title: Linux 常用命令
date: 2018-10-02 20:17:35
tags: Linux
---
# 一 用户与用户组

# 二 文件权限

# 三 目录
- 压缩与解压：tar
```
tar
-c 创建.tar格式的文件
-x 解开.tar格式的文件
-f 使用归档文件
-v 显示详细信息
-t 查看包内文件
-j 使用baip2程序
-z 使用gzip程序

-p 打包时保留文件及目录的权限
-P 打包时保留文件及目录的绝对路径
-C 释放的目的地
```

# 四 磁盘

# 五 软件管理
1. 源码包安装软件：（解压、编译、安装）
- 解压：[参考博文](https://blog.csdn.net/xiongchun11/article/details/53939402)
```
*.tar 用 tar –xvf 解压
*.gz 用 gzip -d 或者 gunzip 解压
*.tar.gz 和 *.tgz 用 tar –xzf 解压
*.bz2 用 bzip2 -d 或者用 bunzip2 解压
*.tar.bz2 用 tar –xjf 解压
*.Z 用 uncompress 解压
*.tar.Z 用 tar –xZf 解压
*.rar 用 unrar e 解压
*.zip 用 unzip 解压
```

- 编译与安装：
```
先进入目标软件的文件夹
./configure --prefix=/opt/filename
make
make install
```

2. 编译好的软件压缩包：直接解压后放入 /opt 目录，运行该软件文件夹中的可执行文件。

3. 用包管理：