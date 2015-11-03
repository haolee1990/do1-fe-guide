# HTML Guide

---

HTML规范指南。

---

## 文档目录

1. [代码风格](#1-代码风格)
2. [属性](#2-属性)
3. [标签](#3-标签)
4. [head设定](#4-head设定)
5. [图片](#5-图片)
6. [表单](#6-表单)
7. [注释](#7-注释)

## 1 代码风格

### 1.1 缩进
使用一个tab作为一个缩进层级或4个空格；


## 2 属性

### 2.1 属性引号

对于html属性使用双引号，请不要使用单引号，不允许不使用引号；

示例：

```html
<!-- bad -->
<img class='avatar' src="./img/avatar.png" alt='avatar'>

<!-- good -->
<img class="avatar" src="./img/avatar.png" alt="avatar">
```

### 2.2 属性大小写

属性名应该小写，不要大写或大小写混合；

示例：

```html
<!-- bad -->
<table cellSpacing="0">...</table>

<!-- good -->
<table cellspacing="0">...</table>
```

**[[⬆]](#)**


## 3 标签

### 3.1 标签大小写

标签名应该小写，请不要大写或大小写混合；

示例：

```html
<!-- bad -->
<DIV clsss="xxx">...</DIV>

<!-- good -->
<div clsss="xxx">...</div>
```

### 3.4 避免过时标签

避免使用过时的旧标签，请使用新标签或者CSS代替：
```html
<!-- bad -->
<big></big>
<font></font>
<center></center>
...
```
请参详：http://www.w3schools.com/tags/


**[[⬆]](#)**


## 4 head设定

### 4.1 doctype

建议使用 HTML5 的 doctype 来启用标准模式。

示例：

```html
<!DOCTYPE html>
```

### 4.2 页面编码

建议使用无 BOM 的 UTF-8 编码；

示例：

```html
<meta charset="UTF-8">
```

### 4.3 兼容模式

建议PC端启用 IE Edge 模式，并针对360浏览器启用webkit渲染模式；

示例：

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="renderer" content="webkit">
```

### 4.4 引入CSS

引入 CSS 时必须指明 rel="stylesheet"；
在 head 中引入页面需要的所有 CSS 资源，因为在页面渲染的过程中，新的CSS可能导致元素的样式重新计算和绘制，页面闪烁；（脚本动态插入的css可以忽略）

### 4.5 引入JavaScript

**【建议】**JavaScript应当放在页面尾部；出于性能方面的考虑，如非必要，请遵守此条建议；

示例：

```html
<body>
    <!-- a lot of elements -->
    <script src="main.js"></script>
</body>
```

**[[⬆]](#)**


## 5 图片

禁止 `img` 的 `src` 取值为空；延迟加载的图片也要增加默认的 `src`；

`src` 取值为空，会导致部分浏览器重新加载一次当前页面，参考 [Yahoo performance rules](https://developer.yahoo.com/performance/rules.html#emptysrc)

建议为重要图片添加 `alt` 属性；

可以提高图片加载失败时的用户体验。

* 用户头像、用户产生的图片等有潜在下载需求的图片，以 img 形式实现，能方便用户下载；
* 无下载需求的图片，比如：icon、背景、代码使用的图片等，尽可能采用 css 背景图实现。


**[[⬆]](#)**


## 6 表单

有文本标题的控件建议使用 `label` 标签将其与其标题相关联；

有两种方式：

1. 将控件置于 label 内;
2. label 的 for 属性指向控件的 id。

推荐使用第一种，减少不必要的 id。如果 DOM 结构不允许直接嵌套，则应使用第二种。

示例：

```html
<label><input name="confirm" type="checkbox" value="on"> 我已确认上述条款</label>

<label for="username">用户名：</label> <input id="username" name="username" type="checkbox">
```

建议在针对移动设备开发的页面时，根据内容类型指定输入框的 `type` 属性；

根据内容类型指定输入框类型，能获得能友好的输入体验。

示例：

```html
<input type="number" value="1">
```

**[[⬆]](#)**


## 7 注释

**【建议】**对**超过10行**的页面模块进行注释, 以降低开发人员的嵌套成本和后期的维护成本。建议使用结尾注释方式，例如：

```html
<!-- 文章内容 start -->
<section id="post">
   do some things...
</section>
<!-- 文章内容 end -->
```

或者标注模块的class或者id：
```html
<!-- #post start -->
<section id="post">
    do some things...
</section>
<!-- #post end -->
```

**[[⬆]](#)**


参考资料： 

1. [Google HTML编码规范](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)
2. [spec HTML编码规范](https://github.com/ecomfe/spec/blob/master/html-style-guide.md)
