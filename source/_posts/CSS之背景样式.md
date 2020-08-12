---
title: CSS之背景样式
date: 2020-05-16 18:10:52
tags: 
    - CSS
categories: 
    - 前端
    - 后盾人
---
## 背景样式

> [houdunren.com](https://www.houdunren.com/) @ 向军大叔

### 背景颜色

背景颜色可以使用 `rga | rgba | 十六进制` 等颜色格式

```text
<style>
  h2 {
		background-color: red;
  }
</style>
...

<h2>houdunren.com</h2>
```

### 背景图片

可以使用 `png| gif |jpeg` 等图片做为背景使用

```text
background-image: url(icon-s.jpg);
```

### 背景裁切

| 选项        | 说明                 |
| ----------- | -------------------- |
| border-box  | 包括边框             |
| padding-box | 不含边框，包括内边距 |
| content-box | 内容区域             |

```text
background-clip: border-box;
```

### 背景重复

用于设置背景重复的规则

| 选项      | 说明                 |
| --------- | -------------------- |
| repeat    | 水平、垂直重复       |
| repeat-x  | 水平重复             |
| repeat-y  | 垂直重复             |
| no-repeat | 不重复               |
| space     | 背景图片对称均匀分布 |

```text
background-repeat: repeat-y
```

### 背景滚动

用于设置在页面滚动时的图片处理方式

| 选项   | 说明     |
| ------ | -------- |
| scroll | 背景滚动 |
| fixed  | 背景固定 |

```text
background-attachment: fixed;
```

### 背景位置

用于设置背景图片的水平、垂直定位。

| 选项   | 说明     |
| ------ | -------- |
| left   | 左对齐   |
| right  | 右对齐   |
| center | 居中对齐 |
| top    | 顶端对齐 |
| bottom | 底部对齐 |

居中对齐

```text
background-position: center;
或
background-position: 50% 50%;
```

水平居右，垂直居中

```text
background-position: right center;
或
background-position: 100% 50%;
```

使用具体数值定义

```text
background-position: 100px 100px;
也支持使用负值
background-position: -200px 100px;
```

### 背景尺寸

| 选项    | 说明                                       |
| ------- | ------------------------------------------ |
| cover   | 背景完全覆盖，可能会有背景溢出             |
| contain | 图片不溢出的放在容器中，可能会漏出部分区域 |

指定数值定义宽高尺寸

```text
background-size: 50% 100%;
或
background-size: 200px 200px;
```

宽度固定高度自动

```text
background-size: 50% auto;
```

### 多个背景

后定义的背景置于底层

```text
background-image: url(xj-small.png), url(bg.png);
```

多属性定义

```text
background-image: url(xj-small.png), url(bg.png);
background-repeat: no-repeat;
background-position: top left, right bottom;
```

可以一次定义多个背景图片。

```text
background: url(xj-small.png) left 50% no-repeat,
                url(bg.png) right 100% no-repeat red;
```

### 组合设置

可以使用一条指令设置背景

```text
background: red url(xj-small.png) no-repeat right 50% fixed;
```

## 盒子阴影

可以使用 `box-shadow` 对盒子元素设置阴影，参数为 `水平偏移,垂直偏移,模糊度,颜色` 构成。

![image-20190818221126973](data:image/png;base64,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)

```text
box-shadow: 10px 10px 5px rgba(100, 100, 100, .5);
```

## 颜色渐变

### 线性渐变

激变一般用在背景颜色中使用

```text
background: linear-gradient(red, green);
```

渐变角度

```text
background: linear-gradient(30deg, red, green);
```

向右渐变

```text
background: linear-gradient(to right, red, green)
```

向左渐变

```text
background: linear-gradient(to left, red, green);
```

左上渐变

```text
background: linear-gradient(to top left, red, green);
```

右下渐变

```text
background: linear-gradient(to right bottom, red, green);
```

设置多个颜色

```text
background: linear-gradient(red, rgb(0, 0, 200), green, rgba(122, 211, 100, 0));
```

### 径向渐变

设置渐变

```text
background: radial-gradient(red, blue, green);
```

设置渐变宽度与高度

```text
background: radial-gradient(100px 200px, red, blue, green);
```

左下渐变

```text
background: radial-gradient(at bottom left, red, blue);
```

右下渐变

```text
background: radial-gradient(at bottom right, red, blue);
```

左侧向中心渐变

```text
background: radial-gradient(at center left, red, blue);
```

底部向中心渐变

```text
background: radial-gradient(at 50% 100%, red, blue);
```

### 标识位

颜色未指定标识时，颜色会平均分布。

红色与蓝色在50%gc 60%间发生激变.

![image-20190818201418874](http://houdunren.gitee.io/note/assets/img/image-20190818201418874.876f48d4.png)

```text
background: linear-gradient(45deg, red 50%, blue 0%);
```

标识位相同时将没有过渡效果

![image-20190818203701681](http://houdunren.gitee.io/note/assets/img/image-20190818203701681.104054ec.png)

```text
background: linear-gradient(45deg, red 0,red 50%, blue 50%);
```

径向标识位绘制小太阳

![image-20190818235947336](http://houdunren.gitee.io/note/assets/img/image-20190818235947336.94846de5.png)

```text
width: 150px;
height: 150px;
background: radial-gradient(red 0, yellow 30%, black 60%, black 100%);
```

通过在两个颜色间中间点定义过渡位置

```text
background: linear-gradient(45deg, red, 50%, blue);
```

### 渐变重复

下例定义从0到25为蓝色,25px到50px的红色，并进行重复后产生渐变的进度条。

![image-20190818203349935](http://houdunren.gitee.io/note/assets/img/image-20190818203349935.08146f12.png)

```text
background: repeating-linear-gradient(90deg, blue, 25px, yellow 25px, 25px, red 50px);
```

### 径向重复

![image-20190818235802316](http://houdunren.gitee.io/note/assets/img/image-20190818235802316.e6ae0312.png)

```text
width: 200px;
height: 200px;
background: repeating-radial-gradient(100px 100px, red 0%, yellow 40%, black 60%, black 200%);
```
