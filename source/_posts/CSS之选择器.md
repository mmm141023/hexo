---
title: CSS之选择器
date: 2020-05-16 18:02:06
tags: 
    - CSS
categories: 
    - 前端
    - 后盾人
---

## 选择器

> [houdunren.com](https://www.houdunren.com/) @ 向军大叔

样式是做用在元素标签上的，通过本章将可以随意查找元素来应用样式。

## 基本选择器

| 选择器          | 示例       | 描述                           |
| :-------------- | ---------- | :----------------------------- |
| .class          | .intro     | 选择 class="intro" 的所有元素  |
| #id             | #firstname | 选择 id="firstname" 的所有元素 |
| *               | *          | 选择所有元素                   |
| element         | p          | 选择所有元素                   |
| element,element | div,p      | 选择所有元素和所有元素         |
| element element | div p      | 选择元素内部的所有元素         |
| element>element | div>p      | 选择父元素为元素的所有元素     |
| element+element | div+p      | 选择紧接在元素之后的所有元素   |

### 标签选择

使用 `*` 可为所有元素设置样式。

```text
* {
    text-decoration: none;
    color: #6c757d;
}
```

根据标签为元素设置样式

```text
h1 {
	color: red;
}
```

同时设置多个元素组合

```text
h1,h2 {
    color: red;
}
```

元素在多个组件中存在

```text
h1,h2 {
    color: red;
}
h1,h3{
    background: #dcdcdc;
}
```

### 类选择器

类选择器是为一类状态声明样式规则，下面是把文本居中定义为类样式。

```text
.text-center {
    text-align: center;
}
...

<h1 class="text-center">houdunren.com</h1>
<h2 class="text-center">hdcms.com</h2>
```

将类选择器指定为具体标签

```text
.help-block {
    background: red;
}

span.help-block {
    font-size: 12px;
    color: #aaa;
    background: none;
}
...

<span class="help-block">感谢访问后盾人</span>
```

### ID选择器

为有 id 属性的元素设置样式

```text
#container {
    background: red;
}

...
<h1 id="container">houdunren.com</h1>
```

> 文档中ID应该是唯一的，虽然为多个元素设置同一个ID也可以产生样式效果，但这是不符合规范的。
>
> 建议优先使用类选择器

## 结构选择器

| 选择器            | 示例  | 描述                         |
| :---------------- | ----- | :--------------------------- |
| element element   | div p | 选择元素内部的所有元素       |
| element>element   | div>p | 选择父元素为元素的所有元素   |
| element+element   | div+p | 选择紧接在元素之后的所有元素 |
| element1~element2 | p~ul  | 选择前面有元素的每个元素     |

### 后代选择器

HTML中元素是以父子级、兄弟关系存在的。后代选择器指元素后的元素（不只是子元素，是后代元素）。

```text
main article h2,main h1 {
    color: green;
}
...

<main>
	<article>
		<h2 name="houdunren">houdunren.com</h2>
		<aside>
			<h2>houdunwang.com</h2>
		</aside>
	</article>
	<h2 name="hdcms.com">hdcms.com</h2>
	<h1>后盾人</h1>
</main>
```

### 子元素选择

子元素选择器中选择子元素，不包括孙级及以下元素。

```text
main article>h2 {
    color: green;
}
...

<main>
	<article>
		<h2 name="houdunren">houdunren.com</h2>
		<aside>
			<h2>houdunwang.com</h2>
		</aside>
	</article>
	<h2 name="hdcms.com">hdcms.com</h2>
	<h1>后盾人</h1>
</main>
```

### 紧邻兄弟元素

用于选择紧挨着的同级兄弟元素。

```text
main article+h2 {
    color: green;
}
...

<main>
	<article>
		<h2 name="houdunren">houdunren.com</h2>
		<aside>
			<h2>houdunwang.com</h2>
		</aside>
	</article>
	<h2 name="hdcms.com">hdcms.com</h2>
	<h1>后盾人</h1>
</main>
```

### 后面兄弟元素

用于选择后面的所有兄弟元素。

```text
main article~* {
    color: green;
}
...

<main>
	<article>
		<h2 name="houdunren">houdunren.com</h2>
		<aside>
			<h2>houdunwang.com</h2>
		</aside>
	</article>
	<h2 name="hdcms.com">hdcms.com</h2>
	<h1>后盾人</h1>
</main>
```

## 属性选择器

根据属性来为元素设置样式也是常用的场景。

| 选择器              | 示例            | 描述                                        |
| :------------------ | --------------- | :------------------------------------------ |
| [attribute]         | [target]        | 选择带有 target 属性所有元素                |
| [attribute=value]   | [target=_blank] | 选择 title 属性包含单词 "flower" 的所有元素 |
| [attribute~=value]  | [title~=flower] | 选择 title 属性包含单词 "flower" 的所有元素 |
| [attribute\|=value] | [lang\|=en]     | 选择 lang 属性值以 "en" 开头的所有元素。    |
| [attribute*=value]  | a[src*="abc"]   | 选择其 src 属性中包含 "abc" 子串的每个 元素 |
| [attribute^=value]  | a[src^="https"] | 选择其 src 属性值以 "https" 开头的每个 元素 |
| [attribute$=value]  | a[src$=".pdf"]  | 选择其 src 属性以 ".pdf" 结尾的所有 元素    |

为具有 `class` 属性的h1标签设置样式

```text
h1[class] {
    color: red;
}
...

<h1 class="container">houdunren.com</h1>
```

约束多个属性

```text
h1[class][id] {
    color: red;
}
...

<h1 class="container" id >houdunren.com</h1>
```

具体属性值设置样式

```text
a[href="https://www.houdunren.com"] {
    color: green;
}
...

<a href="https://www.houdunren.com">后盾人</a>
<a href="">HDCMS</a>
```

`^` 以指定值开头的元素

```text
h2[name^="hdcms"] {
    color: red;
}
...

<h2 name="houdunren">houdunren.com</h2>
<h2 name="hdcms.com">hdcms.com</h2>
```

`$` 以指定值结尾的元素

```text
<h2 name="houdunren">houdunren.com</h2>
<h2 name="hdcms.com">hdcms.com</h2>
...

h2[name$="com"] {
    color: red;
}
```

`*` 属性内部任何位置出现值的元素

```text
h2[name*="houdunren"] {
    color: red;
}
...

<h2 name="houdunren">houdunren.com</h2>
<h2 name="houdunren.com">hdcms.com</h2>
```

`~` 属性值中包含指定词汇的元素

```text
h2[name~="houdunren"] {
    color: red;
}
...

<h2 name="houdunren">houdunren.com</h2>
<h2 name="houdunren web">hdcms.com</h2>
```

`|` 以指定值开头或以属性连接破折号的元素

```text
h2[name|="houdunren"] {
    color: red;
}
...

<h2 name="houdunren">houdunren.com</h2>
<h2 name="houdunren-web">hdcms.com</h2>
```

## 伪类选择器

为元素的不同状态或不确定存在的元素设置样式规则。

| 状态                 | 示例                  | 说明                                       |
| -------------------- | --------------------- | ------------------------------------------ |
| :link                | a:link                | 选择所有未被访问的链接                     |
| :visited             | a:visited             | 选择所有已被访问的链接                     |
| :hover               | a:hover               | 鼠标移动到元素上时                         |
| :active              | a:active              | 点击正在发生时                             |
| :focus               | input::focus          | 选择获得焦点的 input 元素                  |
| :root                | :root                 | 选择文档的根元素即html。                   |
| :empty               | p:empty               | 选择没有子元素的每个元素（包括文本节点）。 |
| :first-child         | p:first-child         | 选择属于父元素的第一个子元素的每个元素     |
| :last-child          | p:last-child          | 选择属于其父元素最后一个子元素每个元素。   |
| :first-of-type       | p:first-of-type       | 选择属于其父元素的首个元素的每个元素       |
| :last-of-type        | p:last-of-type        | 选择属于其父元素的最后元素的每个元素。     |
| :only-of-type        | p:only-of-type        | 选择属于其父元素唯一的元素的每个元素。     |
| :only-child          | p:only-child          | 选择属于其父元素的唯一子元素的每个元素。   |
| :nth-child(n)        | p:nth-child(2)        | 选择属于其父元素的第二个子元素的每个元素。 |
| :nth-child(odd)      | p:nth-child(odd)      | 选择属于其父元素的奇数元素。               |
| :nth-child(even)     | p:nth-child(even)     | 选择属于其父元素的偶数元素。               |
| :nth-of-type(n)      | p:nth-of-type(2)      | 选择属于其父元素第二个元素的每个元素。     |
| :nth-last-child(n)   | p:nth-last-child(2)   | 同上，从最后一个子元素开始计数。           |
| :nth-last-of-type(n) | p:nth-last-of-type(2) | 同上，但是从最后一个子元素开始计数。       |
| :not(selector)       | :not(p)               | 选择非元素的每个元素                       |

### :超链接伪类

定义链接的不同状态

```text
a:link {
    color: red
}

a:visited {
    color: green
}

a:hover {
    color: blue
}

a:active {
    color: yellow
}
...

<a href="https://www.houdunren.com">后盾人</a>
```

不只是链接可以使用伪类，其他元素也可以使用。下面是对表单的点击与获取焦点状态的样式设置。

```text
input:focus {
    background: green;
}

input:hover {
    background: blue;
}

input:active {
    background: yellow;
}
...

<input type="text">
```

### :target

用于控制具有锚点目标元素的样式

```text
div {
	height: 900px;
}

div:target {
	color: red;
}
...

<a href="#hdcms">hdcms</a>
<div></div>
<div id="hdcms">
	hdcms内容管理系统
</div>
```

### :root

根元素选择伪类即选择html

```text
:root {
    font-size: 100px;
}
```

### :empty

没有内容和空白的元素。下面第一个p标签会产生样式，第二个不会因为有空白内容

```text
:empty {
    border: solid 2px red;
}
...

<p></p>
<p> </p>
```

## 结构伪类

下面来通过结构伪类选择器选择树状结构中的标签元素。

### :first-child

选择元素中`span` 标签并且是第一个。

```text
article span:first-child {
    color: red;
}
...

<article>
	<span>houdunren.com</span>
	<aside>
		<span>houdunwang.com</span>
		<span>hdcms.com</span>
	</aside>
</article>
```

### :first-of-type

选择类型是`span` 的第一个元素

```text
article span:first-of-type {
    color: red;
}
...

<article>
	<span>houdunren.com</span>
	<aside>
		<strong>hdcms.com</strong>
		<span>houdunwang.com</span>
	</aside>
</article>
```

### :last-child

选择元素中`span` 标签并且是最后一个。

```text
article span:last-child {
    color: red;
}
...

<article>
  <span>houdunren.com</span>
  <aside>
    <strong>hdcms.com</strong>
    <span>houdunwang.com</span>
  </aside>
  <span>hdphp.com</span>
</article>
```

### :last-of-type

选择类型为`span` 的最后一个元素

```text
article span:last-of-type {
    color: red;
}
...

<article>
  <span>houdunren.com</span>
  <aside>
  	<span>houdunwang.com</span>
  	<strong>hdcms.com</strong>
  </aside>
  <span>hdphp.com</span>
</article>
```

### :only-child

选择是唯一子元素的`span` 标签

```text
article span:only-child {
    color: red;
}
...

<article>
	<span>houdunren.com</span>
	<aside>
		<span>houdunwang.com</span>
	</aside>
</article>
```

### :only-of-type

选择同级中类型是`span` 的唯一子元素

```text
article span:only-of-type {
    color: red;
}
...

<article>
	<span>houdunren.com</span>
	<aside>
		<span>houdunwang.com</span>
		<span>hdcms.com</span>
	</aside>
</article>
```

### :nth-child(n)

选择第二个元素并且是span标签的

```text
article span:nth-child(2) {
    color: red;
}
...

<article>
  <span>houdunren.com</span>
  <aside>
    <span>houdunwang.com</span>
    <span>hdcms.com</span>
  </aside>
  <span>hdphp.com</span>
</article>
```

### :nth-of-type(n)

选择第二个`span` 元素，不管中间的其他元素

```text
article span:nth-of-child(2) {
    color: red;
}
...

<article>
  <span>houdunren.com</span>
  <aside>
    <span>houdunwang.com</span>
    <span>hdcms.com</span>
  </aside>
  <span>hdphp.com</span>
</article>
```

### 计算数量

n为0/1/2/3... ，下面是隔列变色

```text
table tr>td:nth-child(2n+1) {
    background: green;
    color: white;
}
...

<table border="1">
  <tr>
    <td>houdunren.com</td>
    <td>hdcms.com</td>
    <td>后盾人</td>
    <td>houdunwang.com</td>
    <td>hdcms</td>
  </tr>
</table>
```

从第三个开始设置样式

```text
table tr>td:nth-child(n+3) {
    background: rgb(128, 35, 2);
    color: white;
}
```

设置前三个元素

```text
table tr>td:nth-child(-n+3) {
    background: rgb(128, 35, 2);
    color: white;
}
```

### 奇数元素

选择奇数单元格

```text
table tr>td:nth-child(odd) {
    background: green;
    color: white;
}
...

<table border="1">
  <tr>
    <td>houdunren.com</td>
    <td>hdcms.com</td>
    <td>后盾人</td>
    <td>houdunwang.com</td>
    <td>hdcms</td>
  </tr>
</table>
```

### 偶数元素

选择偶数单元格

```text
table tr>td:nth-child(even) {
    background: green;
    color: white;
}
...

<table border="1">
  <tr>
    <td>houdunren.com</td>
    <td>hdcms.com</td>
    <td>后盾人</td>
    <td>houdunwang.com</td>
    <td>hdcms</td>
  </tr>
</table>
```

### :nth-last-child(n)

从最后一个元素开始获取

```text
table tr>td:nth-last-child(2n+1){
    background: green;
    color: white;
}
...

<table border="1">
  <tr>
    <td>houdunren.com</td>
    <td>hdcms.com</td>
    <td>后盾人</td>
    <td>houdunwang.com</td>
    <td>hdcms</td>
  </tr>
</table>
```

取最后两个元素

```text
main>ul li:nth-last-child(-n+2) {
	color: red;
}
```

### :nth-last-of-type(n)

从最后一个元素开始选择`span` 标签 。

```text
article span:nth-last-of-type(1) {
    background: red;
    color: white;
}
...

<article>
  <aside>
  	<span>houdunren.com</span>
  	<span>houdunwang.com</span>
  	<strong>hdcms.com</strong>
  </aside>
	<span>hdphp.com</span>
</article>
```

### :not(selector)

排除第一个li元素

```text
ul li:not(:nth-child(1)) {
    background: red;
}
...

<ul>
  <li>houdunren.com</li>
  <li>hdcms.com</li>
  <li>后盾人</li>
</ul>
```

## 表单伪类

| 选择器    | 示例           | 说明                        |
| --------- | -------------- | --------------------------- |
| :enabled  | input:enabled  | 选择每个启用的 input 元素   |
| :disabled | input:disabled | 选择每个禁用的 input 元素   |
| :checked  | input:checked  | 选择每个被选中的 input 元素 |
| :required | input:required | 包含`required`属性的元素    |
| :optional | input:optional | 不包含`required`属性的元素  |
| :valid    | input:valid    | 验证通过的表单元素          |
| :invalid  | input:invalid  | 验证不通过的表单            |

### 表单属性样式

```text
input:enabled {
    background: red;
}

input:disabled {
    background: #dddddd;
}

input:checked+label {
    color: green;
}
...

<input type="text" disabled>
<input type="text" name="info">

<input type="radio" name="sex" checked id="boy">
<label for="boy">男</label>
<input type="radio" name="sex" checked id="girl">
<label for="girl">女</label>
```

### 表单必选样式

```text
input:required {
    border: solid 2px blue;
}

input:optional {
	background: #dcdcdc; 
	border: none;
}
...

<input type="text" name="title" required>
<input type="text" name="name">
```

### 表单验证样式

```text
input:valid {
    border: solid 1px green;
}

input:invalid {
    border: solid 1px red;
}
...

<form>
<input type="email">
<button>保存</button>
</form>
```

## 字符伪类

| 状态           | 示例           | 说明                         |
| -------------- | -------------- | ---------------------------- |
| ::first-letter | p:first-letter | 选择每个元素的首字母         |
| ::first-line   | p:first-line   | 选择每个元素的首行           |
| ::before       | p:before       | 在每个元素的内容之前插入内容 |
| ::after        | p:after        | 在每个元素的内容之后插入内容 |

### 首字母大写

```text
p::first-line {
    font-size: 20px;
}
...

<p>
	后盾人不断更新视频教程
</p>
```

### 段落首行处理

```text
p::first-letter {
    font-size: 30px;
}
...

<p>
	后盾人不断更新视频教程
</p>
```

### 在元素前添加

```text
span::before {
    content: '⇰';
    color: red;
}
span::after {
    content: '⟲';
    color: green;
}
...

<span>后盾人</span>
```

### 搜索框示例

![image-20190813223919156](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAKgAAAAhCAYAAABN9OCkAAABRmlDQ1BJQ0MgUHJvZmlsZQAAKJFjYGASSSwoyGFhYGDIzSspCnJ3UoiIjFJgf8zAwcDLIMpgwCCemFxc4BgQ4ANUwgCjUcG3awyMIPqyLsgsOZfwzRZF+Qzt3+54WAqkncZUjwK4UlKLk4H0HyBOSy4oKmFgYEwBspXLSwpA7A4gW6QI6Cggew6InQ5hbwCxkyDsI2A1IUHOQPYNIFsgOSMRaAbjCyBbJwlJPB2JDbUXBHhcXH18FEKNTAzNPQg4l3RQklpRAqKd8wsqizLTM0oUHIGhlKrgmZesp6NgZGBoycAACnOI6s83wGHJKMaBECsQY2CwdGFgYF6MEEuSYmDYDnS/JCdCTGU5AwN/BAPDtoaCxKJEuAMYv7EUpxkbQdjc2xkYWKf9//85nIGBXZOB4e/1//9/b////+8yoPm3GBgOfAMAkoFdEFXeaFAAAAIdSURBVHgB7Zs7roJAFIaP5FZGrIxbsLCyobUnsdQ94Ba0cQ+6BXdhQ2JiQk3UwthYmthgYeV1uOFGg0SYwMB4/kkICDPn8Z0/w9Pa/dEIDQQqSsCoaFwICwRCAhAohFBpAhBopcuD4H6eEez3++ef2AaBXAl0Op3M9l4EKkbLGMnsFQPYEZCd/HCKZycVvRKGQPWqF7toIVB2JdcrYQhUr3qxixYCZVfydAmfz2eazWbkOE66AQX1it3FF+QHZjUiEAQB9Xo9qtfrNJlMSo0cAi0VfzWdL5dLOp1OdL1eQ5GWGSVO8WXSr6jv7XZLo9EoUZzH45Eul4uS6CFQJZj1cmKaJgkRJrXD4UCDwSCcYZP65LUfAs2L5BfZsW2bPM+j+XxO4nr0XVuv1zQcDul2u707nN8+8T1o1Ha7XbSJNXMCi8VCfCccLu12+/68NBqN/2Pj8TgVKVlt1YT1SO7ifSnexUc0sBaPmnzfj82SYnadTqf0ECptNhvqdrsfYclqC3fxH9Hy7dBqtajf78cAGIYRitN13VTijBnIsAPXoBlgoesfgWazSavVKnxWWjQTzKBFE/5C+5ZlKcsKM6gy1HAkQwAClaGGMcoIQKDKUMORDAEIVIYaxigjAIEqQw1HMgQgUBlqGKOMQOwxk+y/75RFDEesCLy86mSVOZLVggBO8VqUiW+QECjf2muROQSqRZn4BgmB8q29Fpn/Ai4t44Qm/srhAAAAAElFTkSuQmCC)

```text
div {
    border: solid 1px #ddd;
    width: 150px;
}

div>input[type="text"] {
    border: none;
    outline: none;
}

div>input[type="text"]+span:after {
    content: "\21AA";
    font-size: 14px;
    cursor: pointer;
}
...

<div>
	<input type="text"><span></span>
</div>
```

### 添加属性内容

```text
h2::before {
	content: attr(title);
}
...

<h2 title="后盾人">houdunren.com</h2>
```
