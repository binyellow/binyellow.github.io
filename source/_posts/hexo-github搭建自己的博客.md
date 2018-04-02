---
title: hexo+github搭建自己的博客
date: 2016-12-03 15:39:37
tags: 
    - Hexo
    - Github
---
### 前期准备工作
1. 首先你要在github上生成name.github.io项目(name是你的注册名不是昵称)，并将SSH密钥设置到github上，这里可以参考我git标签下的一篇[SSH免密](https://binyellow.github.io/2017/04/29/yellowbin/)文章  
2. 安装hexo `npm install -g hexo`  
3. `hexo init s`(会生成一个欢迎界面并开启服务，你可以预览)<!--more-->  
4. 换个炫酷点的主题吧`git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia`(会下载yilia主题到themes下)
5. 配置主题：将根目录的_config.yml中的theme: landscape改为theme: yilia，然后重新执行`hexo clean g`来重新生成
6. 关于主题内的内容和头像要进themes的_config.yml中修改，头像放在source下(source是相对起点)
7. 修改上传配置(在根目录_config.yml末尾添加)  
```js
deploy:
    type: git
    repository: git@github.com:binyellow/binyellow.github.io.git(你name.github.io项目clone选项的ssh地址)
    branch: master
```
### 写文章
1. 创建一个文件夹，如：myBog，cd到myBog里执行`hexo init`命令，初始化工程，生成配置文件等  
2. 执行`hexo new "titlename"`(titlename就是文章名字),执行完会在source/_posts下生成titlename.md文件
3. 执行`hexo generate`（hexo g）会在public文件夹下生成HTML等  
4. 执行`hexo server`(heo s)开启服务器，可在localhost:4000下先调试  

### 部署到线上，执行三个命令
1. `hexo clean`(清除生成的html文件)  
2. `hexo generate`（hexo g生成html）  
3. `hexo deploy`(hexo d上传到github上)  
或者直接执行 `hexo c && hexo g && hexo d`

### 常用命令
- `hexo new` "postName" #新建文章  
- `hexo new page` "pageName" #新建页面  
- `hexo generate` #生成静态页面至public目录  
- `hexo server` #开启预览访问端口（默认端口4000，’ctrl + c’关闭server）  
- `hexo deploy` #将.deploy目录部署到GitHub  
- `hexo help` #查看帮助  
- `hexo version` #查看Hexo的版本  

### 小tips
- 问：如何让文章想只显示一部分和一个 阅读全文 的按钮？  
答：在文章中加一个 <\!--more--> ， <\!--more--> 后面的内容就不会显示出来了。

- 问：本地部署成功了，也能预览效果，但使用 username.github.io 访问，出现 404 .  
答：首先确认 hexo d 命令执行是否报错，如果没有报错，再查看一下你的 github 的 username.github.io 仓库，你的博客是否已经成功提交了，你的 github 邮箱也要通过验证才行。  

- 3.几版本`hexo d`失败怎么办？
`npm install hexo-deployer-git`

- 我怎么备份我的md和主题配置呢？
```js
git init
git checkout -b hexo
git add .
git commit -m 'add code'
git git remote add origin git@github.com:binyellow/binyellow.github.io.git //把远程地址添加到配置文件
git push
```
### 添加阅读量

- 其他主题
next

- 可以参考 [这里](https://www.zhihu.com/question/39620187 "这里")
- [不蒜子](https://crane-yuan.github.io/2016/03/25/Hexo-05-add-site-statistics/)比较简单易用，样式自己可以去css

### 添加评论模块

可以参考这篇文章：[评论模块 ](https://wizardforcel.gitbooks.io/markdown-simple-world/hexo-tutor-7.html)   
这里先总结下：  
1. 网易云评论：必须要有自己的域名，通过绑定域名  
**2. Disqus：我用的这个，但是使用要翻墙**  
3. 多说已经不再维护了  
4. 友言不支持https

### 之后也会把博客和学习笔记搬到这里和大家分享:):)
### tips:想要评论和查看评论先翻墙
<!--more--> 