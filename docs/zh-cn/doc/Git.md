# 什么是 Git

## 概述

![img](https://www.funtl.com/assets/f7246b600c338744a9591cd7530fd9f9d62aa0f8.png)

- Git 是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。
- Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。
- Git 与常用的版本控制工具 CVS, Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持。

# 安装 Git

## 下载

下载地址：https://git-scm.com/downloads

## 安装

双击安装文件，然后出现安装向导界面,点击下一步(Next)即可

可以在cmd里面测试是否设置了Path,是否安装成功. 在CMD中输入 git 或者 git --version 试试

# Git 的一般工作流程

- 克隆 Git 资源作为工作目录。
- 在克隆的资源上添加或修改文件。
- 如果其他人修改了，你可以更新资源。
- 在提交前查看修改。
- 提交修改。
- 在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。

![img](https://www.funtl.com/assets/git-process.png)

# Git 的基本操作

## 获取与创建项目命令

### git init

用 git init 在目录中创建新的 Git 仓库。 你可以在任何时候、任何目录中这么做，完全是本地化的。

```text
git init
```

### git clone

使用 git clone 拷贝一个 Git 仓库到本地，让自己能够查看该项目，或者进行修改。

```text
git clone [url]
```

## 基本快照

### git add

git add 命令可将该文件添加到缓存

```text
git add <filename>
```

### git status

git status 以查看在你上次提交之后是否有修改。

```text
git status
git status -s
```

### git diff

执行 git diff 来查看执行 git status 的结果的详细信息。

git diff 命令显示已写入缓存与已修改但尚未写入缓存的改动的区别。git diff 有两个主要的应用场景。

- 尚未缓存的改动：git diff
- 查看已缓存的改动： git diff --cached
- 查看已缓存的与未缓存的所有改动：git diff HEAD
- 显示摘要而非整个 diff：git diff --stat

### git commit

使用 git add 命令将想要快照的内容写入缓存区， 而执行 git commit 将缓存区内容添加到仓库中。

Git 为你的每一个提交都记录你的名字与电子邮箱地址，所以第一步需要配置用户名和邮箱地址。

```text
git config --global user.name 'yourname'
git config --global user.email youremail
```

将文件写入缓存区并提供提交注释

```text
git commit -m 'update message'
```

### git reset HEAD

git reset HEAD 命令用于取消已缓存的内容。

```text
git reset HEAD -- <filename>
```

## 拉取与推送

### git pull

git pull命令用于从另一个存储库或本地分支获取并集成(整合)。git pull命令的作用是：取回远程主机某个分支的更新，再与本地的指定分支合并，它的完整格式稍稍有点复杂。

```text
git pull <远程主机名> <远程分支名>:<本地分支名>
```

将远程存储库中的更改合并到当前分支中。在默认模式下，`git pull`是`git fetch`后跟`git merge FETCH_HEAD`的缩写。更准确地说，`git pull`使用给定的参数运行`git fetch`，并调用`git merge`将检索到的分支头合并到当前分支中。

### git push

`git push`命令用于将本地分支的更新，推送到远程主机。它的格式与`git pull`命令相似。

```text
git push <远程主机名> <本地分支名>:<远程分支名>
```

## 标签

### git tag

如果你达到一个重要的阶段，并希望永远记住那个特别的提交快照，你可以使用 `git tag` 给它打上标签。

比如说，我们想为我们的 商城 项目发布一个"1.0.0"版本。 我们可以用 `git tag -a v1.0.0` 命令给最新一次提交打上（HEAD） "v1.0.0" 的标签。

`-a` 选项意为"创建一个带注解的标签"。 不用 -a 选项也可以执行的，但它不会记录这标签是啥时候打的，谁打的，也不会让你添加个标签的注解。 我推荐一直创建带注解的标签。

```text
git tag -a v1.0.0
```

如果我们要查看所有标签可以使用以下命令：

```text
git tag
```

# TortoiseGit 简化 Git 操作

TortoiseGit, 中文名海龟 Git. 海龟 Git 只支持 Windows 系统, 有一个前辈海龟 SVN, TortoiseSVN 和 TortoiseGit 都是非常优秀的开源的版本库客户端. 分为 32 位版与 64 位版.并且支持各种语言,包括简体中文

## 下载

下载地址：https://tortoisegit.org/download/

## 安装

我们需要先安装程序包,然后安装语言包(LanguagePack). 因为TortoiseGit 只是一个程序壳,必须依赖一个 Git Core,也就是上一节我们安装的 Git. 所以安装前请确定已完成上一节的操作. 下面以64位版本为演示(64,32位除文件名不一样,其他的操作都一致)

## 安装语言包

## 配置

在空白处点击鼠标右键, 选择 --> TortoiseGit --> Settings, 然后就可以看到配置界面

选中General,在右边的 Language中选择中文. 不勾选自动升级的复选框,可能还需要指定 Git.exe 文件的路径

再次点击鼠标右键,可以看到弹出菜单中已经变成中文. 原来的 Settings 变成 设置; Clone 变为 克隆

