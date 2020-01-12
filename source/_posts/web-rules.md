---
title: 前端规范
date: 2020-01-11 14:23:50
tags:
---


## 规范说明

此为前端开发团队遵循和约定的代码书写规范，意在提高代码的规范性和可维护性。  
此规范为参考规范，统一团队编码规范和风格。让所有代码都是有规可循的，并且能够得到沉淀，减少重复劳动。  

## 编辑器配置

将编辑器按照下面的配置进行设置，以避免常见的代码不一致和差异；
* HTML，CSS，JS 的 tab 统一四个空格，保持代码的一致性。
* 设置文件编码为 UTF-8

## 文件命名(目前项目中大多为驼峰式，需讨论)  

文件名建议只使用小写字母，不使用大写字母，词与词之间通过 “ - ” 连接。  
为了醒目，某些说明文件的文件名，可以使用大写字母，比如 README、LICENSE。  
保证项目有良好的可移植性，可跨平台。

## HTML
### 通用约定
HTML结构大的模块标记开始和结束，方便阅读，新闻类的页面结构遵守SEO标准。  

1. 语法
对于属性的定义，确保全部使用双引号，绝不要使用单引号。  

2. 引入 CSS 和 JavaScript 文件
根据 HTML5 规范，在引入 CSS 和 JavaScript 文件时一般不需要指定 type 属性，因为 text/css 和 text/javascript 分别是它们的默认值。  

3. 标签
    - 自闭合（self-closing）标签，无需闭合 ( 例如： img input br hr 等 )；
    - 可选的闭合标签（closing tag），需闭合 ( 例如：</li> 或 </body> )；
    - 尽量减少标签数量；
```html
<img src="//img.w3cschool.cn/attachments/image/cimg/google.png" alt="Google">
<input type="text" name="title">

<ul>
<li>Style</li>
<li>Guide</li>
</ul>

<!-- Not recommended -->
<span class="avatar">
<img src="...">
</span>

<!-- Recommended -->
<img class="avatar" src="...">
```

4. Class 与 ID（目前项目中大多不统一，同一人代码也有不统一情况）  
    - Class 应以功能或内容命名，不以表现形式命名；
    - Class 与 ID单词字母小写，多个单词组成时，采用中划线 “ - ” 分隔；
    - 使用唯一的 ID，同时避免创建无样式信息的 Class；

```html
<!-- Not recommended -->
<div class="j-hook left contentWrapper"></div>

<!-- Recommended -->
<div id="j-hook" class="sidebar content-wrapper"></div>
```
5. 属性顺序 （不强制遵守）
HTML 属性应该按照特定的顺序出现以保证易读性。
* id
* class
* name
* data-xxx
* src, for, type, href
* title, alt
* aria-xxx, role
```html
<a id="..." class="..." data-modal="toggle" href="###"></a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

6. 引号
属性的定义，统一使用双引号。
```html
<!-- Not recommended -->
<span id='j-hook' class=text>Google</span>

<!-- Recommended -->
<span id="j-hook" class="text">Google</span>
```

7. 嵌套  
语义嵌套约束  
`<li>` 用于 `<ul>` 或`<ol>` 下；  
`<dd>`，`<dt>` 用于 `<dl>` 下；  
`<thead>`，`<tbody>`，`<tfoot>`，`<tr>`，`<td>` 用于 `<table>` 下；

8. 布尔值属性  
HTML5 规范中 disabled、checked、selected 等属性不用设置值。
```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```

## 语义化
语义化的 HTML 结构，有助于机器（搜索引擎）理解，另一方面多人协作时，能迅速了解开发者意图。  
常见标签语义


标签|语义
---|:--
`<p>`	|段落
`<h1>` `<h2>` `<h3>`...	|标题
`<ul>`	|无序列表
`<ol>`	|有序列表
`<b>`	|为样式加粗而加粗
`<storng>`	|为强调内容而加粗
`<i>`	|为样式倾斜而倾斜
`<em>`	|为强调内容而倾斜
`abbr`	|缩写
例:将构建的页面当作一本书，标签的语义对应的其功能和含义；  
书的名称：`<h1>`  
书的每个章节标题：`<h2>`  
章节内的文章标题：`<h3>`  
小标题/副标题：`<h4>` `<h5>` `<h6>`  
章节的段落： `<p>`  

## HEAD
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" /><!--优先使用 IE 最新版本和 Chrome-->
    <meta name="renderer" content="webkit">
    <!-- SEO -->
    <title></title>
    <meta name="viewport" content="width=device-width,minimum-scale=1.0,maximum-scale=1.0,user-scalable=0"/><!-- 为移动设备添加 viewport -->
    <meta name="keywords" content="your keywords"><!--页面关键词keywords-->
    <meta name="description" content="description"><!--页面描述内容description-->
    <meta name="author" content="author,email address">
    <meta name="robots" content="index,follow"><!--定义网页搜索引擎索引方式,robotterms是一组使用英文逗号「,」分割的值，通常有如下几种取值：none，noindex，nofollow，all，index和follow-->
    <!-- http cache -->
    <!-- <meta http-equiv="Cache-Control" content="max-age=7200" /> -->
    <meta http-equiv="Cache-Control" content="no-cache" />
    <link rel="shortcut icon" href="path/to/favicon.ico"><!--设置标题小图标-->
    <!-- iOS 图标 (apple-touch-icon-precomposed 禁止系统对图标添加效果)-->
    <link rel="apple-touch-icon" sizes="57x57" href="touch-icon-iphone.png" />  
    <link rel="apple-touch-icon" sizes="72x72" href="touch-icon-ipad.png" />  
    <link rel="apple-touch-icon" sizes="114x114" href="touch-icon-iphone4.png" />    
    <link rel="apple-touch-icon" sizes="144x144" href="apple-touch-icon-ipad3-144.png" />  
    <!--[if lt IE 9]>
    <script src="//cdn.bootcss.com/html5shiv/3.7.3/html5shiv.min.js"></script>
    <script src="//cdn.bootcss.com/respond.js/1.4.2/respond.min.js"></script>
    <![endif]-->
</head>
```
## css
### 通用约定
1. 代码组织

  - 以组件为单位组织代码段；  
  - 制定一致的注释规范；  
  - 如果使用了多个 CSS 文件，将其按照组件而非页面的形式分拆，因为页面会被重组，而组件只会被移动；  
2. Class 和 ID

  - 使用连字符 “ - ” 作为 ID、Class 名称界定符，不要驼峰命名法和下划线；
  - 命名与功能关联，所有的class名字前加 “ yj- ” 前缀；
  - 使用唯一的 id，同时避免创建无样式信息的 class；
3. 引号使用
url() 、属性选择符、属性值使用双引号。  
```css
/* Not recommended */
@import url(//www.google.com/css/maia.css);

html {
  font-family: 'Microsoft YaHei', arial, sans-serif;
}

/* Recommended */
@import url("//www.google.com/css/maia.css");

html {
  font-family: "Microsoft YaHei", arial, sans-serif;
}

.selector[type="text"] {

}
```
4. 空格

  - 选择器和 { 之间保留一个空格。
  - 属性名后的冒号（:）与属性值之间保留一个空格，冒号前不保留空格。
  - 在用逗号（,）分隔的列表中，逗号后保留一个空格，逗号前不保留空格。
```css
/* Not recommended */
.box{
    width:50px;
    height :30px;
    color: rgba(255,255,255,.3);
    transition: width 1s,height 3s;
}

/* Recommended */
.box {
    width: 50px;
    height: 30px;
    transition: width 1s, height 3s;
}
```
5. 0 值  
当属性值为 0 时，省略可省的单位（长度单位如 px、em，不包括时间、角度等如 s、deg）。
```css
/* Not recommended */
margin-top: 0px;

/* Recommended */
margin-top: 0;
```
6. 媒体查询（Media query）的位置  
将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果分开了，将来只会被遗忘。  
```css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (max-width: 768px) {
  .element { ...}
  .element-avatar { ... }
  .element-selected { ... }
}
```
## Less规范
1. 代码组织（按以下顺序组织）
  - @import
  - 变量声明
  - 样式声明
```css
@import "mixins/size.less";

@default-text-color: #333;

.page {
  width: 960px;
  margin: 0 auto;
}
```
2. @import 语句  
@import 语句引用的文需要写在一对引号内，.less 后缀不得省略。引号使用 "" 。
```css
/* Not recommended */
@import "mixins/size";
@import 'mixins/grid.less';

/* Recommended */
@import "mixins/size.less";
@import "mixins/grid.less";
```
## JavaScript
### 通用约定  

1. 语法
  - 对于属性的定义，确保全部使用单引号，绝不要使用双引号。    

2. 注释原则 (单行注释、多行注释)  
  - 如无必要，勿增注释：尽量提高代码本身的清晰性、可读性。
  - 如有必要，尽量详尽：合理的注释、空行排版等，可以让代码更易阅读、更具美感。

3. 函数/方法注释  
  - 函数/方法注释必须包含函数说明，有参数和返回值时必须使用注释标识；
  - 参数和返回值注释必须包含类型信息和说明；
  - 当函数是内部函数，外部不可访问时，可以使用 @inner 标识；
```javascript
/**
 * 函数描述
 *
 * @param {string} p1 参数1的说明
 * @param {string} p2 参数2的说明，比较长
 *     那就换行了.
 * @param {number=} p3 参数3的说明（可选）
 * @return {Object} 返回值描述
 */
function foo(p1, p2, p3) {
    var p3 = p3 || 10;
    return {
        p1: p1,
        p2: p2,
        p3: p3
    };
}
```

4. 文件注释
  - 文件注释用于告诉不熟悉这段代码的读者这个文件中包含哪些东西。 应该提供文件的大体内容，依赖关系和兼容性信息。

5. 命名 （不强制遵守）  
  - 变量，使用 Camel 命名法。  
```javascript
var loadingModules = {}
```
  - boolean 类型的变量使用 is 或 has 开头。
```javascript
var isReady = false
var hasMoreCommands = false
```
  - 私有属性、变量和方法以下划线 _ 开头。
```javascript
var _privateMethod = {}
```
  - 常量，使用全部字母大写，单词间下划线分隔的命名方式。
```javascript
var HTML_ENTITY = {}
```
  - 函数，使用 Camel 命名法。
  - 函数的参数，使用 Camel 命名法。
```javascript
function stringFormat(source) {}

function hear(theBells) {}
```
  - 类、构造函数，使用 Pascal 命名法。
  - 类的 方法 / 属性, 使用 Camel 命名法。
```javascript
function TextNode(value, engine) {
    this.value = value
    this.engine = engine
}

TextNode.prototype.clone = function () {
    return this
}
```
  - 枚举变量使用 Pascal 命名法。
  - 枚举的属性， 使用全部字母大写，单词间下划线分隔的命名方式。
```javascript
var TargetState = {
    READING: 1,
    READED: 2,
    APPLIED: 3,
    READY: 4
}
```
  - 由多个单词组成的缩写词，在命名中，根据当前命名法和出现的位置，所有字母的大小写与首字母的大小写保持一致。
```javascript
function XMLParser() {}

function insertHTML(element, html) {}

var httpRequest = new HTTPRequest()
```

  - 末尾无需加 ；  
网校项目都不需要加，代码统一  

## 组件
### 以 vue 为例  
组件一般情况下是可以拆成基础/ui部分和业务部分，基础组件一般是承载呈现，基础功能，不和业务耦合部分。  
业务组件一般包含业务功能业务特殊数据等等。  
1. UI组件/基础组件

  - 开发的时候注意可拓展性，支持数据传参进行渲染，支持插槽slot。
2. 容器组件

  - 和当前业务耦合性比较高，由多个基础组件组成，可承载当前页的业务接口请求和数据(vuex)。
3. 组件通讯

  - 避免数据的分发源混乱，不建议使用eventBus控制数据，应使用props来和$emit来数据分发和传送。  
  - 同级组件的通讯一般会有一个中间容器组件作为桥梁，容器组件作为数据的接受和分发点。
  
## 性能优化
### 尽量避免重定向
### 减少http请求次数  
80%的响应时间在下载网页内容，减少请求次数是缩短响应时间的关键。  

### 文件压缩
### 异步加载
### 预加载、延后加载、按需加载
### 将样式表置顶
将样式表（css）放在网页的 HEAD 中会让网页显得加载速度更快，因为这样做可以使浏览器逐步加载已将下载的网页内容，这对内容比较多的网页尤其重要。除此之外，有些浏览器会在 CSS下载完成后才开始渲染页面，如果 CSS放在靠下的位置则会导致浏览器将渲染时间推迟。  

## git规范
#### Commit message

  - 提供更多的历史信息，方便快速浏览。
  - 可以过滤某些commit（比如文档改动），便于快速查找信息。
```
提交信息 类型：内容
```

类型详细说明见下表格：  

类型|	用于说明 commit 的类别，只允许使用下面7个标识
---|:--
feat	|新功能（feature）
fix	|修补bug
docs	|文档（documentation）
style	|格式（不影响代码运行的变动）
refactor	|重构（即不是新增功能，也不是修改bug的代码变动）
test	|增加测试
chore	|构建过程或辅助工具的变动

## 相关参考  
[前端规范](https://www.jianshu.com/p/69c228d5bcbe)