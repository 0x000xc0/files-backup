---
title: 软件工程 C 实践一 环境搭建
date: 2018-10-08 17:21:09
tags: 软件工程
---
> 此笔记的公开课程为中国科学技术大学的《软件工程（C 编码实战）》

# 开发环境一
1. 准备：VM VirtualBox，及安装好的 Ubuntu 操作系统。

- 新安装的系统没给 root 设置密码会切换用户失败。`sudo passwd root` 给 root 设置密码，后 `su - root` 切换为 root 用户。

- 让 Ubuntu 以 root 身份登陆：[参考文章](https://jingyan.baidu.com/article/fedf0737a7d77835ac897796.html) 。

- 更改命令行的提示符颜色：将配置放在 `~/.bashrc` 文件中。 [参考教程](https://jingyan.baidu.com/article/ac6a9a5e2e2e852b653eac0b.html)

2. 注意虚拟机在网络设置里使用桥接（不使用 Host-only 和 NAT 模式），让虚拟机与主机处于同一局域网，让相互访问更加方便。

3. 使用 Termius 等客户端远程 SSH 登陆虚拟机来使用命令行，更加方便：
- `ssh localhost` 查看是否安装了 SSH；
- 没安装用 `apt-get install openssh-server` 安装；
- 注意源是否可用 `apt-get update`、`apt-get upgrade` 来更新升级，还不行在网上找源添加 `vi /etc/apt/sources.list` 后再次更新升级（多半是源的问题，找到对应操作系统版本的源，推荐清华大学的镜像。）；
- 允许 root 用户远程登陆 `vi /etc/ssh/sshd_config` 加入一行 `PermitRootLogin yes` 并注释掉不用密码登陆；
- 将 SSH 加入开机自启，打开 `/etc/rc.local` 文件，在 exit 0 语句前加入
`/etc/init.d/ssh start`；
- 开启服务与查看状态用 `service ssh start`、`ps -s | grep ssh`；
- 使用命令 `ip addr` 查看 ip 地址，用 Termius 填入相关信息后登陆。

![SSH 成功](图1.PNG)

4. 搭建实验环境：
- 先将宿主机建立用于练习的工程文件夹，在属性中设置为共享（查看本机的共享文件夹在，计算机>管理>共享文件夹）；
- 可能要修复破损的依赖关系 `apt-get -f install`；安装 sambaclient 等 `sudo apt-get install smbclient`、`apt-get install cifs-utils`；
- 然后将此文件夹挂载到虚拟机中,先在 /mnt 目录下创建挂载文件夹 `mkdir sharecode`，挂载命令 `mount -t cifs //192.168.50.114/secode /mnt/sharecode/ -o username=mo,password=12345`，不行加上 `,vers=2.0`。
- 卸载 `umount /mnt/sharecode` ；自动挂载，在文件 /etc/rc.local 添加 `mount -t cifs //192.168.50.114/secode /mnt/sharecode/ -o username=mo,password=12345,vers=2.0`

5. 创建一个 c 文件，编译输出 Hello World。
- 创建编辑文件写程序 `vi test.c` ，保存退出；
- 编译成可执行文件 `gcc test.c -o hello` ；
- 执行该文件 `./hello`（点代表当前目录。）；
- 打包 `tar -cvzf mywork.tar.gz ./hello` ;
- 解压 `tar -xvzf mywork.tar.gz` 。

# 开发环境二
使用 Windows 下的 Eclipse CDT 集成开发环境。

- 在 debug 时遇到 `eclipse No source available for "main() ...` ，先清除，重新构建。
![debug 时遇到问题](图2.PNG)

- printf 打印函数，在 console 窗口中并没有打印出信息来，停止后才会有输出。在 debug 调试时， eclipse 将输出的内容存放到了输出缓存区中，没有及时的输出到控制台。等到调试结束时，再将所有的信息一并打印出来。解决方法：每个 printf 函数之后加上 `fflush(stdout);`，或在 main 函数开始设置缓冲类型 `setvbuf(stdout,NULL,_IONBF,0);`。[参考博文](https://blog.csdn.net/w_virgil/article/details/83088228)。

- 默认生成的是 debug 版本，怎样生成 release 版本或怎样重新生成新的 release 版本：Run -> Runconfiguration，设置 build configuration。
![build configuration](图3.PNG)

- debug 模式下不等待输入问题解决：在 Run -> Debug Configurations -> Debugger 中勾选 use externak console for inferior。在 debug 的时候会弹出一个新的 cmd 窗口供用户输入并显示输出。[参考博文](https://blog.csdn.net/li1914309758/article/details/81487870)

- 代码提示（默认是关闭的）：在 Java 中，Eclipse 可以通过修改增加触发点达到所有字母自动触发，CDT 没有。[参考](https://www.zhihu.com/question/24778450)。