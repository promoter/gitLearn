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

创建并且切换到dev分支。

查看当前分支

`git branch`

修改提交之后，合并分支到master主分支(别写错了)

`git merge dev`

切换分支到master(如果当前有修改未提交，切换分支会出错。)：

`git checkout master`

删除分支(不能删除当前所在分支):

`git branch -d dev`



















