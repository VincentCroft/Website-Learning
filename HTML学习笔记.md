# HTML学习笔记

## 1.标签的语法格式

HTML 中的标签就像关键字一样，每个标签都有自己的语义（含义），例如`<p>`标签代表段落，`<b>`标签代表加粗。根据标签的不同，浏览器会使用不同的方式展示标签中的内容。

在实际开发中，有时我们也将 HTML 标签称为 HTML 元素。

一般情况下，一个 HTML 标签由开始标签、属性、内容和结束标签组成，标签的名称不区分大小写，但大多数属性的值需要区分大小写，如下所示：

```html
	      属性
	       ↓
<div class="foo">C语言中文网</div>
 ↑                    ↑     ↑
开始标签              内容   结束标签
```

除了 class 属性外，开始标签中还可以包含其它属性信息，比如 id、title 等，这些我们会在后面进行讲解。

> 注意，虽然 HTML 标签在语法上不区分大小写，但是为了规范和专业，强烈建议在定义标签时一律采用小写。

当使用浏览器打开我们编写的 HTML 文档时，浏览器会从上到下依次读取文档中的内容，并根据 HTML 标签和属性将标签中的内容呈现在浏览器中。

> 一个 HTML 文档中必须具有一些基本的标签，以便浏览器区分普通文本和 HTML 文档。您可以根据想要实现的效果使用任意数量的标签，但有以下几点需要注意：
>
> - 所有 HTML 标签都必须放在尖括号`< >`内；
> - HTML 中不同的标签可以实现不同的效果；
> - 如果使用了某个标签，则必须使用对应的结束标签来结尾（自闭合标签除外）。

有一些 HTML 标签没有单独的结束标签，而是在开始标签中添加`/`来进行闭合，这种标签称为自闭合标签。请看下面的例子：

```html
<img src="./logo.png" alt="C语言中文网Logo" />  <!-- 图像 -->
<hr />  <!-- 分割线 -->
<br />  <!-- 文本换行 -->
<input type="text" placeholder="请输入内容" />  <!-- 文本输入框 -->
```

### 1.1自闭和标签

自闭合标签不用包围内容，所以不需要单独的结束标签。只有少部分 HTML 标签是自闭合的。

> <!-- --> 表示 HTML 注释，用来对 HTML 代码进行说明，浏览器会忽略注释内容，所以用户在网页中看不到注释，我们将会在《HTML注释》中详细讲解。

### 1.2嵌套HTML标签

大多数 HTML 元素都是可以嵌套使用的，也就是说一个 HTML 标签中可以包含其他的 HTML 标签，我们编写的 HTML 文档就是由相互嵌套的 HTML 标签构成，如下例所示：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HTML标签的嵌套</title>
</head>
<body>
    <h1>C语言中文网<font size="4" color="#666">简介</font></h1>
    <p>
        C语言中文网，一个在线学习<b>编程</b>的网站，目前已经发布了将近 <font color="red">50<sup>①</sup></font> 套教程，包括<i>C语言</i>、<i>C++</i>、<i>Java</i>、<i>Python</i> 等，请<a href="http://c.biancheng.net/sitemap/" target="_blank">猛击这里</a>查看所有教程。
        <hr />
        <small>注①：C语言中文网会持续更新优质教程，教程数量将远远超过 50 套。</small>
    </p>
</body>
</html>
```

> 对代码的说明：
>
> - 第 8 行代码，在 <h1> 标签中嵌套了 <font> 标签。<font> 标签用来设置文本样式，此处我们使用 size 属性设置了文本大小，使用 color 属性设置了文本颜色。
> - 第 9~13 行代码，在 <p> 标签中嵌套了多种标签，其中：
>   - <b> 标签用来加粗文本。
>   - <sup> 标签用来设置上角标。
>   - <i> 标签用来设置斜体文本。
>   - <a> 标签用来设置超链接，其中 target 属性用来指明打开方式，`_blank`表示从新标签中打开。
>   - <hr> 标签用来设置分割线，它是一个自闭合标签。
>   - <small> 标签用来呈现小号字体。

> 注意：<font> 是一种不被建议使用的标签，HTML 5 已经不再支持，请尽量使用CSS来设置文本样式。

HTML 标签的嵌套层次是没有限制的，但是我们应尽量保持 HTML 文档的简洁。上面代码中嵌套层次最深的标签是 <sup>，它的嵌套路径为：

```
body -> p -> font -> sup。
```

以上代码结果如下图所示：

![](http://c.biancheng.net/uploads/allimg/210927/1-21092G51236392.png)

## 2.属性的概念和使用

> 通过前面的学习，我们已经对 [HTML 标签](http://c.biancheng.net/view/9382.html)有了简单的认识，知道可以在标签中可以添加一些属性，这些属性包含了标签的额外信息，例如：
>
> - href 属性可以为 <a> 标签提供链接地址；
> - src 属性可以为 <img> 标签提供图像的路径；
> - style 属性可以为几乎所有标签定义 CSS 样式。

本节我们就来讲解一下 HTML 标签属性的概念和用法。

属性可以为 HTML 标签提供一些额外信息，或者对 HTML 标签进行修饰。属性需要添加在开始标签中，语法格式为：

```html
attr="value"
```

attr 表示属性名，value 表示属性值。属性值必须使用双引号`" "`或者单引号`' '`包围。

> 注意:虽然双引号和单引号都可以包围属性值，但是为了规范和专业，请尽量使用双引号。

一个标签可以没有属性，也可以有一个或者多个属性。

使用 HTML 属性的例子：

```html
<p id="user-info" class="color-red">欢迎 <font color="red" size="3">Tom</font> 来到C语言中文网，您已经使用本站 3 年了，这是您第 12 次登录。<p>
<div class="clearfloat">
    <p class="left">这里显示 Tom 的账号信息</p>
    <p class="right">这里显示 Tom 的个性签名</p>
</div>
```

### 2.1专用属性

> HTML 属性有很多，大体可以分为两类：
>
> - 有些属性适用于大部分或者所有 HTML 标签，我们将这些属性称为通用属性；
> - 有些属性只适用于一个或者几个特定的 HTML 标签，我们将这些属性称为专用属性。

HTML 中的 <img> 标签就有 src 和 alt 两个专用属性，<a> 标签也有 href 和 target 两个专用属性，如下例所示：

```html
<img src="./logo.png" alt="C语言中文网Logo" width="100" height="50">
<a href="http://c.biancheng.net/" target="_blank">C语言中文网</a>
```

> 对代码的说明：
>
> - <img> 标签中的 src 属性用来定义图像的路径，alt 属性用来定义图像的描述信息，当图像出现异常无法正常显示时就会显示 alt 中的信息。
> - <a> 标签的 href 属性用来定义链接的地址，target 属性用来定义新页面在浏览器中的打开方式。

### 2.2自定义属性

除了自带的属性，HTML 也允许我们自定义属性，这些属性虽然可以被浏览器识别，但是并不会添加什么特殊效果，我们需要借助 CSS 和 JavaScript 处理自定义属性，为 HTML 标签添加指定样式或者行为。

例如，[C语言中文网首页](http://c.biancheng.net/)的顶部板块为了在手机端实现标签切换（tab 切换）效果，就为 <li> 和<div> 标签添加了一个自定义属性`tabno`，用以指明当前 tab 的编号，请看下图：

![](http://c.biancheng.net/uploads/allimg/210927/1-21092G6134E51.png)

### 2.3通用属性

HTML 标签中有一些通用的属性，如 id、title、class、style 等，这些通用属性可以在大多数 HTML 标签中使用，下面来简单介绍一下它们的用法。

#### （1) id

id 属性用来赋予某个标签唯一的名称（标识符），当我们使用 CSS 或者 JavaScript 来操作这个标签时，就可以通过 id 属性来找到这个标签。
为标签定义 id 属性可以给我们提供很多便利，比如：

- 如果标签中带有 id 属性作为唯一标识符，通过 id 属性可以很方便的定位到该标签；
- 如果 HTML 文档中包含多个同名的标签，利用 id 属性的唯一性，可以很方便的区分它们。

> 注意：在一个 HTML 文档中 id 属性的值必须是唯一的。

示例代码如下所示：

```html
<input type="text" id="username" />
<div id="content">C语言中文网</div>
<p id="url">http://c.biancheng.net/</p>
```

#### （2）class

与 id 属性类似，class 属性也可以为标签定义名称（标识符），不同的是 class 属性在整个 HTML 文档中不必是唯一的，我们可以为多个标签定义相同的 class 属性值。另外，还可以为一个 HTML 标签定义多个 class 属性值，如下所示：

```html
<div class="className1 className2 className3"></div>
<p class="content">C语言中文网</p>
<div class="content">http://c.biancheng.net/</div>
```

当使用 CSS 或者 JavaScript 来操作 HTML 标签时，同样可以使用 class 属性来找到对应的 HTML 标签。由于 class 属性不是唯一的，所以通过 CSS 或 JavaScript 对 HTML 标签的操作会应用于所有具有同名 class 属性的标签中。

#### （3）title

title 属性用来对标签内容进行描述说明，当鼠标移动到该标签上方时会显示出 title 属性的值，如下例所示：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>演示文档</title>
</head>
<body>
    <a href="http://c.biancheng.net/html/" title="HTML教程">HTML教程</a>
</body>
</html>
```

运行结果如下图所示：

![](http://c.biancheng.net/uploads/allimg/210927/1-21092G6293W10.png)

> 注意:将鼠标在链接处悬停片刻才能看到提示框。

#### （4）style

使用 style 属性我们可以在 HTML 标签内部为标签定义 CSS 样式，例如设置文本的颜色、字体等，如下例所示：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>演示文档</title>
</head>
<body>
    <p style="color:red;">http://c.biancheng.net/html/</p>
    <img src="./logo.png" style="height:50px;" alt="C语言中文网LOGO">
    <div style="padding:10px;border:2px solid #999;text-align:center;">C语言中文网</div>
</body>
</html>
```

运行结果如下图所示：

![](http://c.biancheng.net/uploads/allimg/210927/1-21092G63633593.png)

除了上述的属性外，HTML 中的属性还有许多许多，这里简单了解一下即可，后面我们会详细介绍。