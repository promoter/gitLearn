# git指令记录

## 本地创建仓库

` git init ` 

`git init gitlearn`

会在本地目录或者gitlearn目录下创建仓库。 生成 .git目录

## 当前仓库目录下修改状态

`git status`

输出：

$ git status
On branch master

Initial commit 。。。。。。。。。。。。。

## 添加到stage并且提交

`git add a/*`

`git add git指令记录.md`

添加文件。添加之后，文件被放置到“暂存区“（stage）.使用status命令可以看到，当前stage的状态。

![git-repo](https://www.liaoxuefeng.com/files/attachments/919020037470528/0)

如果文件 add错误了，使用rm --cached 撤销add:

`git rm --cached aa.txt`

如果文件修改错了，使用 checkout --  撤销”:(慎重，会删除内容)

`git checkout --aa.txt`

一种是`readme.txt`自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是`readme.txt`已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

提交版本：

`git commit -m '第一次提交'`

## 提交到远程仓库

使用**ssh工具**生成公共密齿，然后添加到github/gitee网站中。

先查看远程库信息:

`git remote -v`

如果没有输出代表没有任何远程库信息

添加远程库(可以同时添加多个远程库)：

`git remote add origin git@gitee.com:promoter/gitLearn.git`

`git remote add origin2 git@github.com:promoter/gitLearn.git`

如果移除远程库：

`git remote rm origin`

提交到远程仓库：

`git push origin master`

`git push origin2 master`

去gitee和github网站上看，可以看到本地多次commit的提交记录了。

## 从远程库中克隆

`git clone git@gitee.com:promoter/gitLearn.git`

`git clone git@github.com:promoter/gitLearn.git`

## 创建使用分支

`git checkout -b dev`

或者

`git branch dev`

`git checkout dev`

(

`git switch -c dev`

(switch指令新版本git才能使用)

)

创建并且切换到dev分支。

查看当前分支

`git branch`
切换分支到master(如果当前有修改未提交，切换分支会出错。)：

`git checkout master`或 `git switch master`

如果当前修改未完成想切换分支，则使用stash保存，然后使用git stash pop恢复。

`git stash`

`git stash list`

`git stash pop`

修改提交之后，合并分支到master主分支(当前在master分区，所以merge dev,是吧)

`git merge dev`

删除分支(不能删除当前所在分支):

`git branch -d dev`

## 多人协作一般做法



把机器的ssh添加到git服务器；

然后clone项目

`git clone git@gitee.com:promoter/gitLearn.git`

clone下拉之后，会发项，如果在git服务器中提交了多个分支，但是clone下载只会看到master分支。

我们一般在dev分支上干活，所以需要在创建远程`origin`的`dev`分支到本地

`git checkout -b dev origin/dev`

或

`git switch -c dev origin/dev`

干完活儿，提交之前，可能同事有提交版本，所以先使用pull拉取服务器上最新的更新

`git pull`

我们之前dev是直接从远程仓库创建到本地的，所以能直接pull,如果是自己在本地创建的dev,pull会失败，因为本地分支没有和服务器分支对应起来，使用参数建立连接

`git branch --set-upstream-to=origin/dev dev`

提交，把dev分支merge到master;然后把master  push提交到远程服务器：

`git switch master`

`git merge dev`

`git push origin master`

或者，直接把dev push到远程库

`git push origin dev`

## 查看git提交路线图

`git log --graph --pretty=oneline --abbrev-commit`

## 标签

查看所有标签,默认无：

`git tag`

查看某个标签信息:

`git show v0.1`

删除本地标签：

`git tag -d v0.1`

给当前版本打标签，或者历史版本打标签,并且添加标签说明：

`git tag -a v1.0 -m 'version 1.0 released' `

`git tag -a v0.1 -m 'version 0.1 released' 9ca2ff4`

把标签推送到远程:

推送单个：

`git push origin v1.0`

推送所有：

`git push origin --tags`

删除远程标签：

`git push origin :refs/tags/v1.2`

















