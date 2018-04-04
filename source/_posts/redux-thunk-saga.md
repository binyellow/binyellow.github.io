---
title: redux-thunk-saga
date: 2017-12-08 09:13:05
tags:
    - Redux
    - Redux-thunk
    - Redux-saga
categories: Redux
---
### thunk
#### 为了让Reducer在异步操作后自动执行，于是出现了thunk
#### thunk加在Reducer还是action或者view中呢？
- 1是纯函数不能进行读写操作
- 2是存放数据的载体，只能被Reducer来操作
- view和state一一对应，也不合适
- 所以只能对dispatch函数进行改造封装
#### 怎么使用？

```js
const store = createStore(
  reducer,
  initial_state,
  applyMiddleware(thunk, promise, logger)
);
```
#### thunk使得dispatch一个函数

```js
(dispatch,getState)=>{
    dispatch(操作开始);
    return axios.get('/',{params}).then(data=>{
        dispatch(recieve(data)) //异步请求完成后再发起请求完成的action
    })
}
```

### saga
#### 特性
- 集中处理 redux 副作用问题
- 被实现为 generator
- 类 redux-thunk 中间件
- watch/worker（监听->执行） 的工作形式
#### Module
1. reducers 处理数据
2. effects   接收数据
3. subscriptions 监听数据
#### Effects
1. Effect 是一个 javascript 对象，里面包含描述副作用的信息，可以通过 yield 传达给 sagaMiddleware 执行,所有的 Effect 都必须被 yield 才会执行
`yield fetch(UrlMap.fetchData)===>yield call(fetch, UrlMap.fetchData)`
2. 其实是一个包含Generator的函数，函数中依次按下面执行的异步操作redux的过程
#### 实现
```js
yield call(service,{params})

yield put({
    type:'',
    payload:{

    }
})

const id = yield select(state=>state.id)
```