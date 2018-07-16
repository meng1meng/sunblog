---
author: "Michael Henderson"
date: 2018-09-13
linktitle: git笔记
title: git笔记
weight: 10
---


# 关于git的使用git-bash
    git clone 克隆 
    git init 初始化
    git checkout -b 创建切换到分支
    git pull命令 推到远程库

## 上传文件
### 将本地项目中的文件添加到暂存区中，可以添加多个
    git add 文件名及后缀
### 将暂存区中的文件提交到git本地仓库
    git commit -m "改动说明"
### pull到远程仓库
     git pull origin master
从远程仓库pull，获取远程仓库的文件到本地仓库（往GitHub上提交东西的时候，会因为远程上有东西更新了但是本地仓库没有更新而造成提交失败，所以我们在push之前，都会pull一遍）
### 将文件从本地仓库上传到GitHub远程仓库
    git push origin master(分支)
## 分支
### 分支的作用
假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险。现在有了分支，就不用怕了。你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。
### 分支的创建与合并
    git checkout -b dev(如工号)  创建一个新的分支dev：
-b表示创建并切换，相当于git branch dev和git checkout dev
git branch命令会列出所有分支，当前分支前面会标一个*号
   dev分支的工作完成后，可以切换回master分支：git checkout master
   把dev分支的工作成果合并到master分支上：git merge dev
   合并完成后，可以删除dev分支：git branch -d dev
## 仓库 
###将代码由本地仓库上传到Github远程仓库
    git push -u origin master
把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。由于远程库是空的，我们第一次推送master分支时，
加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的
推送或者拉取时就可以简化命令。此后，每次本地提交后，只要有必要，就可以使用命令 git push origin master 推送最新修改。
### 克隆
从远程仓库克隆，首先必须知道仓库的地址，然后使用git clone命令克隆。
例如：
    git clone git@github.com:michaelliao/gitskills.git
Cloning into 'gitskills'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (3/3), done.
    cd gitskills
    ls
README.md
Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。
### 删除远程仓库
    git push [远程名] :[分支名]。如果想在服务器上删除 serverfix 分支，运行下面的命令：
  git push origin :serverfix
To git@github.com:schacon/simplegit.git
- [deleted] serverfix
注意origin后的空格
## Git基础命令：
### 回退到上一个版本
    git reset -hard commit_id //回退到版本号为commit_id 的版本
    git log //查看提交历史，以便确定要回退到哪个版本
    git reflog //查看命令历史，以便确定要回到未来的哪个版本。
HEAD指向的版本就是当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令
    git checkout -- file
当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令
    git reset HEAD file
就回到了步骤6，第二步按步骤6操作。
### 查看文件是否被修改过
    git status //查看文件是否被修改过
    git diff //查看修改内容
### 添加远程仓库
    git remote add origin git@github.com:michaelliao/learngit.git
    git remote add origin 网址 //二者取一
把michaelliao 换成你的Git 用户名，把learngit 换成远程仓库的名字。如果已经建立连接，则需要先拆除链接：
    git remote rm origin
### 查看历史记录
    git log
-- 简化信息
    git log --pretty=oneline