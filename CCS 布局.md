#### 第一节：CSS 布局简介
tab 布局过时了

#### 第二节：HTML 布局义化
```
1.方便团队开发与维护
2.有利于SEO(搜索引擎)
3.屏幕阅读软件（盲人）会根据结构来读页面

例如下面的语句：
<div class="header"></div>

<div class="container">
    <div class="aside"></div>
    <div class="main"></div>
</div>

<div class="footer"></div>

义化后的语句：
<header class="header"></header>

<div class="container">
    <daside class="aside"></div>
    <main class="main"></main>
</div>

<foote class="footer"></foote>

更加简介明了，头部尾部一目了然
```


```
深入理解 HTML 语义
HTML 语义当然不仅仅只是几个 HTML 语义标签。

从“文档”说起
很多时候我会把“页面”和“文档”这两个词混着用，比如将 HTML 页面说成“HTML 文档”。

HTML 就是文档，最开始的《Web 简史》中我们有提到过，万维网的雏形是一个文档共享系统，
万维网就是一个放大版的文档共享系统。只是随着 Web 的发展，各种酷炫的页面和应用层出不穷，
倒是让新入行的小伙伴忽略了，HTML 的本质其实是文档（document）。

现实生活中，说到文档，我们的第一反应就是 Microsoft Word ，
其实 Word 当年也有可能成为 Web 标准，当然这是另外一个故事。

文档大纲
所以我们从 Word 说开去，希望你 Word 用的很顺溜哦。

Word 中的标题有一级标题、二级标题……的说法，所有的标题就构建出了这个 Word 文档的大纲。

在 HTML 文档中呢，H1 ~ H6 就是一级到六级标题，它们构成了 HTML 文档的大纲。
腾讯网首页的文档大纲。一个好的页面，必定先是一个好文档，好文档必然有着严谨的文档大纲。

这个是谷歌浏览器查看页面文档大纲的插件，html5-outliner 。

再来看“万维网”
最初的万维网是一个文档共享的网络，现在的万维网则是一个资源共享的网络，包括图片、多媒体等等。

HTML 则是万维网的粘合剂，也是万维网的载体，但是现在 HTML 给我们的感觉啊，就是给人看的，
其实，HTML 同时也会给机器看，比如下图，除了 human 在读 HTML ，各式各样的机器也在读 HTML ，
比如搜索引擎的爬虫和读屏设备。

视觉上的各种酷炫会给人以视觉冲击，但对机器来说，并没有什么用，它们更看重的是语义，这样才能更好地解析内容。
这也是为什么样式会从结构里面分离出来的原因之一。

现在才到 HTML 语义
本文的开头就提到了，HTML 语义当然不仅仅只是几个 HTML 语义标签。在 HTML 本身这个层面上，
语义也有更多的东西，关于这些已经有不少前辈为我们总结好了，参考如下：

HTML5中最看重的理念“语义化”相比HTML有什么区别？
https://segmentfault.com/a/1190000002695791    (很齐全)

HTML 语义
http://justineo.github.io/slideshows/semantic-html/#/2
```



让 IE8 支持 HTML5 语义化标签
```
HTML5是 HTML 最新的修订版本，于2014年10月由万维网联盟（W3C）完成标准制定。而 IE8 面世时间为2009年3月19日，
时间相差如此之大，所以 IE8 作为比较古老的浏览器，不支持 HTML 5 引入的语义化标签
（如 header、nav、menu、section、article 等）也是很正常的。

默认情况下 IE8 对 HTML5 标签的处理
在 IE8 里面，未定义的标签——IE8 不认识所有新引入的 HTML5 标签，所以定义样式是不会生效。比如下面这段代码（抽取主要代码）：

<style>
  section { color: red; }
</style>

<section>
  hello world
</section>
期待展示的效果如下：

chrome

但在 IE8 中实际展示效果如下：

IE8

如何让 IE8 支持 HTML5 标签
虽然默认不支持，但是我们可以通过 JS 使用 document.createElement 来“欺骗” IE 的 CSS 引擎，
让它知道某个标签的存在，具体做法如下：

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>HTML5 test</title>
  </head>
  <body>

    <script>
      document.createElement('section');
    </script>

    <style>
      section { color: red; }
    </style>

    <section>
      Hello!
    </section>

  </body>
</html>
显示效果如下：

IE_HTML5

既然元素默认都不支持，就更没有相关默认的样式了，所以我们还要加上一些重置样式如下：

article, aside, details, figcaption, figure, footer, header, hgroup, main, menu, nav, section, summary {
  display: block;
}
借助 html5shiv.js 让 IE8 支持更多的 HTML5 特性
其实不只是 IE8 ， IE6-9、 Safari 4.x (以及 iPhone 3.x)、还有Firefox 3.x 等等，对 HTML5 的支持都不完善。
所以有了一个库 html5shiv.js 来做统一处理，shiv 意为用作武器的小刀（实际上是一个拼写错误，应该为 shim），
在机械工程中的专业释义为垫片，比喻给那些老旧的浏览器加个垫片，让它们基本能用。

更多阅读
IE8 HTML5 surport
HTML5 shiv
html5shiv.js
github上html5shiv项目readme.md部分的翻译
HTML5 Shiv 的一些趣事 ，英文原文见 The Story of the HTML5 Shiv。

```
#### 第三节：显示类型：display
```
块级元素
p , div , hn ,ul/ol ,li......
display:block/table/list-item......由display:block来定义这些块级元素特征

行内元素
a,span ,img,em......
display:inline/inline-block

有 display 来决定块级元素和行内元素是可以转换的

block
1.每一个都另起一行
2.可设置宽高，行高，上下边距

inline
1.和其他行内元素同一行
2.不可设置宽高，行高，上下边距

inline-block

基本值: none,inline,block,inline-block

flexbox: flex,inline-flex

grid: grid,inline-grid

table: table,table-row,table-cell


border: 1px solid； (去掉 1px solid 表格边框)

vertical-align: middle;（勾选后默认居中）

```

#### 第五节：视觉格式化模型（visual formatting model）
```
前面我们已经学习了盒模型（box model），知道了元素会被渲染成一个个盒子。那么这些盒子在屏幕上
的位置又是怎么放置的呢？这就是我们现在要学习的——CSS 视觉格式化模型(visual formatting model)。
视觉格式化模型是 CSS 布局的一个基础理论体系，需要你有一定的 CSS 功底，所以一时半会是很难掌握的，
但是只要你一掌握，对于 CSS 布局就会豁然开朗。（建议整个 CSS 布局学完后再重新细读深入下。）

盒子的位置摆放
默认情况下，盒子按照元素在 HTML 中的先后位置从左至右自上而下一个接着一个排列摆放。如下图：



在图中我们可以看到，有些元素的盒子被渲染为完整的一行，如h1、p、div；而有些元素的盒子则被渲染为水平排列，
直到该行被占满然后换行，如span、a、strong。

这是因为不同的盒子使用的是不同的格式化上下文（formatting context）来布局，每个格式化上下文都拥有一套
不同的渲染规则，它决定了其子元素将如何定位，以及和其他元素的关系和相互作用。（就如我们参加结婚喜宴一样，
有父母长辈席，好友席，同事席，甚至前男/女朋友席等，不同的身份坐到对应位置即可。）

格式化上下文（formatting context）
我们常见的两个格式化上下文分别为：块格式化上下文（block formatting context 简称 BFC）
和行内格式化上下文（inline formatting context 简称 IFC）

BFC
块级盒（block-level boxes）
当元素的 CSS 属性 display 的计算值为 block，list-item，table，flex 或 grid 时，它是块级元素。
视觉上呈现为块，竖直排列。典型的如 <div> 元素，<p> 元素等都是块级元素。

每个块级元素至少生成一个块级盒，称为主要块级盒(principal block-level box)。一些元素，比如<li>，
生成额外的盒来放置项目符号，不过多数元素只生成一个主要块级盒。

块级盒参与 BFC，被渲染为完整的一个新行。

渲染规则
默认根元素（html 元素）会创建一个 BFC，其块级盒子元素将会按照如下规则进行渲染：

块级盒会在垂直方向，一个接一个地放置，每个盒子水平占满整个容器空间
块级盒的垂直方向距离由上下 margin 决定，同属于一个 BFC 中的两个或以上块级盒的相接的 margin 会发生重叠
BFC 就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此
计算 BFC 的高度时，浮动元素也参与计算
除此之外，还有其他方法可以创建一个新的 BFC，具体可参看：块格式化上下文。除此之外，flexbox 布局和 
grids 布局中的 item 都会创建一个新的 BFC。

具体渲染规则及效果可参看：块格式化上下文

更多关于 BFC 相关内容可参看：

Block formatting contexts
CSS 之 BFC 详解
IFC
行内级盒（inline-level boxes）
当元素的 CSS 属性 display 的计算值为 inline，inline-block，inline-table，inline-flex 
或 inline-grid 时，它是行内级元素。视觉上它将内容与其它行内级元素排列为一行，直到该行被占满然后换行。
典型的如段落内容，文本或图片，都是行内级元素。

注：由于目前几乎所有资料都将行内元素当做行内级元素，所以前面的课程我们也遵循这个美丽的错误。
严格来说，行内元素不包括 inline-block 的，行内级元素才包括。我们要理解其中的区别，知晓这个美丽的错误。

行内级元素生成行内级盒，参与行内格式化上下文（inline formatting context），被渲染为水平排列, 
直到当行被占满然后换行。

行内级盒分为行内盒（inline boxes）和原子行内级盒(atomic inline-level boxes)。前者由非置换元素且 display 
值为 inline 的元素生成；后者由行内级置换元素，或 display 值为 inline-block, 
inline-table, inline-flex, inline-grid 的元素生成。

每一行排列的行内级盒都可以看做由一个匿名的行盒包裹，如下图（使用了两种灰色背景色来模拟）：



渲染规则
当块容器盒（block container box）不包括任何块级盒（block-level boxes）时，就会创建一个行内格式化上下文（IFC）。
（一般来说一个块级盒也是一个块容器盒，具体可参看： Block-level elements and block boxes）

IFC 中的行内级盒将会按照如下规则进行渲染（规则有点多，大概主要点就是行盒，折行机制，水平对齐方式，垂直高度及垂直对齐方式）：

1.盒子一个接一个地水平摆放，当容器宽度不够时就会换行
2.在水平方向上，这些盒的外边距、边框、内边距所占用的空间都会被计算，
但行内盒的垂直的border，padding 与 margin 都不会撑开行盒的高度
3.在垂直方向上，这些盒可能会以不同形式来对齐，可通过 vertical-align 来设置，默认对齐为 baseline
4.每一行将生成一个行盒（line box），包括该行所有的盒子，行盒的宽度是由包含块和存在的浮动来决定
5.行盒一般左右边都贴紧其包含块，但是会因为浮动盒（float 元素）的存在而发生变化。浮动盒会位于包含块边缘与行盒边缘之间，
这样行盒的可用宽度就小于包含块的宽度
6.当所有盒的总宽度小于行盒的宽度，那么行盒中的水平方向排版由 text-align 属性来决定
7.当所有盒的总宽度超过一个行盒时，就会形成多个行盒，多个行盒相互之间垂直方向不能分离，不能重叠
8.当一个行内盒超过行盒的宽度时，它会被分割成多个盒，这些盒被分布在多个行盒里。如果一个行内盒不能被分割
（比如只包含单个字符，或word-breaking机制被禁用，或该行内框受white-space属性值为nowrap或pre的影响），
那么这个行内盒将溢出这个行盒
9.当一个行内盒发生分割时，分割处的 margins, borders 和 padding 不会有任何视觉效果（或者其他任何分裂，只要是有多个行盒）
10行盒的高度由内部元素中实际高度最高的元素计算出来。每个行盒的高度由于内容不一样，所以高度也可能不一样
11在一个行盒中，当他包含的内部容器的高度小于行盒的高度的时候，内部容器的垂直位置可由自己的 vertical-align 属性来确定
注：在 IFC 的环境中，是不能存在块级元素的，如果将块级元素插入到 IFC 中，那么此 IFC 将会被破坏掉变成 BFC，
而块级元素前的元素或文本和块级元素后的元素或文本将会各自自动产生一个匿名块盒其包围。

具体行盒高度及垂直对齐方式渲染效果可参看：

行盒高度：http://coding.imweb.io/demo/p3/vfm/ifc-height.html
行内级元素垂直对齐方式

更多关于 IFC 相关内容可参看：

Inline formatting contexts
深入理解CSS中的行高
其他格式化上下文
除此之外，还有一些其他不同类型的盒子，如下：

表格布局：可以创建一个表格包裹盒(table wrapper box)，包括了表格盒(table box)及任何标题盒(caption boxes)。
多列布局：可以在容器盒与内容之间创建列盒(column boxes)
弹性布局：将会创建一个弹性容器盒（flex container box）
网格布局：将会创建一个网格容器盒（grid container box）
而这些盒子也将采用不用的格式化上下文来渲染，如 table formatting context（table 布局）、
flex formatting context（flexbox 布局）、grid formatting context（grid 布局）。

更多关于盒子的介绍可参看：

盒子的生成)
视觉格式化模型中的各种框
定位方案
上面我们所讨论的其实都是常规流（normal flow）中盒子的摆放。但实际上我们有三种定位方案，分别为：

常规流（normal flow）：盒一个接一个排列，不同的盒子采用不同的格式化上下文渲染。
浮动（float）：盒将从常规流里提出来，放在当前盒的旁边。
绝对定位(absolute positioning)：盒将脱离常规流，其坐标是绝对的（通过 top / bottom / left / right 来设置）。
常规流（normal flow）
默认盒的定位方案就是常规流，但是如果触发了以下任何一个条件，将不会使用常规流：

position 的值非 static 或 relative
float 的值非 none
在常规流中，不同的盒子将采用不同的格式化上下文渲染，也就是上面所讲的部分。

浮动（float）
对于浮动定位方案, 盒称为浮动盒（floating boxes）。它位于当前行的开头或末尾。这导致常规流环绕在它的周边，
除非设置 clear 属性。

要使用浮动定位方案，元素 CSS 属性 position 必须为 static 或 relative，然后 float 不为 none 。如果 float 设为 left,
则浮动定位到当前位置的开始位置，如果设为 right, 则浮动定位到当前位置的最后位置。

具体介绍可学习下面章节：元素浮动——float。

绝对定位（absolute position）
如果元素的属性 position 不是 static 或 relative， 那它就是绝对定位元素。

对于绝对定位方案，盒从常规流中被移除，不影响常规流的布局。 
它的定位相对于它的包含块，定位坐标可通过属性 top、bottom、left、right 来设置 。

固定定位元素(fixed positioned element)也是绝对定位元素，它的包含块是视口。当页面滚动时它固定在屏幕上，因为视口没有移动。

具体介绍可学习下面章节：元素定位——position。

参考资料
视觉格式化模型 | MDN
CSS layout 入门
Layout mode | MDN

```

#### 第六节：深入了解 inline-block
```
在之前的课程中，我们学习到了 inline-block 的基础知识，接下来我将介绍一些使用 inline-block 产生的问题和解决方法
以及其常见的应用场景，来进一步加深了大家对 inline-block 的理解。

水平间隙问题
我们创建一个导航列表，并将其列表 item 设置为 inline-block，主要代码如下：

<div class="nav">
  <div class="nav-item"><a>导航</a></div>
  <div class="nav-item"><a>导航</a></div>
  <div class="nav-item"><a>导航</a></div>
</div>
.nav {
  background: #999;
}
.nav-item{
  display:inline-block; /* 设置为inline-block */
  width: 100px;
  background: #ddd;
}
效果图如下：



我们从效果图中可以看到列表 item 之间有一点小空隙，但是我们在代码中并没有设置 margin 水平间距。那么这个空隙是如何产生的呢？

这是因为我们编写代码时输入空格、换行都会产生空白符。而浏览器是不会忽略空白符的，
且对于多个连续的空白符浏览器会自动将其合并成一个，故产生了所谓的间隙。

对于上面实例，我们在列表 item 元素之间输入了回车换行以方便阅读，而这间隙正是这个回车换行产生的空白符。

同样对于所有的行内元素（inline，inline-block），换行都会产生空白符的间隙。

如何消除空白符
从上面我们了解到空白符，是浏览器正常的表现行为。但是对于某些场景来说，并不美观，而且间隙大小非可控，
所以我们往往需要去掉这个空白间隙。一般来说我们有两种方法来去掉这个换行引起间隙：代码不换行和设置 font-size。

代码不换行
我们了解到，由于换行空格导致产生换行符，因此我们可以将上述例子中的列表 item 写成一行，这样空白符便消失，
间隙就不复存在了。其代码如下：

<div class="nav">
  <div class="nav-item">导航</div><div class="nav-item">导航</div><div class="nav-item">导航</div>
</div>
但考虑到代码可读及维护性，我们一般不建议连成一行的写法。

设置 font-size
首先要理解空白符归根结底是个字符，因此，我们可以通过设置 font-size 属性来控制产生的间隙的大小。
我们知道如果将 font-size 设置为 0，文字字符是没法显示的，那么同样这个空白字也没了，间隙也就没了。

于是顺着这个思路就有了另一个解决方案：通过设置父元素的 font-size 为 0 来去掉这个间隙，
然后重置子元素的 font-size，让其恢复子元素文字字符。

所以该方法代码如下：

.nav {
  background: #999;
  font-size: 0; /* 空白字符大小为0 */
}
.nav-item{
  display:inline-block;
  width: 100px;
  font-size: 16px; /* 重置 font-size 为16px*/
  background: #ddd;
}
使用该方法时需要特别注意其子元素一定要重置 font-size，不然很容易掉进坑里（文字显示不出来）。

对齐问题
由于 inline-block 属于行内级元素，所以 vertical-align 属性同样对其适用。

在正式讲解 vertical-align 之前，我们需要先说一些基本概念。

中线、基线、顶线、底线
中线（middle）、基线（baseline）、顶线（text-top、底线（text-bottom））是文本的几个基本线，其对应位置如下图：



基线（base line）：小写英文字母x的下端沿。
中线（middle line）：小写英文字母x的中间。
顶线（text-top）：父元素 font-size 大小所组成的一个内容区域的顶部
底线（text-bottom）：父元素 font-size 大小所组成的一个内容区域的底部
vertical-align 的值
vertical-align 只接受8个关键字、一个百分数值或者一个长度值。下面我们将看看各关键字如何作用于行内元素。

值	描述
baseline	默认元素的基线与父元素的基线对齐。
sub	将元素的基线与其父元素的下标基线对齐。
super	将元素的基线与其父代的上标 - 基线对齐。
text-top	将元素的顶部与父元素的字体顶部对齐。
text-bottom	将元素的底部与父元素的字体的底部对齐。
middle	将元素的中间与基线对齐加上父元素的x-height的一半。
top	将元素的顶部和其后代与整行的顶部对齐。
bottom	将元素的底部和其后代与整行的底部对齐。
<length>	将元素的基线对准给定长度高于其父元素的基线。
<percentage>	像<长度>值，百分比是line-height属性的百分比。
具体 demo 可参考：行内级元素垂直对齐方式
```
#### 第七节：元素浮动———— float
```
设置元素的浮动———— float
不浮动———— none 
左浮动———— left
右浮动———— right
```
#### 第八节：清除浮动详解
```
清除浮动主要是为了解决由于浮动元素脱离文流导致的元素重叠或者父元素高度坍塌的问题，而这两个问题
分别对应了需要清除浮动的两种种情况：清除前面兄弟元素浮动和闭合子元素浮动（解决父元素高度坍塌）。

清除前面兄弟元素浮动
清除前面兄弟元素浮动很简单，只需要在不想受到浮动元素影响的元素上使用 clear:both 即可， HTML & CSS 代码如下：

<div class="fl">我是左浮动元素</div>
<div class="fr">我是右浮动元素</div>
<div class="cb">我不受浮动元素的影响</div>
.fl {
    float: left;
}
.fr {
    float: right;
}
.cb {
    clear: both;
}
在 CSS2 以前，clear 的原理为自动增加元素的上外边距（margin-top）值，使之最后落在浮动元素的下面。
在 CSS2.1 中引入了一个清除区域（clearance）——在元素上外边距之上增加的额外间距，使之最后落在浮动元素的下面。
所以如果需要设置浮动元素与 clear 元素的间距，得设置浮动的元素的 margin-bottom，而不是 clear 元素的 margin-top。

demo 可见：clear 清除浮动

闭合子元素浮动
我们知道，在计算页面排版的时候，如果没有设置父元素的高度，那么该父元素的高度是由他的子元素高度撑开的。
但是如果子元素是设置了浮动，脱离了文档流，那么父元素计算高度的时候就会忽略该子元素，甚至当所有子元素都是
浮动的时候，就会出现父元素高度为 0 的情况，这就是所谓的父元素高度坍塌问题。为了能让父元素正确包裹子元素的高度，
不发生坍塌，我们需要闭合子元素的浮动。

一般我们有两种办法可以用来闭合子元素浮动：

给最后一个元素设置 clear: both
给父元素新建一个 BFC(块格式化上下文)
clear:both
由于我们最后一个元素使用 clear:both，所以该元素就能不受浮动元素影响出现在父元素的最底部，而父元素
计算高度的时候需要考虑到这个正常元素的位置，所以高度自然包裹到了最底部，也就没有了坍塌。

对于这个方法，以前我们是利用新增一个空元素（<b> 或 <span> 或 <div> 等）来实现的，如下：

<div class="container">
    <div class="box"></div>
    <span class="clear-box"></span>
</div>
.box {
    float: left;
}
.clear-box {
    clear: both;
}
虽然这种办法比较直观，但是不是很优雅，因为增加了一个无用的空白标签，比较冗余而且不方便后期维护（一般不太建议使用该办法）。
所以后期有了通过父元素的伪元素（::after）实现的著名 clearfix 方法，代码如下：

<div class="container clearfix">
    <div class="box"></div>
</div>
.clearfix::after {
    content:"";
    display:table;
    clear: both;
}
上面方法给父元素增加一个专门用于处理闭合子元素浮动的 clearfix 类名，该类使用 ::after 伪元素类选择器
增加一个内容为空的结构来清除浮动，可能你们比较疑惑的是为什么要设置 display:table 属性，这其实涉及到
一个比较复杂的进化过程，具体可以参考资料——clearfix浮动进化史

新建 BFC
该方法的原理是：父元素在新建一个 BFC 时，其高度计算时会把浮动子元素的包进来。

下面我们以实例为证：如下图我们的图片为浮动，父元素 article 的高度就出现了坍塌（没有包括图片），
而根元素 HTML （默认情况下我们的根元素 HTML 就是一个 BFC）的高度则包括了图片的高度。





既然新建一个 BFC 可以解决父元素高度坍陷问题，那就好办了，下面这些都可以创建一个 BFC ：

1.根元素或其它包含它的元素
2.浮动 (元素的 float 不是 none)
3.绝对定位的元素 (元素具有 position 为 absolute 或 fixed)
4.内联块 inline-blocks (元素具有 display: inline-block)
5.表格单元格 (元素具有 display: table-cell，HTML表格单元格默认属性)
6.表格标题 (元素具有 display: table-caption, HTML表格标题默认属性)
7.块元素具有overflow ，且值不是 visible
8.display: flow-root
虽然有这么多方法可用，可我们常用的就是 overflow: hidden，代码如下：

<div class="container">
    <div class="box"></div>
</div
.container {
    overflow: hidden;
}
.box {
    float: left;
}
总结
上面主要讲解了我们比较常的一些清除浮动解决方案，看似简单的清除浮动方法其实则涉及到了很多复杂的CSS规则，
大家在实际操作的时候可以针对不同的情况参考上面的方法。










