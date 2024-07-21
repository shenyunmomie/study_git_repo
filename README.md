---
title: git
cover: img/categories_bg.jpg
date: 2024-05-22 11:13:32
updated:
tags: git
categories: git
---

[TOC]

---

# 安装

不同系统安装教程详见

[菜鸟教程-git安装](https://www.runoob.com/git/git-install-setup.html)

# git入门教程

此为使用git相关功能的教程
git是一款**分布式版本控制系统**

## Git核心概念
+ Workspace： 工作区，就是你平时存放项目代码的地方

+ Index / Stage： 暂存区，用于临时存放你的改动，事实上它只是一个文件，保存即将提交到文件列表信息

+ Repository： 仓库区（或版本库），就是安全存放数据的位置，这里面有你提交到所有版本的数据。其中HEAD指向最新放入仓库的版本

+ Remote： 远程仓库，托管代码的服务器，可以简单的认为是你项目组中的一台电脑用于远程数据交换
![image](https://github.com/shenyunmomie/git_teaching/assets/95114009/2ece9523-dcf9-4926-bed3-9df53f6ce6de)
![image](https://github.com/shenyunmomie/git_teaching/assets/95114009/4acafcba-7178-4900-aa2c-36c45bf1a59e)

在初始化git版本库之后会生成一个隐藏的文件 .git ，可以将该文件理解为git的版本库 repository，而我们自己建立的项目文件夹即工作区 working directory ,在.git 文件夹里面还有很多文件，其中有一个index 文件 就是暂存区也可以叫做 stage ,git还为我们自动生成了一个分支master以及指向该分支的指针head

![image](https://github.com/shenyunmomie/git_teaching/assets/95114009/a866d62c-3126-4e6a-96b7-8bf14c1f6cf9)

从图中可以看出来respository包括分支master和stage, working diretory 可以理解为我们打开开发环境如eclipse，里面的内容即工作区的内容，在工作区里面有的代码以及配置文件等我们需要提交到版本库里面，最终是到了分支master上面，暂存区只是一个临时保存修改文件的地方。

 **比喻：**

这就像是搭积木，要搭一个村庄，工作区就是桌子，我们从零件开始一个个搭房子，搭好一个房子后，将其转移到暂存区保存，因为桌子上不安全，会疏忽大意毁掉房子。

搭好所有房子后，全部放到暂存区组合，就完成了村子(一个版本)，这时候能运行就可以提交到仓库区保存，这是第一个版本。

如果不满意需要修改，从仓库区中拉取，到暂存区和工作区，在工作区一个房子一个房子的修改，然后提交暂存区，如果这时觉得某个房子还是不修改好看，则直接回滚。

（未完待改）

## Git工作流程

+ 从远程仓库中克隆 Git 资源作为本地仓库；
+ 从本地仓库中checkout代码然后进行代码修改；
+ 在提交本地仓库前先将代码提交到暂存区；
+ 提交修改，提交到本地仓库；本地仓库中保存修改的各个历史版本；
+ 在需要和团队成员共享代码时，可以将修改代码push到远程仓库。
  ![image](https://github.com/shenyunmomie/git_teaching/assets/95114009/b26afd68-351a-43f2-9911-0fc1084326ba)
  ![image-20240719183245131](https://shenyunmomie.oss-cn-beijing.aliyuncs.com/imags/202407191832288.png)

## git配置
设置用户名称和 email 地址。这是非常重要的，因为每次 Git 提交都会使用用户信息。

```python
git config
git config --global user.name shenyunmomie
git config --global user.email sw18732566535@gmail.com
```

+ --local（默认高优先级）：只会影响到本地仓库
+ --global(中优先级）：只会影响到当前用户的git仓库
+ --system（低优先级）:影响到全系统git仓库

## git术语

- Repository：简称Repo，可以理解为“仓库”，我们的项目就存放在仓库之中。也就是说，如果我们想要建立项目，就得先建立仓库；有多个项目，就建立多个仓库。

- Issues：可以理解为“问题”，举一个简单的例子，如果我们开源一个项目，如果别人看了我们的项目，并且发现了bug，或者感觉那个地方有待改进，他就可以给我们提出Issue，等我们把Issues解决之后，就可以把这些Issues关闭；反之，我们也可以给他人提出Issue。

- Star：可以理解为“点赞”，当我们感觉某一个项目做的比较好之后，就可以为这个项目点赞，而且我们点赞过的项目，都会保存到我们的Star之中，方便我们随时查看。在 GitHub 之中，如果一个项目的点星数能够超百，那么说明这个项目已经很不错了。

- Fork：可以理解为“拉分支”，如果我们对某一个项目比较感兴趣，并且想在此基础之上开发新的功能，这时我们就可以Fork这个项目，这表示复制一个完成相同的项目到我们的 GitHub 账号之中，而且独立于原项目。之后，我们就可以在自己复制的项目中进行开发了。

- Pull Request：可以理解为“提交请求”，此功能是建立在Fork之上的，如果我们Fork了一个项目，对其进行了修改，而且感觉修改的还不错，我们就可以对原项目的拥有者提出一个Pull请求，等其对我们的请求审核，并且通过审核之后，就可以把我们修改过的内容合并到原项目之中，这时我们就成了该项目的贡献者。

- Merge：可以理解为“合并”，如果别人Fork了我们的项目，对其进行了修改，并且提出了Pull请求，这时我们就可以对这个Pull请求进行审核。如果这个Pull请求的内容满足我们的要求，并且跟我们原有的项目没有冲突的话，就可以将其合并到我们的项目之中。当然，是否进行合并，由我们决定。

- Watch：可以理解为“观察”，如果我们Watch了一个项目，之后，如果这个项目有了任何更新，我们都会在第一时候收到该项目的更新通知。

- Gist：如果我们没有项目可以开源或者只是单纯的想分享一些代码片段的话，我们就可以选择Gist。不过说心里话，如果不翻墙的话，Gist并不好用。
  **原文链接**：https://blog.csdn.net/qq_35246620/article/details/68921398

## git常用命令

- **git init**

初始化仓库

- **git status**

检查状态

![image-20240711183020185](https://shenyunmomie.oss-cn-beijing.aliyuncs.com/imags/202407111830170.png)

- **git add**

添加到暂存区，被修改(未暂存)和新创建(未跟踪)的文件，都需要添加到暂存区，后续才可被commit提交。

> 许多软件会自动实现将所有文件git add

- **git commit**

提交本地库，将暂存区的内容，作为一个版本存储到本地仓库

```shell
-m "" :message 提交信息
```

- **git log**

查看Git 仓库提交日志

```shell
git log --stat  # 显示历史，已经变更文件信息
git log -S [keyword] # 搜索提交历史
git log [tag] HEAD --pretty=format:%s  
# 列出从 [tag] 标签到 HEAD 的提交历史，并且只显示每个提交的提交信息
# [tag]: 可以是一个具体的标签名或者提交的哈希值。这个命令会从这个标签或者提交开始向后查找历史记录。
# --pretty=format:%s: 这个选项指定了输出格式，%s 表示只显示提交信息（commit message），省略了作者、日期等其它信息。
git log [tag] HEAD --grep feature  
# 列出从 [tag] 标签到 HEAD 的提交历史中，包含关键词 feature 的提交。
# --grep feature: 这个选项用于根据关键词来过滤提交历史，只显示包含关键词 feature 的提交。
git log --follow [file]
```

- **git blame**

```shell
git blame [filename] # 显示filename文件被什么人在什么时间修改过
```

- **git diff**

```shell
git diff	# 显示工作区中当前文件与暂存区之间的差异。
git diff -cached [filename]  # 显示暂存区与最近一次提交之间的差异。
git diff HEAD  # 显示工作区中当前文件与最后一次提交之间的差异
```

- **git show**

```shell
git show [commitid] [filename]
# 查看特定提交中某个文件的详细变动信息。
```

- **git branch**

查看分支情况

```shell
git branch <--> : 创建分支
git branch -d/-D <-->: delete，删除分支
```

- **git checkout**

切换分支

```shell
-b <--> : 创建并切换到分支
# ！！最好不要使用，有歧义，切换时可以用
git switch []
```

- **git merge**

合并分支

```shell
# 在a分支下
git merge b
# 可将b分支合并到a分支中
```

> 在合并分支的时候，要考虑到两个分支是否有冲突，如果有冲突，则不能直接合并，需要先解决冲突；反之，则可以直接合并。

- **git tag**

标记commit，指向该commit的指针。当前分支有效

```shell
git tag 0623
```

---

- **git push**

推送代码到远程仓库

```shell
git push origin 远程分支名:本地分支名
-- force 强制推送
```

- **git pull**

从远程仓库拉取代码

```shell
git pull origin 远程分支名:本地分支名
```

<<<<<<< HEAD
- **git fetch**

从远程仓库获取最新的更新，区别是fetch只获取，不改变本地仓库的任何内容。

=======
>>>>>>> 2651014a9b3459d04175d339f6bc517959b90ca0
- **git remote**

关联远程仓库

```shell
git remote add origin <url>
git remote -v : 查看远程仓库信息
```

- **rm -rf .git**

删除本地仓库

- **git rm**

文件移除

```shell
git rm [file1] [file2] ...  # 从 Git 跟踪的文件列表中移除指定的文件
git rm --cached [file]  
# 使用 --cached 选项可以将文件从 Git 的暂存区（Index）中移除，但保留工作目录中的实际文件
git rm -f [file]  
# 使用 -f 选项可以强制删除文件，即使该文件已经被修改过且未提交。
git rm -r [dir]
# 使用 -r 选项可以递归地删除目录及其内容。
```

- **git mv**

文件重命名

```shell
git mv [源文件名] [新文件名]  # 将一个已经被 Git 跟踪的文件进行移动或重命名操作
-f #  强制移动或重命名，即使目标文件已存在也强制覆盖
```

- **git checkout**

文件恢复

```shell
git checkout [commit] --[folder]
# 指定提交（[commit]）中的某个目录（[folder]）的内容恢复到当前工作目录中。
git checkout [commit] --[file]
# 指定提交（[commit]）中的某个文件（[file]）的内容恢复到当前工作目录中。
git checkout [file]
# 从当前分支检出（恢复）指定文件 [file] 的命令
```

- **git reset**

```shell
git reset HEAD [file]  # 用于取消暂存（unstage）指定文件 [file] 的命令
```

- **git stash**

保存当前的修改，将工作区和暂存区的状态存储起来一遍后续恢复

```shell
git stash	# 将当前工作目录中的修改（包括已暂存和未暂存的修改）保存到一个新的 stash 条目中
git stash save 'message' # 创建带有描述的stash
git stash push -m 'message' # 保存修改到 stash，并且可以添加一条描述性的消息。
# 比save更新，推荐使用，push允许指定路径，以便只保存指定文件或目录的修改到stash中，而不是全部修改。
git stash list # 显示当前存储的所有 stash 条目的列表。
git stash show [stashid] # 显示指定 stash 条目的具体修改内容。
git stash apply [stashid] # 将指定 stash 条目的修改应用到当前工作目录中，但并不会将 stash 删除。
git stash drop [stashid] # 丢弃指定 stash 条目，从 stash 列表中移除。
git stash clear # 清空所有的 stash 条目，通常在不再需要任何 stash 且希望释放空间时使用。
git stash pop # 应用并移除最新的 stash 条目，相当于 git stash apply 后立即执行 git stash drop。
git stash pop [--index] [stashid] 
# 应用并移除指定的 stash 条目，并且可以选择是否恢复暂存区的修改 
# 默认行为是仅恢复工作目录的修改。
git stash apply [commit] # 将指定的存储（stash）内容应用到当前工作目录的命令。
```

- **git reflog**

查看所有分支点操作记录

- **git rebase**

合并为一个线性分支

```shell
git rebase [branchName]
```

## git配置

- **git config --命令**

```shell
git config --list  #查看配置信息
git config -e --global  #编辑Git配置文件
git config --global user.name ""  #设置作者信息
git config --global user.email ""  #设置作者信息
```



# github远程仓库创建

将本地项目通过git上传到服务器，开源给其他人只需三步：

1. 本地安装git，初始化本地项目
2. 远程服务器安装git，创建远程仓库
3. 将本地项目连接远程仓库

- **本地安装git，初始化本地项目**

安装前面有，主要将初始化本地项目。

初始化本地项目其实就是建立本地仓库，执行`git init`命令就可以，这样你项目所在文件夹就变成了一个git仓库，可以看到里面有.git文件，那个就是存放有个git仓库的内容。

另外讲讲.gitignore文件，它用来忽略不需要版本控制的文件，比如/dist/、.idea、/target/和yml配置文件。在其中添加相对路径即可。

不要忘记先把项目git add。最后只要commit成功就算完成此步。

- **远程服务器安装git，创建远程仓库**

自己搭建的是远程服务器，github也是。

github创建仓库简单，new一下，填入仓库名称即可。

自己的服务器步骤差不多。

- **将本地项目连接远程仓库**

感觉自己好像哪里没整明白，就先说我怎么连接的。

首先在本地仓库目录

```shell
git remote add <自定义远程连接的仓库名> <从github复制的HTTPS或SSH地址>
```

一般这时候还会报错

```shell
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
权限被拒绝（公钥）。
致命：无法从远程存储库中读取。
请确保您拥有正确的访问权限
```

从github主页的setting界面中，选择SSH and GPG keys，然后new了一个SSH keys，这里key值取自本地生成的id_rsa.pub文件，详细命令：

```shell
# 检查
ls ~/.ssh
# 生成
ssh-keygen -t rsa -C "邮箱"
```

![image-20240522185639935](https://shenyunmomie.oss-cn-beijing.aliyuncs.com/imags/202405221856722.png)

<<<<<<< HEAD
## 远程仓库的操作命令

- git remote

```shell
git remote  # 列出已经存在的远程分支
git remote -v  # 列出详细信息
git remote show [远端仓库名称]  # 显示某个远程仓库的信息
git remote add [远端仓库名称] [远端仓库url]  # 增加一个新的仓库
git remote add origin [远端仓库url]  # 本地仓库关联远程仓库
git remote rm [远端仓库名称]  # 删除一个远程仓库
```

- git fetch

```shell
git fetch  # 下载远程仓库的所有变动
git fetch [远端仓库名]  # 下载指定远程仓库的所有变动
git fetch [远端仓库名] [远端分支名] # 下载指定远程仓库指定分支的所有变动
git fetch [远端仓库名] [远端分支名]:[本地分支名] # 下载指定远程仓库指定分支的所有变动到本地分支
```

- git pull

```shell
git pull [远端仓库名] [远端分支名]:[本地分支] # 将远程分支拉取到指定本地分支
```

- git push

```shell
git push [远端仓库名] [远端分支名]:[本地分支名] # 上传本地指定分支到远程仓库
git push -u [远程仓库名] [本地分支名] # 本地分支指定一个默认远程仓库
git push --force [远程仓库名] [本地分支名] # 强行推送
git push --all [远程仓库名] # 推送所有分支到远程仓库
```
=======

>>>>>>> 2651014a9b3459d04175d339f6bc517959b90ca0

# git进阶

## 版本回退和撤销修改

1. 查看历史，确定需要回退的版本

```shell
git log
---
commit 784da28e8a1785655a19da629ff1ec9ec141414a (HEAD -> friend_match)
Author: shenyunmomie <18731548870@163.com>
Date:   Fri Jul 19 17:55:41 2024 +0800

    v0.2 swagger接口文档配置
# commit后面是版本号
```

2. 回退版本

> HEAD表示当前版本，也就是最新提交。HEAD^表示上一个版本

```shell
git reset --hard HEAD^ 
# 将当前分支的 HEAD 指针向后移动一个父提交
# 重置工作区和暂存区，使用这个命令会导致未提交的更改丢失
git reset HEAD~[n] 
# HEAD~[n] 表示当前提交的前第 n 个提交，其中 n 是一个整数。
# 这个命令用于将 HEAD 指针向后移动 n 个提交，并且会保留工作区的更改
git reset [--hard] [commitid] # 重新设置当前 HEAD 指针和暂存区的状态
--soft  # 将 HEAD 指针移动到指定的提交，但是会保留工作区和暂存区的当前状态。
--mixed  # (默认)将 HEAD 指针移动到指定的提交，并且会重置暂存区，但是会保留工作区的当前状态。
--hard  # 将 HEAD 指针移动到指定的提交，并且会重置暂存区和工作区，使它们完全匹配指定的提交状态。
```

```shell
git revert
# 撤销一个或多个已提交的更改
# 撤销之前的某个版本，但保留该版本后的其他版本，产生一个
# 创建一个新的提交，该提交会将指定提交的更改内容完全反向应用到当前分支上，从而达到撤销指定提交的效果，而不影响之前的提交历史。
git revert [commitid] # 撤销单个提交
git revert HEAD # 撤销最新的提交所引入的更改，并创建一个新的撤销提交。
git revert [startid]..[endid] # 撤销范围内的提交
```

```shell
git restore
# 撤销工作区或暂存区更改
# 恢复文件的状态，使其回到之前的某个状态，或者丢弃工作区的更改
git restore [file]  # 恢复工作区的文件到最近的暂存区（Index）状态
git restore --worktree [file] # 丢弃工作区对文件的修改（不影响暂存区）
git restore --staged [file] # 恢复暂存区的文件到最近的提交状态
git restore .  # 恢复整个工作区的所有文件到最近的提交状态
```

```shell
git checkout --[file]  #撤销对单个文件的修改
git checkout --.  #所有文件
```

```shell
git reset命令
```

## 解决冲突和补丁操作

- [x] 本地分支和本地分支冲突

如：两个开发者同时修改文件a，将修改合并到主代码库，就会产生冲突，需要手动解决。

解决方法：

1. git status
2. vim a.txt手动解决冲突，修改文件内容，wq保存退出
3. 将解决后的版本commit提交到本地仓库

- [x] 本地分支和远程分支冲突

如：本地分支A修改了文件b提交到本地仓库，而远程分支A也修改了文件b，push会产生冲突

解决方法：

1. 先pull到本地，会提示B.txt有冲突
2. vim b.txt手动解决冲突，修改文件内容，wq保存退出
3. 解决后commit本地
4. 推送到远程

- [x] 多分支维护，补丁操作

如：多个分支一起维护，但有时候无法直接通过合并来进行维护的。例如：两个版本，一个是标准版，一个是旗舰版，有一个bug在两个版本都存在，修改好都需要同步更新，就需要打补丁了，我们把在一个版本的修改作为一个补丁，然后在其他版本都同步。

1. 生成补丁

```shell
git diff > test.patch

```

## stash藏匿/存储的用法

> git stash用于将当前工作目录中的修改保存到一个临时存储区域（称为 stash），以便你可以在不提交更改的情况下切换分支或执行其他操作。

常用场景：

- **临时保存工作以切换分支**
- **保持工作目录干净**：在进行一些不确定的试验或测试时，使用 `git stash` 可以避免提交不必要的修改，保持提交记录的整洁。
- **避免合并冲突**：当你在一个分支上有未提交的修改而想要合并另一个分支的更改时，可能会遇到冲突。这时，你可以先使用 git stash 保存当前的修改，进行合并，然后再恢复修改。

```shell
git stash	# 将当前工作目录中的修改（包括已暂存和未暂存的修改）保存到一个新的 stash 条目中
git stash apply 'stash@{1}' # 有时需要加个引号，不然会报错。
# 命令
save #废弃
push
list
show
apply
drop
clear
pop
```

## 分支管理

企业开发一般会有较为复杂的代码管理规范，以便协调和维护。

**Git Flow**：广泛使用的分支管理模型，适合频繁发布和维护多个版本的项目。

- main分支：主线分支，只接受来自**hotfix和release的合并**，不允许直接修改
- develop分支：开发分支，包含直到下一个release的开发代码，
- feature分支：功能分支，用来开发一个新功能，由develop分支而来，最后merge回去
- release分支：版本发布，从develop中创建，待发布完成后合并到develop和main分支去
- hotfix分支：热补丁，修复分支，从main中创建，用于紧急修复生产环境中的问题

详细教程：[大厂git分支管理规范：gitflow规范指南](https://www.cnblogs.com/kevin-ying/p/14329768.html)，[Git之GitFlow工作流 | Gitflow Workflow](https://blog.csdn.net/sunyctf/article/details/130587970)

# 实践记录

- git status和git log的区别

status查看当前分支中暂存区和工作区的内容。log查看所有commit，包括不同分支。

![image-20240721150838892](https://shenyunmomie.oss-cn-beijing.aliyuncs.com/imags/202407211508818.png)

![image-20240721150807172](https://shenyunmomie.oss-cn-beijing.aliyuncs.com/imags/202407211508263.png)

- git reset和git checkout的区别

reset默认将暂存区的文件恢复到工作区，也可指定某个commit。checkout将仓库区的某个commit中的文件恢复到工作区。

reset恢复大的，所有的。checkout恢复小的，单个的。

- 无论是新建还是修改后文件，都用add添加到暂存区
- git show和git blame的区别

show只会查看指定commit的改动信息。blame查看文件的改动信息。

![image-20240721150626610](https://shenyunmomie.oss-cn-beijing.aliyuncs.com/imags/202407211506910.png)

![image-20240721150718537](https://shenyunmomie.oss-cn-beijing.aliyuncs.com/imags/202407211507779.png)

- git tag的使用

```shell
git tag # 查看所有tag
git tag [tagName] # 给当前提交添加tag
git tag [tagName] [commitid] # 给指定commit添加tag
git tag -d [tagName]

# tag是指向commit的指针，相当于给commitId起了个变量名
# 使用commitId的命令都可以换成tagName
git show tag
git checkout tag
```

- git reset和git revert的区别

reset完全重置，类似删除。revert安全删除，生成一个新的commit。

- 冲突问题

两个分支分别修改同一个文件，然后merge。

![image-20240721183809206](https://shenyunmomie.oss-cn-beijing.aliyuncs.com/imags/202407211838387.png)

![image-20240721183912766](https://shenyunmomie.oss-cn-beijing.aliyuncs.com/imags/202407211839084.png)

![image-20240721183923402](https://shenyunmomie.oss-cn-beijing.aliyuncs.com/imags/202407211839543.png)
