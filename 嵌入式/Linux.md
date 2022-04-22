Linux 是一个开源的 类 UNIX 操作系统。

## 文件系统

### 目录树

Linux 的所有数据都以文件形式呈现，而文件的高效呈现由仰赖于其目录树架构(diretory tree)。

### 挂载

挂载即为将一个目录作为一个磁盘分区的入口。

> 目录树的根目录一定是挂载到某个分区上。

### 分区

- 初次安装建议分为 `/` 和 `Swap` 即可。
- 建议预留一个备用的剩余磁盘容量

### 目录与设备

设备|目录
---|---
SATA硬盘|/dev/sd[a-d]
CDROM|/dev/cdrom
打印机|/dev/lp[0-2]
软盘机|/dev/fd[0-1]

### 读取频繁容量要求大的目录

- /boot
- /
- /home
- /var
- Swap

### 一些特殊的目录

- /usr是Linux的可执行程序及相关的文件摆放的目录，它的容量需求较大
- /home 是使用者的个人资料夹，以 `/home/<username>` 命名


## 切换图形界面与终端界面

通过按 `ctrl + alt + [F1 - F6]` 可以切换各个界面，其中 `F1` 是图形界面，`F2 - F6` 是终端界面。

这六个界面分别称为 tty1 - tty6

如果当前没有图形界面可以用 `startx` 指令启动

## 指令

- `ls`
	显示目录
- `locale`
	: 显示支持语言，若出现乱码，可以把语言改为英文(en_US.utf8)
- `date`
	显示日期与时间
	可以通过 `date +%Y/%m/%d %H:%M` 来指定显示格式
- `cal [month] [year]`
	显示日历
- `bc`
	启用计算器
- `man [command]`
	显示操作说明。  
	可以通过 `/[keyword]` 来搜索关键词
- `info`
	类似 `man` 也是可以查找信息的工具
- `nano`
	一个简单的文本编辑器
- `who`
	显示还有谁在线上
- `netstat -a`
	显示网络连接状态
- `ps -aux`
	查看背景执行程序
- `shutdown`
	关机
- `chgrp`
	改变群组
- `chown`
	改变所有人
- `chmod`
	改变权限
- `cp`
	复制文件
- `rm`
	删除文件
- `mkdir`
	创建文件夹
- `touch`
	创建新文件

## 功能快捷键

- `tab`
	补全功能，按一下自动补全，按两下显示所有可能的结果。补全可以是指令、文件名或参数等。
- `ctrl+c`
	中断目前运行的程序
- `ctrl+d`
	表示输入结束，有时也等同于 `exit`
- `shift+PageUp/down`
	翻页

## 镜像

### CentOS
-   国家高速网络中心：[http://ftp.twaren.net/Linux/CentOS/7/isos/](http://ftp.twaren.net/Linux/CentOS/7/isos/)
-   昆山科技大学：[http://ftp.ksu.edu.tw/FTP/Linux/CentOS/7/isos/](http://ftp.ksu.edu.tw/FTP/Linux/CentOS/7/isos/)
-   CentOS官方网站：[http://mirror.centos.org/centos/7/isos/](http://mirror.centos.org/centos/7/isos/)