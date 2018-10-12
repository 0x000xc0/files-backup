---
title: Windows 批处理（Windows 平台）
date: 2018-10-06 01:19:46
tags: 操作系统命令与脚本
---
> 参考文章：http://www.cn-dos.net/newdos/dosuse.htm#dosbat
参考文章：[百度百科](https://baike.baidu.com/item/%E6%89%B9%E5%A4%84%E7%90%86/1448600?fr=aladdin)

# 一 概述
批处理是一种简化的脚本语言，也称作宏。它应用于 DOS 和 Windows 系统中，它是由 DOS 或者 Windows 系统内嵌的命令解释器（通常是 COMMAND. COM 或者 CMD.EXE）解释运行。类似于 Unix 中的 Shell 脚本。

# 二 具体命令
## 1 命令
- `echo`：
`echo on 或 echo off` 来打开或关闭回显，`echo off` 等效 `@`，但它是一个单独的命令，而不能像@那样放在其它命令之前，常在开头用 `@echo off` 不显示批处理过程。
显示指定的信息。通常显示在屏幕上。在实际应用中我们会把这条命令和重定向符号结合来实现输入一些命令到特定的文件中。

- `rem`：
用来注释。

- `pause`：
暂停，会挂起批处理。显示 Press any key to continue

- `call`：
从一个批处理程序调用另一个批处理程序，调用完后继续执行原来的批文件,是调用，可以相互传值。
例 `call c:\document\test.bat`

- `start`
调用外部程序，所有的 DOS 命令和命令行程序都可以由 start 命令来调用，是执行，只能单向传值给被调用程序。
例 `start calc.exe`

- `goto`：
程序指针跳转到指定的标签，从标签后的第一条命令开始继续执行批处理程序。
例
```
goto labeltest
:labeltest
XXX
```

- `set`：
显示、设置或删除变量。
显示变量：set 或 set s 前者显示批处理当前已定义的所有变量及其值，后者显示所有以 s 开头的变量及值。
设置和调用变量：`set a=7`，调用变量加百分号 `echo %a%`

- `choice`:
选择语句。
例：
```
set /p choice=是否显示当前时间？（y/n)
if /i not %choice% EQU n echo 当前时间是：%date% %time%
pause
```

## 2 符号
- `@`：
不显示此条命令。`echo off` 不显示所有命令。

- `> 和 >>`：
将输出信息重定向到指定的设备或文件。系统默认输出到显示器。后者为追加。

- `<`：
将输入信息来源重定向为指定的设备或文件。系统默认从显示器读取输入信息。
例：从 a.txt 文件输入给变量 input，注意 set 命令有个参数 /p
```
@echo off
set /p input=<a.txt
echo content:
echo %input%
pause
```

- `|`：
管道命令，将管道符号前面命令的输出结果重定向输出到管道符号后面的命令中去，作为后面命令的输入。

- `^`：
转义符。
例 `echo aaaa^>test.txt`

- `&、&&、||`：
`&`：它的作用是用来连接多个 DOS 命令，并把这些命令按顺序执行，而不管是否有命令执行失败。
`&&`：当 `&&` 前面的命令成功执行时，执行 `&&` 后面的命令，否则不执行。
`||`：当 `||` 前面的命令失败时，执行 `||` 后面的命令，否则不执行。

# 三 语句结构
## 1 if 语句
1. 字符串比较：
`/i` 则不区分字符串大小写；选择 `not` 项，则对判断结果进行逻辑非。
== 等于，EQU 等于，NEQ 不等于，LSS 小于，LEQ 小于或等于，GTR 大于，GEQ 大于或等于。
也可以用数学符号，但注意要转义。

2. 存在判断：
存在判断的功能是判断文件或文件夹是否存在。
```
if not exist filename (command1) else (command2)
rem 单个命令可不加括号。 
```

3. 定义判断：
定义判断的功能是判断变量是否存在，即是否已被定义。
例:
```
set var=111
if defined var (echo var=%var%) else echo var尚未定义！
```

4. 结果判断:
```
masm test.asm
if errorlevel 1 pause & edit test.asm
link %1.obj
```
先对源代码进行汇编，如果失败则暂停显示错误信息，并在按任意键后自动进入编辑界面；否则用 link 程序连接生成的 obj 文件，这种用法是先判断前一个命令执行后的返回码（也叫错误码，DOS 程序在运行完后都有返回码），如果和定义的错误码符合（这里定义的错误码为 1），则执行相应的操作（这里相应的操作为 pause & edit %1.asm 部分）。

## for 语句
