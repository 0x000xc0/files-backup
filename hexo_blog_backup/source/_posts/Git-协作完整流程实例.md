---
title: Git 协作完整流程实例
date: 2018-09-12 20:31:51
tags: 版本控制
---
# 一 实例描述与大致流程
现有 A、B 两个程序员合作写一个 Hello World 程序。
A 创建主库，B 为协作者。
A 写的程序为 Hello Word；B 将获取后修改为 Hello World 提交；A 创建分支测试，成功后合并到主分支。

已安装好 git，并设置好用户名称、邮箱，SSH 公钥已添加至 GitHub。

1. 程序员 A 本地创建仓库 AREP，远端创建仓库并关联后推送远端,作为中心仓库：
- 本地创建仓库：创建文件夹 AREP，在文件夹内用 Git Bash，`git init`。
- 远端创建仓库：登陆 GitHub 使用网页创建仓库 AREPTEST。
- 本地仓库与远端仓库关联：`git remote add origin git@github.com:Marlous/AREPTEST.git` (一个项目可以同时拥有好几个远端仓库为了能够区分，通常会起不同的名字。通常主远端仓库被称为 origin。
- 获取合并：`git pull origin master 如（git pull [remote-name] [branch-name]）`。
- 编写程序、提交并做成版本：`git add -A 多次添加某个文件（git add <file>）`、`git commit -m "fixed"`。
- 推送到远端：`git push origin master 如（git push [remote-name] [branch-name]）`。

2. 程序员 B 直接将其 clone 到本地，直接提交 A 的远程仓库（或 fork 一份自己的远程仓库，克隆到本地，提交到自己的远程仓库，然后 pull request 到 A 的远程仓库）
- 克隆 A 的仓库：`git clone git@github.com:Marlous/AREPTEST.git`。

3. 程序员 B 创建特性分支，修改文件和提交分支，pull request：
- 程序员 B 创建特性分支并切换分支：`git branch fix`、`git checkout fix`。
- 修改了文件后提交到远端：`git push -u origin fix`，-u 标记将它添加为远程跟踪的分支。（记得 add 和 commit）。
- 如果完成了本次任务再次提交：`git push`。
- 然后在 Git 界面上发起了一个 pull request，一起讨论审核代码。

4. 测试 pull request，并确认合并：
- A 程序员切换到将要被合并的分支（确保代码是最新的用 `git pull`）直接合并 `git pull origin fix`，结束；或创建临时测试分支并切换到临时测试分支。
- 获取同时合并到临时测试分支 `git pull origin fix`（或从 B 的远程仓库获取）。
- 测试没问题后将 fix 分支合并到想要接受合并的分支（同意 pull request），删除临时分支；有问题则反馈问题等待修改完成。

5. 注意：
搞清楚分支情况，搞清楚哪些分支需要更新合并，搞清楚哪个分支向哪个分支更新合并，`git log --graph`。

# 二 两种开发合作模式
参考：[参考问题回答](https://segmentfault.com/q/1010000004362882/a-1020000004415897)

1. 大家使用同一个仓库进行合作开发，分支开发功能，开发完毕，建立 merge request，进行 code review，最终合并到 develop 分支。

2. 大家 fork 仓库，开发完毕后，建立 pull request 到主仓库，由管理代码的人进行合并。

# 三 总结
![流程图](图1.png)
注：两种开发合作模式。
当自己属于主仓库团队项目贡献者一员时，可选择是否 pull request；
不是其中一员则必须 fork 一份到自己的远端仓库，本地修改完，提交到自己的远端仓库，然后从自己的远端仓库通过 pull request 向主仓库贡献代码。

1. 项目管理者创建 master 分支，在 master 分支上创建 dev 分支。

2. 任务分配给不同的人员（不同特性），不同人员克隆 dev 分支（或克隆此项目），在此 dev 分支上创建自己的分支（然后可以提交自己的分支到远端备份让其他成员知道进度，远程跟踪分支 `git push -u origin feature`）。

3. 更新本地 dev 分支，将更新的本地 dev 分支合并到自己的任务分支，得到要推送的分支，然（请求）合并到远端主 dev 分支；也可以 rebase 得到要推送的分支（rebase 和 merge 效果一样，但让之前的分支提交记录消失，让分支线看起来更清晰）。然后见 4。
注：在开始下个任务前或任务中需注意更新自己本地的 dev 分支。

4. 团队需要 pull request 的话，管理者收到 pull request，先在主 dev 分支上创建临时分支，然后获取请求的分支并与临时分支合并，测试没问题即接受请求，有问题则在 pull request 中讨论和解决问题，然后管理者接受合并到主 dev 分支。