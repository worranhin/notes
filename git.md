# git

官方参考文档：[Git - Reference (git-scm.com)](https://git-scm.com/docs/)

## 常用指令

### status

检查当前状态，会显示当前 branch，修改的、暂存的文件等

`-s` 后缀可以简短输出

### commit

`--amend`  `commit`到上一次提交

### diff

显示文件工作区与暂存区的改变

`--staged` 后缀显示文件暂存区与上次提交的改变

### rm

删除文件

`--cached` 在本地保留但在 git 中删除

### mv

`mv file_from file_to` 可以用来改名

### log

显示历史提交记录

`-<num>` 指定现实的条目数

`--stat` 显示摘要数据

`-p` 显示详细更改

`--pretty=oneline` 在一行中显示一条提交记录

`--decorate` 可以显示分支指向

此外还有更多有意思的显示格式可以在[这里][log-1]还有[这里][log-2]查看。

### remote

`git remote add <shortname> <url>` 用于添加新的远程仓库

`git remote show` 可以显示更多信息

`git remote rename A B` 将 A 更名为 B 

### tag

打标签

### branch

查看当前所有的分支。

`--merge` 仅查看已经合并的分支，常用来查看能删除的分支。

`--no-merge` 查看没合并的分支。

`-vv` 后缀能查看分支跟踪的远程分支，并显示领先和落后的状态，一般要在这个操作前 fetch 一下。

`-d`  删除分支

`git branch --delete --remotes <remote>/<branch>`  删除跟踪分支

### checkout

`git checkout <branch-name>` 检出分支。

`-b` 创建并检出分支

`git checkout --track origin/serverfix` 检出并跟踪远程分支

`git checkout -b sf origin/serverfix`  创建新分支并检出并跟踪

### push

`git push <remote> <branch>`  推送分支

`git push origin --delete serverfix`  删除远程分支

### fetch

抓取远程分支

`-p`  删除没用的跟踪分支

### reset

版本回退

```bash
git reset --hard HEAD^  # 回退到上一个版本
git reset --hard HEAD~10 # 回退 10 个版本
```

## 一些支持 git 的平台

[这个网站](https://git.wiki.kernel.org/index.php/GitHosting) 上罗列了一些支持托管 git 的平台。

[log-1]: https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E6%9F%A5%E7%9C%8B%E6%8F%90%E4%BA%A4%E5%8E%86%E5%8F%B2#log_options
[log-2]: https://git-scm.com/book/zh/v2/ch00/limit_options

## git 工作流

![[Pasted image 20220412221449.png]]
