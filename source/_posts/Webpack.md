---
title: Webpack
date: 2018-02-13 23:57:56
tags:
    - Webpack
categories: Webpack
---
*注意插件和loader版本问题,要适配webpack4.0*
### Webpack自动刷新和模块热替换
#### 自动刷新
- iframe模式
-  inline模式
#### 模块热替换（--hot): 是指不需要完全刷新就能更新各个模块
- 要使用模块热替换需指定publicPath: 因为存在path的情况下,webpack-dev-server生成的包并没有放在你的真实目录中,而是放在了内存中
- publicPath: 为项目中的所有资源指定一个基础路径
<!--more-->
### loader要怎么写？
#### 写法有很多,简单点说话的方式简单点
```js
module: {
    rules: [
        {
            test: /\.js$/,
            exclude: /node_modules/,
            use: {
                loader: 'babel-loader',
                options: {
                    preset: ['env','react']
                }
            }
        },
        {
            test: /\.less$/,
            user: [
                'style-loader','css-loader?modules','less-loader'
            ]
        },
        {
            test: /\.(jpg|png|svg|gif)$/,
            use: ['file-loader']
        }
    ]
}
```

- file-loader
file-loader会把import进来的图片资源路径最后转换成输出目录图像的最终路径,同理css-loader也会将background-image:url('path')一样处理

- extract-text-webpack-plugin插件分离css后用html-webpack-plugin来动态加载css

### plugins
#### eslint
- 在webpack中配置eslint-loader
- .eslintrc.js中可配置extends:["standard"]等规范
- 在rules：{}中添加自己的规范