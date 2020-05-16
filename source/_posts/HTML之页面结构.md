---
title: HTML之页面结构
date: 2020-05-16 21:43:35
tags: 
    - HTML
categories: 
    - 前端
    - 后盾人
---
## 语义标签

> [houdunren.com](https://www.houdunren.com/) @ 向军大叔

HTML标签都有具体语义，非然技术上可以使用div标签表示大部分内容，但选择清晰的语义标签更容易让人看明白。比如 `h1`表示标题、`p`标签表示内容、强调内容使用`em`标签。

```text
<article>
	<h1>后盾人</h1>
	<p>在线学习平台</p>
</article>
```

## 嵌套关系

元素可以互相嵌套包裹，即元素存在父子级关系。

```text
<article>
  <h1>后盾人</h1>
  <div>
    <p>在线学习平台</p>
    <span>houdunren.com</span>
  </div>
</article>
```

![image-20190725120421647](http://houdunren.gitee.io/note/assets/img/image-20190725120421647.95e6e1d0.png)

## 基本结构

下面是HTML文档的基本组成部分

```text
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <meta name="keyword" content="Mysql,Laravel,Javascript,HTML,CSS,ES6,TYPESCRIPT,后盾人,后盾人教程" />
    <meta name="description" content="后盾人专注WEB开发，高密度更新视频教程" />
    <title>后盾人</title>
</head>
<body>
   
</body>
</html>
```

| 标签        | 说明                                            |
| ----------- | ----------------------------------------------- |
| DOCTYPE     | 声明为HTML文档                                  |
| html        | lang:网页的语言，如en/zh等，非必选项目          |
| head        | 文档说明部分，对搜索引擎提供信息或加载CSS、JS等 |
| title       | 网页标题                                        |
| keyword     | 向搜索引擎说明你的网页的关键词                  |
| description | 向搜索引擎描述网页内容的摘要信息                |
| body        | 页面主体内容                                    |

## 内容标题

标题使用 `h1 ~ h6` 来定义，用于突出显示文档内容。

- 从 h1到h6对搜索引擎来说权重会越来越小
- 页面中最好只有一个h1标签
- 标题最好不要嵌套如 h1内部包含 h2

下面是使用默认样式的标题效果，掌握CSS后我们就可以随意美化了。

```text
<h1>后盾人</h1>
<h2>houdunren.com</h2>
<h3>hdcms.com</h3>
<h4>houdunwang.com</h4>
<h5>doc.houdunren.com</h5>
<h6>www.hdcms.com</h6>
```

![image-20190725143133097](http://houdunren.gitee.io/note/assets/img/image-20190725143133097.6b8ac92e.png)

## 页眉页脚

### header

header标签用于定义文档的页眉，下图中的红色区域都可以使用`header`标签构建。

![image-20190725143914516](http://houdunren.gitee.io/note/assets/img/image-20190725143914516.bcffc293.png)

```text
<body>
    <header>
        <nav>
            <ul>
                <li><a href="">系统学习</a></li>
                <li><a href="">视频库</a></li>
            </ul>
        </nav>
    </header>
    <article>
        <h2>后盾人网站动态</h2>
        <ul>
            <li><a href="">完成签到 开心每一天</a></li>
            <li><a href="">完成签到 来了，老铁</a></li>
        </ul>
    </article>
   	...
</body>
```

### footer

footer 标签定义文档或节的页脚，页脚通常包含文档的作者、版权信息、使用条款链接、联系信息等等。

![image-20190725144209867](http://houdunren.gitee.io/note/assets/img/image-20190725144209867.e3ad5cf8.png)

```text
<body>
    ...
    <article>
        <h2>后盾人网站动态</h2>
        <ul>
            <li><a href="">完成签到 开心每一天</a></li>
            <li><a href="">完成签到 来了，老铁</a></li>
        </ul>
    </article>
    <footer>
        <p>
            我们的使命：传播互联网前沿技术，帮助更多的人实现梦想
        </p>
    </footer>
</body>
```

## 导航元素

在HTML中使用`nav`设置导航链接。

![image-20190725155313952](http://houdunren.gitee.io/note/assets/img/image-20190725155313952.6de67df5.png)

```text
<header>
        <nav>
            <ul>
                <li>
                    <a href="">系统学习</a>
                </li>
                <li>
                    <a href="">视频库</a>
                </li>
            </ul>
        </nav>
</header>
```

## 主要区域

HTML5中使用 `main` 标签表示页面主要区域，一个页面中`main`元素最好只出现一次。

![image-20190725160319383](http://houdunren.gitee.io/note/assets/img/image-20190725160319383.782b883c.png)

```text
<body>
		...
    <main>
        <article>
            <h2>网站动态</h2>
            <ul>
                <li><a href="">完成签到 开心每一天</a></li>
                <li><a href="">完成签到 来了，老铁</a></li>
            </ul>
        </article>
    </main>
    ...
</body>
```

## 内容区域

使用 `article` 标签规定独立的自包含内容区域。不要被单词的表面意义所局限，`article` 标签表示一个独立的内容容器。

![image-20190725161743627](http://houdunren.gitee.io/note/assets/img/image-20190725161743627.feb72e82.png)

```text
<main>
	<article>
    <h2>后盾人网站动态</h2>
    <ul>
      <li><a href="">完成签到 开心每一天</a></li>
      <li><a href="">完成签到 来了，老铁</a></li>
    </ul>
	</article>
</main>
```

## 区块定义

使用 `section` 定义一个区块，一般是一组相似内容的排列组合。

![image-20190725162232253](http://houdunren.gitee.io/note/assets/img/image-20190725162232253.578dfcf0.png)

```text
<main>
   <article>
     <section>
       <h2>锁机制</h2>
     </section>
     <section>
      <h2>事物处理</h2>
     </section>
   </article>
</main>
```

## 附加区域

使用 `aside` 用于设置与主要区域无关的内容，比如侧面栏的广告等。

![image-20190725164542103](http://houdunren.gitee.io/note/assets/img/image-20190725164542103.82f1400c.png)

```text
<body>
  <main>
    <article>
      ...
    </article>
    </main>
    <aside>
      <h2>社区小贴</h2>
      <p>后盾人是一个主张友好、分享、自由的技术交流社区。</p>
    </aside>
  </main>
</body>
```

## 通用容器

`div` 通用容器标签是较早出现的，也是被大多数程序员使用最多的容器。不过我们应该更倾向于使用有语义的标签如`article/section/aside/nav` 等。

有些区域这些有语义的容器不好表达，这时可以采用`div`容器，比如轮播图效果中的内容。

![image-20190725165638145](http://houdunren.gitee.io/note/assets/img/image-20190725165638145.edf4b8f0.png)

```text
<div>
  <header>
    <nav>
      <ul>
        <li><a href="">后盾人</a></li>
        <li><a href="">系统课程</a></li>
      </ul>
    </nav>
  </header>
  
  <main>
    <article>
      <section>
        <h2>事物处理</h2>
      </section>
    </article>
    <aside>
      <h2>社区小贴</h2>
      <p>后盾人是一个主张友好、分享、自由的技术交流社区。</p>
    </aside>
  </main>
  
  <footer>
    <p>
    我们的使命：传播互联网前沿技术，帮助更多的人实现梦想
    </p>
  </footer>
</div>
```
