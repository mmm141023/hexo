---
title: HTML之表格与多媒体
date: 2020-05-16 21:55:00
tags: 
    - HTML
categories: 
    - 前端
    - 后盾人
---
## 表格

> [houdunren.com](https://www.houdunren.com/) @ 向军大叔

表格在网页开发中使用频率非常高，尤其是数据展示时。

### 基本使用

| 属性    | 说明         |
| ------- | ------------ |
| caption | 表格标题     |
| thead   | 表头部分     |
| tbody   | 表格主体部分 |
| tfoot   | 表格尾部     |

```text
<table border="1">
        <caption>后盾人表格标题</caption>
        <thead>
            <tr>
                <th>标题</th>
                <th>时间</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>后盾人</td>
                <td>2020-2-22</td>
            </tr>
        </tbody>
</table>
```

### 单元格合并

下面是水平单元格合并

![image-20190806225621113](http://houdunren.gitee.io/note/html/assets/image-20190806225621113.png)

```text
<table border="1">
        <thead>
            <tr>
                <th>标题</th>
                <th>时间</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td colspan="2">后盾人 2020-2-22</td>
            </tr>
        </tbody>
    </table>
```

下面是垂直单元格合并

![image-20190806225731776](http://houdunren.gitee.io/note/html/assets/image-20190806225731776.png)

```text
<table border="1">
        <thead>
            <tr>
                <th>标题</th>
                <th>时间</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td rowspan="2">后盾人</td>
                <td>2030-03-19</td>
            </tr>
            <tr>
                <td>2035-11-08</td>
            </tr>
        </tbody>
</table>
```

## 视频

Adobe与苹果公司对 FLASH都不支持或消极状态，这时HTML提供对视频格式的支持，除了使用html提供的标签来播放视频外，也有很多免费或付费的插件，如[video.js](https://videojs.com/) 、[阿里云播放器](https://help.aliyun.com/document_detail/57314.html) 等等。

**属性说明**

| 属性     | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| autoplay | 如果出现该属性，则视频在就绪后马上播放（需要指定类型如 `type="video/mp4"`)。 |
| preload  | 如果出现该属性，则视频在页面加载时进行加载，并预备播放。如果使用 "autoplay"，则忽略该属性。 如果视频观看度低可以设置为 `preload="none"` 不加载视频数据减少带宽。 如果设置为 `preload=metadata`值将加载视频尺寸或关键针数据，目的也是减少带宽占用。 设置为`preload="auto"` 时表示将自动加载视频数据 |
| controls | 如果出现该属性，则向用户显示控件，比如播放按钮。             |
| height   | 设置视频播放器的高度。                                       |
| width    | 设置视频播放器的宽度。                                       |
| loop     | 如果出现该属性，则当媒介文件完成播放后再次开始播放。         |
| muted    | 规定视频的音频输出应该被静音。                               |
| poster   | 规定视频下载时显示的图像，或者在用户点击播放按钮前显示的图像。 |
| src      | 要播放的视频的 URL。                                         |

![image-20190805223010377](http://houdunren.gitee.io/note/assets/img/image-20190805223010377.ea46ad2d.png)

```text
<video src="houdunren.mp4" autoplay="autoplay" 
	loop muted controls width="800" height="200">
	
	<source src="houdunren.mp4" type="video/mp4">
  <source src="houdunren.webm" type="video/webm">
  
</video>
```

## 声音

HTML对声音格式文件也提供了很好的支持。

**属性说明**

| 属性     | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| autoplay | 如果出现该属性，则视频在就绪后马上播放。                     |
| preload  | 如果出现该属性，则视频在页面加载时进行加载，并预备播放。如果使用 "autoplay"，则忽略该属性。 如果视频观看度低可以设置为 `preload="none"` 不加载视频数据减少带宽。 如果设置为 `preload=metadata`值将加载视频尺寸或关键针数据，目的也是减少带宽占用。 设置为`preload="auto"` 时表示将自动加载视频数据 |
| controls | 如果出现该属性，则向用户显示控件，比如播放按钮。             |
| loop     | 如果出现该属性，则当媒介文件完成播放后再次开始播放。         |
| muted    | 规定视频的音频输出应该被静音。                               |
| src      | 要播放的视频的 URL。                                         |

![image-20190806224227295](http://houdunren.gitee.io/note/html/assets/image-20190806224227295.png)

```text
<audio controls autoplay loop preload="auto">
	<source src="houdunren.ogg" type="audio/ogg">
	<source src="houdunren.mp3" type="audio/mp3">
</audio>
```
