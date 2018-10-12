---
title: Windows 批处理实例 发布博客与备份博文
date: 2018-10-13 02:27:31
tags: 操作系统命令与脚本
---
# 一 发布博客
```
@echo off
rem @author：Marlous 2018/10/13
rem 脚本说明：自动发布博客脚本

rem ---设置---博客所在盘符，目录。
set disk=E:
set blogPath=E:\WorkZone\Repositories\my-blog

%disk%
cd %blogPath%

call  hexo clean
call  hexo g
call  hexo d

pause
```

# 二 备份博文
```
@echo off
rem @author：Marlous 2018/10/13
rem 脚本说明：自动备份博文到备份文件夹，推送到远端仓库。
rem 1.先删除备份文件夹；2.进入备份文件夹盘符，具体位置；3.创建备份文件夹；4.将要备份文件夹内容复制到备份文件夹；5.推送到远端仓库。

rem ---设置---要删除的备份文件夹。
set buckupDocumentPath=E:\WorkZone\Repositories\files-backup\hexo_blog_backup\source
rd /S /Q %buckupDocumentPath%

rem ---设置---进入备份文件夹（被删除）所在盘符。
set disk=E:
%disk%

rem ---设置---,进入备份文件夹（被删除）所在位置。
set buckupDocumentSite=E:\WorkZone\Repositories\files-backup\hexo_blog_backup
cd %buckupDocumentSite%

rem ---设置---创建的备份文件夹名称。
set buckupDocumentName=source
mkdir %buckupDocumentName%

rem 将要备份的文件夹中内容复制到备份文件夹中。
rem ---设置---需要做备份的文件夹路径。
set documentPath=E:\WorkZone\Repositories\my-blog\source
xcopy /E %documentPath% %buckupDocumentPath%

rem 获取系统时间变量，年月日 yyyy/mm/dd，第一个数字为起始，第二个为长度。
set yyyy=%DATE:~0,4%
set mm=%DATE:~5,2%
set dd=%DATE:~8,2%

rem 添加所有文件到缓冲区，做成版本（添加 commit 内容），推送到远程端。
git add -A
git commit -m "v%yyyy%%mm%%dd%"
git push origin master

rem pause>nul 进行从定向，所有的提示都不显示。
pause
```