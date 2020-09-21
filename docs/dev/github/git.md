# Git 基本使用

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

# Git 分支

## 说明

### master

> - 主分支，用作生产分支，里面的代码是准备部署到生产环境的。master 永远处于稳定状态，这个分支代码可以随时用来部署。
> - master 不提交代码，只合并代码。
> - 合并代码到 master 的操作，由项目对应的集成管理员专人负责。
> - 各分支要定期将 master 代码合并进来，避免后续分支合并到 master 时容易产生冲突，以减轻集成管理员的合并负担。
> - 发版之后，要打 tag 

### develop

> - 从哪个分支分离开来：master
> - 可以合并到哪个分支上：release

Develop（开发）分支，包含了项目最新的功能和代码，所有开发都在 develop 上进行。一般情况下小的修改直接在这个分支上提交代码。

### release

> - 从哪个分支分离开来：develop
> - 必须要合并到哪个分支上：develop 与 master
> - 分支的命名规范：release-*

Release （发行）分支，是为发行正式的生产版本做准备。当开发的差不多了，准备发行就可以创建一个发行分支，在这个分支上可以做一些小的 bug 修复，准备发行的元数据，比如版本号，发行日期之类的。这时候，develop 分支可以继续接收新的提交，为下一个发行做准备。

### feature

> - 从哪个分支分离开来：develop
> - 必须要合并到哪个分支上：develop
> - 分支的命名规范：除了 master，develop，release-，或者 hotfix- 以外的名字都可以

Feature（功能） 分支，有时候也叫 Topic 分支。在这种分支上去开发新的功能。当开发功能的时候，这个功能属于哪个目标发行还不知道。功能如果一直在开发，对应的这个功能分支就可以一直存在，不过到最后还是要合并到 develop 分支上，或者如果不想要开发的这个功能了，可以直接扔掉它。 Feature 分支一般只在开发者的 repo 里，而不是在 origin 上。

### hotfix

> - 从哪个分支分离开来：master
> - 必须要合并到哪个分支上：develop 与 master
> - 分支的命名规范：hotfix-*

当在生产版本上遇到 bug，你需要立即修复的时候，可以创建一个 Hotfix 分支，这个分支可以基于生产环境使用的对应的在 master 分支上的 tag 来创建。

### bugfix

> - 从哪个分支分离开来：master
> - 必须要合并到哪个分支上：develop 与 master
> - 分支的命名规范：hotfix-*

等同于hotfix，只是紧急性没有hotfix那么急迫。

## 分支开发

新版本开始：每个人从最新develop上checkout一个本地分支做开发； 本阶段：禁止直接在develop上开发； 如预期需要协助，可以几个人协同一个远端分支开发；一般会在远端创建version-develop分支

> - 开发周期：一个版本的迭代周期，我们分成3个里程碑(v1, v2, v3);
> - v1版本：开发完成，会merge各自分支到develop；此时develop才进入下一个开发周期； 同时发布v1包给测试； v1的Bug，大家可以选择在develop上直接修改，或者继续在各自的本地分支上修改；
> - v2、v3版本：建议还是在各自的本地分支上继续开发； 完成feature后，同样merge回develop；

## 分支操作

### master

```
# 合并release分支
git checkout master
git pull origin master --rebase
git merge  --no-ff  release
git tag V1.0
git push origin master


# 或者合并hotfix分支
git checkout master
git pull origin master --rebase
git merge  --no-ff  release
git tag V1.1
git push origin master
```

### develop

```
# 创建develop分支(第一次)
git checkout master
git pull origin master --rebase
git checkout -b develop
git push origin develop


# 合并一般的feature分支（推送到远程的feature分支）
git checkout develop
git pull origin develop --rebase
git merge  --no-ff  feature
git push origin develop


# 合并较小的feature分支（不推送到远程的feature分支）
# 1)获取最新develpo分支内容
git checkout develop
git pull origin develop --rebase
# 2）回合develop
git checkout feature
git rebase develop
# 3）merge feature
git merge  --no-ff  feature
git push origin develop
```

### release

```
# 从develop切出realse分支
git checkout -b release

# 合并develop分支
git pull origin release --rebase
git merge  --no-ff  develop
git push origin develop
```

### feature

```
# 从develop切出feature分支
1) #拉取最新develop分支代码
git checkout develop
git pull origin develop  --rebase
2）#切出新的feature分支
git checkout -b feature
3) #合并到develop(merge)
git checkout develop
git pull origin develop  --rebase
git merge --no-ff feature
git push origin develop

3) #合并到develop(rebase)
git checkout develop
git pull origin develop  --rebase
git checkout feature
git rebase develop
# 如果有冲突，修改好后，执行以下（千万不要执行git commit XX）
|| git add .
|| git rebase --continue
git checkout develop
git merge --no-ff feature
git push origin develop
```

### hotfix

```
# 从master切出hotfix分支
git checkout master 
git pull origin master --rebase 
git checkout -b hotfix
# master合并分支hotfix
git checkout master 
git pull origin master --rebase 
git merge --no-ff hotfix 
git tag V1.1 
git push origin master
# develop合并分支hotfix
git checkout develop 
git pull origin develop --rebase 
git merge --no-ff hotfix 
git push origin develop
```

### bugfix

同hotfix，但不一定是从master分支切出.