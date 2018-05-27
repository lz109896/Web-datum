
#### 第一章：HTML 语法
##### 第一节：认识HTML
```
1.点离开任何网页，右击，都会出现显示“查看源代码”的选项。
```
##### 第二节：HTML 基础结构
```
<!DOCTYPE html>
<html>
<head>
    <title>基本HTML结构</title>
</head>
<body>
    <h1>我是一级标题</h1>
    <p>我是一段文本段落</p>
</body>
</html>

释义：
<!DOCTYPE html>  文档声明，告诉浏览器使用哪个HTML版本进行解析**千万不要忘记**
例如：<!DOCTYPE HTML PUBLIC"-//W3C//DTD HTML 4.01//EN""http://www.w3.org/TR/html4/stritct.dtd">

<html>
......
</html>
属于html 元素，顶级元素或根元素；只能包含 head 元素或者 body 元素

<head>
    <title>基本HTML结构</title>
</head>
属于<head> 元数据
例如：《word 文档》内容：标题、段落....
     元数据就是：文件名、创建时间、修改时间....

title：表示页面的名称是什么。还会显示在标签页的浏览器上<链接>

<body>
    <h1>我是一级标题</h1>
    <p>我是一段文本段落</p>
</body>
body元素:存放页面的内容

```
###### 深入了解 head 元素
```
<head>元素用于定义网页的常规信息和元数据，虽然在网页中不可见，但是也是非常的重要。
（该篇文档对于现在的你可能有点困难，可以先简单过下有个印象，等学完 p3 再回过头来查看）

总得来说其里面的子元素大概分为三类，分别是：
1.描述网页基本信息的，
2.指向渲染网页需要其他文件链接的，
3.各大厂商根据自己需要定制的。

网页基本信息
一个网页，首先得有个标题，就跟人有名字一样。除此之外，还可以根据实际需要补充一些基本信息。

文档标题（浏览器标签中显示的文本）：<title>深入了解 head 元素</title>
编码格式：<meta charset="utf-8">（你可能还看到 gb2312格式，不过不建议使用），
如果你的页面出现乱码，那一般就是编码格式不对
视窗设置：<meta name="viewport" content="width=device-width, initial-scale=1.0">
搜索引擎优化相关内容： <meta name="description" content=“帮助你深层次了解HTML文档结构”>
IE浏览器版本渲染设置：<meta http-equiv="X-UA-Compatible" content="ie=edge">
其他文件链接
一个完整的网页光有 HTML 结构是非常简陋的，就如一个毛坯房。有了结构之后，我们还需要加入样式与行为为网页增添色彩。

指向渲染网页
CSS 文件：<link rel="stylesheet" type="text/css" href="style.css">
JavaScript 文件：<script src=“script.js"></script>

厂商定制
比喻开启双核浏览器先河的360浏览器就定制了一个默认使用哪个内核来渲染页面，
可以设置为 webkit 内核、IE 标准，IE 兼容三种模式。代码分别为：

<meta name="renderer" content="webkit"> <!-- 默认webkit内核 -->     
<meta name="renderer" content="ie-stand"> <!-- 默认IE标准模式 -->
<meta name="renderer" content="ie-comp"> <!-- 默认IE兼容模式 -->
同样分享页面到QQ的聊天窗口，有些页面直接就是一个链接，但是有些页面有标题，图片，还有文字介绍。
为什么区别这么明显呢？其实就是看有没有设置下面这三个内容（具体参阅：腾讯移动WEB开发平台）。

<meta itemprop="name" content="这是分享的标题"/>
<meta itemprop="image" content="http://imgcache.qq.com/qqshow/ac/v4/global/logo.png" />
<meta name="description" itemprop="description" content="这是要分享的内容" />
还有IOS也定制了一些移动开发设置如下：

<meta name="apple-mobile-web-app-capable" content="yes" /> 
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<link rel="apple-touch-icon" href="touch-icon-iphone.png">
<link rel="apple-touch-startup-image" href="/startup.png">

```
##### 第三节： HTML元素
###### HTML元素
```
元素是什么？
一个成对出现的结构称之为元素

```
![HTML元素图解](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/a551fd44fc276c0507a3b017c347143a1278f99d/20180516.png)
```
并不是所有的元素都是成对出现的
一般来说元素由开始标签、内容及结束标签构成，而开始标签可以添加一些属性来修饰元素。
但是也有一些元素只有开始标签，没有结束标签，这种元素可称为空元素，如 img 元素。
例如：以下单标签
<img src="image.jpg">   img元素（没有结束标签）

```
###### HTML注释
```
<!-- 标题，请勿改动-->
<!-- 由于版本升级，下卖弄这段内容暂时不用 -->
<!-- todos: 这段代码需要优化下 -->

注释内容：标题，请勿改动(给程序员看的)

<h1>我是h1标题</h1>
注释内容：标题说明

<div class="">...</div>

<！-- <p>我是一段暂时不用的内容</p> -->
注释内容:注释一段内容
```
###### HTML 属性
```
HTML 属性
为了表示元素的一些特征，我们可以在开始标签中添加一些属性。如下：
```
![HTML 属性](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/335d4c55cecaf0ec3d7ec9ec5049909ee0240880/20180516125118.png)

```
属性特征
一般属性都具有以下特征：

每个属性之间或与元素名之间都有一个空格隔开
属性名后面紧跟等号
属性值必须使用双引号包裹
但也有一些属性只有属性名，没有属性值，这种属性我们称之为布尔属性，
如下disabled就是布尔属性，表示是否禁用，有该属性则为禁用：

<input type="text" disabled>
除此之外，我们还可以自定义属性来存储我们的一些数据以便 JS 使用。
具体可参考：HTML data-* 属性。（我们后面的课程会讲解，先不用纠结）

属性分类
属性有很多种，从使用来说大概可以分为三类：

可以用于每个元素的全局属性，如class属性
可用于某一类元素的，如form表单相关元素的name、value属性
只用于某一个元素的，如alt属性只用于img元素
这里我们先介绍几个常用的全局属性，其他得两种属性我们在稍后的相关课程将会说明。

class
用来设置元素的一个或多个类名，这样以后的 CSS 或 JS 就可以方便对该元素进行操作。具有以下特点：
类名不能以数字开头（一定要牢记）
类名可以设置多个值，以空格分开，如<div class="box box--menu"></div>
不同的元素可以有相同的类名
简单示例如下：
<p class="p1 red">文本段落</p>
<div class="red">我也有一个类名为red</div>

id
设置元素的唯一性，经常用于 JS 操作或 CSS 操作，也可用作定义锚点。具有以下特点：
在整个 HTML 文档中必须是唯一的，也就是说一个 HTML 文档中不能出现两个一样的id值
不可以和 class 那样设置多个值
简单示例如下：
<p id="text">文本段落</p>
<div id="block">区块内容</div>

title
用来设置元素的额外信息，鼠标滑过元素暂停一会会显示 title 属性的内容。大概效果如下图：
简单示例如下：
<a title="全部的链接文字" href="#">链接文字很多...</a>

style
用于设置元素的行内样式，一般用于 JS 动态改变元素的样式。(以后讲 CSS 的时候会详细介绍)
简单示例如下：
<div style="display: none;">我是隐藏的区域，可以通过JS来切换显示</div>
<p style="width: 500px;">设置宽度为500px</p>
更多全局属性参考
HTML 全局属性 | W3school
HTML 全局属性 | MDN
另附 HTML 属性参考手册一份：HTML 属性参考。
```
##### 常用基本元素
```
HTML 定义了各种元素，每个元素都起着不同的作用。一时半会是记不住那么多的，不过我们可以先了解熟悉最常用的一些
（HTML 5 语义化标签我们第三章再介绍），然后其余的可以查阅下面的 MDN 或 W3school 的参考手册。
```
HTML 元素参考 | MDN
HTML 参考手册 | w3school
```
从上面两个参考手册，我们会发现，MDN 的叫法是元素，而 W3school 的叫法是标签，这两者都有什么区别呢？
前面我们也讲过，元素一般是由开始标签、内容和结束标签组成的。所以严格来说，单纯的<p>就是标签，
而<p>一个段落</p>则是元素。不过一般标签和元素这两个都是混着叫，所以叫什么不重要，
重要的你是你要理解它们的本质区别就可以了。
```
标题(Headding)元素
```
<h1>、 <h2>、 <h3>、 <h4>、 <h5>、 <h6>标签用来定义标题，其大小依次减小，<h1>为最大的标题，<h6>为最小的标题。
实例如下：
<h1>这是标题 1</h1>
<h2>这是标题 2</h2>
<h3>这是标题 3</h3>
<h4>这是标题 4</h4>
<h5>这是标题 5</h5>
<h6>这是标题 6</h6>
注意：标题具有明确的语义性，请根据文档结构合理使用，而不要只是用来标识字体大小。

下面让我们来创建一个博客文章标题：
<h1>H5活动宣传页通用布局技术解决方案</h1>
```
段落(Paragraph)元素
```
<p>标签定义段落，每一个<p>标签默认都另起一行。

实例如下：
<p>这是段落文字</p>
<p>这是另一个段落文字，另起一行开始</p>

下面让我们来创建几个博客文章段落：
<p>一般来说，活动宣传页都是全屏的滑动，而移动端的视窗大小确实是有点零碎化，
于是将内容在不同的手机上良好展示出现就显得有点挑战了。</p>
<p>本文旨在通过对一个个疑难点进行攻克而形成一种通用解决方案。</p>
```
图片(image)元素
```
<img>标签用来在网页中嵌入图片，该标签没有结束标签。（如这种只有一个标签的元素都可以称之为“空元素（empty element）”）
<img>标签有两个必需的属性：src属性 和 alt 属性。其中src属性为图片地址，alt属性为如果图片加载失败显示的替换文字。

实例如下：
<img src="//placehold.it/300" alt="我是图片加载失败后显示的文字">
除了必须属性外，还可以添加控制大小的属性width和height，如下：

<img src="//placehold.it/300" alt="我是图片加载失败后显示的文字" width="150" height="150">
下面让我们来添加一个博客图片：

<img src="imweb-logo.png" alt="IMWeb 学院">
```
链接(anchor)元素
```
<a>标签定义超链接，用于网页之间的跳转（从一个网页到另一个网页），它有一个重要的属性href，用来指定链接的目标。
实例如下：
<a href="http://imweb.io">我是一个超链接，指向IMWeb学院</a>
如果需要新标签页打开，则要添加另一个属性target，如下：

<a href="http://imweb.io" target="_blank">我是一个超链接，指向IMWeb学院</a>
如果图片也需要超链接，则可以通过元素嵌套实现，如下：

<a href="http://imweb.io" target="_blank">
    <img src="imweb-logo.png" alt="IMWeb 学院">
</a>
下面让我们来添加一个博客文字链接：

<p>我们打算使用现有的动画库<a href="https://github.com/daneden/animate.css/">animate.css</a>来实现我们的动画效果</p>
```
列表(list)元素
```
列表分为无序(unorder list)列表及有序(order list)列表两种，其中无序列表标签为<ul>，
有序列表标签为<ol>，其直接的子元素标签为<li>(不能是其他标签)
如我们要实现WEB三大语言的列表，因为这三大语言没有严格的顺序关系，所以采用无序列表来实现，如下：

<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JS</li>
</ul>
ul元素下面只能放li元素，有归属关系

如我们要实现把大象装进冰箱的步骤列表，有严格的顺序要求，则采用有序列表来实现，如下：

<ol>
    <li>首先把冰箱门打开</li>
    <li>然后把大象关进去</li>
    <li>最后把冰箱门关上</li>
</ol>
下面让我们来添加一个博客的标签列表：

<ul>
    <li>CSS</li>
    <li>响应式</li>
    <li>移动端重构</li>
</ul>
```
div (division)元素
```
<div>标签用来分割为独立的、不同的部分，每一个<div>标签默认都另起一行。

如我们要创建一个区块，包含<h2>和<p>元素：

<div>
    <h2>区块标题/h2>
    <p>区块描述文字</p>
</div>
下面我们来添加一个博客发表的相关内容：

<div>
    <p>作者：xxx</p>
    <p>发布时间：xx-xx-xx</p>
    <p>浏览量：xxxx</p>
</div>
```
span 元素
```
<span>标签被用来组合文档中的行内元素。如下：

<p>前端三大语言：<span>HTML</span>、<span>CSS</span>、<span>Javascript</span></p>
下面我们来用<span>元素对博客发表的相关内容进一步改造：

<div>
    <p><span>作者：</span><span>xxx</span></p>
    <p><span>发布时间：</span><span>xx-xx-xx</span></p>
    <p><span>浏览量：</span><span>xxxx</span></p>
</div>
```
换行元素
```
标签可插入一个简单的换行符，它是个空元素，没有结束标签，不包含任何内容。所以</br>或换行</br>都是错误的。
正确的用法应该是

与<p>的区别在于，它只是简单地开始新的一行，不包含任何内容，而<p>标签一般是有内容的，
且浏览器默认会在相邻的段落之间插入一些垂直的间距。

简单实例如下：

<p>第一行内容 
 第二行内容</p>
参考资料
最后除了上面的 HTML 参考手册外，如果你的英文还不错的话，建议阅读下 HTML 元素的 wiki 文档：HTML element - 
```
##### HTML 字符实体

预留字符
```
在 HTML 中，某些字符是预留的不能直接使用，如小于号（<）和大于号（>），直接使用会误认为它们是标签。

所以如果我们希望正确地显示预留字符，那必须在 HTML 源代码中使用字符实体（character entities），
如可以使用&lt;表示小于号（<），&gt;表示大于号（>）。
```
空格
```
浏览器总是会截短 HTML 页面中的连续空格。所以如果你在HTML代码中连续输入多个空格，最后也只会显示一个空格。

那么如何才能实现连续多个空格呢？这就需要用到我们的&nbsp;字符实体了。

简单示例如下：

<p>空格            好多啊，但是只显示成一个</p>
<p>空格&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;好多啊，全部显示</p>
常用字符实体
字符实体可以有两种方法表示：一种为实体名称，一种为实体编号。如小于号（<）既可以用实体名称&lt;表示，
也可以用实体编号&#60;表示。
```
常用几个字体字符如下：

显示结果|	描述	|实体名称|	实体编号
------ | ------ | ------ | ---------
            空格	  &nbsp;   &#160;
            空格    &nbsp;   &#160;
<	       小于号	  &lt;     &#60;
>	       大于号    &gt;     &#62;
&	        和号     &amp;    &#38;
©	版权（copyright） &copy;   &#169;
×	        乘号	   &times;  &#215;

```
更多可参看：HTML Symbol Entities Codes
```
块级元素
```
默认占据整行宽度
p,div,hn,ul/ol,li....
```
行内元素
```
同行显示
默认宽度由内容决定
a,span,img,em....
```
块级元素默认会占据整行宽度，且每个块级元素都会新起一行；而行内元素默认会与其他行内元素同行显示，
且宽度由内容多少决定。
```
该分类方式跟 CSS 相关（后面 CSS 部分会详细介绍），更多关于块级元素与行内元素介绍可参考 MDN 的
块级元素和行内元素。

除此之外，我们还可以把元素分为替换元素（replaced element）和非替换元素（non-replaced element），
英文解释如下：

A replaced element is any element whose appearance and dimensions are defined by an
external resource. Examples include images (<img> tags), plugins (<object> tags), and 
form elements (<button>, <textarea>, <input>, and <select> tags). All other elements 
types can be referred to as non-replaced elements.

更多可参考 MDN 的可替换元素
```
#### 第四节：嵌套及 HTML树

![HTML树.](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/117a9b9043102c307bbdfba4400fb5f084ea5a93/HTML%20%E6%A0%91.png)
![html嵌套](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/bc23a6d058ef52d0386cc4f9713dd998ee3d62cc/html%20%E5%B5%8C%E5%A5%97.png)

#### 第五节：专业级开发环境
##### 编辑器：sublimetext
```
1.代码高亮
2.错误提示
3.格式化
4.自动完成
.....

下载网址：http://www.sublimetext.com/
扩展名：必须是  .html

绝对不要使用 WPS word 文本来写代码，属于副文本，有隐藏的字符
不建议使用记事本编写代码，可以运行但，功能太弱

IDE  集成开发环境
工具：Xcode、 Visual STUDIO 、WebStorm.
```
###### 浏览器介绍
```
不同于其他语言的开发，前端开发并不需要一个专门的编译器来编译自己的代码，你只需要将你的网页在浏览器上打开，
浏览器就可以自动编译你的代码了。这确实是一件十分酷的事，因为这意味着你无需额外安装任何软件，只要在编辑器
中写下你的代码并保存，然后双击你的 html 文件就可以自动启用默认浏览器打开你的网页。

虽然所有的浏览器基本上都能编译你的网页，但不同的浏览器能够兼容的 HTML / CSS / JavaScript 特性也不尽相同，
对网页的渲染方式也有一些小差异。这意味着在开发过程中，我们需要在不同浏览器中对网页的兼容性进行测试。

当然，现在我们暂时不需要做这些工作，这里我们只是简单介绍下浏览器，让你有个大概的了解。
```
Chrome
```

目前全球占比最大的浏览器。支持全平台，不仅界面简洁，插件丰富，
还提供了强大的开发者工具让开发效率得到巨大的提高。

你可以从Chrome官网下载，若无法访问官网，可使用 腾讯电脑管家 或者其他软件管理工具下载。

如果你的默认浏览器还不是Chrome，可以参考：怎样把谷歌浏览器设置为默认浏览器。

注：如果你还没有安装或设置为默认，那么赶紧搞起吧，这样就可以更好的体验我们后面的课程了。
```
IE / Edge

```
Windows 系统默认的浏览器，有 IE6-11，总共6个版本（尤其是 6-8 这三个版本，因为过于古老所
以功能方面非常落后，幸好正在慢慢退出历史舞台），不过从 Windows 10 系统起就换成 Edge 版本了。

从前的很长一段时间 IE 浏览器都处在绝对的领先地位，后来由于新技术的不断发展而 IE 浏览器版本迭代太慢，
所以慢慢就被抛弃了。
```
Firefox
```

经典的浏览器，也是众多开发者的选择。支持全平台，有丰富而强大的插件，也提供了很不错的开发者工具供开发者们使用。
还有一个非常好用的开发文档：Mozilla Developer Network（简称 MDN）（后面的课程会经常用到这个开发文档）

同样你可以从官网下载，或使用其他软件管理工具下载。

虽然这款浏览器也比较好用，但是一直处于不温不火的状态，以前是 IE 压制，现在是 Chrome 天下，所以它的地位非常尴尬，
但是这并不影响它也是一款非常优秀的浏览器。

其他浏览器
其他浏览器包括 Safari、QQ 浏览器、360浏览器、搜狗浏览器等。

首先 Safari 是 macOS 或 iOS 的默认浏览器，并不支持其他平台，所以并不推荐为前端开发首先，而且其跟 Chrome 
都是基于 Webkit 内核的，所以有很多相似点。

而国产的一些浏览器一般都是套了个壳的双核浏览器（浏览器内核介绍），如 QQ 浏览器，360浏览器、搜狗浏览器，
猎豹浏览器等，一般只用来测试兼容性（因为你的用户在用这些浏览器）。
```
###### 路径指南

认识路径
```
首先，你以前肯定接触过路径，如你电脑中的某个文件 E:\娱乐\音乐\蓝莲花.mp3，或者你在网上看到的某个图片 
https://8.url.cn/edu/download/images/s-3-bg.86430f50.jpg，这些都是路径。

而我们在前面学习的<a>元素和<img>元素，说到的链接地址（href属性）和图片地址（src属性），
这两个属性的值也是路径，如下：

<a href="http://imweb.io" target="_blank">
 <img src="imweb-logo.png" alt="IMWeb 学院">
</a>
```
路径介绍
```
简单来说，路径就是指向资源的存放位置，资源可以是各种文件，图片，视频等。这跟实际生活中我们
经常以地址来描述一个位置一样。
```
路径分为绝对路径和相对路径。
```
绝对路径：以站点根目录为参考基础的路径。
相对路径：由文件本身所在的路径引起的跟其它文件（或文件夹）的路径关系。
以我们现实生活中地址为例来说，如果我们要描述腾讯大厦的位置就可以说“中国广东省深圳市南山区
高新科技园中区一路腾讯大厦”，也可以说万利达大厦旁边的大厦。前者就是绝对地址，后者就是一个相对地址。

现在如果要在img.html文件中引入一个图片（img-style.png）和一个样式文件（style.css）：

如果以相对路径来引入的话，我们可以写成：

图片：../../img/img-style.png
样式：style.css或./style.css
```
在使用相对路径时，我们用符号“./”来表示当前目录，用符号“../”来表示当前目录的父目录。
```
现在我们解释下上面的相对路径：

img.html在exercises目录，那么它的父目录就是p2，父目录的父目录就是Front-end目录，
于是先通过../../两个父目录找到Front-end目录，而img-style.png在img目录，img目录在Front-end目录中，
于是img-style.png相对于img.html的相对路径就是../../img/img-style.png
而style.css和img.html在同一个目录，所以可以直接使用style.css或./style.css来表示
如果以绝对路径来引入的话，我们可以写成：

图片：/img/img-style.png
样式：/p2/exercises/style.css
在使用绝对路径时，我们使用"/" 代表根目录，Front-end站点目录内部所有文件都可以使用“/”表示根目录Front-end。

但是如果是其他站点要访问该目录时，则需要加上我们的域名地址，以图片为例，
其绝对地址为：http://coding.imweb.io/img/img-style.png。

如果以本地文件与网络文件为区分的话，我们的路径还可以分为本地路径及网络路径。

同样以刚才的图片为例，我们如果在本地浏览器中打开，则地址显示如下：



而如果我们访问线上地址，则地址显示如下：



如第一个本地路径，你电脑里面的文件我是打开不了，我电脑里面的文件同样你也打开不了，所以如果我们要互相
都可以访问的话，那就只好上传到网上了，这样大家都可以访问。

注：本地路径方面，如在磁盘里面访问，Windows 约定使用反斜线 () 作为路径中的分隔符，如"E:\娱乐\音乐\蓝莲花.mp3"；
而UNIX系统使用正斜线（/），如“/ users / marvin / music /蓝莲花.mp3”。
```

#### 第六节:项目提交

1.注册关联gitimwed
2.派生（fork）老师的项目到自己的仓库






















