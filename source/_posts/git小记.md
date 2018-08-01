---
title: git小记
date: 2018-07-05 20:12:09
tags:
    - git
categories: git
---
### 创建的默认仓库是msater

### 代码提交
```
git add file //git add .添加所有
git commit -m content //提交到本地仓库
git pull [origin master] //从指定分支拉取代码
git push
```

### 在本地创建仓库
```
git init
git remote add origin git@github.com:binyellow/test.git //关联到远程仓库
```

<!--more-->
### 分支

#### 创建新分支
1. `git checkout -b name`
2. `git push origin localName:remoteName`   //本地推送到远程分支

#### 删除分支
1. `git branch -d name`
2. `git push :remoteBranch`

#### 查看分支
1. 本地分支`git branch`
2. 远程分支`git branch -a/-r`

#### 分支回退
1. 本地回退
    `git log`查看记录
    `git reset --hard commitID`
2. 远程回退
    `git push HEAD --force`
3. 重返过去
    `git reflog`
    `git reset --hard versionCode`

#### 分支合并
1. 从其他分支拉到当前分支
    `git pull origin remoteBranch[:localBranch]`
2. 当其他分支更新后merge
    `git merge develop`
<!--more-->