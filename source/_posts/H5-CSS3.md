---
title: H5-CSS3
date: 2016-10-18 20:30:05
tags:
    - H5
    - CSS3
categories:
    - CSS
    - HTML
---
### CSS3
#### Animation
1. 首先先定义动画
```css
@-webkit-keyframes name {
    0%   {background:red; left:0px; top:0px;}
    25%  {background:yellow; left:200px; top:0px;}
    50%  {background:blue; left:200px; top:200px;}
    75%  {background:green; left:0px; top:200px;}
    100% {background:red; left:0px; top:0px;}
}
```
<!--more-->
2. 使用动画,并设置动画属性
```css
div {
    animate: move 3s ease-in-out infinite alternate;
}
```
- `animate-name`: 动画名
- `animate-duration`: 持续时间
- `animate-timing-function:linear |ease |ease-in |ease-out |ease-in-out`: 动画速度曲线
- `animate-delay`: 延迟执行
- `animate-iteration-count`: 执行次数
- `animate-direction: normal |alternate`: 逆向执行
- `animate-fill-mode: none |forwards |backwards |both`: 最后的状态,默认回到最初的状态,backwards和none是回到最初,其他保留最后状态

#### Transition
```css
div s{
    width:100px;
    transition: width 2s;
    -moz-transition: width 2s; /* Firefox 4 */
    -webkit-transition: width 2s; /* Safari 和 Chrome */
    -o-transition: width 2s; /* Opera */
}
```
- `transition-property`: 过渡效果的css属性(width)
- `transition-duration`: 过渡时间
- `transition-timing-function`: 速度曲线
- `transition-delay`: 延时

#### 媒体查询
```css
@media mediatype and|not|only (media feature) {
    CSS-Code;
}
```
- 媒体类型: `screen、all`
- 媒体功能: `min-width`(*注意这里是符合最小宽度的意思*)...
- 注意: 媒体查询要放到样式后面
- [更多](http://www.runoob.com/cssref/css3-pr-mediaquery.html)

#### 怪异盒模型
- 当html顶部不声明doctype时,width=border+padding
- 在CSS3中可以设置box-sizing: border-box |content-box

#### content-increment
1. 先定义counter-reset计数器: 这个定义在哪,**他的作用于就在定义的区块内**
2. counter-increment(计数器)
3. counter(计数器)
4. [详解](https://github.com/binyellow/Notes/blob/master/CSS/Details/Counter-Increment.md)

#### Tranform2D/3D转换
- translate(x,y): 平移
- scale(x,y): 缩放
- rotate(x deg): 倾斜角度
- skew(x,y)

### 几种布局
#### 怪异盒模型
- 当html顶部不声明doctype时,width=border+padding
- 在CSS3中可以设置box-sizing: border-box |content-box

#### 定位
- 相对定位relative: 仍占用原来位置,相对正常文档流偏移
- 绝对定位absolute: 脱离文档流,相对不为stctic的父元素定位
- 浮动float: 脱离文档流,clear的含义是当前元素的某个位置没有浮动元素

#### 流式布局
- 宽度用百分比,高度固定,会导致缩放不正常

#### 弹性布局、flex布局、Grid布局
- [包裹文字的父元素用em做单位,会使文字随页面缩放](./Flex_Grid/README.md)

#### 自适应布局
- 使用媒体查询来适应不同尺寸

#### 响应式布局
- 使用媒体查询+流式布局+弹性布局
- 圣杯、双飞翼布局：是基于2边浮动、中间overflow:hidden、然后margin-left:100%,-width;会向左移的原理实现的