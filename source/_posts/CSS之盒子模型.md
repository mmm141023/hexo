---
title: CSS之盒子模型
date: 2020-05-16 18:07:14
tags: 
    - CSS
categories: 
    - 前端
    - 后盾人
---
## 盒子模型

> [houdunren.com](https://www.houdunren.com/) @ 向军大叔

![image-20190817163854641](http://houdunren.gitee.io/note/assets/img/image-20190817163854641.0f6c1947.png)

下而是基本使用示例

```text
<style>
  a {
    display: inline-block;
    border: solid 1px #ddd;
    text-align: center;
    padding: 10px 20px;
    margin-right: 30px;
  }
</style>
...

<a href="">MYSQL</a>
<a href="">LINUX</a>
<a href="">PHP</a>
```

## 外边距

### 声明定义

边距顺序依次为：上、右、下、左。

![image-20190817185522220](http://houdunren.gitee.io/note/assets/img/image-20190817185522220.41d1113e.png)

```text
<style>
  main {
    border: solid 1px red;
    width: 500px;
    height: 500px;
    margin: 0 auto;
  }

  h2 {
    border: solid 2px green;
    width: 300px;
    height: 300px;
    margin: 50px 80px 100px 150px;
  }
</style>
...

<main>
<h2>houdunren.com</h2>
</main>
```

下例定义上下`50px`边距，左右`80px`边距

```text
 margin: 50px 80px;
```

下面将边距全部定义为 `100px`

```text
margin:100px;
```

### 居中设置

`margin` 设置auto 后，浏览器会自动

```text
<style>
article {
	border: solid 1px red;
}

h2,h3 {
	border: solid 10px #ddd;
}

h2 {
  width: 300px;
  margin-left: 200px;
  margin-right: 200px;
}

h3 {
  width: 500px;
  margin-left: auto;
  margin-right: auto;
}
</style>
...

<article>
<h2>houdunren.com</h2>
<h3>hdcms.com</h3>
</article>
```

### 负值设置

```text
<style>
  main {
    border: solid 1px red;
    width: 300px;
    margin: 0 auto;
  }

  h2 {
    border: solid 2px green;
    margin-left: -50px;
    margin-right: -50px;
    text-align: center;
  }
</style>
...

<main>
	<h2>houdunren.com</h2>
</main>
```

### 边距合并

相邻元素的纵向外边距会进行合并

```text
<style>
	h2 {
    border: solid 2px green;
    margin-bottom: 20px;
  }

  h3 {
    border: solid 2px green;
    height: 20px;
  }
</style>
...

<h2>houdunren.com</h2>
<h2>hdcms.com</h2>
<h3></h3>
```

## 内边距

内边距使用 `padding` 进行定义，使用语法与 `margin` 相似。

### 基本使用

```text
<style>
  a {
    padding: 10px 30px;
    border: solid 1px #ddd;
    border-radius: 5px;
  }

  a:hover {
    background: rgb(3, 78, 110);
    color: white;
  }
</style>
...

<a href="">MYSQL</a>
<a href="">CSS</a>
```

## BOX-SIZING

宽度与高度包括内边距与边框。

```text
h2 {
  border: solid 10px #ddd;
  height: 60px;
  width: 200px;
  padding:50px;
  box-sizing: border-box;
}
...

<h2>houdunren.com</h2>
```

## 边框设计

### 样式选择

| 类型   | 描述                                                  |
| :----- | :---------------------------------------------------- |
| none   | 定义无边框。                                          |
| dotted | 定义点状边框。在大多数浏览器中呈现为实线。            |
| dashed | 定义虚线。在大多数浏览器中呈现为实线。                |
| solid  | 定义实线。                                            |
| double | 定义双线。双线的宽度等于 border-width 的值。          |
| groove | 定义 3D 凹槽边框。其效果取决于 border-color 的值。    |
| ridge  | 定义 3D 垄状边框。其效果取决于 border-color 的值。    |
| inset  | 定义 3D inset 边框。其效果取决于 border-color 的值。  |
| outset | 定义 3D outset 边框。其效果取决于 border-color 的值。 |

一次定义四个边

```text
h2 {
	border-style: double;
}
```

样式顺序为上、右、下、左，可以分别进行定义

```text
h2 {
	border-style: outset solid dotted double;
	border-width: 8px;
}
```

单独设置一边样式

| 规则                | 说明 |
| ------------------- | ---- |
| border-top-style    | 顶边 |
| border-right-style  | 右边 |
| border-bottom-style | 下边 |
| border-left-style   | 左边 |
| border-style        | 四边 |

```text
h2 {
	border-top-style: double;
	border-width: 8px;
}
```

### 边框宽度

边框可以通过以下规则来设置

| 规则                | 说明 |
| ------------------- | ---- |
| border-top-width    | 顶边 |
| border-right-width  | 右边 |
| border-bottom-width | 下边 |
| border-left-width   | 左边 |
| border-width        | 四边 |

### 边框颜色

| 规则                | 说明 |
| ------------------- | ---- |
| border-top-color    | 顶边 |
| border-right-color  | 右边 |
| border-bottom-color | 下边 |
| border-left-color   | 左边 |
| border-color        | 四边 |

### 简写规则

| 规则          | 说明 |
| ------------- | ---- |
| border-top    | 顶边 |
| border-right  | 右边 |
| border-bottom | 下边 |
| border-left   | 左边 |
| border        | 四边 |

设置底部边框

```text
border-bottom: solid 5px red;
```

### 行元素边框

行元素也可以进行边框设置

```text
em {
	border-bottom: solid 2px red;
}
```

### 圆角边框

使用 `border-radius` 规则设置圆角，可以使用`px | %` 等单位。也支持四个边分别设置。

| 选项                       | 说明 |
| -------------------------- | ---- |
| border-top-left-radius     | 上左 |
| border-top-right-radius    | 上右 |
| border-bottom-left-radius  | 下载 |
| border-bottom-right-radius | 下右 |

```text
h2 {
	border-radius: 10px;
	border: solid 2px red;
}
```

通过边框绘制圆

```text
div {
  width: 100px;
  height: 100px;
  border: solid 3px red;
  border-radius: 50%;
}
```

定义不同边

```text
border-radius: 10px 30px 50px 100px;
```

行元素绘制圆角

![image-20190817193835791](http://houdunren.gitee.io/note/assets/img/image-20190817193835791.b20aec8a.png)

```text
em {
	border-radius: 50%;
	border-bottom: solid 2px red;
}
```

## 轮廓线

元素在获取焦点时产生，并且轮廓线不占用空间。可以使用伪类 `:focus` 定义样式。

- 轮廓线显示在边框外面
- 轮廓线不影响页面布局

### 线条样式

| 值     | 描述                                                |
| :----- | :-------------------------------------------------- |
| none   | 默认。定义无轮廓。                                  |
| dotted | 定义点状的轮廓。                                    |
| dashed | 定义虚线轮廓。                                      |
| solid  | 定义实线轮廓。                                      |
| double | 定义双线轮廓。双线的宽度等同于 outline-width 的值。 |
| groove | 定义 3D 凹槽轮廓。此效果取决于 outline-color 值。   |
| ridge  | 定义 3D 凸槽轮廓。此效果取决于 outline-color 值。   |
| inset  | 定义 3D 凹边轮廓。此效果取决于 outline-color 值。   |
| outset | 定义 3D 凸边轮廓。此效果取决于 outline-color 值。   |

```text
outline-style: double;
```

### 线宽设置

```text
outline-width: 10px;
```

### 线条颜色

```text
outline-color: red;
```

### 组合定义

```text
outline: red solid 2px;
```

### 表单轮廓线

表单默认具有轮廓线，但有时并不好看，使用以下样式规则去除。

```text
input:focus {
	outline: none;
}
```

## DISPLAY

### 控制显示隐藏

使用 `display` 控制元素的显示机制。

| 选项         | 说明                        |
| ------------ | --------------------------- |
| none         | 隐藏元素                    |
| block        | 显示为块元素                |
| inline       | 显示为行元素，不能设置宽/高 |
| inline-block | 行级块元素，允许设置宽/高f  |

### 行转块元素

```text
a {
  border: solid 1px #ddd;
  display: block;
  margin-bottom: 5px;
}
...

<a href="">houdunren.com</a>
<a href="">houdunren.com</a>
<a href="">houdunren.com</a>
```

### 块转为行元素

```text
ul>li {
  display: inline;
  padding: 5px 10px;
  border: solid 1px #ddd;
}

ul>li:hover {
  background: green;
  color: white;
  cursor: pointer;
}
...

<ul>
<li>hdcms.com</li>
<li>houdunren.com</li>
<li>后盾人</li>
</ul>
```

### 行级块使用

```text
a {
  display: inline-block;
  width: 30%;
  height: 50px;
  border: solid 1px #ddd;
  text-align: center;
  line-height: 3em;
}
...

<a href="">MYSQL</a>
<a href="">LINUX</a>
<a href="">PHP</a>
```

## VISIBILITY

控制元素的显示隐藏，在隐藏后空间位也保留。

![image-20190822213523648](data:image/png;base64,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)

```text
<style>
	article {
    padding: 30px;
    border: solid 2px red;
    width: 200px;
  }
  article div {
    width: 100px;
    height: 100px;
    border: solid 2px red;
    padding: 20px;
  }
  article div:nth-of-type(1) {
    visibility: hidden;
  }
</style>

<article>
	<div></div>
	<div></div>
</article>
```

## 溢出控制

### 隐藏控制

| 选项   | 说明                                                 |
| ------ | ---------------------------------------------------- |
| hidden | 溢出内容隐藏                                         |
| scroll | 显示滚动条（有些浏览器会一直显示，有些在滚动时显示） |
| auto   | 根据内容自动处理滚动条                               |

**溢出隐藏**

![image-20190822210806149](http://houdunren.gitee.io/note/assets/img/image-20190822210806149.53098d3a.png)

```text
div {
  width: 400px;
  height: 100px;
  border: solid 2px #ddd;
  padding: 20px;
  overflow: hidden;
}
```

**溢出产生滚动条**

不同浏览器处理方式不同，有些直接显示出来，有些在滚动时才显示。

![image-20190822210842353](http://houdunren.gitee.io/note/assets/img/image-20190822210842353.e45f2ebb.png)

```text
div {
  width: 400px;
  height: 100px;
  border: solid 2px #ddd;
  padding: 20px;
  overflow: scroll;
}
```

### 文本溢出

**单行文本溢出**

![image-20190822211257747](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAcgAAABXCAYAAACA5tXIAAABRmlDQ1BJQ0MgUHJvZmlsZQAAKJFjYGASSSwoyGFhYGDIzSspCnJ3UoiIjFJgf8zAwSDGIMhgxiCcmFxc4BgQ4ANUwgCjUcG3awyMIPqyLsisHo35nyq0l2u+fd+g+ZftWDWmehTAlZJanAyk/wBxenJBUQkDA2MKkK1cXlIAYncA2SJFQEcB2XNA7HQIewOInQRhHwGrCQlyBrJvANkCyRmJQDMYXwDZOklI4ulIbKi9IMDr464Q6hMS5Bju6eJKwL0kg5LUihIQ7ZxfUFmUmZ5RouAIDKVUBc+8ZD0dBSMDQ0sGBlCYQ1R/vgEOS0YxDoRYgRgDg8UMoOBDhFg80A/b5RgY+PsQYmpA/wp4MTAc3FeQWJQIdwDjN5biNGMjCJt7OwMD67T//z+HMzCwazIw/L3+///v7f///13GwMB8i4HhwDcAR71hseitBrYAABypSURBVHgB7ZwDlCRJ14Zjdmdt25i1bdu2bdu2bdv2ztrmrG3b9eUT/39ro6Mjs7Ora2qnct57TnVmRgbfuHEVkd2rlpETCQEhIASEgBAQAh0QGKTDkx6EgBAQAkJACAgBj4AUpBhBCAgBISAEhEACASnIBChKEgJCQAgIASEgBSkeEAJCQAgIASGQQEAKMgGKkoSAEBACQkAISEGKB4SAEBACQkAIJBDoHaf169cvTtKzEBACQkAICIHKIdCnT5/CMcmDLIRHL4WAEBACQmBgRaCTB2lAdKVZLZ+uQkAICAEhIATaCYGykVJ5kO00q+qrEBACQkAItAwBKciWQa2GhIAQEAJCoJ0QkIJsp9lSX4WAEBACQqBlCEhBtgxqNSQEhIAQEALthIAUZDvNlvoqBISAEBACLUNACrJlUKshISAEhIAQaCcEpCDbabbUVyEgBISAEGgZAlKQLYNaDQkBISAEhEA7ISAF2U6zpb4KASEgBIRAyxCQgmwZ1GpICAgBISAE2gkBKch2mi31VQgIASEgBFqGgBRky6BWQ0JACAgBIdBOCEhBttNsqa9CQAgIASHQMgSkIFsGtRoSAkJACAiBdkJACrKdZkt9FQJCQAgIgZYhIAXZMqjVkBAQAkJACLQTAlKQ7TRb6qsQEAJCQAi0DAEpyJZBrYaEgBAQAkKgnRCQgmyn2VJfhYAQEAJCoGUISEG2DGo1JASEgBAQAu2EgBRkO82W+ioEhIAQEAItQ0AKsmVQqyEhIASEgBBoJwQGaAX5888/9wjLb7/91v31119d1vH222+79957r8t8qQxffPGFe/rpp93ff/+det0WaTfffLP7+OOPG+5rrVZzn3zyifvnn39y6/j+++/dSy+9lPueF5R/55133FdffVWYr3++pO3nnnuufzaRrBt8Hn/8cffnn38m33eV+Msvv7h7773X/frrrz7riy++6N56662uinV6f+utt7rPPvvMp1Nnd9Yg83f//fc71t1/RV9//bV75pln/qvm3SuvvNIln3e3c6yvzz//vGHeyGvv999/d/fcc0+dZ/LyDczpvVs9eCabhffTTz+5H3/80S9ArjD2m2++6d544w336quvOhY46TDG6KOPXu8mAhRhzsKlHlvEP/zwg/voo4/cu+++61B41AGdcsopbuutt66XT93stddebthhh3Xnnntu6nVh2lFHHeWuvPLKhhVsYeUtePnEE0+45ZZbzl111VVu1VVXbajFgw8+2O2///5un332cdyn6OGHH3bLLLOMN1gGHXTQVBaHkphkkkncfvvt5w488MBkHkt88skn3aOPPmqPpa5DDjmk22KLLXLzwjcLLLCA56Pdd9/dHX744a5Xr165+Zv1AiNuzTXX9IIdvh1llFFKVQ3fmTGBoXbQQQe5Aw44wI066qjutNNOc8MPP7xbZ5116nVtuOGGbuihh64/c7PZZpu5RRdd1M89a405uu2229ySSy7p1w3r8I477nCjjTZah3Kph/vuu8/X9cILL7iRRhoplaWexpjvvvvu+nOZm/nnn79T/+Ny1157rdtll10c8qAr+u2339xQQw3lhhtuODfCCCPkZkeu7Ljjju64447LzWMv4FvG369fP0vKvTJ3GOYmy5CJ3HMlHVlHPSbLjj32WLfTTjvV6+tp/7/77js/XxdffHGdTzCQmP8Urb766m6++eZLvapsWssVJILn6KOP7gQoSpCFPdlkk7l5553XbbLJJm7yySf3iivMfNhhh3lFRn6U2ogjjuiGGWYYn+Whhx5yG220kVtqqaXceOON538TTDBBWDx5j/eH8CxDKHHzhFD2Z511lmeaG2+8sVPx6aabzk066aQd0rGuGT+KCZp77rn94osFyg033OCoE6FteEw00UQd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)

```text
div {
  width: 400px;
  height: 100px;
  border: solid 2px #ddd;
  padding: 20px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

**多行文本溢出控制**

![image-20190822212007695](http://houdunren.gitee.io/note/assets/img/image-20190822212007695.0de35203.png)

```text
div {
  width: 200px;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
}
```

## 尺寸定义

可以使用多种方式为元素设置宽、高尺寸。

| 选项           | 说明             |
| -------------- | ---------------- |
| width          | 宽度             |
| height         | 高度             |
| min-width      | 最小宽度         |
| min-height     | 最小高度         |
| max-width      | 最大宽度         |
| max-height     | 最大高度         |
| fill-available | 撑满可用的空间   |
| fit-content    | 根据内容适应尺寸 |

### min&max

正文中不希望图片太大造成溢出窗口，也不希望太小影响美观，使用以下代码可以做到约束。

![image-20190822205823322](http://houdunren.gitee.io/note/assets/img/image-20190822205823322.95f03715.png)

```text
<style>
	div {
    width: 600px;
    border: solid 2px #ddd;
    padding: 20px;
  }
  div img {
    min-width: 50%;
    max-width: 90%;
  }
</style>
```

### fill-available

在`chrome` 浏览器中使用前缀 `-webkit` 书写样式。

下面是行块元素可以撑满可用空间后的效果。

![image-20190928120513013](data:image/png;base64,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)

```text
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        body {
            width: 100vw;
            height: 100vh;
            background: #2c3e50;
        }

        main {
            background: #9b59b6;
            height: 100px;
            padding: 20px;
            box-sizing: border-box;
        }

        span {
            background: #e67e22;
            display: inline-block;
            width: -webkit-fill-available;
            height: -webkit-fill-available;
        }
    </style>
</head>

<body>
    <main>
        <span>
            houdunren.com
        </span>
    </main>
</body> 
```

### fit-content

下面是根据内容自动适应宽度，让元素居中显示的效果。

![image-20190928112415984](data:image/png;base64,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)

```text
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        body {
            width: 100vw;
            height: 100vh;
            background: #2c3e50;
        }

        h2 {
            text-align: center;
            background: #f1c40f;
            width: fit-content;
            margin: auto;
        }
    </style>
</head>

<body>
    <h2>houdunren.com</h2>
</body>
```

### min-content

使用`min-content` 将容器尺寸按最小元素宽度设置。

![image-20190928113203223](data:image/png;base64,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)

```text
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        body {
            width: 100vw;
            height: 100vh;
            background: #2c3e50;
        }

        main {
            width: min-content;
            margin: auto;
        }

        div {
            margin-bottom: 20px;
            background: #f1c40f;
            word-break: break-all;
            padding: 10px;
        }

        div:nth-child(1) {
            width: 100px;
        }
    </style>
</head>

<body>
    <main>
        <div>houdunren.com</div>
        <div>hdcms.com</div>
    </main>
</body>
```

### max-content

容器尺寸按子元素最大宽度设置。

![image-20190928113523718](http://houdunren.gitee.io/note/assets/img/image-20190928113523718.9c10a85d.png)

```text
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        body {
            width: 100vw;
            height: 100vh;
            background: #2c3e50;
        }

        main {
            width: max-content;
            margin: auto;
        }

        div {
            margin-bottom: 20px;
            background: #f1c40f;
            word-break: break-all;
            padding: 10px;
        }
    </style>
</head>

<body>
    <main>
        <div>在线视频教程学习网站。houdunren.com</div>
        <div>hdcms.com</div>
    </main>
</body>
```
