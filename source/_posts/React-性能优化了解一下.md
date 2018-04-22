---
title: React-性能优化了解一下
date: 2018-04-22 18:38:52
tags:   
    - React
    - Performance
categories: Performance
---
### 性能优化总述
1. 减少dom操作
2. 减少网络请求
3. 优化访问速度

### Chrome怎么查看React渲染的时间
- 在url后面加?react_perf即可进performance查看性能图

### 关于React简单的优化
1. 当为onClick添加事件时,bind要在构造函数中执行,而不是在调用的时候每次渲染的时候bind
2. 当父组件render时,默认子组件也会render一次,所以子组件应该手动调用shouldComponentUpdate(nextProps,nextState)来决定是否渲染
3. 木偶组件直接继承PureComponent,定制了shouldComponentUpdate,当props或state没变化时不会渲染
4. 使用immutable:
    1. 优点
        - 减少内存使用
        - 便于比较复杂数据,方便定制shouldComponentUpdate
        - 函数式变程
        - 并发安全
        - 降低项目复杂度？
    2. 缺点
        - 库大小
        - 项目入侵太严重
    3. 可替代库：seamless-immutable