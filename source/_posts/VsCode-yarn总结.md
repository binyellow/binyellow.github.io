---
title: VsCode yarn总结
date: 2018-04-15 22:17:02
tags:
    - IDE
    - npm
categories: Dev-Tools
---

## VsCode常用插件

### 首先是如何备份和还原
- Settings Sync插件
- 上传`shift+alt+u`会自动进入github令牌界面,生成key并点gist
- 将生成的秘钥输入命令行
- 下载`shift+alt+d`

### 主题
1. Dark+(default dark)
2. theme-dark-monokai
<!--more-->

### 插件
1. Auto Close Tag: 自动闭合标签
2. Auto Rename Tag: 自动重命名标签
3. Beautify: 格式化不同格式代码
4. Bracket Pair Colorizer: 括号颜色
5. Code Outline: 将源代码的方法、变量、类单独列出来
6. Code Runner: 执行选中的代码
7. Code Spell Checker: 检验代码拼写
8. Document This: 为方法添加注释
9. ESLint: eslint代码检查
10. GitLens: 显示代码对应修改人和时间
11. Guides: 代码缩进标线
12. Git history: git历史提交
12. JavaScript(ES6)code snippets: ES6代码缩写速配
13. MarkDown All in One: MarkDown编写自动提示
14. MarkDown Preview Github: github预览模式
15. Node.js Modules Intellisense: 模块导入提示
16. Open in browser: alt+B打开浏览器
17. Path intellisense: 路径提示
18. psioniq File Header: 文件头标识
19. React/Redux/React-Router Snippets: React提示
20. React.js code snippets: React提示
21. Todo Highlight: todos高亮
22. vscode-icon: 图标区分

## yarn
npm|yarn|说明
---|---|---
npm install|yarn|
npm i --save|yarn add|
npm uninstall package --save|yarn remove package|
npm i package -D|yarn add package -D|
npm install [package] --global|yarn global add [package]|
rm -rf node_modules && npm install|yarn upgrade|