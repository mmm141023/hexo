---
title: HTML之基础知识
date: 2020-05-16 21:38:42
tags: 
    - HTML
categories: 
    - 前端
    - 后盾人
---
## 学习环境

> [houdunren.com](https://www.houdunren.com/) @ 向军大叔

- 前端学习基本上存在浏览器和开发工具即可
- 浏览器使用`chrome`
- 开发工具使用 `vscode` 免费开源跨平台（[后盾人已经录制视频](https://www.houdunren.com/edu/front/lesson/263)）
- 用到后台服务器时使用 `wamp`、`xampp`、`mamp`根据自己的操作系统选择（[后盾人已经录制视频](https://www.houdunren.com/edu/front/system/3)）

### chrome

`chrome`是`google`推出的市场占有率最高的浏览器。因为`chrome`是开源的所以我们用的很多国内浏览器都是基于 `chrome`开发的。

**查看源码**

通过查看其他网站源码有助于新手学习，同时有些HTML是后台脚本如PHP渲染出来的，通过查看源码可以帮助我们分析问题。

![image-20190725125429044](http://houdunren.gitee.io/note/assets/img/image-20190725125429044.f4b244a7.png)

**控制台**

`console`是使用最多的调试功能，在`html/css/js`都会使用到

![image-20190725125609883](http://houdunren.gitee.io/note/assets/img/image-20190725125609883.88bdad58.png)

## 基础知识

HTML 不是一种编程语言，而是一种标记语言 (markup language)，是网页制作所必备的。用于按不同标签声明网页中的内容。

通过下图我们可以看到，一个网页是由很多区域组合构成的，即使用HTML标签布局。

![image-20190725115528125](http://houdunren.gitee.io/note/assets/img/image-20190725115528125.cb1c451b.png)

### 文件命名

- 使用小写字线命名文件，不要出现中文字符
- 扩展名标准是.html，当然也可以使用.htm
- 多个单词可以使用`-` 或 `_` 连接，建议使用`-` 字符如`user-create.html`

### URL

统一资源定位符，用于表示资源在网络上的地址，每个部分以`/`进行分隔。

**http资源访问**

```text
https://www.houdunren.com/edu/front/lesson/298.html
```

**FTP文件下载**

```text
ftp://ftp.houdunren.com/download/php.pdf
```

**MAILTO邮箱地址**

```text
mailto:2300071698@qq.com
```

**参数说明**

| 参数              | 说明                              |
| ----------------- | --------------------------------- |
| https             | 访问协议 http或https、ftp、mailto |
| www.houdunren.com | 服务器地址                        |
| edu/front/lesson  | 资源目录                          |
| 298.html          | 文件名                            |

### 访问路径

#### 绝对路径

绝对路径包含`主机+服务器地址+目录+文件名`的完整路径

```text
https://www.houdunren.com/edu/front/lesson/298.html
```

#### 相对路径

相对路径是指相对当前目录的地址

```text
# 当前目录的文件
2.html

# 上级目录中的文件
../3.html

# 子目录中的文件
block/user.html

# 根目录中的文件
/bootstrap.html
```

## 注释

使用注释对一段html代码进行说明，方便自己或同事在未来清楚的明白代码意图。

```text
<!-- 这是导航条 START -->
<header role="navigation">
  <nav>
    <ul>
      <li>
      	<a href="">后盾人首页</a>
      </li>
      <li>
      	<a href="">系统课程</a>
      </li>
    </ul>
  </nav>
</header>
<!-- 这是导航条 END -->
```
