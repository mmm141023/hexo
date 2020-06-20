---
title: CSS之文本控制
date: 2020-05-16 18:06:26
tags: 
    - CSS
categories: 
    - 前端
    - 后盾人
## 文本基础

> [houdunren.com](https://www.houdunren.com/) @ 向军大叔

### 字体设置

可以定义多个字体，系统会依次查找，比如 `'Courier New'` 字体不存在将使用 `Courier` 以此类推。

要使用通用字体，比如你电脑里有 `后盾人宋体` 在你电脑可以正常显示，但不保证在其他用户电脑可以正常，因为他们可能没有这个字体。

```text
font-family: 'Courier New', Courier, monospace;
```

**自定义字体**

可以声明自定义字段，如果客户端不存在将下载该字体，使用方式也是通过 `font-family` 引入。

```text
<style>
  @font-face {
  	font-family: "houdunren";
  	src: 	url("SourceHanSansSC-Light.otf") format("opentype"),
  				url("SourceHanSansSC-Heavy.otf") format("opentype");
  }

  span {
  	font-family: 'houdunren';
  }
</style>
```

| 字体  | 格式              |
| ----- | ----------------- |
| .otf  | opentype          |
| .woff | woff              |
| .ttf  | truetype          |
| .eot  | Embedded-opentype |

不建议使用中文字体，因为文件太大且大部分是商业字体。

### 字重定义

字重指字的粗细定义。取值范围 `normal | bold | bolder | lighter | 100 ~900`。

400对应 `normal`,700对应 `bold` ，一般情况下使用 bold 或 normal 较多。

```text
<style>
span {
	font-weight: bold;
}

strong:last-child {
	font-weight: normal;
}
</style>
...

<span>houdunren.com</span>
<strong>hdcms.com</strong>
```

### 文本字号

字号用于控制字符的显示大小，包括 `xx-small | x-small | small | meidum | large | x-large | xx-large`。

**百分数**

百分数是子元素相对于父元素的大小，如父元素是20px，子元素设置为 200%即为你元素的两倍大小。

```text
<style>
  article {
  	font-size: 20px;
  }

  span {
  	font-size: 500%;
  }
</style>
...

<article>
	<span>houdunren.com</span>
</article>
```

**em**

em单位等同于百分数单位。

```text
<style>
  article {
  	font-size: 20px;
  }

  span {
  	font-size: 5em;
  }
</style>
...

<article>
	<span>houdunren.com</span>
</article>
```

### 文本颜色

**字符串颜色**

可以使用如 `red | green` 等字符颜色声明

```text
color:red;
```

**使用十六进制网页颜色**

```text
color:#ddffde
```

如果颜色字符相同如 `#dddddd` 可以简写为 `#ddd`

**使用RGB颜色**

```text
color:rgb(38, 149, 162);
```

**透明颜色**

透明色从 `0~1` 间，表示透明到不透明

```text
color:rgba(38, 149, 162,.2);
```

### 行高定义

```text
div {
	line-height: 2em;
}
```

### 倾斜风格

字符的倾斜样式控制

```text
<style>
  span {
  	font-style: italic;
  }

  em {
  	font-style: normal;
  }
</style>
...

<span>houdunren.com</span>
<hr>
<em>hdcms.com</em>
```

### 组合定义

可以使用 `font` 一次将字符样式定义，但要注意必须存在以下几点：

- 必须有字体规则
- 必须有字符大小规则

```text
span {
	font: bold italic 20px/1.5 'Courier New', Courier, monospace;
}
...

<span>houdunren.com</span>
```

> 上例中的 20px 为字体大小，1.5为1.5倍行高定义

## 文本样式

### 大小转换

小号大写字母

```text
span {
	font-variant: small-caps;
}
...

<span>houdunren.com</span>
```

字母大小写转换

```text
<style>
h2 {
  /* 首字母大小 */
  text-transform: capitalize;

  /* 全部大小 */
  text-transform: uppercase;

  /* 全部小写 */
  text-transform: lowercase;
  }
</style>
```

### 文本线条

添加隐藏删除线

```text
a {
	text-decoration: none;
}

span.underline {
	text-decoration: underline;
}

span.through {
	text-decoration: line-through;
}

span.overline {
	text-decoration: overline;
}
...

<a href="">houdunren.com</a>
<hr>
<span class="underline">下划线</span>
<hr>
<span class="through">删除线</span>
<hr>
<span class="overline">上划线</span>
```

### 阴影控制

参数顺序为：颜色，水平偏移，垂直偏移，模糊度。

![image-20190816173740680](http://houdunren.gitee.io/note/assets/img/image-20190816173740680.5ca4bee3.png)

```text
<style>
  h2 {
  	text-shadow: rgba(13, 6, 89, 0.8) 3px 3px 5px;
  }
</style>
...

<h2>houdunren.com</h2>
```

### 空白处理

使用 `white-space` 控制文本空白显示。

| 选项     | 说明                                    |
| -------- | --------------------------------------- |
| pre      | 保留文本中的所有空白，类似使用 pre 标签 |
| nowrap   | 禁止文本换行                            |
| pre-wrap | 保留空白，保留换行符                    |
| pre-line | 空白合并，保留换行符                    |

```text
h2 {
	white-space: pre;
	width: 100px;
	border: solid 1px #ddd;
}
...

<h2>hou        dunren     .com</h2>
```

### 文本溢出

溢出文本容器后换行处理

```text
h2 {
  overflow-wrap: break-word;
  width: 100px;
	border: solid 1px #ddd;
}
...

<h2>houdunren.com</h2>
```

溢出添加 `...`，需要将overflow 设置在 text-overflow 前面。

```text
h2 {
  width: 100px;
  border: solid 1px #ddd;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
...

<h2>houdunren.com</h2>
```

## 段落控制

### 文本缩进

控制元素部的文本、图片进行缩进操作

```text
<style>
  p {
	  text-indent: 2em;
  }
</style>
<p>
后盾人自2010年创立至今，免费发布了大量高质量视频教程，视频在优酷、土豆、酷六等视频网站均有收录，很多技术爱好者受益其中。除了免费视频外，后盾人还为大家提供了面授班、远程班、公益公开课、VIP系列课程等众多形式的学习途径。后盾人有一群认真执着的老师，他们一心为同学着想，将真正的知识传授给大家是后盾人永远不变的追求。
</p>
```

### 水平对齐

使用 `left|right|center` 对文本进行对齐操作

```text
h2 {
	text-align: center;
}
...
<h2>houdunren.com</h2>
```

为了让段落内容看得舒服，需要设置合适的行高

```text
p {
	text-indent: 2em;
	line-height: 2em;
}
...
<p>
后盾人自2010年创立至今，免费发布了大量高质量视频教程，视频在优酷、土豆、酷六等视频网站均有收录，很多技术爱好者受益其中。除了免费视频外，后盾人还为大家提供了面授班、远程班、公益公开课、VIP系列课程等众多形式的学习途径。后盾人有一群认真执着的老师，他们一心为同学着想，将真正的知识传授给大家是后盾人永远不变的追求。
</p>
```

### 垂直对齐

使用 `vertical-align` 用于定义内容的垂直对齐风格，包括`middle | baseline | sub | super` 等。

**图像在段落中居中对齐**

```text
img {
	height: 50px;
	width: 50px;
	vertical-align: middle;
}
...

<p>
<img src="houdunren.jpg">后盾人自2010年创立至今，免费发布了大量高质量视频教程，视频在优酷、土豆、酷六等视频网站均有收录，很多技术爱好者受益其中。除了免费视频外，后盾人还为大家提供了面授班、远程班、公益公开课、VIP系列课程等众多形式的学习途径。后盾人有一群认真执着的老师，他们一心为同学着想，将真正的知识传授给大家是后盾人永远不变的追求。
</p>
```

**顶部与底部对齐**

`bottom | top` 相对于行框底部或顶部对齐。

```text
h2>span {
	vertical-align: bottom;
	font-size: 12px;
}
...

<h2>houdunren.com <span>hdcms</span></h2>
```

**使用单位对齐**

可以使用具体数值设置对齐的位置。

```text
h2>span {
	vertical-align: -20px;
	font-size: 12px;
}
```

### 字符间隔

**单词与字符间距**

使用 `word-spacing` 与 `letter-spacing` 控制单词与字答间距。

```text
h2 {
	word-spacing: 2em;
	letter-spacing: 3em;
}
```

### 排版模式

| 模式          | 说明                                     |
| ------------- | ---------------------------------------- |
| horizontal-tb | 水平方向自上而下的书写方式               |
| vertical-rl   | 垂直方向自右而左的书写方式               |
| vertical-lr   | 垂直方向内内容从上到下，水平方向从左到右 |

![image-20190816183805169](http://houdunren.gitee.io/note/assets/img/image-20190816183805169.311a6bb3.png)

```text
div {
  height: 200px;
  border: solid 1px #ddd;
  writing-mode: vertical-rl;
}
...

<div>
后盾人自2010年创立至今，免费发布了大量高质量视频教程，视频在优酷、土豆、酷六等视频网站均有收录，很多技术爱好者受益其中。除了免费视频外，后盾人还为大家提供了面授班、远程班、公益公开课、VIP系列课程等众多形式的学习途径。后盾人有一群认真执着的老师，他们一心为同学着想，将真正的知识传授给大家是后盾人永远不变的追求。
</div>
```
