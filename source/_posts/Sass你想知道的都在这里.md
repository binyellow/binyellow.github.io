---
title: Sass你想知道的都在这里
date: 2017-7-31 12:22:29
tags: 
	- Sass
categories: CSS
---
1. 变量：**$变量名**;变量可以嵌套使用
2. 要写一大串指向页面中同一块的样式时，往往需要 一遍又一遍地写同一个ID

```css
#content article h1 { color: #333 }
#content article p { margin-bottom: 1.4em }
#content aside { background-color: #EEE }
```

像这种情况，sass可以让你只写一遍，且使样式可读性更高。
<!--more-->

```css
#content {
	article {
		h1 { color: #333 }
		p { margin-bottom: 1.4em }
	}
	aside { background-color: #EEE }
}
```

3. 父选择器的标识符&
4. 群组选择器的嵌套：中间用,隔开
5. 子组合选择器和同层组合选择器：>、+和~：
	- 同层相邻组合选择器+选择header元素后紧跟的p元素：
	- `header + p { font-size: 1.1em }`
	- 同层全体组合选择器~，选择所有跟在article后的同层article元素，不管它们之间隔了多少其他元素：
	- `article ~ article { border-top: 1px dashed #ccc }`
	- 子组合选择器>选择一个元素的直接子元素:
	- ```
		article section { margin: 5px }
		article > section { border: 1px solid #ccc }
		```
	- 上例中，第一个选择器会选择article下的**所有命中**section选择器的元素。第二个选择器只会选择article下**紧跟着的子元素**中命中section选择器的元素。

6. 嵌套属性:
- ```css
	nav {
		border: 1px solid #ccc {
		left: 0px;
		right: 0px;
		}
	}
	```
- ```css
	nav {
		border: 1px solid #ccc;
		border-left: 0px;
		border-right: 0px;
	}
	```

7. 导入SASS文件:
	- @import"sidebar":即把siderbar.scss文件导入进来了，可以省略后缀
		- sass的@import规则在生成css文件时就把相关文件导入进来。这意味着所有相关的样式被归纳到了同一个css文件中，而无需发起额外的下载请求
	- 只导入部分scss文件：
		- 那些专门为@import命令而编写的sass文件，并不需要生成对应的独立css文件，这样的sass文件称为局部文件
		- sass局部文件的文件名以下划线开头：_night-sky.scss
		- 你导入时可以不写文件的全名，即省略文件名开头的下划线。(`themes/\_night-sky.scss=>@import "themes/night-sky";`)
	- 默认变量值:`$fancybox-width: 400px !default;`
	- 嵌套导入：
		- _blue-theme.scss文件内容如下
			- ```css
				aside {
				  background: blue;
				  color: white;
				}
				```
			- 现在想把他导入`.blue-theme {@import "blue-theme"}`这个类中
			- ```css
				.blue-theme {
				  aside {
				    background: blue;
				    color: #fff;
				  }
				}
				```
	- 原生的CSS导入:你可以把原始的css文件改名为.scss后缀，即可直接导入了。
	- 静默注释:不希望每个浏览网站源码的人都能看到所有注释
		- ```css
			body {
			  color: #333; // 这种注释内容不会出现在生成的css文件中
			  padding: 0; /* 这种注释内容会出现在生成的css文件中 */
			}
			```
		- css的标准注释格式/* ... */内的注释内容亦可在生成的css文件中抹去。
			- 注释出现在原生css不允许的地方，如在css属性或选择器中，sass将不知如何将其生成到对应css文件中的相应位置，于是这些注释被抹掉。
			- ```css
				body {
				  color /* 这块注释内容不会出现在生成的css中 */: #333;
				  padding: 1; /* 这块注释内容也不会出现在生成的css中 */ 0;
				}
				```
	- 混合器:大段大段的重用样式的代码---使用@mixin标识符定义
		- ```css
			@mixin rounded-corners {
			  -moz-border-radius: 5px;
			  -webkit-border-radius: 5px;
			  border-radius: 5px;
			}
			```  
			引用
			```css
			notice {
			  background-color: green;
			  border: 2px solid #00aa00;
			  @include rounded-corners;
			}
			```
		- 传参：
			```css
			@mixin link-colors($normal, $hover, $visited) {
			  color: $normal;
			  &:hover { color: $hover; }
			  &:visited { color: $visited; }
			}
			```  
			`a {@include link-colors(blue, red, green);}`  
			最终生成：
			```css
			a { color: blue; }
			a:hover { color: red; }
			a:visited { color: green; }
			```  
8. 使用选择器继承来精简CSS
```css
.error {
	border: 1px solid red;
	background-color: #fdd;
}
.seriousError {
	@extend .error;
	border-width: 3px;
}
```  
.seriousError不仅会继承.error自身的所有样式，任何跟.error有关的组合选择器样式也会被.seriousError以组合选择器的形式继承
<!--more-->