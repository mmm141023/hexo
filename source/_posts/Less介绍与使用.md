---
title: Less介绍与使用
date: 2020-05-18 16:41:12
tags: 
    - Less
categories: 
    - 前端
---
# Command Line Usage



> 使用命令行工具将 `.less` 文件编译成 `.css` 文件。

当心！如果你不喜欢使用命令行，请了解更多有关 [Less 图形界面工具](https://less.bootcss.com/tools/#guis-for-less) 的信息。

## 安装

通过 [npm](https://www.npmjs.org/) 安装

```bash
npm install less -g
```

`-g` 参数表示将 `lessc` 命令安装到全局环境。对于特定版本（或 tag），你可以在软件包（package）名称后面添加 `@VERSION` ，例如 `npm install less@2.7.1 -g`。

### 针对 Node Development 配置段安装 Less

或者，如果你不想将编译器安装到全局环境，则可以

```bash
npm i less --save-dev
```

这将在项目文件夹中安装 lessc 的最新正式版本，并将其添加到 `package.json` 文件中的 `devDependencies` 配置段中。

### lessc 的 Beta 版

随着新功能的不断开发，lessc 版本将发布到 npm，标记为 beta。这些内部版本 _不会_ 作为 `@latest` 正式版本发布，并且通常会在该版本中包含 beta 标识（利用 `lessc -v` 命令获取当前版本号）。

由于 patch（补丁）版本是向后兼容的，因此我们将及时发布 patch 版本，alpha/beta/candidate 版本将作为 minor（次要）或 major（主要）版本进行发布并升级（从 1.4.0 版本开始，我们将努力遵循 [语义化版本命名规范](http://semver.org/))。

## 服务器端和命令行用法

该仓库中包含的二进制文件 `bin/lessc` 能够在 *nix、OS X 和 Windows 平台上的 [Node.js](http://nodejs.org/) 上运行。

**用法**： `lessc [option option=parameter ...]  [destination]`

### 命令行用法

```bash
lessc [option option=parameter ...] <source> [destination]
```

如果 source 设置为 `-' （破折号或连字符减号），则从 stdin 读取输入。

#### 示例

将 bootstrap.less 编译为 bootstrap.css

```bash
lessc bootstrap.less bootstrap.css
```

## 特定于 `lessc` 的参数

*有关其他所有参数的信息，请参见 [Less 参数列表](https://less.bootcss.com/usage/#less-options)。*

#### Silent

lessc -s lessc --silent

不显示任何警告信息。

#### Version

```bash
lessc -v
lessc --version
```

#### Help

|                |      |
| :------------- | :--- |
| `lessc --help` |      |
| `lessc -h`     |      |

展示所有参数的帮助信息并退出。

#### Makefile

```bash
lessc -M
lessc --depends
```

Outputs a makefile import dependency list to stdout.

#### No Color

*不推荐使用*。

```bash
lessc --no-color
```

#### Clean CSS

在 v2 版本的 less 中，Clean CSS 不再作为直接依赖项而存在。如需将 clean css 与 lessc 一起使用，请使用 [clean css 插件](https://github.com/less/less-plugin-clean-css)。



# Browser Usage



> Using Less.js in the browser is the easiest way to get started and convenient for developing with Less, but in production, when performance and reliability is important, we recommend pre-compiling using Node.js or one of the many third party tools available.

To start off, link your `.less` stylesheets with the `rel` attribute set to "`stylesheet/less`":

```html
<link rel="stylesheet/less" type="text/css" href="styles.less" />
```

Next, [download less.js](https://github.com/less/less.js/archive/master.zip) and include it in a `` tag in the `` element of your page:

```html
<script src="less.js" type="text/javascript"></script>
```

### Setting Options

You can set options either programmatically, by setting them on a less object **before** the script tag - this then affects all initial link tags and programmatic usage of less.

```html
<script>
  less = {
    env: "development",
    async: false,
    fileAsync: false,
    poll: 1000,
    functions: {},
    dumpLineNumbers: "comments",
    relativeUrls: false,
    rootpath: ":/a.com/"
  };
</script>
<script src="less.js"></script>
```

The other way is to specify the options on the script tag, e.g.

```html
<script>
  less = {
    env: "development"
  };
</script>
<script src="less.js" data-env="development"></script>
```

Or for brevity they can be set as attributes on the script and link tags:

```html
<script src="less.js" data-poll="1000" data-relative-urls="false"></script>
<link data-dump-line-numbers="all" data-global-vars='{ "myvar": "#ddffee", "mystr": "\"quoted\"" }' rel="stylesheet/less" type="text/css" href="less/styles.less">
```

### Browser Support

Less.js supports all modern browsers (recent versions of Chrome, Firefox, Safari, IE11+, and Edge). While it is possible to use Less on the client side in production, please be aware that there are performance implications for doing so (although the latest releases of Less are quite a bit faster). Also, sometimes cosmetic issues can occur if a JavaScript error occurs. This is a trade off of flexibility vs. speed. For the fastest performance possible for a static web site, we recommend compiling Less on the server side.

There are reasons to use client-side less in production, such as if you want to allow users to tweak variables which will affect the theme and you want to show it to them in real-time - in this instance a user is not worried about waiting for a style to update before seeing it.

### Tips

- Make sure you include your stylesheets **before** the script.
- When you link more than one `.less` stylesheet each of them is compiled independently. So any variables, mixins or namespaces you define in a stylesheet are not accessible in any other.
- Due to the same origin policy of browsers, loading external resources requires [enabling CORS](http://enable-cors.org/)

### Watch Mode

To enable Watch mode, option `env` must be set to `development`. Then AFTER the less.js file is included, call `less.watch()`, like this:

```html
<script>less = { env: 'development'};</script>
<script src="less.js"></script>
<script>less.watch();</script>
```

Alternatively, you can enable Watch mode temporarily by appending `#!watch` to the URL.

### Modify Variables

Enables run-time modification of Less variables. When called with new values, the Less file is recompiled without reloading. Simple basic usage:

```js
less.modifyVars({
  '@buttonFace': '#5B83AD',
  '@buttonText': '#D9EEF2'
});
```

### Debugging

It is possible to output rules in your CSS which allow tools to locate the source of the rule.

Either specify the option `dumpLineNumbers` as above or add `!dumpLineNumbers:mediaquery` to the url.

You can use the `mediaquery` option with [FireLESS](https://addons.mozilla.org/en-us/firefox/addon/fireless/) (it is identical to the SCSS media query debugging format). Also see [FireLess and Less v2](http://bassjobsen.weblogs.fm/fireless-less-v2/). The `comment` option can be used to display file information and line numbers in the inline compiled CSS code.

### Options

Set options in a global `less` object **before** loading the less.js script:

```html
<!-- set options before less.js script -->
<script>
  less = {
    env: "development",
    logLevel: 2,
    async: false,
    fileAsync: false,
    poll: 1000,
    functions: {},
    dumpLineNumbers: "comments",
    relativeUrls: false,
    globalVars: {
      var1: '"quoted value"',
      var2: 'regular value'
    },
    rootpath: ":/a.com/"
  };
</script>
<script src="less.js"></script>
```

## Options specific to Less.js in the browser

*For all other options, see [Less Options](https://less.bootcss.com/usage/#less-options).*

#### async

Type: `Boolean`

Default: `false`

Whether to request the import files with the async option or not. See [fileAsync](https://less.bootcss.com/usage/#using-less-in-the-browser-fileasync).

#### env

Type: `String` Default: depends on page URL

Environment to run may be either `development` or `production`.

In production, your css is cached in local storage and information messages are not output to the console.

If the document's URL starts with `file://` or is on your local machine or has a non standard port, it will automatically be set to `development`.

e.g.

```js
less = { env: 'production' };
```

#### errorReporting

Type: `String`

Options: `html`|`console`|`function`

Default: `html`

Set the method of error reporting when compilation fails.

#### fileAsync

Type: `Boolean`

Default: `false`

Whether to request the import asynchronously when in a page with a file protocol.

#### functions (Deprecated - use @plugin)

Type: `object`

User functions, keyed by name.

```js
less = {
    functions: {
        myfunc: function() {
            return less.Dimension(1);
        }
    }
};
```

and it can be used like a native Less function e.g.

```less
.my-class {
  border-width: unit(myfunc(), px);
}
```

#### logLevel

Type: `Number`

Default: 2

The amount of logging in the javascript console. Note: If you are in the `production` environment you will not get any logging.

```bash
2 - Information and errors
1 - Errors
0 - Nothing
```

#### poll

Type: `Integer`

Default: `1000`

The amount of time (in milliseconds) between polls while in watch mode.

#### relativeUrls

Type: `Boolean`

Default: `false`

Optionally adjust URLs to be relative. When false, URLs are already relative to the entry less file.

#### useFileCache

Type: `Boolean`

Default: `true` (previously `false` in before v2)

Whether to use the per session file cache. This caches less files so that you can call modifyVars and it will not retrieve all the less files again. If you use the watcher or call refresh with reload set to true, then the cache will be cleared before running.



# Less.js Options



## 跨平台参数

### Include Paths

|                                    |                                 |
| :--------------------------------- | :------------------------------ |
| `lessc --include-path=PATH1;PATH2` | `{ paths: ['PATH1', 'PATH2'] }` |

If the file in an `@import` rule does not exist at that exact location, Less will look for it at the location(s) passed to this option. You might use this for instance to specify a path to a library which you want to be referenced simply and relatively in the Less files.

### Rootpath

|                                                      |                              |
| :--------------------------------------------------- | :--------------------------- |
| `lessc -rp=resources/` `lessc --rootpath=resources/` | `{ rootpath: 'resources/' }` |

Allows you to add a path to every generated import and url in your css. This does not affect Less import statements that are processed, just ones that are left in the output css.

For instance, if all the images the css use are in a folder called resources, you can use this option to add this on to the URL's and then have the name of that folder configurable.

### Rewrite URLs

|                                                |                            |
| :--------------------------------------------- | :------------------------- |
| `lessc -ru=off` `lessc --rewrite-urls=off`     | `{ rewriteUrls: 'off' }`   |
| `lessc -ru=all` `lessc --rewrite-urls=all`     | `{ rewriteUrls: 'all' }`   |
| `lessc -ru=local` `lessc --rewrite-urls=local` | `{ rewriteUrls: 'local' }` |

By default URLs are kept as-is (`off`), so if you import a file in a sub-directory that references an image, exactly the same URL will be output in the css. This option allows you to rewrite URLs in imported files so that the URL is always relative to the base file that has been passed to Less. E.g.

```css
/* main.less */
@import "global/fonts.less";
/* global/fonts.less */
@font-face {
  font-family: 'MyFont';
  src: url('myfont/myfont.woff2') format('woff2');
}
```

With nothing set or with `rewriteUrls: 'off'`, compiling `main.less` will output:

```css
/* main.less */
/* global/fonts.less */
@font-face {
  font-family: 'MyFont';
  src: url('myfont/myfont.woff2') format('woff2');
}
```

With `rewriteUrls: 'all'`, it will output:

```css
/* main.less */
/* global/fonts.less */
@font-face {
  font-family: 'MyFont';
  src: url('./global/myfont/myfont.woff2') format('woff2');
}
```

With `rewriteUrls: 'local'`, it will only rewrite URLs that are explicitly relative (those starting with a `.`):

```css
url('./myfont/myfont.woff2') /* becomes */ url('./global/myfont/myfont.woff2')
url('myfont/myfont.woff2') /* stays */ url('myfont/myfont.woff2')
```

This can be useful in case you're combining Less with [CSS Modules](https://github.com/css-modules/css-modules) which use similar resolving semantics like Node.js.

You may also want to consider using the data-uri function instead of this option, which will embed images into the css.

### Math

*Released v3.7.0*

|                                             |                        |
| :------------------------------------------ | :--------------------- |
| `lessc -m=[option]` `lessc --math=[option]` | `{ math: '[option]' }` |

Less has re-built math options to offer an in-between feature between the previous `strictMath` setting, which required parentheses all the time, and the default, which performed math in all situations.

In order to cause fewer conflicts with CSS, which now liberally uses the `/` symbol between values, there is now a math mode that *only* requires parentheses for division. "Strict math" has also been tweaked to operate more intuitively, although the legacy behavior is supported.

The for options available for `math` are:

- `always` (current default) - Less eagerly does math
- `parens-division` **(future default)** - No division is performed outside of parens using `/` operator (but can be "forced" outside of parens with `./` operator)
- `parens` | `strict` - A more intuitive form of legacy `strictMath: true`
- `strict-legacy` (deprecated) - As named, operates exactly like current `strictMath: true`, with the exception that `width: -(1);` (single dimension values in parens) will now output `width: -1;` vs previous behavior of `width: -(1)`

**always** Example:

```less
.math {
  a: 1 + 1;
  b: 2px / 2;
  c: 2px ./ 2;
  d: (2px / 2);
}
```

Outputs:

```css
.math {
  a: 2;
  b: 1px;
  c: 1px;
  d: 1px;
}
```

**parens-division**

Example:

```less
.math {
  a: 1 + 1;
  b: 2px / 2;
  c: 2px ./ 2;
  d: (2px / 2);
}
```

Outputs:

```css
.math {
  a: 2;
  b: 2px / 2;
  c: 1px;
  d: 1px;
}
```

**strict**

```less
.math {
  a: 1 + 1;
  b: 2px / 2;
  c: (2px / 2) + (3px / 1);
}
```

Output:

```css
.math {
  a: 1 + 1;
  b: 2px / 2;
  c: 1px + 3px;
}
```

**strict-legacy**

In legacy `strictMath` mode, mixed expressions outside of parentheses means entire parentheses won't evaluate. (Probably not what you want.)

```less
.math {
  a: 1 + 1;
  b: 2px / 2;
  c: (2px / 2) + (3px / 1);
}
```

Output:

```css
.math {
  a: 1 + 1;
  b: 2px / 2;
  c: (2px / 2) + (3px / 1);
}
```

#### Strict Math (Deprecated)

*This has been replaced by the [`math`](https://less.bootcss.com/usage/#less-options-math) option.*

#### Relative URLs (deprecated)

|                                     |                          |
| :---------------------------------- | :----------------------- |
| `lessc -ru` `lessc --relative-urls` | `{ relativeUrls: true }` |

*Has been replaced by `rewriteUrls: "all"`*

### Strict Units

|                                          |                         |
| :--------------------------------------- | :---------------------- |
| `lessc -su=on` `lessc --strict-units=on` | `{ strictUnits: true }` |

Defaults to off/false.

Without this option, Less attempts to guess at the output unit when it does maths. For instance

```less
.class {
  property: 1px * 2px;
}
```

In this case, things are clearly not right - a length multiplied by a length gives an area, but css does not support specifying areas. So we assume that the user meant for one of the values to be a value, not a unit of length and we output `2px`.

With strict units on, we assume this is a bug in the calculation and throw an error.

#### IE8 Compatibility (Deprecated)

|                     |                      |
| :------------------ | :------------------- |
| `lessc --ie-compat` | `{ ieCompat: true }` |

False by default starting in v3.0.0. Currently only used for the data-uri function to ensure that images aren't created that are too large for the browser to handle.

#### Enable Inline JavaScript (Deprecated)

|              |                               |
| :----------- | :---------------------------- |
| `lessc --js` | `{ javascriptEnabled: true }` |

False by default starting in v3.0.0. Enables evaluation of JavaScript inline in `.less` files. This created a security problem for some developers who didn't expect user input for style sheets to have executable code.

Replaced with the `@plugin` option.

#### Global Variables

|                                   |                                     |
| :-------------------------------- | :---------------------------------- |
| `lessc --global-var="color1=red"` | `{ globalVars: { color1: 'red' } }` |

This option defines a variable that can be referenced by the file. Effectively the declaration is put at the top of your base Less file, meaning it can be used but it also can be overridden if this variable is defined in the file.

#### Modify Variables

|                                   |                                     |
| :-------------------------------- | :---------------------------------- |
| `lessc --modify-var="color1=red"` | `{ modifyVars: { color1: 'red' } }` |

As opposed to the global variable option, this puts the declaration at the end of your base file, meaning it will override anything defined in your Less file.

#### URL Arguments

|                                  |                              |
| :------------------------------- | :--------------------------- |
| `lessc --url-args="cache726357"` | `{ urlArgs: 'cache726357' }` |

This option allows you to specify a argument to go on to every URL. This may be used for cache-busting for instance.

#### Line Numbers (Deprecated)

|                                                              |                                   |
| :----------------------------------------------------------- | :-------------------------------- |
| `lessc --line-numbers=comments` `lessc --line-numbers=mediaquery` `lessc --line-numbers=all` | `{ dumpLineNumbers: 'comments' }` |

Generates inline source-mapping. This was the only option before browsers started supporting sourcemaps.

#### Pre-Loaded Plugin

See: [Pre-Loaded Plugins](https://less.bootcss.com/usage/#plugins)

#### Lint

|                   |                  |
| :---------------- | :--------------- |
| `lessc --lint -l` | `{ lint: true }` |

Runs the less parser and just reports errors without any output.

#### Compress (Deprecated)

|                       |                      |
| :-------------------- | :------------------- |
| `lessc --compress -x` | `{ compress: true }` |

Compress using less built-in compression. This does an okay job but does not utilise all the tricks of dedicated css compression. In general, we recommend looking at third-party tools that clean and compress CSS after your Less has been transformed to CSS.

#### Allow Imports from Insecure HTTPS Hosts

|                    |                      |
| :----------------- | :------------------- |
| `lessc --insecure` | `{ insecure: true }` |

## Source Map Options

Most of these options are not applicable to using Less.js in the browser, as you should generate a source map with your pre-compiled Less files.

#### Generate a Source Map

|                      |                     |
| :------------------- | :------------------ |
| `lessc --source-map` | `{ sourceMap: {} }` |

Tells less to generate a sourcemap.

#### Source Map Output Filename

|                               |                                                 |
| :---------------------------- | :---------------------------------------------- |
| `lessc --source-map=file.map` | `{ sourceMap: { outputFilename: 'file.map' } }` |

#### Source Map Rootpath

|                                          |                                                      |
| :--------------------------------------- | :--------------------------------------------------- |
| `lessc --source-map-rootpath=dev-files/` | `{ sourceMap: { sourceMapRootpath: 'dev-files/' } }` |

Specifies a rootpath that should be prepended to each of the less file paths inside the sourcemap and also to the path to the map file specified in your output css.

Because the basepath defaults to the directory of the input less file, the rootpath defaults to the path from the sourcemap output file to the base directory of the input less file.

Use this option if for instance you have a css file generated in the root on your web server but have your source less/css/map files in a different folder. So for the option above you might have

```bash
output.css
dev-files/output.map
dev-files/main.less
```

#### Source Map Basepath

|                                           |                                                       |
| :---------------------------------------- | :---------------------------------------------------- |
| `lessc --source-map-basepath=less-files/` | `{ sourceMap: { sourceMapBasepath: 'less-files/' } }` |

This is the opposite of the rootpath option, it specifies a path which should be removed from the output paths. For instance if you are compiling a file in the less-files directory but the source files will be available on your web server in the root or current directory, you can specify this to remove the additional `less-files` part of the path.

It defaults to the path to the input less file.

#### Include Less Source in the Source Map

|                                     |                                              |
| :---------------------------------- | :------------------------------------------- |
| `lessc --source-map-include-source` | `{ sourceMap: { outputSourceFiles: true } }` |

This option specifies that we should include all of the Less files in to the sourcemap. This means that you only need your map file to get to your original source.

This can be used in conjunction with the map inline option so that you do not need to have any additional external files at all.

#### Source Map Map Inline

|                             |                                                |
| :-------------------------- | :--------------------------------------------- |
| `lessc --source-map-inline` | `{ sourceMap: { sourceMapFileInline: true } }` |

This option specifies that the map file should be inline in the output CSS. This is not recommended for production, but for development it allows the compiler to produce a single output file which in browsers that support it, use the compiled css but show you the non-compiled less source.

#### Source Map URL

|                                         |                                                     |
| :-------------------------------------- | :-------------------------------------------------- |
| `lessc --source-map-url=../my-map.json` | `{ sourceMap: { sourceMapURL: '../my-map.json' } }` |

Allows you to override the URL in the css that points at the map file. This is for cases when the rootpath and basepath options are not producing exactly what you need.



# Pre-Loaded Plugins



> 在 Less.js 开始解析之前加载插件

使用插件的最简单方式是使用 [`@plugin` 规则](https://less.bootcss.com/features/#plugin-atrules-feature)，在 Node.js 环境中，你可以通过命令行或在 [Less 参数](https://less.bootcss.com/usage/#less-options)中指定需要预加载的全局 Less.js 插件。

### 预处理

如果要添加 Less.js 预处理器，则必须预加载插件。也就是说，在 Less 源码被解析之前，插件就被调用并接收到 Less 源码。例如 [Sass-To-Less 预处理器插件](https://less.bootcss.com/tools/#plugins)。

注意： 预加载对于 *pre-evaluation（预求值）* 插件不是必须的（只要在 Less 源码被解析之后，且在被求值之前即可）。

## Node.js

### 使用命令行

如果你使用的是 lessc，则要做的第一件事就是安装该插件。在 NPM 之类的注册表中，我们建议将 Less.js 插件注册为带有 "less-plugin-" 前缀的插件名（以便于搜索），虽然这不是必需的。然后，对于自定义插件，就可以以如下方式安装：

```
npm install less-plugin-myplugin
```

要使用该插件，你可以在命令行中通过以下指定即可：

```
lessc --myplugin
```

每当存在未知的 Less 参数时（例如 "myplugin"），Less.js 就会尝试将 "less-plugin-myplugin" 模块和 "myplugin" 模块作为插件加载。

你还可以使用以下命令显式指定插件：

```
lessc --plugin=myplugin
```

要将参数传递给插件，你可以使用以下两种方法之一。

```
lessc --myplugin="advanced"
lessc --plugin=myplugin=advanced
```

## 通过 Less.js 加载插件

在 Node 中，需要通过 require 指令加载插件并将其作为插件参数数组传递给 `less` 。例如：

```js
var LessPlugin = require('less-plugin-myplugin');
less.render(myCSS, { plugins: [LessPlugin] })
  .then(
    function(output) { },
    function(error) { }
  );
```



# Programmatic Usage



The main entry point into `less` is the `less.render` function. This takes the following format

```js
less.render(lessInput, options)
    .then(function(output) {
        // output.css = string of css
        // output.map = string of sourcemap
        // output.imports = array of string filenames of the imports referenced
    },
    function(error) {
    });

// or...

less.render(css, options, function(error, output) {})
```

The options argument is optional. If you specify a callback then a promise will not be returned, where as if you do not specify a callback a promise will be given. Under the hood, the callback version is used so that less can be used synchronously.

If you wanted to render a file, you would first read it into a string (to pass to less.render) and then set the filename field on options to be the filename of the main file. less will handle all the processing of the imports.

The `sourceMap` option is an object which enables you to set sub sourcemap options. Available sub options are: `sourceMapURL`,`sourceMapBasepath`,`sourceMapRootpath`,`outputSourceFiles` and `sourceMapFileInline`. Notice that the `sourceMap` option is not available for the less.js in browser compiler now.

```js
less.render(lessInput)
    .then(function(output) {
        // output.css = string of css
        // output.map = undefined
}
//,
less.render(lessInput, {sourceMap: {}})
    .then(function(output) {
        // output.css = string of css
        // output.map = string of sourcemap
}
//or,
less.render(lessInput, {sourceMap: {sourceMapFileInline: true}})
    .then(function(output) {
        // output.css = string of css \n /*# sourceMappingURL=data:application/json;base64,eyJ2ZXJ..= */
        // output.map = undefined
}
```

### Getting Access to the Log

You can add a log listener with the following code

```js
less.logger.addListener({
    debug: function(msg) {
    },
    info: function(msg) {
    },
    warn: function(msg) {
    },
    error: function(msg) {
    }
});
```

Note: all functions are optional. An error will not be logged, but instead is passed back to the callback or promise in less.render



# API



> Coming soon



# Contributing to Less.js



Thanks for thinking about contributing! Please read the [contributing instructions](https://less.bootcss.com/usage/CONTRIBUTING.md) carefully to avoid wasted work.

## Install These Tools

- **node** - http://nodejs.org/
- **phantomjs** - http://phantomjs.org/download.html

make sure the paths are setup. If you start your favourite command line and type `node -v` you should see the node compiler. If you run `phantomjs -v` you should see the phantomjs version number.

- clone your less.js repository locally
- navigate to your local less.js repository and run `npm install` this installs less' npm dependencies.

## Usage

[Grunt](https://gruntjs.com/) is used in order to run development commands such as tests, builds, and benchmarks. You can run them either with `grunt [command_name]` if you have `grunt-cli` installed globally or with `npm run grunt -- [command_name]`.

If you go to the root of the Less repository you should be able to do `npm test` (a handy alias for `npm run grunt -- test`) - this should run all the tests. For the browser specific only, run `npm run grunt -- browsertest` If you want to try out the current version of less against a file, from here do `node bin/lessc path/to/file.less`

To debug the browser tests, run `npm run grunt -- browsertest-server` then go to http://localhost:8088/tmp/browser/ to see the test runner pages.

Optional: To get the current version of the Less compiler do `npm -g install less` - npm is the node package manager and "-g" installs it to be available globally.

You should now be able to do `lessc file.less` and if there is an appropriate `file.less` then it will be compiled and output to the stdout. You can then compare it to running locally (`node bin/lessc file.less`).

Other grunt commands

- `npm run grunt -- benchmark` - run our benchmark tests to get some numbers on performance
- `npm run grunt -- stable` to create a new release
- `npm run grunt -- readme` to generate a new readme.md in the root directory (after each release)

## How to Run Less in Other Environments

If you look in the libs folder you will see `less`, `less-node`, `less-browser`. The `less` folder is pure javascript with no environment specifics. if you require `less/libs/less`, you get a function that takes an environment object and an array of file managers. The file managers are the same file managers that can also be written as a plugin.

```js
var createLess = require("less/libs/less"),
    myLess = createLess(environment, [myFileManager]);
```

The environment api is specified in [less/libs/less/environment/environment-api.js](https://github.com/less/less.js/blob/master/lib/less/environment/environment-api.js) and the file manager api is specified in [less/libs/less/environment/file-manager-api.js](https://github.com/less/less.js/blob/master/lib/less/environment/file-manager-api.js).

For file managers we highly recommend setting the prototype as a new AbstractFileManager - this allows you to override what is needed and allows us to implement new functions without breaking existing file managers. For an example of file managers, see the 2 node implementations, the browser implementation or the npm import plugin implementation.

## Guide

If you look at http://www.gliffy.com/go/publish/4784259, This is an overview diagram of how less works. Warning! It needs updating with v2 changes.
