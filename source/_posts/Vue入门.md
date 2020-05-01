---
title: Vue入门
date: 2020-05-01 20:36:47
tags: 
    - Vue
categories: Vue
---

#### 第一部分：了解什么是Vuejs及入门

##### 01、Vuejs是什么？(了解)

##### 02、什么是MVVM模式(了解)

##### 03、Vuejs快速入门(重点)

#### 第二部分：掌握和学习Vuejs的内置指令及生命周期（重点）

##### 01、Vuejs中常用的内置指令(重点)

##### 02、Vuejs操作样式和class

##### 03、Vuejs的生命周期(了解)

#### 第三部分：掌握和学习Vuejs实战开发以及应用场景（重点）

##### 01、掌握Vuejs中通过Axios完成异步请求(重点)

##### 02、Vuejs实战应用开发 (重点)







## 第一部分：了解什么是Vuejs及入门

### 01 - Vuejs介绍和下载【理解】



官网：https://cn.vuejs.org/

入门文档：<https://cn.vuejs.org/v2/guide/>

##### 目标

什么是vuejs以及如何下载和安装Vuejs。

##### 官网概述

Vue (读音 /vjuː/，类似于 **view**) 是一套用于构建用户界面的**渐进式框架**。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。==Vue 的核心库只关注视图层==，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与[现代化的工具链](https://cn.vuejs.org/v2/guide/single-file-components.html)以及各种[支持类库](https://github.com/vuejs/awesome-vue#libraries--plugins)结合使用时，Vue 也完全能够为复杂的单页应用提供驱动。

##### 小结

>vuejs就是js框架。一个基于==mvvm框架==。易于开发易于集成。我不需要把视图层的代码和js混合，我要想办法分开。类似于java的mvc 和ssm。
>
>下载：
>
>```js
><script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
>```
>
>然后在浏览器访问·`https://cdn.jsdelivr.net/npm/vue/dist/vue.js` 另存为vue.js即可。









### 02 - 基于传统的DOM操作-基于JQuery操作数据渲染方式【理解】

##### 目标

>  理解和掌握传统JQuery的操作dom如何将数据渲染到html中。

![1552546115308](assets/1552546115308.png)



比如在开发一个业务数据用户渲染的时候：

>  jquery历史版本下载：http://code.jquery.com/jquery/	

##### 步骤

>1：新建`02-基于传统jquery操作数据渲染方式.html页面`
>
>2：引入jquery.min.js文件
>
>3：定义<div id="app"></div>

##### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

    <!--第二步：定义dom-->
    <div id="app"></div>
    <!--第一步，引入jquery.js文件-->
    <script src="js/jquery-1.12.4.min.js"></script>

    <script>


        $(function(){
            // 第三步：准备数据
            //初始化在这里
            var userData = [{
                id: 1,
                username: "徐柯老师",
                age: 33,
                male: 1,
                address: "广州广东",
                tel: "15074816437"
            },{
                id: 2,
                username: "张三老师",
                age: 28,
                male: 1,
                address: "广州广东",
                tel: "18923442345"
            },{
                id: 2,
                username: "女神老师",
                age: 12,
                male: 0,
                address: "广州广东",
                tel: "17074816437"
            }];

            // 第四步：利用jquery完成数据的渲染
            var html = "";
            for(var i=0;i<userData.length;i++){
                html+="<ul>"
                var user = userData[i];
                for(var key in user){
                    html+="<li>"+key+":"+user[key]+"</li>";
                }
                html+="</ul>";
            }

            $("#app").html(html);
        });


    </script>


</body>
</html>
```

##### 小结

>1：繁复的拼接，不便于维护。
>
>2：性能也比较低下。





### 03 - 基于MVVM模式-VueJs如何将数据渲染方式【理解】

##### 目标

>  完成基于MVVM模式-VueJs如何将数据渲染方式

##### 步骤

```
 1: 先引入 vuejs
 2: 然后定义渲染的dom
 3：初始化vuejs的实例对象
 4: 准备数据 model
 5：利用vuejs把数据通过指令和插值表达式完成数据的渲染
```

##### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>03 - 基于MVVM模式-VueJs如何将数据渲染方式【理解】</title>
</head>
<body>

    <!--2:然后定义渲染的dom view-->
    <div id="app">
        <!--// 5: 利用vuejs把数据通过指令和插值表达式完成数据的渲染--->
        <ul v-for="(user,index) in users">
            <li v-for="(key,value) in user">
                {{key}}:{{value}}
            </li>
        </ul>
    </div>

    <!--1: 先引入 vuejs-->
    <script src="js/vue.js"></script>
    <script>
        // 1: 先引入 vuejs
        // 2: 然后定义渲染的dom
        // 3：初始化vuejs的实例对象
        //初始化在这里
        // 4: 准备数据 model
        var userData = [{
            id: 1,
            username: "徐柯老师",
            age: 33,
            male: 1,
            address: "广州广东",
            tel: "15074816437"
        },{
            id: 2,
            username: "张三老师",
            age: 28,
            male: 1,
            address: "广州广东",
            tel: "18923442345"
        },{
            id: 2,
            username: "女神老师",
            age: 12,
            male: 0,
            address: "广州广东",
            tel: "17074816437"
        }];

        
        // vm---model-view进行数据渲染。
        var app = new Vue({
            el:"#app",
            data:{users:userData}
        });

        
    </script>

</body>
</html>
```

##### 小结

>这也是MVVM的核心思想：关注Model的变化，让MVVM框架利用自己的机制去自动更新DOM，从而把开发者从操作DOM的繁琐中解脱出来！也就是所谓的 数据 - 视图分离，数据驱动视图， 视图不影响数据，再也不用管繁琐的DOM结构操作了，世界顿时清净，完美！

##### 问题

>1：什么是指令
>
>2：定义规则是什么
>
>3：什么插值表达式
>
>4：如何绑定事件如何添加样式？









### 04 - Vuejs实操系列 - 快速入门【应用】

##### 目标

快速理解 vuejs的定义和注意事项

##### 步骤

1、引入vue.js文件

2、定义Vuejs对象和数据

3、定义dom

4、定义视图渲染数据

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title> 04 - Vuejs实操系列 - 快速入门【应用】</title>
</head>
<body>

    <!--3:定义dom-->

    <div id="app">
        <!--4：利用插值表达式或者指令完成数据的渲染-->
        {{title}}
        <span v-text="title"></span>
    </div>

    <!--1:引入vuejs-->
    <script src="js/vue.js"></script>
    <script>
        // 2: 定义vuejs对象，
        // 参数属性说明：
        // 1: el：代表vuejs从哪个dom开始进行管辖，一旦被el定义，那么会把当前dom中的视图（dom）中存在的指令或者插值表达式
        // 通通进行数据的渲染。
        //2: 而数据的来源必须一定要在data中进行定义，也就是告诉只要在el管辖的范围内需要的数据必须要data中定义，否则无效。

        // 注意事项：
        // 1：注意点：el :#app 必须用id，可以用class吗。不推荐
        // 2:注意点：Vue首字母必须是大写。
        var app = new Vue({
            el:"#app",
            data:{title:"传智播客，专业的Java学习平台！！"}
        })

    </script>
</body>
</html>
```



##### 小结

```properties
1: el：代表vuejs从哪个dom开始进行管辖，一旦被el定义，那么会把当前dom中的视图（dom）中存在的指令或者插值表达式
通通进行数据的渲染。
2: 而数据的来源必须一定要在data中进行定义，也就是告诉只要在el管辖的范围内需要的数据必须要data中定义，否则无效。

注意事项：
1：注意点：el :#app 必须用id，可以用class吗。不推荐
2:注意点：Vue首字母必须是大写。
```









### 05 - Vuejs实操系列 - 插值表达式【应用】

##### 语法

>  数据绑定最常见的形式就是使用“Mustache”语法 (双大括号) 的文本插值，Mustache 标签将会被替代为对应数据对象上属性的值。无论何时，绑定的数据对象上属性发生了改变，插值处的内容都会更新。
>
>  Vue.js 都提供了完全的 JavaScript 表达式支持。
>
>  1：支持+，-，*，/，%，等相关算数运算符
>
>  2：
>
>  {{ number + 1 }} 
>
>  {{ ok ? 'YES' : 'NO' }}
>
>  
>
>  这些表达式会在所属 Vue 实例的数据作用域下作为 JavaScript 被解析。有个限制就是，每个绑定都只能包含**单个表达式**，所以下面的例子都**不会**生效。
>
>  <!-- 这是语句，不是表达式 -->
>
>  {{ var a = 1 }}
>
>  <!-- 流控制也不会生效，请使用三元表达式 -->
>
>  {{ if (ok) { return message } }}

##### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>05 - Vuejs实操系列 - 插值表达式【应用】</title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">
        <p>{{title}}</p>
        <p>{{price + num}}</p>
        <p>{{price * num}}</p>
        <p>{{price / num}}</p>
        <p>{{price - num}}</p>
        <p>{{price % num}}</p>
        <p>{{flag?"男":"女"}}</p>
    </div>

    <!-- 第二步：导入vue.js文件 -->
    <script src="js/vuejs-2.5.16.js"></script>
    <script>
        
         //  插值表达式：语法：{{}} 组成的一种结构。
          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          var app = new Vue({
              el:"#app",
              data:{
                  title:"Hello world!",
                  price:10.67,
                  num:23,
                  flag:false
              }
          }) ;

    </script>
</body>
</html>
```

##### 小结

>```
>//  插值表达式：语法：{{}} 组成的一种结构。
>```









## 第二部分：掌握和学习Vuejs的内置指令及生命周期（重点）



### 06 - Vuejs中常用的内置指令掌握和学习【应用】

##### 目标

掌握和学习vuejs提供的内置指令。

##### 指令对照表

<https://cn.vuejs.org/v2/api/>

| 指令名称           | 描述           | 用法                                                         |
| ------------------ | :------------- | :----------------------------------------------------------- |
| v-on               | 事件绑定       | v-on:事件 = “事件名”<br/><font color="red">缩写：@事件 = “事件名”</font><br/>点击事件：click,dblclick,change,blur<br/>键盘事件：keydown/keyupkeypress<br/>鼠标事件：mousedown,mouseover,mousemove,mouseout |
| v-text/v-html      | 文本取值       | &lt;span v-text="title"&gt; 或者 &lt;span v-html="title"&gt;<br>两者的区别是：v-text不支持标签解析，v-html支持标签解析。 |
| v-bind             | 属性取值       | v-bind:属性 = “属性值”<br/>缩写：:属性 = “属性值”<br/>解决在标签的属性上如何获取动态的数据值的问题。 <br/>比如：&lt;span v-bind:title="title"&gt; 或者&lt;span :title="title"&gt; |
| v-model            | 获取form控件值 | 用于form表单控制元素值的相关获取和同步。                     |
| v-for              | 循环迭代       | 一般用于循环数组，对象和对象数组。                           |
| v-show/v-if/v-else | 隐藏/显示      | v-show：是控制元素display:none/block的切换。v-if：是逻辑判断，控制元素的存在与不存在。 |
| v-pre              | 原样输出不解析 | 如果你不想解析插值表达式，原样输入可以使用v-pre              |
| v-once             | 渲染一次       | 如果你想渲染一次，后面改变数据不会影响视图的变化，可以使用v-once。 |
| v-cloak            | 解决网络延迟   | 往往在真实的场景中，插值表达式渲染会很慢，<br/>而造成插件表达式的外漏，可以借助v-cloak和[v-cloak]{display:none;}来解决这个问题 |









### 07 - Vue内置指令-事件指令-v-on指令-点击事件【应用】

##### 目标

掌握事件指令v-on的语法定义。

##### 语法

>  <strong>事件操作是开发中用的最频繁的操作：vuejs中采用v-on指令+methods的方式来完成事件的定义和绑定。</strong>
>
>  语法如下：v-on:事件类型="事件名称" 比如：v-on:click="fun1"
>
>  <strong style="color:red">简写：@事件类型="事件名称"。比如：@click="fun1"</strong>	



###### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title> 07 - Vue内置指令-事件指令-v-on指令-点击事件</title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">
        <button v-on:click="login">点击</button>
    </div>

    <!-- 第二步：导入vue.js文件 -->
    <script src="js/vuejs-2.5.16.js"></script>    
    <script>

          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          var app = new Vue({
              el:"#app",
              data:{title:"Hello world!"},
              methods:{
                  // 事件定义在此处
                  login:function(){
                      console.log("你触发的是点击事件!!!!");
                  }
              }
          }) ;

    </script>
</body>
</html>
```









### 08 - Vue内置指令-事件指令-v-on指令-键盘事件【应用】

##### 目标

熟练掌握事件内置指令键盘事件。

##### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title> 08 - Vue内置指令-事件指令-v-on指令-键盘事件【应用】</title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">
        <input type="text" v-on:keydown="fun1">
        <input type="text" v-on:keydown="fun2('good')">
        <input type="text" v-model="dvalue" v-on:keydown="fun3('good',$event)">

        <p>你当前输入的建码是：{{keyCode}}</p>
    </div>

    <!-- 第二步：导入vue.js文件 -->
    <script src="js/vuejs-2.5.16.js"></script>    
    <script>

          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          // 键盘事件：keydown keyup keypress --- 大家肯定会在txtarea会做一个字数限制的案例，就会需要键盘事件
          // 或者需要通过建码组合的时候就用户此事件类型。
          var app = new Vue({
              el:"#app",
              data:{keyCode:0,dvalue:""},
              methods:{
                  fun1:function(){
                    console.log("你触发的是键盘事件.....")
                  },

                  fun2:function(value){
                      console.log(value)
                  },

                  fun3:function(value,event){
                      // 用户输入enter键的时候就提交
                      if(event.keyCode==13){
                          this.login();
                      }

                      // 代表用户输入的esc键，清空
                      if(event.keyCode==27){
                          this.$data.dvalue = "";
                      }


                      this.$data.keyCode = event.keyCode;
                  },
                  login:function(){
                      alert("你提交把!!" + this.$data.dvalue);
                  }
              }
          }) ;

    </script>
</body>
</html>
```





### 09 - Vue内置指令-事件指令-v-on指令-按键修饰符【应用】

##### 目标

Vue.js通过由点(.)表示的指令后缀来调用修饰符。

##### 语法

```html
Vue 允许为 v-on 在监听键盘事件时添加按键修饰符

全部的按键别名：
	
	.enter(enter键)
	.tab (Tab键)
	.delete (捕获 "删除" 和 "退格" 键)
	.esc （退出键）
	.space（空格键）
	.up (向上)
	.down(向下)
	.left(向左)
	.right(向右)
	

	.ctrl
	.alt
	.shift
	.meta

注意：在 Mac 系统键盘上，meta 对应 command 键 (⌘)。在 Windows 系统键盘 meta 对应 Windows 徽标键 (⊞)。在 Sun 操作系统键盘上，meta 对应实心宝石键 (◆)。在其他特定键盘上，尤其在 MIT 和 Lisp 机器的键盘、以及其后继产品，比如 Knight 键盘、space-cadet 键盘，meta 被标记为“META”。在 Symbolics 键盘上，meta 被标记为“META”或者“Meta”。
```

##### 代码

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title> 09 - Vue内置指令-事件指令-v-on指令-事件修饰符</title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">
        <input placeholder="输入enter键"  type="text" @keydown="fun1($event)">
        <input placeholder="输入enter键"  type="text" @keydown.enter="fun2()">
        <input placeholder="输esc键"  type="text" @keydown.esc="fun2()">

        <input placeholder="输入enter键" type="text" @keydown.13="fun2()">
        <input placeholder="ctrl+enter组合触发我" type="text" @keydown.ctrl.13="fun2()">
        <input placeholder="ctrl+enter组合触发我" type="text" @keydown.ctrl.enter="fun2()">
    </div>

    <!-- 第二步：导入vue.js文件 -->
    <script src="js/vuejs-2.5.16.js"></script>    
    <script>

          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          // 需求：用户按 `enter` 键触发事件
          var app = new Vue({
              el:"#app",
              data:{title:"Hello world!"},
              methods:{
                  fun1:function(event){
                      if(event.keyCode==13) {
                          alert("触发我!!!")
                      }
                  },

                  fun2:function(){
                      alert("触发我!!!func2")
                  }
              }
          }) ;

    </script>
</body>
</html>
```







### 10 - Vue内置指令-事件指令-v-on指令-事件修饰符【应用】

##### 目标

掌握事件指令v-on事件操作符应用场景

##### 语法

```html
.stop 组织子元素冒泡到父元素上
.prevent 去掉浏览器默认行为
.once 事件只绑定一次。
=====stop==============================================================
<!-- 阻止单击事件继续传播 -->
<a v-on:click.stop="doThis"></a>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title> 10 - Vue内置指令-事件指令-v-on指令-事件修饰符【应用】</title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">
        <div class="parent" v-on:click="divclick">
            <button @click.stop="btnclick">点我</button>
        </div>
    </div>

    <!-- 第二步：导入vue.js文件 -->
    <script src="js/vuejs-2.5.16.js"></script>    
    <script>

          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          var app = new Vue({
              el:"#app",
              data:{title:"Hello world!"},
              methods:{
                  divclick : function(){
                      console.log("1-------------div parent");
                  },

                  btnclick : function(){
                      console.log("2-------------btn click children");
                  }

              }
          }) ;

    </script>
</body>
</html>

=======prevent======================================================================

<!-- 提交事件不再重载页面 -->
<form v-on:submit.prevent="onSubmit"></form>
<!-- 修饰符可以串联 -->
<a v-on:click.stop.prevent="doThat"></a>
<!-- 只有修饰符 -->
<form v-on:submit.prevent></form>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title> 10 - Vue内置指令-事件指令-v-on指令-事件修饰符【应用】</title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">
        <a href="http://www.baidu.com" @click.prevent="clickme">去百度</a>
        <form action="xxxx.action" v-on:submit.prevent="saveuser">
            <input type="submit" value="提交">
        </form>
    </div>

    <!-- 第二步：导入vue.js文件
        a:他是一个连接，默认行为：跳转锚点。href对应的地址
    -->
    <script src="js/vuejs-2.5.16.js"></script>    
    <script>

          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          var app = new Vue({
              el:"#app",
              data:{title:"Hello world!"},
              methods:{
                  clickme : function(){
                      console.log("1-------------去百度");
                  },

                  saveuser:function(){
                      console.log(" save user");
                      return false;
                  }
              }
          }) ;

    </script>
</body>
</html>


======once==========================================================================
  <a href="http://www.baidu.com" @click.prevent.once="clickme">抽奖</a>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title> 10 - Vue内置指令-事件指令-v-on指令-事件修饰符【应用】</title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">
        <a href="http://www.baidu.com" @click.prevent.once="clickme">抽奖</a>
    </div>

    <!-- 第二步：导入vue.js文件
        a:他是一个连接，默认行为：跳转锚点。href对应的地址
    -->
    <script src="js/vuejs-2.5.16.js"></script>    
    <script>

          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          var app = new Vue({
              el:"#app",
              data:{title:"Hello world!"},
              methods:{
                  clickme : function(){
                      console.log("1-------------去百度");
                  }
              }
          }) ;

    </script>
</body>
</html>
```

##### 















### 11 - Vue内置指令-文本指令-v-text v-html指令【应用】

##### 目标

了解和掌握文本指令的用法，以及v-text和v-html的区别

##### 小结

>  v-text和v-html 都是属于文本的值管理范畴，唯独的差别就是：
>
>  <strong style="color:red">提示：v-text不支持标签解析，v-html支持标签解析</strong>

##### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>11 - Vue内置指令-文本指令-v-text v-html指令【应用】</title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">
        {{title}}
        {{content}}
        <div>
            <span v-text="title"></span>
            <span v-text="content"></span>
        </div>
        <div>
            <span v-html="title"></span>
            <span v-html="content"></span>
        </div>
    </div>

    <!-- 第二步：导入vue.js文件 -->
    <script src="js/vuejs-2.5.16.js"></script>    
    <script>

          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          var app = new Vue({
              el:"#app",
              data:{
                  title:"Hello world!",
                  content:"<strong>Hello world</strong>"
              }
          }) ;

    </script>
</body>
</html>
```









###  12 - Vue内置指令 - 属性绑定指令 - v-bind-指令【应用】

##### 目标

了解和掌握属性动态绑定的v-bind的指令使用规则。

##### 小结

>  <strong>插值语法：{{}}   是不能直接使用在属性上，需要借助v-bind指令来解决此问题！</strong>
>
>  语法：v-bind:属性=''data数据key"
>
>  <strong style="color:red">简写：:属性="data数据的key",比如：:src="imgsrc"</strong>
>
>  ![1557907358338](assets/1557907358338.png)

##### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>12 - Vue内置指令 - 属性绑定指令 - v-bind-指令【应用】</title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">
        <img v-bind:src="imgsrc" alt="">
        <img :src="imgsrc" alt="">
    </div>

    <!-- 第二步：导入vue.js文件 -->
    <script src="js/vuejs-2.5.16.js"></script>    
    <script>

          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          var app = new Vue({
              el:"#app",
              data:{
                  imgsrc:"https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1557917216914&di=4a08e3a2bbea6f1b3ffc808571685807&imgtype=0&src=http%3A%2F%2Fmedia-cdn.tripadvisor.com%2Fmedia%2Fphoto-s%2F01%2F48%2Fa9%2Ff6%2Ftup-island.jpg"
              }
          }) ;

    </script>
</body>
</html>
```

##### 小结

```
如果想把data中的数据，放入到元素的属性上，那么久必须使用v-bind指令来完成。
```







### 13 - 基于传统JQuery获取form控件值的方式【应用】

##### 目标

如何利用jquery获取form控件元素的值操作！

##### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title></title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">

        <form>
            <p>用名：<input type="text" id="username"></p>
            <p>密码：<input type="text" id="password"></p>
            <p>性别：
                <label><input type="radio" name="male" checked value="1">男</label>
                <label><input type="radio" name="male" value="0">女</label>
            </p>
            <p>兴趣：
                <label><input type="checkbox" name="hobbys"  checked value="看书">看书</label>
                <label><input type="checkbox" name="hobbys"  checked value="旅游">旅游</label>
                <label><input type="checkbox" name="hobbys" value="逛街">逛街</label>
                <label><input type="checkbox" name="hobbys" value="写代码">写代码</label>
            </p>
            <p>介绍：<textarea id="intro" cols="30" rows="10"></textarea></p>
            <p>地址：
                <select id="address">
                    <option value="">--请选择--</option>
                    <option selected value="s1001">长沙</option>
                    <option value="s1002">广州</option>
                    <option value="s1003">深圳</option>
                </select>
            </p>
            <input type="submit" id="save" value="保存">
        </form>
    </div>

    <!-- 第二步：导入vue.js文件 -->
    <script src="js/jquery-1.12.4.min.js"></script>
    <script>

        $(function(){
            $("#save").on("click",function(e){

                var username = $("#username").val();
                var password = $("#password").val();
                var male = $("input[type='radio'][name='male']:checked").val();
                var hobbys = [];
                $("input[type='checkbox'][name='hobbys']:checked").each(function(index,item){
                   hobbys.push(item.value);
                });
                var intro = $("#intro").val();
                var address = $("#address").val();
                var addressValue = $("#address").find("option:selected").val();
                var addressText = $("#address").find("option:selected").text();
                console.log(username,password,male,hobbys,intro,address,addressValue,addressText);
                e.preventDefault();
            });
        })

    </script>
</body>
</html>
```









### 14 - Vue内置指令-v-model指令获取form控件值的方式【应用】

##### 目标

如何获取form控件元素值。

##### 小结

>  <strong style="color:red">Form元素是开发中使用最多的控件，如何获取空间元素的值。就必须借助于：v-model指令</strong>	

##### 代码

```html
	<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title></title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">

        <form action="" v-on:submit.prevent="save">
            <p>用名：<input type="text" v-model="user.username"></p>
            <p>密码：<input type="text" v-model="user.password"></p>
            <p>性别：
                <label><input type="radio" name="male" v-model="user.male" value="1">男</label>
                <label><input type="radio" name="male" v-model="user.male" value="0">女</label>
            </p>
            <p>兴趣：
                <label><input type="checkbox" name="hobbys" v-model="user.hobbys" value="看书">看书</label>
                <label><input type="checkbox" name="hobbys" v-model="user.hobbys" value="旅游">旅游</label>
                <label><input type="checkbox" name="hobbys" v-model="user.hobbys" value="逛街">逛街</label>
                <label><input type="checkbox" name="hobbys" v-model="user.hobbys" value="写代码">写代码</label>
            </p>
            <p>介绍：<textarea v-model="user.intro" cols="30" rows="10"></textarea></p>
            <p>地址：
                <select v-model="user.address">
                    <option value="">--请选择--</option>
                    <option v-for="(test,index) in tests" :value="test">{{test.text}}</option>
                </select>

                <select v-model="user.address2">
                    <option value="">--请选择--</option>
                    <option v-for="(test,index) in tests" :value="test.value">{{test.text}}</option>
                </select>

                <select v-model="user.addresses" multiple>
                    <option value="">--请选择--</option>
                    <option v-for="test in tests" :value="test">{{test.text}}</option>
                </select>
            </p>
            <input type="submit" value="保存">
        </form>

        {{user}}

    </div>

    <!-- 第二步：导入vue.js文件 -->
    <script src="js/vuejs-2.5.16.js"></script>
    <script>

          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          var app = new Vue({
              el:"#app",
              data:{title:"Hello world!",  tests: [
                      { value: "s1001", text: '长沙' },
                      { value: "s1002", text: '广州' },
                      { value: "s1003", text: '深圳' },
                      { value: "s1004", text: '上海' },
                  ],user:{
                username:"",
                password:"",
                male:0,
                hobbys:[],
                intro:"",
                address:{},
                address2:"",
                addresses:[]
              }},

              // 定义事件
              methods:{
                save:function(){
                    var username = this.$data.user.username;
                    var password = this.$data.user.password;
                    var male = this.$data.user.male;
                    var maletext = male==1?"男":"女";
                    var hobbys = this.$data.user.hobbys;
                    var intro = this.$data.user.intro;
                    // 获取 select的text/value的第一种方式
                    var address = this.$data.user.address.value;
                    var addresstext = this.$data.user.address.text;
                    //获取select的text/value的第二种方式：
                    var address2 = this.$data.user.address2;
                    var address2text = this.tests.find(function(item){
                        return item.value == address2})['text']
                    var addresses = this.$data.user.addresses;
                    console.log(username);
                    console.log(password);
                    console.log(male);
                    console.log(hobbys);
                    console.log(intro);
                    console.log(address);
                    console.log(addresstext);
                    console.log(addresses);
                    console.log(address2);
                    console.log(address2text);
                    console.log("==================")
                }
              },
              // dom加载完毕执行的回调函数
              mounted:function(){
              }
          }) ;

    </script>
</body>
</html>		
```









### 15 - Vue内置指令 - 循环指令 - v-for指令【应用】

##### 目标

>  数据往往存在多种形态：对象，数组，对象数组。如果将对象的key和value分别取出来，如何取出数组中的每个元素，是开发中非常常见的操作。vue提供了：v-for指令，可以轻松完成这个事情。

###### 操作数组

```properties
html部分
<div>
    <p v-for="(value,index) in names">{{index}}:{{value}}</p>
</div>

js部分
var app = new Vue({
    el:"#app",
    data:{
        title:"Hello world!",
        names:["zhangsan","lisi","wangwu"]
    }
}) ;

```

###### 操作对象



![1557910291171](assets/1557910291171.png)

```properties
# html 部分
<div>
    <p v-for="(value,key) in user">{{key}}:{{value}}</p>
</div>

js部分
// 第三步：定义vuejs对象，开始进行视图和数据的渲染
var app = new Vue({
    el:"#app",
    data:{
        title:"Hello world!",
        user:{id:1,username:"徐承飞老师",age:32}
     }
}) ;

```

###### 操作对象数组

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title> 15 - Vue内置指令 - 循环指令 - v-for指令【应用】</title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">
        {{title}}
        <span v-html="title"></span>
        <div>
            <span>{{user.id}}</span>
            <span>{{user.username}}</span>
            <span v-html="user.age"></span>
        </div>
        <hr>
        <div>
            <p v-for="(value,key) in user">{{key}}:{{value}}</p>
        </div>
        <hr>
        <div>
            <p v-for="(value,index) in names">{{index}}:{{value}}</p>
        </div>
        <hr>
       <div>
           <p v-for="(user,index) in users">
               {{index}}:
               {{user.id}}
               {{user.username}}
               {{user.age}}
               {{user.address}}
               {{user.tel}}
               {{user.male}}
           </p>
       </div>


    </div>

    <!-- 第二步：导入vue.js文件 -->
    <script src="js/vuejs-2.5.16.js"></script>    
    <script>

          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          var app = new Vue({
              el:"#app",
              data:{
                  title:"Hello world!",
                  user:{id:1,username:"徐承飞老师",age:32},
                  names:["zhangsan","lisi","wangwu"],
                  users:[{
                      id: 1,
                      username: "徐柯老师",
                      age: 33,
                      male: 1,
                      address: "广州广东",
                      tel: "15074816437"
                  },{
                      id: 2,
                      username: "张三老师",
                      age: 28,
                      male: 1,
                      address: "广州广东",
                      tel: "18923442345"
                  },{
                      id: 3,
                      username: "女神老师",
                      age: 12,
                      male: 0,
                      address: "广州广东",
                      tel: "17074816437"
                  }]
              }
          }) ;

    </script>
</body>
</html>
```

##### 小结

```
索引的获取是定义 v-for=(user,index) in 对象、数组、数组对象都可以.
```









### 16 - Vue内置指令 - 条件指令 - v-if/v-else-if/v-else 指令【应用】

##### 目标

掌握v-if/v-else和v-if/v-else-if/v-else标签的使用

##### 需求

用户输入步同年龄阶段，显示这个阶段对应的时期。

##### 代码

###### v-if/v-else 例子

```html

```

###### v-if/v-else-if/v-else例子

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title> 16 - Vue内置指令 - 条件指令 - v-if v-else-if v-else 指令【应用】</title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">
       请输入年龄：<input type="text" v-model="age">
        <p>
            <span v-if="age>=0 && age<=10">儿童0-10</span>
            <span v-else-if="age>=11 && age<=18">少年11-18</span>
            <span v-else-if="age>=19 && age<=35">青年19-35</span>
            <span v-else-if="age>=36 && age<=55">中年36-55</span>
            <span v-else>老年</span>
        </p>
    </div>

    <!-- 第二步：导入vue.js文件 -->
    <script src="js/vue.js"></script>
    <script>
          //需求：用户输入步同年龄阶段，显示这个阶段对应的时期。
          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          var app = new Vue({
              el:"#app",
              data:{
                  age:0
              }
          }) ;

    </script>
</body>
</html>
```

##### 小结

```
注意点，指令和指令之间不能断层，否则无效。
```









### 17 - Vue内置指令 - 显示指令 -v-show 指令【应用】

##### 目标

掌握和学习v-show的使用方式，以及v-show和v-if的区别

##### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title> 17 - Vue内置指令 - 显示指令 -v-show 指令【应用】</title>
</head>
<body>

    <!--第一步：定义vuejs管理渲染的范围-->
    <div id="app">
        <span v-show="flag"> {{title}}---show</span>
        <span v-show="!flag"> {{title}}---hidden</span>

        <span v-if="flag"> {{title}}---if</span>
    </div>

    <!-- 第二步：导入vue.js文件 -->
    <script src="js/vuejs-2.5.16.js"></script>    
    <script>

          // 第三步：定义vuejs对象，开始进行视图和数据的渲染
          var app = new Vue({
              el:"#app",
              data:{title:"Hello world!",flag:true}
          }) ;

    </script>
</body>
</html>
```

##### 小结

==v-if是根据表达式的值来决定是否渲染元素==

==v-show是根据表达式的值来切换元素的display css属性==









### 18-Vuejs生命周期 - Vuejs的生命周期(了解)

##### 目标

>掌握vuejs的声明周期和数据渲染流程？

##### 图例

![Vue å®ä¾çå½å¨æ](assets/lifecycle.png)

##### 代码

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>生命周期</title>
</head>
<body>


<div id="app">{{message}}</div>

<script src="js/vue.js"></script>

<script>

    //vm
    var vm = new Vue({
        el : "#app",
        data : {
            message : 'hello world'
        },
        beforeCreate : function() {
            console.log(this);
            showData('1：创建vue实例前-beforeCreate', this);
        },
        created : function() {
            // 如果你要想获取数据必须在这里定义你要获取的业务。
            showData('2:创建vue实例后-created', this);
        },
        beforeMount : function() {
            showData('3:挂载到dom前-beforeMount', this);
        },
        mounted : function() {
            //$(function(){})
            showData('4:挂载到dom后-mounted', this);
        },
        beforeUpdate : function() {
            showData('5:数据变化更新前-beforeUpdate', this);
        },
        updated : function() {
            showData('6:数据变化更新后-updated', this);
        },
        beforeDestroy : function() {
            vm.test = "3333";
            showData('7:vue实例销毁前-beforeDestroy', this);
        },
        destroyed : function() {
            showData('8:vue实例销毁后-destroyed', this);
        }
    });

    function realDom() {
        console.log('真实dom结构：' + document.getElementById('app').innerHTML);
    }

    function showData(process, obj) {
        console.log(process);
        console.log('data 数据：' + obj.message)
        console.log('挂载的对象：')
        console.log(obj.$el)
        realDom();
        console.log('------------------')
        console.log('------------------')
    }

    //vm.message = "good...";
    //vm.$destroy();
</script>
</body>
</html>
```

##### 小结

在开发里面只需要关注两个函数就可以，分别是`created`和`mounted`。推荐如果业务的初始化操作就建议在`mounted`完成。







## 第三部分：掌握和学习Vuejs实战开发以及应用场景（重点）













### 19 - Vuejs实操系列 - Vuejs实战应用开发 + 用户认证中心(应用)



##### 案例需求

>  完成用户的查询与修改操作，

##### 步骤

###### 1：数据库表设计

```sql
/*Table structure for table `user` */
CREATE TABLE `user` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `username` VARCHAR(50) DEFAULT NULL,
  `password` VARCHAR(50) DEFAULT NULL,
  `name` VARCHAR(50) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=INNODB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
/*Data for the table `user` */
INSERT INTO `user`(`id`,`username`,`password`,`name`) VALUES (1,'zhangsan','123','张三');
INSERT INTO `user`(`id`,`username`,`password`,`name`) VALUES (2,'lisi','123','李四');
```

###### 2：创建maven工程搭建ssm

###### 3：创建用户实体

```java
public class User {
    public Long id;
    public String username;
    public String password;
    public String name;
    
    // 此处省略getter/setter
}

```

###### 4：配置pom.xml文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-
instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.itheima.vuejsDemo</groupId>
	<artifactId>vuejsDemo</artifactId>
	<version>1.0-SNAPSHOT</version>
	<packaging>war</packaging>
	<name>vuejsDemo Maven Webapp</name>
	<!-- FIXME change it to the project's website -->
	<url>http://www.example.com</url>
	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<maven.compiler.source>1.8</maven.compiler.source>
		<maven.compiler.target>1.8</maven.compiler.target>
		<spring.version>5.0.2.RELEASE</spring.version>
		<slf4j.version>1.6.6</slf4j.version>
		<log4j.version>1.2.12</log4j.version>
		<mybatis.version>3.4.5</mybatis.version>
	</properties>
	<dependencies> <!-- spring -->
		<dependency>
			<groupId>org.aspectj</groupId>
			<artifactId>aspectjweaver</artifactId>
			<version>1.6.8</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-aop</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context-support</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-web</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-orm</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-beans</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-core</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-test</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-tx</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>4.12</version>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>javax.servlet-api</artifactId>
			<version>3.1.0</version>
			<scope>provided</scope>
		</dependency>
		<dependency>
			<groupId>javax.servlet.jsp</groupId>
			<artifactId>jsp-api</artifactId>
			<version>2.0</version>
			<scope>provided</scope>
		</dependency>
		<dependency>
			<groupId>jstl</groupId>
			<artifactId>jstl</artifactId>
			<version>1.2</version>
		</dependency> <!-- log start -->
		<dependency>
			<groupId>log4j</groupId>
			<artifactId>log4j</artifactId>
			<version>${log4j.version}</version>
		</dependency>
		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>slf4j-api</artifactId>
			<version>${slf4j.version}</version>
		</dependency>
		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>slf4j-log4j12</artifactId>
			<version>${slf4j.version}</version>
		</dependency> <!-- log end -->
		<dependency>
			<groupId>org.mybatis</groupId>
			<artifactId>mybatis</artifactId>
			<version>${mybatis.version}</version>
		</dependency>
		<dependency>
			<groupId>org.mybatis</groupId>
			<artifactId>mybatis-spring</artifactId>
			<version>1.3.0</version>
		</dependency>
		<dependency>
			<groupId>c3p0</groupId>
			<artifactId>c3p0</artifactId>
			<version>0.9.1.2</version>
			<type>jar</type>
			<scope>compile</scope>
		</dependency>
		<dependency>
			<groupId>com.github.pagehelper</groupId>
			<artifactId>pagehelper</artifactId>
			<version>5.1.2</version>
		</dependency>
		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<version>5.1.5</version>
		</dependency>
		<dependency>
			<groupId>com.fasterxml.jackson.core</groupId>
			<artifactId>jackson-core</artifactId>
			<version>2.9.5</version>
		</dependency>
		<dependency>
			<groupId>com.fasterxml.jackson.core</groupId>
			<artifactId>jackson-databind</artifactId>
			<version>2.9.5</version>
		</dependency>
	</dependencies>
	<build>
		<finalName>vuejsDemo</finalName>
		<plugins>
			<plugin>
				<groupId>org.apache.tomcat.maven</groupId>
				<artifactId>tomcat7-maven-plugin</artifactId>
				<version>2.2</version>
			</plugin>
		</plugins>
	</build>
</project>

```



###### 5：配置web.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<web-app xmlns="http://java.sun.com/xml/ns/javaee" 
		 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
		 xsi:schemaLocation="http://java.sun.com/xml/ns/javaee 
		 					 http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd" 
		 id="WebApp_ID" 
		 version="2.5">  
  <!-- 手动指定 spring 配置文件位置 -->  
  <context-param> 
    <param-name>contextConfigLocation</param-name>  
    <param-value>classpath:applicationContext.xml</param-value> 
  </context-param>  
  <!-- 配置 spring 提供的监听器，用于启动服务时加载容器 。
	该间监听器只能加载 WEB-INF 目录中名称为 applicationContext.xml 的配置文件 -->  
  <listener> 
    <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class> 
  </listener>  
  <!-- 配置 spring mvc 的核心控制器 -->  
  <servlet> 
    <servlet-name>springmvcDispatcherServlet</servlet-name>  
    <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>  
    <!-- 配置初始化参数，用于读取 springmvc 的配置文件 -->  
    <init-param> 
      <param-name>contextConfigLocation</param-name>  
      <param-value>classpath:springmvc.xml</param-value> 
    </init-param>  
    <!-- 配置 servlet 的对象的创建时间点：应用加载时创建。取值只能是非 0 正整数，表示启动顺序 -->  
    <load-on-startup>1</load-on-startup> 
  </servlet>  
  <servlet-mapping> 
    <servlet-name>springmvcDispatcherServlet</servlet-name>  
    <url-pattern>*.do</url-pattern> 
  </servlet-mapping>  
  <!-- 配置 springMVC 编码过滤器 -->  
  <filter> 
    <filter-name>CharacterEncodingFilter</filter-name>  
    <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>  
    <!-- 设置过滤器中的属性值 -->  
    <init-param> 
      <param-name>encoding</param-name>  
      <param-value>UTF-8</param-value> 
    </init-param>  
    <!-- 启动过滤器 -->  
    <init-param> 
      <param-name>forceEncoding</param-name>  
      <param-value>true</param-value> 
    </init-param> 
  </filter>  
  <!-- 过滤所有请求 -->  
  <filter-mapping> 
    <filter-name>CharacterEncodingFilter</filter-name>  
    <url-pattern>/*</url-pattern> 
  </filter-mapping>  
  <welcome-file-list> 
    <welcome-file>index.html</welcome-file>  
    <welcome-file>index.htm</welcome-file>  
    <welcome-file>index.jsp</welcome-file>  
    <welcome-file>default.html</welcome-file>  
    <welcome-file>default.htm</welcome-file>  
    <welcome-file>default.jsp</welcome-file> 
  </welcome-file-list> 
</web-app>

```

###### 6：配置springmvc.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:mvc="http://www.springframework.org/schema/mvc" xmlns:context="http://www.springframework.org/schema/context"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/beans
						http://www.springframework.org/schema/beans/spring-beans.xsd
						http://www.springframework.org/schema/mvc
						http://www.springframework.org/schema/mvc/spring-mvc.xsd
						http://www.springframework.org/schema/context
						http://www.springframework.org/schema/context/spring-context.xsd">
	<!-- 配置创建 spring 容器要扫描的包 -->
	<context:component-scan base-package="com.itheima">
		<!-- 制定扫包规则 ,只扫描使用@Controller 注解的 JAVA 类 -->
		<context:include-filter type="annotation" expression="org.springframework.stereotype.Controller" />
	</context:component-scan>
	<mvc:annotation-driven></mvc:annotation-driven>
</beans>
```

###### 7：配置jdbc.properties

```java
jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/test?useUnicode=true&characterEncoding=UTF-8
jdbc.username=root
jdbc.password=passw0rd
```

###### 8：配置applicationContext.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:aop="http://www.springframework.org/schema/aop"
	xmlns:tx="http://www.springframework.org/schema/tx" xmlns:context="http://www.springframework.org/schema/context"
	xsi:schemaLocation="http://www.springframework.org/schema/beans
						http://www.springframework.org/schema/beans/spring-beans.xsd
						http://www.springframework.org/schema/tx
						http://www.springframework.org/schema/tx/spring-tx.xsd
						http://www.springframework.org/schema/aop
						http://www.springframework.org/schema/aop/spring-aop.xsd
						http://www.springframework.org/schema/context
						http://www.springframework.org/schema/context/spring-context.xsd">
	<!-- 配置 spring 创建容器时要扫描的包 -->
	<context:component-scan base-package="com.itheima">
		<!--制定扫包规则，不扫描@Controller 注解的 JAVA 类，其他的还是要扫描 -->
		<context:exclude-filter type="annotation"
			expression="org.springframework.stereotype.Controller" />
	</context:component-scan>
	<!-- 加载配置文件 -->
	<context:property-placeholder location="classpath:db.properties" />
	<!-- 配置 MyBatis 的 Session 工厂 -->
	<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
		<!-- 数据库连接池 -->
		<property name="dataSource" ref="dataSource" />
		<!-- 加载 mybatis 的全局配置文件 -->
		<property name="configLocation" value="classpath:SqlMapConfig.xml" />
	</bean>
	<!-- 配置数据源 -->
	<bean id="dataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource">
		<property name="driverClass" value="${jdbc.driver}"></property>
		<property name="jdbcUrl" value="${jdbc.url}"></property>
		<property name="user" value="${jdbc.username}"></property>
		<property name="password" value="${jdbc.password}"></property>
	</bean>
	<!-- 配置 Mapper 扫描器 -->
	<bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
		<property name="basePackage" value="com.itheima.dao" />
	</bean>
	<tx:annotation-driven />
	<!-- (事务管理)transaction manager, use JtaTransactionManager for global tx -->
	<bean id="transactionManager"
		class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
		<property name="dataSource" ref="dataSource" />
	</bean>
</beans>
```

###### 9：创建Controller

```java
@RequestMapping("/user")
@Controller
@ResponseBody
public class UserController {
	@Autowired
	private IUserService userService;
	@RequestMapping("/findAll.do")
	public List<User> findAll() {
		return userService.findAll();
	}
	@RequestMapping("/findById.do")
	public User findById(Integer id) {
		return userService.findById(id);
	}
	@RequestMapping("/update.do")
	public void update(@RequestBody User user) {
		userService.update(user);
	}
}
```

###### 10：创建Service和ServiceImpl

```java
public interface IUserService {
	List<User> findAll();
	User findById(Integer id);
	void update(User user);
}
```

```java
@Service
@Transactional
public class UserServiceImpl implements IUserService {
    @Autowired
    private IUserDao userDao;
    @Override
    public List<User> findAll() {
        return userDao.findAll();
    }
    @Override
    public User findById(Integer id) {
        return userDao.findById(id);
    }
    @Override
    public void update( User user) {
        userDao.update(user);
    }
}

```



###### 11：创建UserDao

```java
public interface IUserDao {

    @Select("select * from user")
    public List<User> findAll();

    @Select("select * from user where id=#{id}")
    User findById(Integer id);

    @Update("update user set username=#{username},password=#{password},name=#{name} where id=#{id}")
    void update(User user);
}

```

###### 12：创建user.html

```html

```

###### 13：创建user.js

```js

```









### 20 -Vuejs实操系列 - 掌握Vuejs中Axios完成异步请求【应用】

##### 目标

>  什么是Axios，语法结构和定义是什么？

##### 下载

>  https://github.com/axios/axios

##### 方式

导入axios的js

```js
 <script src="js/axios-0.18.0.js"></script>
```

###### get方式+传参方式一：

```js
 axios.get("http://localhost:8080/vuessm-user/get/"+id).then(function(response){
     console.log(response);
     if(response.status==200){
         that.$data.user = response.data;
         $("#myModal").modal("show");//让模态框弹出来
     }
 });
```

###### get方式+传参方式二

```js
var opid = 1;
axios.get("http://localhost:8080/vuessm-user/get/",{
                params:{
                    id:opid
                }
            }).then(function(response){
               console.log(response);
                if(response.status==200){
                    that.$data.user = response.data;
                    $("#myModal").modal("show");//让模态框弹出来
                }
           });
```

###### post请求+传参

<strong style="color:red">注意后台springmvc必须设置：@RequestBody 才可以获取到值</strong>

```js
 axios.post(url,_this.user).then(function (res) {
     //成功之后直接刷新页面
     _this.findAll();
 }).catch(function (err) {
     console.log(err)
 });
```

##### 小结













### 21 - Vue内置指令 -杂项 -v-pre - v2

##### 1. v-pre

>  如果不想渲染任何动态的部分或者插值部分，可以使用v-pre指令：

```html
!--第一步：定义vuejs管理渲染的范围-->
<div id="app">
    <p v-pre>
        {{title}}
        <span v-text="title"></span>
    </p>
    <hr>
    {{title}}
</div>

<!-- 第二步：导入vue.js文件 -->
<script src="js/vuejs-2.5.16.js"></script>
<script>

    // 第三步：定义vuejs对象，开始进行视图和数据的渲染
    var app = new Vue({
        el:"#app",
        data:{title:"Hello world!"}
    }) ;

</script>
```

##### 2. v-once

>  只渲染元素和组件**一次**。随后的重新渲染或者数据改变都不会在渲染和发生改变。

```html
 <!--第一步：定义vuejs管理渲染的范围-->
<div id="app">
    <p v-pre>
        {{title}}
        <span v-text="title"></span>
    </p>
    <hr>
    <p v-once>
        {{title}}
        <span v-text="title"></span>
    </p>
    <hr>
    <p >
        {{title}}
        <span v-text="title"></span>
    </p>
</div>

<!-- 第二步：导入vue.js文件 -->
<script src="js/vuejs-2.5.16.js"></script>
<script>

    // 第三步：定义vuejs对象，开始进行视图和数据的渲染
    var app = new Vue({
        el:"#app",
        data:{title:"Hello world!"}
    }) ;

</script>
```

##### 3. v-cloak

>  ```html
>  <!DOCTYPE html>
>  <html lang="en">
>  <head>
>  <meta charset="UTF-8">
>  <title>18 - Vue内置指令 -杂项 -v-pre - v-once -v-cloak指令【应用】-02</title>
>  <style>
>      [v-cloak] {
>          display: none;
>      }
>  </style>
>  </head>
>  <body>
>  
>  <!--第一步：定义vuejs管理渲染的范围-->
>  <div id="app" >
>  
>  
>      <span v-text="title"></span>
>  
>  </div>
>  
>  <!-- 第二步：导入vue.js文件 -->
>  <script src="js/vuejs-2.5.16.js"></script>
>  <script>
>        // 第三步：定义vuejs对象，开始进行视图和数据的渲染
>        var app = new Vue({
>            el:"#app",
>            data:{title:"Hello world!"}
>        }) ;
>  
>  </script>
>  </body>
>  </html>
>  ```

##### 小结

>  插值表达式，在网络很慢或者有延迟的情况，会把插值表达式暴露在浏览器上，这样会影响用户的体验以及暴露你技术架构，vuejs提供了v-cloak指令来解决和弥补问题。但是一定加[v-cloak] { display: none;}.原理是：先把元素全部隐藏，等渲染完毕以后vuejs会自动把v-cloak指令的范围进行显示。
>
>  建议大家在开发中尽量使用：v-text/v-html来取代插值表达式

