---
thumbnail: 'https://picsum.photos/1280/720?random=5 #111'
title: Git常用命令
date: 2021-12-06 22:43:43
tags:
- 🔥前端
- 📔笔记
- 🥚Git
---

# 查看用户名和邮箱地址：

 `git config user.name  git config user.email`

# 修改用户名和邮箱地址：

  `git config --global user.name  "xxxx"   git config --global user.email  "xxxx"`

# 创建SSH密匙：

`ssh-keygen -t rsa -C "（邮箱）"`

# 克隆远程仓库

`git clone` 

# 暂存更改

`git add .`

# 提交更改

`git commit -m 'xxxx'`

# 查看历史提交（目标版本）

`git log`

# 查看所有分支

`git branch -a`

# 切换分支

`git checkout (分支名)`

# 从远程分支下载最新代码并合并

`git pull (远程仓库名) (远程分支)`

# 从远程分支上传最新代码并合并

`git push (远程仓库名) (远程分支)` 

# 该选项可以合并两个独立启动仓库的历史

`git pull origin master --allow-unrelated-histories`

# 新建远程仓库地址

`git remote add <远程仓库名> <远程仓库地址>`

# 回退版本操作

`git reset --hard <目标版本>`

`git checkout (分支名)`

# 提交时不会生成新的提交

`git add .`

`git commit --amend`

`git push -f`
