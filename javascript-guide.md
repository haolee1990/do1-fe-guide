
原文: https://github.com/ecomfe/spec/blob/master/javascript-style-guide.md

注：部分规范有删改

# JavaScript编码规范



[1 前言](#user-content-1-前言)

[2 代码风格](#user-content-2-代码风格)

　　[2.1 文件](#user-content-21-文件)

　　[2.2 结构](#user-content-22-结构)

　　　　[2.2.1 缩进](#user-content-221-缩进)

　　　　[2.2.2 空格](#user-content-222-空格)

　　　　[2.2.3 换行](#user-content-223-换行)

　　　　[2.2.4 语句](#user-content-224-语句)

　　[2.3 命名](#user-content-23-命名)

　　[2.4 注释](#user-content-24-注释)

　　　　[2.4.1 单行注释](#user-content-241-单行注释)

　　　　[2.4.2 多行注释](#user-content-242-多行注释)

　　　　[2.4.3 文档化注释](#user-content-243-文档化注释)

　　　　[2.4.4 类型定义](#user-content-244-类型定义)

　　　　[2.4.5 文件注释](#user-content-245-文件注释)

　　　　[2.4.6 命名空间注释](#user-content-246-命名空间注释)

　　　　[2.4.7 类注释](#user-content-247-类注释)

　　　　[2.4.8 函数/方法注释](#user-content-248-函数/方法注释)

　　　　[2.4.9 事件注释](#user-content-249-事件注释)

　　　　[2.4.10 常量注释](#user-content-2410-常量注释)

　　　　[2.4.11 复杂类型注释](#user-content-2411-复杂类型注释)

　　　　[2.4.12 细节注释](#user-content-2413-细节注释)

[3 语言特性](#user-content-3-语言特性)

　　[3.1 变量](#user-content-31-变量)

　　[3.2 条件](#user-content-32-条件)

　　[3.3 循环](#user-content-33-循环)

　　[3.4 类型](#user-content-34-类型)

　　　　[3.4.1 类型检测](#user-content-341-类型检测)

　　　　[3.4.2 类型转换](#user-content-342-类型转换)

　　[3.5 字符串](#user-content-35-字符串)

　　[3.6 对象](#user-content-36-对象)

　　[3.7 数组](#user-content-37-数组)

　　[3.8 函数](#user-content-38-函数)

　　　　[3.8.1 函数长度](#user-content-381-函数长度)

　　　　[3.8.2 参数设计](#user-content-382-参数设计)


　　[3.9 面向对象](#user-content-39-面向对象)

　　[3.10 动态特性](#user-content-310-动态特性)

　　　　[3.10.1 eval](#user-content-3101-eval)

　　　　[3.10.2 动态执行代码](#user-content-3102-动态执行代码)

　

[4 浏览器环境](#user-content-4-浏览器环境)

　　[4.1 DOM](#42-dom)

　　　　[4.1.1 DOM 操作](#user-content-424-dom-操作)

　　　　[4.1.2 DOM 事件](#user-content-425-dom-事件)



## 1 前言

本文档的目标是使JavaScript代码风格保持一致，容易被理解和被维护。

## 2 代码风格

### 2.1 文件


##### **【建议】** `JavaScript` 文件使用无 `BOM` 的 `UTF-8` 编码。

解释：

UTF-8 编码具有更广泛的适应性。BOM 在使用程序或工具处理文件时可能造成不必要的干扰。


### 2.2 结构


#### 2.2.1 缩进


#####  使用 `4` 个空格做为一个缩进层级 或 `tab` 字符。



#### 2.2.2 空格


##### **【建议】** 二元运算符两侧必须有一个空格，一元运算符与操作对象之间不允许有空格。

示例：

```javascript
var a = !arr.length;
a++;
a = b + c;
```

##### `,` 和 `;` 前不允许有空格。

示例：

```javascript
// good
callFunc(a, b);

// bad
callFunc(a , b) ;
```

#### 2.2.3 换行


##### 每个独立语句结束后必须换行。

##### **【建议】** 运算符处换行时，运算符必须在新行的行首。

示例：

```javascript
// good
if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
) {
    // Code
}

var result = number1 + number2 + number3
    + number4 + number5;


// bad
if (user.isAuthenticated() &&
    user.isInRole('admin') &&
    user.hasAuthority('add-admin') ||
    user.hasAuthority('delete-admin')) {
    // Code
}

var result = number1 + number2 + number3 +
    number4 + number5;
```


##### **【建议】** 不同行为或逻辑的语句集，使用空行隔开，更易阅读。

示例：

```javascript
// 仅为按逻辑换行的示例，不代表setStyle的最优实现
function setStyle(element, property, value) {
    if (element == null) {
        return;
    }

    element.style[property] = value;
}
```

##### **【建议】** 在语句的行长度超过 `120` 时，根据逻辑条件合理缩进。

示例：

```javascript

// 特别的，对于HTML片段的拼接，通过缩进，保持和HTML相同的结构。
var html = ''
    + '<article>'
    +     '<h1>Title here</h1>'
    +     '<p>This is a paragraph</p>'
    +     '<footer>Complete</footer>'
    + '</article>';

// 也可使用数组来进行拼接，相对 + 更容易调整缩进。
var html = [
    '<article>',
        '<h1>Title here</h1>',
        '<p>This is a paragraph</p>',
        '<footer>Complete</footer>',
    '</article>'
];
html = html.join('');

```

#### 2.2.4 语句


##### **【建议】** 不要省略语句结束的分号。

#####  在 `if / else / for / do / while` 语句中，即使只有一行，也不要省略块 `{...}`。

示例：

```javascript
// good
if (condition) {
    callFunc();
}

// bad
if (condition) callFunc();
if (condition)
    callFunc();
```

#####  函数定义结束不要添加分号。

示例：

```javascript
// good
function funcName() {
}

// bad
function funcName() {
};

// 如果是函数表达式，分号是不允许省略的。
var funcName = function () {
};
```

### 2.3 命名


#####  `变量` 使用驼峰式命名。

示例：

```javascript
var loadingModules = {};
```

##### **【建议】** `常量` 使用 `全部字母大写，单词间下划线分隔` 的命名方式。

示例：

```javascript
var HTML_ENTITY = {};
```

#####  `函数` 使用驼峰式命名。

示例：

```javascript
function stringFormat(source) {
}
```

#####  `类` 使用 `Pascal命名法`。

示例：

```javascript
function TextNode(value, engine) {
    this.value = value;
    this.engine = engine;
}

TextNode.prototype.clone = function () {
    return this;
};
```

### 2.4 注释


##### 多写注释提高代码的可读性，减少维护成本



#### 2.4.5 文件注释


##### **【建议】** 文件顶部包含文件注释，用 `@file` 标识文件说明。

示例：

```javascript
/**
 * @file Describe the file
 */
```

##### **【建议】** 文件注释中可以用 `@author` 标识开发者信息。

解释：

开发者信息能够体现开发人员对文件的贡献，并且能够让遇到问题或希望了解相关信息的人找到维护人。通常情况文件在被创建时标识的是创建者。随着项目的进展，越来越多的人加入，参与这个文件的开发，新的作者应该被加入 `@author` 标识。

`@author` 标识具有多人时，原则是按照 `责任` 进行排序。通常的说就是如果有问题，就是找第一个人应该比找第二个人有效。比如文件的创建者由于各种原因，模块移交给了其他人或其他团队，后来因为新增需求，其他人在新增代码时，添加 `@author` 标识应该把自己的名字添加在创建人的前面。

`@author` 中的名字不允许被删除。任何劳动成果都应该被尊重。

业务项目中，一个文件可能被多人频繁修改，并且每个人的维护时间都可能不会很长，不建议为文件增加 `@author` 标识。通过版本控制系统追踪变更，按业务逻辑单元确定模块的维护责任人，通过文档与wiki跟踪和查询，是更好的责任管理方式。

对于业务逻辑无关的技术型基础项目，特别是开源的公共项目，应使用 `@author` 标识。


示例：

```javascript
/**
 * @file Describe the file
 * @author author-name(mail-name@domain.com)
 *         author-name2(mail-name2@domain.com)
 */
```


## 3 语言特性

### 3.1 变量

#####  变量在使用前必须通过 `var` 定义。

解释：

不通过 var 定义变量将导致变量污染全局环境。


示例：

```javascript
// good
var name = 'MyName';

// bad
name = 'MyName';
```


### 3.2 条件


##### **【建议】** 对于相同变量或表达式的多值条件，用 `switch` 代替 `if`。

示例：

```javascript
// good
switch (typeof variable) {
    case 'object':
        // ......
        break;
    case 'number':
    case 'boolean':
    case 'string':
        // ......
        break;
}

// bad
var type = typeof variable;
if (type === 'object') {
    // ......
} 
else if (type === 'number' || type === 'boolean' || type === 'string') {
    // ......
}
```

### 3.3 循环


##### **【建议】** 不要在循环体中包含函数表达式，事先将函数提取到循环体外。

解释：

循环体中的函数表达式，运行过程中会生成循环次数个函数对象。


示例：

```javascript
// good
function clicker() {
    // ......
}

for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    addListener(element, 'click', clicker);
}


// bad
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    addListener(element, 'click', function () {});
}
```

##### **【建议】** 对循环内多次使用的不变值，在循环外用变量缓存。

示例：

```javascript
// good
var width = wrap.offsetWidth + 'px';
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    element.style.width = width;
    // ......
}


// bad
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    element.style.width = wrap.offsetWidth + 'px';
    // ......
}
```


##### **【建议】** 对有序集合进行遍历时，缓存 `length`。

解释：

虽然现代浏览器都对数组长度进行了缓存，但对于一些宿主对象和老旧浏览器的数组对象，在每次 length 访问时会动态计算元素个数，此时缓存 length 能有效提高程序性能。


示例：

```javascript
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    // ......
}
```



### 3.4 类型


#### 3.4.1 类型检测


##### **【建议】** 类型检测优先使用 `typeof`。对象类型检测使用 `instanceof`。`null` 或 `undefined` 的检测使用 `== null`。

示例：

```javascript
// string
typeof variable === 'string'

// number
typeof variable === 'number'

// boolean
typeof variable === 'boolean'

// Function
typeof variable === 'function'

// Object
typeof variable === 'object'

// RegExp
variable instanceof RegExp

// Array
variable instanceof Array

// null
variable === null

// null or undefined
variable == null

// undefined
typeof variable === 'undefined'
```


#### 3.4.2 类型转换


##### **【建议】** 转换成 `string` 时，使用 `+ ''`。

示例：

```javascript
// good
num + '';

// bad
new String(num);
num.toString();
String(num);
```

##### **【建议】** `string` 转换成 `number`，要转换的字符串结尾包含非数字并期望忽略时，使用 `parseInt`。

示例：

```javascript
var width = '200px';
parseInt(width, 10);
```

#####  使用 `parseInt` 时，请指定进制。

示例：

```javascript
// good
parseInt(str, 10);

// bad
parseInt(str);
```

##### **【建议】** 转换成 `boolean` 时，使用 `!!`。

示例：

```javascript
var num = 3.14;
!!num;
```

##### **【建议】** `number` 去除小数点，使用 `Math.floor / Math.round / Math.ceil`，不使用 `parseInt`。

示例：

```javascript
// good
var num = 3.14;
Math.ceil(num);

// bad
var num = 3.14;
parseInt(num, 10);
```




### 3.5 字符串


##### **【建议】** 字符串开头和结束使用单引号 `'`。

解释：

1. 输入单引号不需要按住 shift，方便输入。
2. 实际使用中，字符串经常用来拼接 HTML。为方便 HTML 中包含双引号而不需要转义写法。

示例：

```javascript
var str = '我是一个字符串';
var html = '<div class="cls">拼接HTML可以省去双引号转义</div>';
```

##### **【建议】** 使用 `数组` 或 `+` 拼接字符串。

解释：

1. 使用 + 拼接字符串，如果拼接的全部是 StringLiteral，压缩工具可以对其进行自动合并的优化。所以，静态字符串建议使用 + 拼接。
2. 在现代浏览器下，使用 + 拼接字符串，性能较数组的方式要高。
3. 如需要兼顾老旧浏览器，应尽量使用数组拼接字符串。

示例：

```javascript
// 使用数组拼接字符串
var str = [
    // 推荐换行开始并缩进开始第一个字符串, 对齐代码, 方便阅读.
    '<ul>',
        '<li>第一项</li>',
        '<li>第二项</li>',
    '</ul>'
].join('');

// 使用 + 拼接字符串
var str2 = '' // 建议第一个为空字符串, 第二个换行开始并缩进开始, 对齐代码, 方便阅读
    + '<ul>',
    +    '<li>第一项</li>',
    +    '<li>第二项</li>',
    + '</ul>';
```

##### **【建议】** 复杂的数据到视图字符串的转换过程，选用一种模板引擎。

解释：

使用模板引擎有如下好处：

1. 在开发过程中专注于数据，将视图生成的过程由另外一个层级维护，使程序逻辑结构更清晰。
2. 优秀的模板引擎，通过模板编译技术和高质量的编译产物，能获得比手工拼接字符串更高的性能。

推荐
- artTemplate: 体积较小，在所有环境下性能高，语法灵活。
- etpl: 体积较小，在所有环境下性能高，模板复用性高，语法灵活。





### 3.6 对象


##### **【建议】** 使用对象字面量 `{}` 创建新 `Object`。

示例： 

```javascript
// good
var obj = {};

// bad
var obj = new Object();
```

##### **【建议】** 不建议修改和扩展任何原生对象和宿主对象的原型。

示例： 

```javascript
// 以下行为绝对禁止
String.prototype.trim = function () {
};
```

##### **【建议】** 属性访问时，尽量使用 `.`。

解释：

属性名符合 Identifier 的要求，就可以通过 `.` 来访问，否则就只能通过 `[expr]` 方式访问。

通常在 JavaScript 中声明的对象，属性命名是使用 Camel 命名法，用 `.` 来访问更清晰简洁。部分特殊的属性(比如来自后端的JSON)，可能采用不寻常的命名方式，可以通过 `[expr]` 方式访问。


示例： 

```javascript
info.age;
info['more-info'];
```

##### **【建议】** `for in` 遍历对象时, 使用 `hasOwnProperty` 过滤掉原型中的属性。

示例：

```javascript
var newInfo = {};
for (var key in info) {
    if (info.hasOwnProperty(key)) {
        newInfo[key] = info[key];
    }
}
```




### 3.7 数组


#####  使用数组字面量 `[]` 创建新数组，除非想要创建的是指定长度的数组。

示例：

```javascript
// good
var arr = [];

// bad
var arr = new Array();
```

#####  遍历数组不使用 `for in`。

解释：

数组对象可能存在数字以外的属性, 这种情况下 for in 不会得到正确结果.

示例：

```javascript
var arr = ['a', 'b', 'c'];
arr.other = 'other things'; // 这里仅作演示, 实际中应使用Object类型

// 正确的遍历方式
for (var i = 0, len = arr.length; i < len; i++) {
    console.log(i);
}

// 错误的遍历方式
for (i in arr) {
    console.log(i);
}
```

### 3.8 函数



#### 3.8.1 函数长度


##### **【建议】** 一个函数的长度控制在 `50` 行以内。

解释：

将过多的逻辑单元混在一个大函数中，易导致难以维护。一个清晰易懂的函数应该完成单一的逻辑单元。复杂的操作应进一步抽取，通过函数的调用来体现流程。

特定算法等不可分割的逻辑允许例外。



#### 3.8.2 参数设计


##### **【建议】** 参数过多时，通过 `options` 参数传递参数。

解释：

有些函数的参数并不是作为算法的输入，而是对算法的某些分支条件判断之用，此类参数建议通过一个 options 参数传递。



### 3.9 面向对象


##### **【强制】** 类的继承方案，实现时需要修正 `constructor`。

解释：

通常使用其他 library 的类继承方案都会进行 constructor 修正。如果是自己实现的类继承方案，需要进行 constructor 修正。


示例：

```javascript
/**
 * 构建类之间的继承关系
 * 
 * @param {Function} subClass 子类函数
 * @param {Function} superClass 父类函数
 */
function inherits(subClass, superClass) {
    var F = new Function();
    F.prototype = superClass.prototype;
    subClass.prototype = new F();
    subClass.prototype.constructor = subClass;
}
```

##### **【建议】** 声明类时，保证 `constructor` 的正确性。

示例：

```javascript
function Animal(name) {
    this.name = name;
}

// 直接prototype等于对象时，需要修正constructor
Animal.prototype = {
    constructor: Animal,

    jump: function () {
        alert('animal ' + this.name + ' jump');
    }
};

// 这种方式扩展prototype则无需理会constructor
Animal.prototype.jump = function () {
    alert('animal ' + this.name + ' jump');
};
```


##### **【建议】** 属性在构造函数中声明，方法在原型中声明。

解释： 

原型对象的成员被所有实例共享，能节约内存占用。所以编码时我们应该遵守这样的原则：原型对象包含程序不会修改的成员，如方法函数或配置项。

```javascript
function TextNode(value, engine) {
    this.value = value;
    this.engine = engine;
}

TextNode.prototype.clone = function () {
    return this;
};
```


### 3.10 动态特性

##### **【建议】** 尽量避免使用 `eval` 函数。


#### 3.10.2 动态执行代码


##### **【建议】** 使用 `new Function` 执行动态代码，代替eval。

解释：

通过 new Function 生成的函数作用域是全局使用域，不会影响当当前的本地作用域。如果有动态代码执行的需求，建议使用 new Function。


示例：

```javascript
var handler = new Function('x', 'y', 'return x + y;');
var result = handler($('#x').val(), $('#y').val());
```


## 4 浏览器环境


#### 4.1.1 DOM 操作


##### **【建议】** 操作 `DOM` 时，尽量减少页面 `reflow`。

解释：

页面 reflow 是非常耗时的行为，非常容易导致性能瓶颈。下面一些场景会触发浏览器的reflow：

- DOM元素的添加、修改（内容）、删除。
- 应用新的样式或者修改任何影响元素布局的属性。
- Resize浏览器窗口、滚动页面。
- 读取元素的某些属性（offsetLeft、offsetTop、offsetHeight、offsetWidth、scrollTop/Left/Width/Height、clientTop/Left/Width/Height、getComputedStyle()、currentStyle(in IE)) 。


##### **【建议】** 尽量减少 `DOM` 操作。

解释：

DOM 操作也是非常耗时的一种操作，减少 DOM 操作有助于提高性能。举一个简单的例子，构建一个列表。我们可以用两种方式：

1. 在循环体中 createElement 并 append 到父元素中。
2. 在循环体中拼接 HTML 字符串，循环结束后写父元素的 innerHTML。

第一种方法看起来比较标准，但是每次循环都会对 DOM 进行操作，性能极低。在这里推荐使用第二种方法。




#### 4.1.2 DOM 事件


##### **【建议】** 优先使用 `addEventListener / attachEvent` 绑定事件，避免直接在 HTML 属性中或 DOM 的 `expando` 属性绑定事件处理。

解释：

expando 属性绑定事件容易导致互相覆盖。


##### **【建议】** 使用 `addEventListener` 时第三个参数使用 `false`。

解释：

标准浏览器中的 addEventListener 可以通过第三个参数指定两种时间触发模型：冒泡和捕获。而 IE 的 attachEvent 仅支持冒泡的事件触发。所以为了保持一致性，通常 addEventListener 的第三个参数都为 false。





