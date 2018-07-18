---
title: Git 常用命令
date: 2018-06-16 23:17:42
tags: Git
---
Git 笔记。
图形化 GUI 工具可以使用 GitHub 官方客户端或 SourceTree 等。

参考文档：
[Git 参考文档](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE) 
[廖雪峰 Git 教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000) 
[Git 命令快速入门](http://blog.jobbole.com/102957/)

# 一 安装配置
通过 Git Bash Here 进行配置。
1. 设置 git 时的用户名称，邮箱：
```
$ git config --global user.name "you account name"
$ git config --global user.email youemail@example.com
```

2. 生成 SSH 公钥，并添加至 GitHub网站。
```
ssh-keygen -t rsa -C "youemail@example.com"
ssh git@github.com  //测试是否成功。
```
3. 可选择更改仓库提交的用户邮箱：
[主题文档教程](https://help.github.com/articles/setting-your-commit-email-address-in-git/)

# 二 Git 获取项目,创建项目
- 将远程的代码 clone 到本地仓库:
克隆获取远程项目：`git clone git://github.com/schacon/grit.git`

- 将本地的代码关联到远程仓库:
初始化一个仓库：`git init` （如果是新的仓库）。
关联远程仓库：`git remote add [shortname] [url]`
// `git remote add origin git@server-name:path/repo-name.git`
(一个项目可以同时拥有好几个远端仓库为了能够区分，通常会起不同的名字。通常主远端仓库被称为origin。)

# 三 获取与推送
有新修改的内容记得 add 和 commit。

1. 获取远程数据：
`git fetch [remote-name]` 不会合并，
`git pull [remote-name] [branch-name]` 会获取并合并。 // `git push origin master`

2. 推送本地数据：
`git push [remote-name] [branch-name]`。  // `git push origin master`

# 四 从创建分支到提交
## 1 创建，切换，合并，删除分支
- 查看分支：`git branch`
- 创建分支：`git branch [name]`
- 切换分支：`git checkout [name]`
- 创建+切换分支：`git checkout -b [name]`
- 合并分支：先切到要合并到的分支，`git merge [name]`
- 删除分支：`git branch -d [name]`

## 2 查看文件
- 查看文件状态用 `git status` 命令。
- 查看具体修改了什么地方，可以用 `git diff` 命令。
- 查看分支合并图 `git log --graph`。

## 3 添加文件
使用命令 `git add <file>` 添加文件到暂存区，注意，可反复多次使用，添加多个文件。
提交目录下的所有内容：`git add -A`

## 4 提交文件
使用 `git commit -m "fixed"` 提交更改，实际上就是把暂存区的所有内容提交到当前分支。
因为我们创建 Git 版本库时，Git 自动为我们创建了唯一一个 master 分支，所以，现在，git commit 就是往 master 分支上提交更改。

# 五 版本退回
1. 穿梭前，用 `git log` 可以查看提交历史，以便确定要回退到哪个版本。

2. 在版本的历史之间穿梭使用命令 `git reset --hard [commit_id]`。

3. 要重返未来，用 `git reflog` 查看命令历史，以便确定要回到未来的哪个版本。

# 六 撤销操作
[Git 参考文档 撤销操作](https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E6%92%A4%E6%B6%88%E6%93%8D%E4%BD%9C)

- 回滚某个文件到之前的版本: `git checkout 09bd8cc1 hello.txt`
- 回滚最新一次提交: `git revert HEAD`
- 回滚某次提交：`git revert b10cc123`

# 七 操作标签
- 命令 `git tag -a v1.4 -m 'my version 1.4'` 创建附注标签。
- 命令 `git push origin [tagname]` 可以推送一个本地标签。
- 命令 `git push origin --tags` 可以推送全部未推送过的本地标签。
- 命令 `git tag -d [tagname]` 可以删除一个本地标签。
- 命令 `git push origin :refs/tags/[tagname]` 可以删除一个远程标签。

# 八 多人协作的工作模式
1. 首先试图用 `git push origin branch-name` 推送自己的修改。

2. 如果推送失败，则因为远程分支比你的本地更新，需要先用 `git pull` 试图合并。

3. 如果合并有冲突，则解决冲突，并在本地提交。

4. 没有冲突或者解决掉冲突后，再用 `git push origin branch-name` 推送就能成功。

5. 如果 `git pull` 提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，用命令 `git branch --set-upstream branch-name origin/branch-name`。

# 九 小结
1. 查看远程库信息，使用 `git remote -v`。

2. 本地新建的分支如果不推送到远程，对其他人就是不可见的。

3. 从本地推送分支，使用 `git push origin branch-name`，如果推送失败，先用 `git pull` 抓取远程的新提交。

4. 在本地创建和远程分支对应的分支，使用 `git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致。

5. 建立本地分支和远程分支的关联，使用 `git branch --set-upstream branch-name origin/branch-name`。

6. 从远程抓取分支，使用 `git pull`，如果有冲突，要先处理冲突。