---
title: CSS开发积累.md
date: 2020-05-24 13:33:16
tags: 
    - CSS
    - 前端
categories: 前端面试复习
---
### 让flex盒子中的子元素们，居中

flex布局常用的三行代码：

```
    display: flex;
    justify-content: center; // 子元素在横轴的对齐方式 （左右居中）
    align-items: center;  // 子元素在竖轴的对齐方式（上下居中）
```


### 让文字只显示一行，超出显示省略号

```
	overflow: hidden;
	white-space: nowrap;
	text-overflow: ellipsis;

```


### 让文字最多只显示两行，超出后显示省略号

```
	overflow:hidden;
	text-overflow:ellipsis;
	display:-webkit-box;
	-webkit-box-orient:vertical;
	-webkit-line-clamp:2;
```

### 问题描述：文本内容里自带了换行，但是在前端没有展示出来

解决办法：增加如下属性即可。

```
white-space: pre-wrap;
```

或者：

```
white-space: pre-line;
```



### 2019-11-12-CSS的逗号和空格

CSS的逗号一般写在()里。**不同属性值之间，用的是空格**，不是逗号。比如：

```css
	transform: translate(-50%, -50%);  /* 这种写逗号 */
	transform: translate(-50%, -50%) scale(0.5);   /* 不同属性值之间，用的是空格 */

	background-size: 100% 100%;  /* 这里是空格，不是逗号 */
```


### 2019-11-01

价格中的羊角符号，有半角和全角之分：

- ¥半角

- ￥全角

可以看出，半角的宽度更小。考虑到容器的空间一般比较紧张，所以推荐使用**半角**。


### 2019-11-19-鼠标悬停时，弹出提示文字

参考链接：[css实现鼠标悬浮后的提示效果](https://www.cnblogs.com/zhaojian-08/p/10074660.html)


### 2019-11-27-图片的宽度固定，高度自适应

这个场景下，别用background。直接放img元素就好了，将图片的高度设置为`auto`。


### 2020-03-26-通过CSS扩大点击热区

```css
.button {
	position: relative;
	/* [其余样式] */
}

.button::before {
	content: '';
	position: absolute;
	top: -10px;
	right: -10px;
	bottom: -10px;
	left: -10px;
}
```
注意，button 里面不要写 `overflow: hidden` 属性，否则扩大的热区无效。


参考链接：<https://www.jianshu.com/p/b83fc87cb222>







