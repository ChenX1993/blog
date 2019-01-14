---
title: GitHub Memo
date: 2018-11-06 01:31:28
tags:
- github
categories:
- tools
---
# 一些常用指令
`git rebase -i HEAD~3`  
`git rebase -i 3a4226b`  

如果git rebase 有冲突

```
git add .
git rebase --continue
```
如果想放弃rebase  
`git rebase --abort`

强制push  
`git push origin master --force`

`git add -u`: 将文件的修改、文件删除，添加到暂缓区  
`git add .`: 将文件的修改、文件的新建，添加到暂缓区  
`git add -A`: 两者的结合，修改，新建，删除


# 远程仓库
## 查看远程仓库信息

```
# 查看关联的远程仓库的名称
git remote
# 查看关联的远程仓库的详细信息
git remote -v
```
## 添加远程仓库的关联
```
# git_url 为你的远程仓库的 url，可采用 http 协议或 ssh（git） 协议
git remote add origin <url>
```

## 删除远程仓库的关联
`git remote remove <name>`

## 修改远程仓库的关联

`git remote set-url <name origin/upstream> <newurl>`


# 远程分支
## 创建
`git push -u origin mybranch`

## 删除
`git push origin --delete <branchName>`


# Commit大文件无法push
`git log`查看提交历史  
`git reset commit_id` 撤销未被传送到远程代码库的提交

# Work FLow

# Pull Request
[https://www.cnblogs.com/kidsitcn/p/5319282.html](https://www.cnblogs.com/kidsitcn/p/5319282.html)

# Git fork出来的project和上游project同步更新
> 问题描述：当我们在github上fork出一个项目后，如果原有的项目更新了，怎样使我们fork出来的项目和原有项目保持同步呢？怎样提交我们的代码更新呢？即怎样保持fork出的项目和上游项目保持更新，怎样创建pull request？关键步骤是使用git 的rebase命令。

 
 步骤：

1.  在 Fork 的代码库中添加上游代码库的 remote 源，该操作只需操作一次即可。

如: git remote add upstream https://github.scm.corp.ebay.com/montage/frontend-ui-workspace

其中 #upstream 表示上游代码库名， 该名字可以任意。 

 

2. 将本地的修改提交commit

 

3. 在每次 Pull Request 前做如下操作，即可实现和上游版本库的同步。

 

      3.1 ： git remote update upstream

      3.2 ： git rebase upstream/{branch name}

需要注意的是在操作3.2之前，一定要切换到到{branch name}所指定的branch，如切换到develop branch

执行: git checkout develop

 

当然还有更简单的方法，即执行git pull upstream {branch name}

 

4. Push 代码到 Github

git push

 

5. 然后可以去github上自己的托管空间上创建pull request。

# Folk Repo 保持master始终和Upstream同步
[https://stackoverflow.com/questions/29049650/github-fork-your-branch-is-5-commits-ahead-how-to-clean-this-without-pushing](https://stackoverflow.com/questions/29049650/github-fork-your-branch-is-5-commits-ahead-how-to-clean-this-without-pushing)

# Current GitHub Collaboration Flow
# Recommended method via Ry's Git Tutorial

*"Never, ever rebase commits that have been pushed to a shared repository."--Hodson, Ryan*

```
git checkout -b css-edits
git commit -a -m "Add CSS styles for headings and links"
git rebase -i master # rebase to local master
git checkout master
git merge --ff-only css-edits
git branch -d css-edits

git fetch origin
git log master..origin/master
git log origin/master..master
git rebase origin/master

git push origin master
```

A shortcut to the `git fetch origin` then `git rebase origin/master` is to `git pull --rebase`. 

Be sure to `git branch -d` before rebasing `origin/master`, otherwise when you delete your local branch later, you'll run into an `not fully merged` error like this:

# SSH
Create a repo. Make sure there is at least one file in it (even just the README) Generate ssh key:  

```
ssh-keygen -t rsa -C "your_email@example.com"
```

Copy the contents of the file ~/.ssh/id_rsa.pub to your SSH keys in your GitHub account settings. Test SSH key:  

```
ssh -T git@github.com
clone the repo:
git clone git://github.com/username/your-repository
```

