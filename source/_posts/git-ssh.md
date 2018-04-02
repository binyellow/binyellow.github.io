---
title: git ssh
date: 2017-01-02 14:37:03
tags: 
    - git
categories: git
---
1. 在github上创建项目
2. 使用Git clone 你的项目 克隆到本地
3. 编辑项目 
4. `git add . ` :将改动添加到暂存区
5. `git commit -m` :提交说明
6. `git pull origin master` 如果在github的remote上已经有了文件，会出现错误。此时应当先pull一下
7. `git push origin master` 将本地更改推送到远程master分支。
<!--more-->
SSH设置和免密
1.  设置Git的user name和email：(如果是第一次的话)
```js
$ git config --global user.name "yourname"  
$ git config --global user.email "yuor mail"
```

2.  生成密钥

`$ ssh-keygen -t rsa -C "humingx@yeah.net"` 
按回车，最后得到了两个文件：id_rsa和id_rsa.pub。

3. 将id_rsa.pub全部复制到自己gitlab代码库的SSH KEYS.(SSH KEYS的位置：打开自己的gitlab,点击右上角的倒三角，选择profile seetings,进去该页面后选择SSH KEYS)
4. 修改你本地的ssh remote url. 不用https协议，改用git 协议
可以用git remote -v 查看你当前的remote url

$ Git remote -v  
origin https://github.com/someaccount/someproject.git (fetch)  
origin https://github.com/someaccount/someproject.git (push)  
可以看到是使用https协议进行访问的。
你可以使用浏览器登陆你的github，在上面可以看到你的ssh协议相应的url。类似如下：

`git@github.com:someaccount/someproject.git`  
这时，你可以使用git remote set-url 来调整你的url。

`git remote set-url origin `
`git@github.com:someaccount/someproject.git`完了之后，你便可以再用 git remote -v 查看一下。
之后再执行git pull和git push就不需要输入密码了。