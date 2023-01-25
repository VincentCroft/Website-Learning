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

## 3.标题标签

HTML 中提供了从`<h1>`到`<h6>`六个级别的标题标签，`<h1>`标签的级别最高，`<h6>`标签的级别最低，通过这些标签可以定义网页中的标题（与 word 中的标题类似），合理使用标题可以使网页的层次结构更加清晰。

> 提示：HTML 中的标题可帮助搜索引擎理解网页的结构和内容。

默认情况下，浏览器会以比普通文本更大和更粗的字体显示标题中的内容，使用`<h1>`标签定义的标题字体最大，而使用`<h6>`标签定义的标题字体最小，如下例所示：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HTML标题标签演示</title>
</head>
<body>
    <h1>h1 标题</h1>
    <h2>h2 标题</h2>
    <h3>h3 标题</h3>
    <h4>h4 标题</h4>
    <h5>h5 标题</h5>
    <h6>h6 标题</h6>
</body>
</html>
```

![](http://c.biancheng.net/uploads/allimg/210928/1-21092QP129B5.png)

> 注意：在网页上使用标题标签时，浏览器内置的样式会在每个标题的上下添加一定的空白区域（外边距），您可以使用 [CSS margin](http://c.biancheng.net/css3/margin.html) 属性来调整空白区域的大小。

关于标题标签的使用，有以下几点需要注意：

- HTML 标题标签只能用来定义标题，不可以使用标题标签来对文本进行加粗设计；
- 由于搜索引擎（例如百度）是使用标题来索引网页结构和内容的，因此使用标题标签有利于搜索引擎的抓取；
- 标题标签并不是随意使用的，要根据具体的使用环境，按照级别由高到低的使用标题标签。

> 提示：应该使用`<h1>`标签来标记最重要的标题，该标题通常位于页面顶部，而且一个 HTML 文档中通常应该有且仅有一个`<h1>`标题，至于较低级别的标题标签（例如`<h2>`、`<h3>`、`<h4>`等）的使用则可以不加限制。

## 4.段落标签

HTML 中可以使用段落标签 `<p>`来将文档中的内容分割为若干个段落，语法格式如下：

```html
<p>段落中的内容。</p>
```

段落标签由开始标签`<p>`和结束标签`</p>`组成，开始和结束标签之间的内容会被视为一个段落。段落标签是一个非常基本的标签，我们在网页上发布文章时就会用到它，如下例所示：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HTML段落标签演示</title>
</head>
<body>
    <p>C语言中文网，一个在线学习编程的网站，网址：<a href="http://www.biancheng.net/" target="_blank">http://www.biancheng.net/</a></p>
    <p>C语言中文网目前已经发布了将近 <b>50</b> 套教程，包括 HTML、CSS、JavaScript 等，您可以<a href="http://c.biancheng.net/sitemap/" target="_blank">猛击这里</a>查看所有教程。</p>
    <p>我们的 Slogan：千锤百炼，只为大作；精益求精，句句斟酌；这种教程，看一眼就倾心。</p>
</body>
</html>
```

运行结果如下图所示：

![](http://c.biancheng.net/uploads/allimg/210928/1-21092R02634B5.png)

> 注意：浏览器内置的样式会在段落的上下自动添加一定的空白区域（外边距），您可以使用 [CSS margin](http://c.biancheng.net/css3/margin.html) 属性来设置空白区域的大小。

在 HTML4 以及更早的版本中，可以省略段落标签的结束标签，浏览器会自动补全缺失的结束标签，如下所示：

```html
<p>C语言中文网
<p>HTML教程
<p>http://www.biancheng.net/html/
```

### 4.1段落中空白符

> 默认情况下，段落标签会对文本中的空白符进行合并，将多个连续的空白符显示为一个空格的效果，具体表现为：
>
> - 如果段落中出现多个连续的空格，浏览器会忽略这些空格只保留一个；
> - 如果段落中出现多个连续的换行，浏览器会将这些换行转换成一个空格。

下面通过一个示例来演示段落中的空白符：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HTML段落中的空白符</title>
</head>
<body>
    <p>C语言中文网</p>
    <p>http:            //c.biancheng.net/html/</p>
    <p>
        HTML      教
    程</p>
</body>
</html>
```

运行结果如下图所示：

![](http://c.biancheng.net/uploads/allimg/210928/1-21092R03441438.png)

如果想要在段落中换行，需要使用专门的换行标签`<br />`，`<br />`标签属于自闭和标签，因此不需要对应的结束标签`</br>`，如下例所示：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>使用&lt;br&gt;标签换行</title>
</head>
<body>
    <p>C语言中文网<br />http://c.biancheng.net/html/<br />HTML教程</p>
</body>
</html>
```

运行结果如下图所示：

![](http://c.biancheng.net/uploads/allimg/210928/1-21092R04042Y5.png)

## 5.文本格式化

一些 HTML 标签除了具有一定的语义（含义）外，还有默认的样式，例如`<b>`（加粗）、`<em>`（倾斜）等，通过这些标签我们无需借助 CSS 就可以为网页中的内容定义样式。在这些具有语义和默认样式的标签中，有许多是针对文本的，通过这些标签我们可以格式化文本（为文本添加样式），例如使文本加粗、倾斜或者添加下划线等。

HTML 中有许多用来格式化文本的标签，如下表所示：

|              标签              | 描述                                                         |
| :----------------------------: | ------------------------------------------------------------ |
|          `<b>...</b>`          | 加粗标签中的字体                                             |
|         `<em>...</em>`         | 强调标签中的内容，并使标签中的字体倾斜                       |
|          `<i>...</i>`          | 定义标签中的字体为斜体                                       |
|      `<small>...</small>`      | 定义标签中的字体为小号字体                                   |
|     `<strong>...</strong>`     | 强调标签中的内容，并将字体加粗                               |
|        `<sub>...</sub>`        | 定义下标文本                                                 |
|        `<sup>...</sup>`        | 定义上标文本                                                 |
|        `<ins>...</ins>`        | 定义文档的其余部分之外的插入文本                             |
|        `<del>...</del>`        | 在文本内容上添加删除线                                       |
|       `<code>...</code>`       | 定义一段代码                                                 |
|        `<kbd>...</kbd>`        | 用来表示文本是通过键盘输入的                                 |
|       `<samp>...</samp>`       | 定义程序的样本                                               |
|        `<var>...</var>`        | 定义变量                                                     |
|        `<pre>...</pre>`        | 定义预格式化的文本，被该标签包裹的文本会保留所有的空格和换行符，字体也会呈现为等宽字体 |
|       `<abbr>...</abbr>`       | 用来表示标签中的内容为缩写形式                               |
|    `<address>...</address>`    | 用来定义文档作者的联系信息，被该标签包裹的文本通常会以斜体呈现，并在文本前面换行 |
|        `<bdo>...</bdo>`        | 定义标签中的文字方向                                         |
| `<blockquote>...</blockquote>` | 定义一段引用的文本，例如名人名言，文本会换行输出，并在左右两边进行缩进 |
|          `<q>...</q>`          | 定义一段短的引用，浏览器会将引用的内容使用双引号包裹起来     |
|       `<cite>...</cite>`       | 表示对某个文献的引用，例如书籍或杂志的名称，文本会以斜体显示 |
|        `<dfn>...</dfn>`        | 用来定义一个术语，标签中的文本会以斜体呈现                   |

> 按照作用的不同，可以将这些用来格式化文本的标签分为两类：
>
> - 物理标签：这类标签用来为设置文本的外观；
> - 逻辑标签：这类标签用来赋予文本一些逻辑或语义值。

通过上表可以看出，有些标签的呈现效果虽然相同，但语义却不同，例如`<strong>`和`<b>`标签、`<em>`和`<i>`标签，下面就来详细介绍一下。

### 5.1`<strong>`和`<b>`标签的区别

默认情况下，`<strong>`和`<b>`标签都可以使文本以粗体展示标签中的文本，但是`<strong>`标签的语义是标签中的内容具有很高的重要性，而`<b>`标签的语义仅仅是加粗文本以引起读者的注意，并没有特殊的意思。

示例代码如下所示：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>&lt;strong&gt;和&lt;b&gt;标签演示</title>
</head>
<body>
    <p>当您决定使用C语言中文网，您已经超越了 <strong>90%</strong> 的程序员，请记住网址 <b>http://c.biancheng.net/</b>。</p>
</body>
</html>
```

此处给`90%`添加 <strong> 标签是为了强调C语言中文网的重要性，以及它带来的震撼效果；而给网址添加 <b> 标签仅仅是为了视觉上的加粗效果，这样能引起读者的注意。

运行结果如下图所示：

![](http://c.biancheng.net/uploads/allimg/210928/1-21092R05513Q1.png)

### 5.2`<em>`和`<i>`标记之间的区别

同样，`<em>`和`<i>`标签默认情况下均以斜体显示标签中的文本，但是`<em>`标签具有强调的语义，用来表示标签中的内容很重要，而`<i>`标签仅仅用于定义斜体文本。

示例代码如下：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>&lt;em&gt;和&lt;i&gt;标签演示</title>
</head>
<body>
    <p>当您决定使用C语言中文网，您已经超越了 <em>90%</em> 的程序员，请记住网址 <i>http://c.biancheng.net/</i>。</p>
</body>
</html>
```

同上例一样，给`90%`添加 <em> 标签是为了强调C语言中文网带来的震撼效果，而给网址添加 <i> 标签仅仅是为了引起读者的注意。

运行结果如下图所示：

![](http://c.biancheng.net/uploads/allimg/210928/1-21092R10120Q7.png)

根据 HTML5 的规范，标题应该用`<h1>`~`<h6>`标签定义，被强调的文本应该用`<em>`标签定义，重要的文本应该用`<strong>`标签定义，被标记的或者高亮显示的文本应该用`<mark>`标签定义等等，类似这样的规范还有很多，后面我们会一一为大家介绍。

## 6.超链接标签

在 HTML 中，我们使用 `<a>` 标签来表示超链接。

超链接（Hyperlink）通常简称为链接（Link），是指从一个网页指向另一个目标的连接关系，这个目标可以是另一个网页，也可以是当前网页中的其它位置，还可以是图片、文件、应用程序等。链接的两端分别称为源锚点和目标锚点，通过点击源锚点即可以跳转到目标锚点。

> 超链接是网页中最常见的元素之一，整个互联网都是基于超链接而构建的。网站由众多网页构成，超链接使得网页之间不再独立，它就像一根线，把网页连接在一起，形成一个网状结构。互联网之所以能够称之为“网”，就是因为有超链接的存在。

`<a>` 标签的语法格式如下：

```html
<a href="url"  target="opentype">链接文本</a>
```

其中，href 属性用来指明要跳转到的 url，target 属性用来指明新页面的打开方式，链接文本需要写在 `<a>` 和 `</a>` 之间。

例如，链接到C语言中文网首页，并在浏览器新窗口中打开：

```html
<a href="http://c.biancheng.net" target="_blank">C语言中文网</a>
```

链接到 HTML 教程的第一篇文章，并在当前窗口中打开：

```html
<a href="http://c.biancheng.net/view/7410.html" target="_blank">网站到底是什么</a>
```

### 6.1href属性

> href 属性指定链接的目标，也就是要跳转到什么位置。href 可以有多种形式，例如：
>
> - href 可以指向一个网页（.html、.php、.jsp、.asp 等格式），这也是最常见的形式，例如 href="http://c.biancheng.net/view/1719.html"；
> - href 可以指向图片（.jpg、.gif、.png 等格式）、音频（.mp3、.wav等格式）、视频（.mp4、.mkv格式）等媒体文件，例如 href="/uploads/allimg/181221/134I32557-0.jpg"；
> - href 可以指向压缩文件（.zip、.rar 等格式）、可执行程序（.exe）等，一些下载网站的链接就可以写成这种形式，例如 href="./../uploads/data_package/ComputerFoundation.zip"；
> - href 甚至还可以指向本机的文件，只是很少这样使用，例如 href="D:/Program Files/360/360safe/360Safe.exe"。

你看，href 本质上就是指向一个文件，这个文件几乎可以是任意格式的。如果浏览器支持这种格式，那么它就可以在浏览器上显示，比如常见的图片、音频、视频等，如果浏览器不支持这种格式，那么就提示用户下载。

另外，href 使用的路径可以是绝对路径，也可以是相对路径。绝对路径往往以域名为起点，例如 http://c.biancheng.net/view/1719.html；相对路径往往以当前文件或者当前域名为起点，例如 ./../uploads/data_package/ComputerFoundation.zip。对 URL 结构不了解的读者，请转到《[绝对路径与相对路径](http://c.biancheng.net/view/7538.html)》进行学习。

### 6.2target属性

target 是可选属性，用来指明新页面的打开方式。默认情况下，新页面在当前浏览器窗口中打开，我们可以使用 target 属性来改变新页面的打开方式。常见的打开方式如下表所示：

| target 属性值 |
| :-----------: |

| 属性值  | 说明                                           |
| ------- | ---------------------------------------------- |
| _self   | 默认，在现有窗口中打开新页面，原窗口将被覆盖。 |
| _blank  | 在新窗口中打开新页面，原窗口将被保留。         |
| _parent | 在当前框架的上一层打开新页面。                 |
| _top    | 在顶层框架中打开新页面。                       |

绝大部分情况下，target 属性要么不写，保持默认的 _self，要么将它的值设置为 _blank，在新窗口中打开页面。例如：

```html
<a href="http://c.biancheng.net/html/" target="_blank">HTML教程（新窗口打开）</a>
<a href="http://c.biancheng.net/css3/">CSS教程（当前窗口打开）</a>
```

### 6.3`<a>`标签的默认样式

浏览器会为 <a> 标签设置一些默认样式。

**1) 鼠标样式**

当鼠标移入链接区域时，会变成一只小手；当鼠标移出链接区域时，会变回箭头形状。

**2) 颜色及下划线**

超链接被点击之前为蓝色，超链接被点击之后变成紫色。超链接默认带有下划线，下划线颜色和文本颜色保持一致。 

浏览器根据历史记录来判断超链接是否被点击过，如果 href 属性和历史记录中的某条 URL 重合，那么说明该链接被点击了。清空浏览器的历史记录会让超链接的颜色再次变回蓝色。

【示例】HTML 超链接的多种形式：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HTML &lt;a&gt;标签演示</title>
</head>
<body>
    <p>
        <a href="http://c.biancheng.net/html/" target="_blank">HTML教程（新窗口打开）</a><br>
        <a href="http://c.biancheng.net/css3/">CSS教程（当前窗口打开）</a><br>
        <a href="http://c.biancheng.net/js/">JS教程（被点击过）</a>
    </p>
</body>
</html>
```

运行效果：

![](http://c.biancheng.net/uploads/allimg/210929/1-21092Z9442V60.png)

## 7.插入图片

HTML 使用 `<img>` 标签插入图片，img 是 image 的简称。`<img>` 是自闭和标签，只包含属性，没有结束标签。`<img>` 标签的语法格式如下：

```html
<img src="url" alt="text">
```

> 对属性的说明：
>
> - src 是必选属性，它是 source 的简称，用来指明图片的地址或者路径。src 支持多种图片格式，比如 jpg、png、gif 等。src 可以使用相对路径，也可以使用绝对路径。
> - alt 是可选属性，用来定义图片的文字描述信息。当由于某些原因（例如图片路径错误、网络连接失败）导致图片无法加载时，就会显示 alt 属性中的信息。

【示例】使用 `<img>` 标签插入图片：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HTML插入图片</title>
</head>
<body>
    <!-- 使用绝对路径插入网络图片 -->
    <img src="http://c.biancheng.net/cpp/templets/new/images/logo.jpg?v=3.994" alt="C语言中文网Logo"> <br>
    <!-- 在当前 HTML 文档的上层目录中有一个 images 文件夹，该文件夹下有一张图片 html5.png -->
    <img src="../images/html5.png" alt="HTML5 Logo">
</body>
</html>
```

显示效果：

![](http://c.biancheng.net/uploads/allimg/210929/1-210929102314950.png)

可以看到，图片 html5.png 不存在，加载失败，此时显示出 alt 属性中的文本信息。

### 7.1设置图片的宽度和高度

在 `<img>` 标签中可以使用 width 和 height 属性来指定图片的宽度和高度。默认情况下，这些属性的值都是以像素为单位的。

```html
<img src="./logo.gif" alt="C语言中文网Logo" width="150" height="150">
<img src="./html5.png" alt="HTML5 Logo" width="100" height="100">
```

除此之外，您也可以使用 style 属性指定图片的宽度和高度，如下所示：

```html
<img src="./logo.gif" alt="C语言中文网Logo" style="width: 100px; height: 100px;">
<img src="./html5.png" alt="HTML5 Logo" style="width: 150px; height: 150px;">
```

> 注意:width 和 height 属性只是临时修改图片的尺寸，并不会改变图片原始文件的大小。

关于 width 和 height 属性的两点建议：

- 一般建议为图片设置 width 和 height 属性，以便浏览器可以在加载图片之前为其分配足够的空间，否则图片加载过程中可能会导致您的网站布局失真或闪烁。
- 如果您的页面使用响应式布局（自适应布局），建议在上传图片之前裁剪好尺寸，而不要设置 width 和 height 属性，这样图片能够跟随屏幕宽度自动改变尺寸，从而不会变形，或者超出屏幕宽度。

### 7.2HTML5中的图片属性

有时我们需要按照比例来放大或缩小图片的尺寸以适应不同的设备，避免图片过大超出屏幕的范围，为此 HTML5 中增加了`<picture>`标签，该标签允许您针对不同类型的设备定义多个版本的图片。

在 `<picture>` 标签中包含零个或多个 `<source>` 标签，通过 `<source>` 标签中的 media 属性可以设定匹配条件（允许哪个版本的图片显示），通过 srcset 属性可以定义图片的路径。另外，在 `<picture>` 标签的最后还需要定义一个 `<img>` 标签。如下例所示：

```html
<picture>
    <source media="(min-width: 1000px)" srcset="logo-large.png">
    <source media="(max-width: 500px)" srcset="logo-small.png">
    <img src="logo-default.png" alt="C语言中文网默认Logo">
</picture>
```

浏览器将评估每个 `<source>` 标签，并在其中选择最合适的 `<source>` 标签，如果未找到匹配项，则使用 `<img>` 标签所定义的图片。另外，`<img>` 必须是 `<picture>` 标签的最后一个子元素。

### 7.3图像映射

图像映射允许您在一个图片中定义超链接，实现思想就是在图像中划分一些区域，并在这些区域中定义超链接。例如，我们可以按照地图的划分为每个国家或城市所在的区域定义超链接。

下面通过示例来演示一下：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>HTML图片映射</title>
</head>
<body>
    <img src="logo.png" usemap="#objects" alt="C语言中文网Logo">
    <map name="objects">
        <area shape="rect" coords="0,0,82,126" href="http://c.biancheng.net/html/" alt="HTML教程">
        <area shape="circle" coords="90,58,3" href="http://www.biancheng.net/css3/" alt="CSS教程">
        <area shape="circle" coords="124,58,8" href="http://www.biancheng.net/js/" alt="JavaScript教程">
    </map>
</body>
</html>
```

```
<map> 标签的 name 属性对应的是 <img> 标签的 usemap 属性，<area>标签用于定义图片的可点击区域，您可以在图像中定义任意数量的可点击区域。
```

> 注意：图片映射不能应用于网站导航，因为它对搜索引擎并不友好。图像映射经常与地图一起使用，有许多工具都可以创建图像映射，例如 Adobe Dreamweaver 就可轻松创建图像地图。

### 7.4shape和coords属性

在 <area> 标签中可以通过 shape 属性来定义可点击区域的形状，并通过 coords 属性来定义形状所对应的坐标。其中 shape 属性的可选值有三个，分别是 rect（矩形）、circle（圆形）和 poly（多边形），coords 属性中坐标的值则取决于可点击区域的形状。

假如定义一个矩形的可点击区域，示例代码如下：

```html
<area shape="rect" coords="x1, y1, x2, y2" href="http://c.biancheng.net/" alt="">
```

其中 x1、y1 代表矩形的左上角坐标，x2、y2 代表矩形的右下角坐标。

假如定义一个圆形的可点击区域，示例代码如下：

```html
<area shape="circle" coords="x, y, radius" href="" alt="">
```

其中 x、y 代表圆心的坐标，而 radius 则是圆的半径。

假如定义一个多边形的可点击区域，示例代码如下：

```html
<area shape="poly" coords="x1, y1, x2, y2, x3, y3, ..., xn, yn" href="http://c.biancheng.net/" alt="">
```

其中每对 x 和 y 的值都代表一个多边形的顶点坐标。

> 注意：所有坐标都是相对于图片的左上角来计算的。