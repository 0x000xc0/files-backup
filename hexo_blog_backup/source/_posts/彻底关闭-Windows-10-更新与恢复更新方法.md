---
title: 彻底关闭 Windows 10 更新与恢复更新方法
date: 2018-12-15 21:26:46
tags: 记录小结
---
> 参考资料：
关闭更新：[链接](https://jingyan.baidu.com/article/636f38bb9f7b29d6b84610cf.html)
恢复更新：[链接](https://jingyan.baidu.com/article/3c343ff72eeec70d377963f7.html)

# 一 关闭更新
1. 在服务中找到 windows update 关闭，并在“恢复”选项卡中将第...次失败全设置成无操作（任务管理器中）。
![服务](图1.PNG)

2. 先备份注册表，按 WIN+R，输入 regedit，打开注册表。

3. 设置注册表：
- 找到 HKEY_LOCAL_MACHINE -> SYSTEM -> CurrentControlSet -> Services -> wuauserv 文件夹。
- 在 SYSTEM32 里建个空的文件夹，命名为如 NOUPDATE.exe
- 在刚才找到的注册表中，将 Imagepath 的值改为 `%systemroot%\system32\NOUPDATE.exe`

# 二 恢复更新
1. 如果修改完注册表后，使用系统管理软件清理注册表会导致修改的部分被清理掉。这时想恢复更新，设置中会显示错误代码 0x80070424
![错误代码](图2.PNG)

2. 几个解决方法参考：[链接](https://jingyan.baidu.com/article/3c343ff72eeec70d377963f7.html)
- 运行 Windows Update 疑难解答程序
- 下载后运行 Microsoft Fix it
- 重新启动 Windows Update 服务
- 下载并安装 Windows Update 代理