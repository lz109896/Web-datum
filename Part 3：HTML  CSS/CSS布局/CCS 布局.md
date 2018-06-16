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

##### 深入理解 HTML 语义
```

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
##### 让IE8 支持 HTML5 语义化标签
```
HTML5是 HTML 最新的修订版本，于2014年10月由万维网联盟（W3C）完成标准制定。而 IE8 面世时间为2009年3月19日，
时间相差如此之大，所以 IE8 作为比较古老的浏览器，不支持 HTML 5 引入的语义化标签
（如 header、nav、menu、section、article 等）也是很正常的。

默认情况下 IE8 对 HTML5 标签的处理
在 IE8 里面，未定义的标签——IE8 不认识所有新引入的 HTML5 标签，所以定义样式是不会生效。
比如下面这段代码（抽取主要代码）：

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

IFC 中的行内级盒将会按照如下规则进行渲染
（规则有点多，大概主要点就是行盒，折行机制，水平对齐方式，垂直高度及垂直对齐方式）：

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
在之前的课程中，我们学习到了 inline-block 的基础知识，接下来我将介绍一些使用 inline-block 
产生的问题和解决方法以及其常见的应用场景，来进一步加深了大家对 inline-block 的理解。

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



我们从效果图中可以看到列表 item 之间有一点小空隙，但是我们在代码中并没有设置 margin 水平间距。
那么这个空隙是如何产生的呢？

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

```
#### 第九节：float 布局
```
左中右三栏布局

#navsecond {
    float: left;
    width: 180px;
}
释义：左边栏，宽度180，向左浮动

#maincontent {
    float: left;
    width: 740px;
}
释义：中间主内容区，宽度740，向左浮动

#sidebar {
    float: left;
    width: 180px;
}
释义：右边栏，宽度180，向左浮动

width: 1200px;现在比较主流的宽度，适合PC

流体布局
内容区域先写class="main"  （宽度是 width:100%）（有个子元素 margin:0 200px;(上下是0，左右的200px)
再写左边栏     浮动宽度 width:200px;  margin-left: -100%    左边距浮动 -100%
再写右边栏     margin-left: -200%  右边距浮动 -200%

当不勾选  margin-left: -100%；和 margin-left: -200%； 时，都被内容区域挤到换行。
当都勾选时，都被拽回去对应左边栏和右边栏

```
#### 第十节：网格布局系统
```
视频中涉及到的网址如下：

960s 栅格布局
960 grid system（官网）
注：960s 是网格布局系统的鼻祖，当然随着技术的发展，基于它又发展了很多其他的网格布局系统，但是思想是想通的，
无非是整体多少宽度分成几分，间距是多少，如何组合等。
为什么是12列呢？因为12可以被2，3，4，6整除，这样做等分的时候是非常方便的。

注：以前设置浮动的时候，一般还需要设置display: inline来兼容 IE6、7，以避免出现双倍 margin 的间距。

```
#### 第十一节：元素位置
```
注：position 还有一个 sticky 取值，不过兼容有点问题，具体可参考：sticky（具体使用可参考下面的 Resources 部分链接）

position :设置元素的定位方式

static :静态
relative ：相对
absolute :绝对
fixed ：固定

 
坐标点：  x  ：left（左）/right（右）
         y   : top（上）/bottom（下）
         
参考点
relative ：相对于自己的位置偏移
absolute :相对于非 static 最近的父级元素（relative ，absolute，fixed）
fixed ：一般来说相对于视窗（相对于浏览器的整个界面）

```
#### 第十二节：元素层级——z-index
```
1.默认HTML结构顺序，谁最后出现谁最高级
2.position(非static值)元素高于其他元素
3.position(非static值)元素之间先通过z-index 值判断
4.如果z-index 相同则按照HTML结构顺序
```
#### 第十三节：深入了解 z-index
```
网页正常文档流排版可以理解为在一个平面立面里面，元素占据空间，依次排列，互不覆盖。但是当页面中元素设置了定位属性的时候，
难免会出现元素之间相互重叠的情况，比如下图小猫和小狗的图片都设置了绝对定位，2张图片的位置重叠了，小猫图显示在小狗图上面。
现在如果我们想要小狗图显示在上面，就需要涉及到 CSS 中的 z-index 属性了。

z-index

z-index
z-index 属性用于指定已定位元素在垂直于页面方向的排列顺序，其属性值有2种：auto（默认值）和整数。这里有2个需要注意的点：

z-index 属性只对定位元素元素生效，也就是 position 属性不为 static 的元素。
除了默认值 auto， z-index 可以设置为任意整数，正数，0，负数都可以。
一般情况下，z-index 值进行比较有下面2条规则：

数值大的在上面(auto 数值上相当于0)。
数值相同的，在 HTML 结构中排后面的在上面。
所以上面例子，2张图都没设置 z-index 的值，在 dom 结构上排后面的小猫图展示在上面。
如果想小狗图展示在小猫图上面，只需要设置小狗图的 z-index 属性值大于0就可以了。

<img class="dog" src="http://coding.imweb.io/img/p3/z-index/dog.png" alt="dog">
<img class="cat" src="http://coding.imweb.io/img/p3/z-index/cat.png" alt="cat">
.dog {
  position: absolute;
  top: 10px;
  left: 100px;
  z-index: 1; /* 设置小狗图的 z-index 值大于0 */
}
.cat {
  position: absolute;
  top: 80px;
  left: 70px;
}
给 .dog 元素增加了 z-index: 1 属性就可以让小狗图相比于小猫图在垂直于页面的方向上离我们更近，
这样效果就是小狗图显示在上面了。

z-index

层叠上下文
上面说到，z-index 默认值 auto 数值上等于0，那设置了 z-index:0 和 默认的 z-index:auto; 有没有区别呢？
答案是有区别的。区别在于设置了 z-index 属性为整数值(包括0)的元素，自身会创建一个层叠上下文。
而创建一个层叠上下文之后，其子元素的层叠顺序就相对于父元素计算，不会与外部元素比较。这样说比较抽象，我们来看个例子。

<div class="dog-container">
  <img class="dog" src="http://coding.imweb.io/img/p3/z-index/dog.png" alt="dog">
</div>
<div class="cat-container">
  <img class="cat" src="http://coding.imweb.io/img/p3/z-index/cat.png" alt="cat">
</div>
img {
  width: 200px;
}
.dog-container {
  width: 200px;
  height: 100px;
  background: red;
  position: relative;
  z-index: auto; /* 默认值auto */
}
.dog {
  position: absolute;
  top: 10px;
  left: 100px;
  z-index: 2;
}
.cat {
  position: absolute;
  top: 80px;
  left: 70px;
  z-index: 1;
}
上面例子中，我们给 .dog 和 .cat 增加了容器 .dog-container 和 .cat-container,并且 .dog 和 .cat 都
设置了 z-index 值，所以都显示在红色背景的 .container 之上，而且 .dog z-index 数值比较大，所以显示在上面。

z-index

但是当我们设置了 .dog-container 的 z-index 属性值为0之后，
我们发现，z-index 值比较大的 .dog 元素反而到 z-index值比较小的 .cat 下面了

.dog-container {
  width: 200px;
  height: 100px;
  background: red;
  position: relative;
  z-index: 0; /* 将 z-index 值改成0 */
}
效果：

z-index

其原因就在于我们给 .dog-container 设置了 z-index:0 之后，.dog-container 就创建了自己的层叠上下文，
其子元素 .dog 在比较层叠顺序的时候只会在 .dog-container 内比较，而不会与外面的 .cat 比较。如下图所示:

z-index

上面例子告诉我们，并不是所有情况 z-index 值大的元素都会在上面，我们在进行 z-index 比较的时候要留意其
祖先元素有没有建立独立的层叠上下文，z-index 只有在同一个层叠上下文中比较才有意义。另外，对定位元素设置
z-index 属性不是唯一创建层叠上下文的方法，具有下面属性的元素都会创建层叠上下文（具体可参看：层叠上下文 | MDN）：

根元素 (HTML)
z-index 值不为 "auto"的 绝对/相对定位
一个 z-index 值不为 "auto"的 flex 项目 (flex item)，即：父元素 display: flex|inline-flex
opacity 属性值小于 1 的元素
transform 属性值不为 "none"的元素，
mix-blend-mode 属性值不为 "normal"的元素，
filter值不为“none”的元素，
perspective值不为“none”的元素，
isolation 属性被设置为 "isolate"的元素，
position: fixed
在 will-change 中指定了任意 CSS 属性，即便你没有直接指定这些属性的值（参考这篇文章）
-webkit-overflow-scrolling 属性被设置 "touch"的元素
也就是说，上面例子中， .dog-container 满足上面任意一条属性，也会一样出现上面的情况。比如设置 opacity 属性：

.dog-container {
  width: 200px;
  height: 100px;
  background: red;
  position: relative;
  opacity: 0.6; /* 设置 opacity 属性小于1也会创建层叠上下文 */
}
效果如下：

z-index

总结
z-index 属性用于描述定位元素在垂直于页面方向上的排列顺序。
z-index 一般比较规则是值大在上，值相同则排后面的在上。
元素在设置了某些属性的时候会创建层叠上下文，z-index 值比较大小只有在同一个层叠上下文才有效。
参考文档
深入理解CSS中的层叠上下文和层叠顺序
理解CSS的 z-index属性
层叠上下文-MDN
```
#### 第十四节：flexbox 基本概念
```
.box {
    display: fiex
}


父元素 ( display: fiex)的直接子元素形成布局模型，可以很容易对齐及分布
如果子元素里面含有子元素是不受影响的

fiex container ：容器
main axis：  主轴
main start： 主轴开始的地方
main end：   主轴结束的地方
main size：  是指item在主轴main axis 上所占的尺寸大小


cross axis： 交叉轴
cross end：  交叉轴开始的地方
cross start  交叉轴结束的地方
cross size： 是指item在交叉轴cross axis 上所占的尺寸大小



* 为默认值
flex-direction：设置主轴的
*flex-direction: row;                三页界面1.2.3一行向左对齐
flex-direction: row-reverse;         三页界面3.2.1一行向右对齐
flex-direction: column;              三页界面从上到下1.2.3变一竖
flex-direction: column-reverse;      三页界面从上到下3.2.1变一竖

lex-wrap: 换行
*flex-wrap: nowrap         显示一行，不换行（禁止文字换行）
flex-wrap: wrap            三页界面当宽度达到换行条件时，变成两行（第一行第1.2页面，第二行第3页面），变成两条轴线
flex-wrap: wrap-reverse    三页界面当宽度达到换行条件时，变成两行（第一行第3页面，第二行第1.2页面），变成两条轴线

justify-content： item 在主轴（main axis）上的对齐方式。主轴是可以设置的
*justify-content: flex-start        三页界面1.2.3一行向左对齐
justify-content: flex-end           三页界面1.2.3一行向右对齐
justify-content: center             三页界面1.2.3一行中间对齐
justify-content: space-between      三页界面1.2.3一行分部对齐，每个页面中间有相同间距
justify-content: space-around       三页界面1.2.3一行分部对齐，
                                    每个页面 item 左右两边都有相等的距离=两个页面左右之间 item 的距离

align-item：item 在 cross轴上的对齐方式
*align-item: stretch            
align-item: flex-start     三页界面向左边一行，拉伸展开全部的界面
align-item: flex-end       三页界面在左边一行，收起界面末尾向下对齐
align-item: center         三页界面在左边一行，收起界面末尾中间对齐
align-item: baseline       三页界面在左边一行，收起界面末尾向上对齐

align-content：只有一行（或只有一条轴）是不会有变化的，需要宽度达到最大值，flex-wrap: wrap 可换行条件
*align-content: stretch        
align-content: flex-start      两条轴线向上对齐，第一行是第1.2页面，第二行是第三3页面
align-content: flex-end        两条轴线向下对齐，第一行是第1.2页面，第二行是第三3页面
align-content: center          两条轴线中间对齐，第一行是第1.2页面，第二行是第三3页面，最上面和最下面还留有距离
align-content: space-between   两条轴线分别最上和最下对齐，最上是第1.2页面，最下是第3页面，中间留有最大的空隙
align-content: space-around    两条轴线分布中间对齐，第一行是第1.2页面，第二行是第三3页面，
                               每个页面 item 上下两边都有相等的距离=两个页面上下之间 item 的距离




fiex-item
fiex-item：arder     数值越大 item 排序越后

flex-grow             充分利用fiex container 的空间，剩余空间怎么分配
如：设置 item 值分别为1、 0、 0时，fiex container为4等份，第一个 item 占比两等份
    设置 item 值分别为1、 1、 0时，fiex container为4等份，第一个和第二个 item 占比三等份
    设置 item 值分别为1、 1、 1时，fiex container为3等份，第一个和第二个和第三个 item 占比三等份，都一样

shrink：缩小(压缩)的意思，剩余空间怎么压缩
flex-shrink    当宽度超过最大时，都不会换行，选择 flex-wrap: wrap 时，将会换行看到真实的 item 宽度
如：设置 flex-shrink 值为：0时，item 不（不允许）压缩
    设置 flex-shrink 值为：1，1,1时，三个 item 等比例压缩
    设置 flex-shrink 值为：2，1,1时，第一个 item 再次压缩一份
    
    
flex-basis：可以理解为像素
flex-basis：设置值为：300时（也可以设置为%比），第一个 item 再次压缩一份
当既有flex-basis，也有width 宽度时，flex-bassie 权重比较高，会覆盖width 宽度值



align-self：item 在cross axis交叉轴的对齐方式
align-self 和 align-item 都有相同的属性；align-self 里面的属性会覆盖 align-item 的属性
flex-start     单个页面 item 向上对齐
flex-end       单个页面 item 向下对齐
center         单个页面 item 中间对齐
baseline


```
![flexbox](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/350594f034616e7818b4c27f4a5a7340e4c4e978/flexbox.png)
![flexbox1](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/350594f034616e7818b4c27f4a5a7340e4c4e978/flexbox1.png)
![flexbox2](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/350594f034616e7818b4c27f4a5a7340e4c4e978/flexbox2.png)
![flexbox3](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/f60032fac90de6d83da41db3e63ed0c2b3aa36ae/flexbox3.png)



#### 第十五节：flexbox 剩余空间分配规则
```
前面我们学习到了 flexbox 布局。通过使用 flexbox 布局，我们可以更轻松实现以往很难实现的页面布局。
本文主要讲解 flexbox 布局是如何去分配和计算布局剩余空间的。（本文阅读前要求你对 flexbox 已经有了初步的认知，
如果不是很了解，建议先学习前面视频内容。）

基础概念
为了更好地理解本文内容，我们需要先了解下面一些基础概念。

flexbox 容器 (flexbox container)
flexbox 容器又称弹性容器，通过设置 display: flex 而产生，简单示例如下：

.container {
  display: flex; /* 或者 inline-flex */
}

flexbox 项目 (flexbox item）
当设置一个元素为 flexbox 容器时，其直接子元素将自动成为容器成员，也可以称之为：flexbox 项目。

注：因为 flexbox 布局是发生在父元素和子元素之间的，所以下面为了行文方便，统一将 flexbox 容器称为“父容器”，
而 flexbox 项目统一称为“子元素”

剩余空间
剩余空间就是指父容器在主轴方向上剩余未分配的空间，它是 flexbox 布局中一个很重要的词。我们可以借助下面的例子来更好地理解：

<div class="container" width="600px" style="display:flex;">
  <span class="item1" width="200px">item1</span>
  <span class="item2" width="200px">item2</span>
</div>
上面代码，我们定义了一个宽度为600px的父容器 container，以及宽度为200px的子元素 item1 和 item2 ，
那么我们得出其剩余空间为200px，计算公式为：

剩余空间 = 父容器的宽度 - item1的宽度 - item2的宽度

剩余空间分配相关属性
flexbox 布局中的子元素可以通过设置 flex 属性来改变其所分配到的空间大小。
flex 属性包括了 flex-basis、 flex-grow、flex-shrink

flex-basis
flex-basis 用来定义子元素的默认宽或高。如果父容器 flex-direction 属性的方向为水平方向则为宽度，
如为垂直方向则为高度。相当于给子元素设置宽或高。如果同时设置了该属性与宽或高，则该属性权重大于宽或高的值。

flex-grow
flex-grow 用来指定父容器多余空间的分配比率，默认值为0。看到这里，大家可能还是没有概念。
为了更形象地理解，我们一起看下下面的例子。

例子： 只设置 item1 的 flex-grow 为1

其 HTML 代码如下：

<div class="container">
  <span class="item item-flex-grow">item1</span>
  <span class="item item2">item2</span>
</div>

其 CSS 代码如下：

/* css 部分 */
.container {
  display: flex;
  width: 600px;
  height: 140px;
  align-items: center;
  background-color: #ddd;
}
.item {
  width: 200px;
  height: 120px;
  line-height: 120px;
  text-align: center;
  background-color: orange;
}
.item2 {
  background-color: green;
}
.item-flex-grow{
  flex-grow:1;
  background-color: 
}

这里我们对 item1 设置flex-grow:1 后，我们可以看到 item1 的所占空间宽度变成400px，
也就是说 item1 把之前我们所说的父容器剩余的200px空间都占用了。

在这里我们可以得出：其实 flex-grow 即定义如何去分配父容器的剩余空间 ，当值为0时，则子元素都不会索取父容器的剩余空间。
当 item1 设置 flex-grow: 1 的时候，由于 item2 没有设置 flex-grow 的值，则剩余空间将会被分成一份，并且分别分给了 item1。

例子： 设置 item1 的 flex-grow 为1，且 item2 的 flex-grow 为3
如果此时我们设置 item2 的flex-grow:3 ，item2 也将会参与索取父容器的剩余空间，此时父容器的剩余空间将分为4份，
然后1份分配到 item1，而分配3份到 item2.

如果子元素的宽度的总和超过父容器，flex-grow 将不生效。
上面的例子，我们只考虑了子元素的宽度总和都是没有超过父容器的宽度的情况，则其可以使用 flex-grow 来分配父容器的剩余空间。
那么当子元素的宽度总和超过父容器的宽度时，这时剩余空间还可以分配吗？此时 flex-grow 是否还有效呢？让我们先看看下面的例子：

这里我们设置上面例子的 item1 和 item2 的宽度为350px，则子元素的宽度总和为700px且超过父容器container的600px宽度。


我们可以看到 flex-grow 并没有起到作用，且两个 item 的宽度还被压缩到只有300px。

通过之前学到的如何计算剩余空间的方法，我们可以算出本例子的剩余空间为600px - 700px即 -100px,这里可以得出由于没有剩余空间，
则定义了 flex-grow 的子元素能分配到的空间为0，故不生效。另外我们需要知道的是 flexbox 环境的父容器的宽度600px并不会因为
子元素的总宽而改变，即子元素的宽度总和最多等于父容器的宽度，所以为了让子元素完整显示在父容器内，只有两个办法：

通过设置 flex-wrap 来使子元素换行
通过压缩子元素来使其能容纳在父容器内

flex-shrink
flex-shrink 用来指定父容器空间不够时子元素的缩小比例，默认为1。
如果一个 flexbox 项目的 flex-shrink 属性为0，则该元素不会被压缩。

为什么需要 flex-shrink 来定义缩小比例呢？
上面我们可以知道，当子元素的宽度总和大于 flexbox 父容器的宽度时，其剩余空间将为负数，如果没有设置换行的情况下，其将会通
过压缩子元素来使其能够容纳在父容器内。那么我们如何控制子元素的压缩比例呢？答案就是通过将通过设置 flex-shrink 这个属性。

例子：设置项目的flex-shrink
下面例子，我们设置两个 item 的宽度为350px，而容器 container 的宽度仍为600px。
同时定义了 item1 和 item2 的 flex-shrink 的属性分别为1和4。如下所示：


代码如下：

/* 这里只展示关键css */
.container {
  display: flex;
  width: 600px;
  height: 140px;
}
.item {
  width: 350px;
  height: 120px;
}
.item1 {
  flex-shrink: 1;
}
.item2{
  flex-shrink: 4;
}
我们看到由于缺少100px的空间，按照 item1 和 item2 定义的 flex-shrink 的值，缺少的100px将分成5份。item1
将压缩其中的 1/5 即20px，item2 的将压缩其中的 4/5 即80px。

例子：设置项目的 flex-shrink 为0
在上面的知识中，我们了解到 flex-shrink 默认值为1，即默认子元素在父容器空间不足时会被压缩。
现在我们把项目的 flex-shrink 设为0来看下不压缩的情况。如下所示：

代码如下：

/* 这里只展示关键css */
.container {
  display: flex;
  width: 600px;
  height: 140px;
}
.item {
  width: 350px;
  height: 120px;
  flex-shrink: 0;
}
```
#### 第十六节：grids 布局系统
```
我们之前有提到过网格系统，比如960s，bootstrap 的网格系统，但是这些网格系统都是模拟出来的（使用 float 或 flexbox），
而并非天生的，虽然可以解决一些常见布局问题，但面临 Win10 UI 还是有点力所不及.


但是随着 CSS 的不断发展及完善，一种新的网格布局方式被纳入规范，它将会解决所有的网格问题，
这就是我们要说的 CSS Grid Layout。

网格系统基础概念
在说 CSS Grid Layout 之前，我们先来看看 excel 的表格。

excel css gri layout

以我们的 Sheet1 的 A1 单元格为例，先是有上下左右四条线围着，然后定位是由竖直的 A 栏与横向的1行二维坐标表示 A1。
如果有需要甚至还还可以和邻近的单元格合并。

现在我们提炼下上面的几个概念：线条，栏(竖直)，行(横向)，单元格，合并。接下来我们把这些概念对应到我们的网格系统：

CSS Grid Layout

Grid Container：首先我们要设置父元素的布局为 grid，通过使用 display 属性给元素显式设置属性值grid或inline-grid，
此时这个元素将自动变成网格容器，对应上图的Sheet1

Grid Item：Item 是 container 的直接子元素，如果不考虑单元格的合并跟下面的 cell 是一样的，
如果有单元格合并，在该 item 可能包括几个cell，对应上图的一个个格子，如蓝色的 A1

Grid Lines：网格线分为水平线和垂直线，对应上图的橙色线条
Grid Track：就是由lines构成的水平和垂直空间，对应到上图的水平和垂直灰色区域，而对于table来说就是row和column
Grid Cell：简单来说就是单元格了，对应到上图就是蓝色的A1，而对于table来说就是单元格
Grid Area：网格区域是由任意四条网格线组成的空间，可能由一个或多个单元格组成。
对应到上图就是红色区域，相当于表格中的合并单元格之后的区域

网格系统基本属性
网格系统布局其实跟 flexbox 布局差不多，都是由父子元素构成的布局。所以属性分为父元素属性和子元素属性。

因篇幅有限，这里只简单介绍每个属性的用途，具体的属性取值请参考：

A Complete Guide to Grid:   https://css-tricks.com/snippets/css/complete-guide-grid/#prop-align-items
grid | MDN:   https://developer.mozilla.org/en-US/docs/Web/CSS/grid


父元素（Grid Container）属性
这里我们将父元素属性大概分为三大类，其中第一类与第二类属性可以简写为 grid 属性（不包括 display 属性）：

第一类：如何去定义一个网格系统，行列及间距等。

display：grid/inline-grid，定义使用网格系统
grid-template-columns：定义垂直栏
grid-template-rows：定义水平行
grid-template-areas：定义区域
grid-column-gap：定义垂直栏与垂直栏之间的间距，如上图的A与B之间的间距
grid-row-gap：定义水平行与水平行之间的间距，如上图的1与2之间的间距
grid-gap：上面两个栏与行间距的缩写

第二类：自动分配形式，当定义的行或列数量不够时，多出 item 的自动排列方式：

grid-auto-columns：定义多出的 item 的自动column的宽度大小
grid-auto-rows：定义多出的 item 自动 row 的高度大小
grid-auto-flow：定义自动 item 是按照先水平方向排列还是垂直方向排列

第三类：分布对齐的方式（属性跟 flexbox 的有点像）。

justify-items：item 在水平行中的对齐方式
align-items：item 在垂直栏中的对齐方式
justify-content：整个水平行在 grid 范围的对齐方式，这里有个好用的 space-evenly 值，
补足了以前flex的 space-around 和 space-between 的不足

align-content：整个垂直栏在 grid 范围的对齐方式
子元素（Grid Item）属性

接下来是我们的 item 属性，同样这里我也将它分为两类：

第一类：单元格所占格子多少

grid-column-start：item 的起始栏
grid-column-end：item 的结束栏
grid-column：起始栏和结束栏的简写
grid-row-start：item 的起始行
grid-row-end：item 的结束行
grid-row：起始行与结束行的简写
grid-area：item所在区域

第二类：单元格的自定义对齐方式，这个跟 flexbox 的 item 有点相似。

justify-self：自定义 item 的水平方向对齐方式
align-self：自定义 item 的垂直方向对齐方式

实例演示
百说不如一练，我们接下来使用网格系统来实战下我们的 Win10 UI，如下图：

grids demo)

html结构为：

<div class="grid">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">5</div>
    <div class="item">6</div>
    <div class="item">7</div>
    <div class="item">8</div>
    <div class="item">9</div>
    <div class="item">10</div>
    <div class="item">11</div>
</div
写好结构后，我们就开始使用刚才说得 grid 来实现我们的效果了。先拆分成最小的单元格为 6栏 * 3行，
最小单元格的大小为140px，整体内容一屏水平垂直居中。

html,body {
 height: 100%;
}
.grid {
  height: 100%;
  display: grid; /* 网格布局 */

  /* 整体水平垂直居中 */
  justify-content: center;
  align-content: center;

  /* 定义6栏3行 */
  grid-template-columns: 140px 140px 140px 140px 140px 140px;
  grid-template-rows: 140px 140px 140px;

  /* 定义item之间的间距为20px */
  grid-gap: 20px;

  background: #efefef;
}
.item{
  background: #ccc;
}
现在我们可以看到效果如下：



接下来要合并单元格实现我们的最终效果。合并单元格有两种实现方式一种是 line 的开始与结束（包括 colunm 与 row），
另一种就是在 grid 上面定义的 area，这里我们使用第一种方法。

这里重提下上面的 Grid Lines 概念，如要实现 n栏 * m行的网格，则需要n+1条垂直line，m+1条水平线。

第一个 item 元素单元格占了两列，第一列和第二列，那么就垂直栏开始于第一条 line，
结束于第三条 line，同样第5个 item 元素也是如此

.item:nth-child(1),
.item:nth-child(5) {
  grid-column: 1 / 3; /* 起始于1，结束于3 */
}

而第二个 item 元素栏和行都跨了两个，CSS 代码如下：

.item:nth-child(2) {
  grid-column: 3 / 5; /* column起始于3，结束于5 */
  grid-row: 1 / 3;  /* row起始于1，结束于3 */
}
同样第七个 item 元素行跨了两个，第9个 item 元素栏跨了两个，CSS 代码如下：

.item:nth-child(7) {
  grid-column: 6;
  grid-row: 2 / 4; /* row起始于2，结束于4 */
}
.item:nth-child(9) {
  grid-column: 2 / 4; /* column起始于2，结束于4 */
}
这个布局就这么简单的完成了，效果可见 demo

浏览器支持
现代浏览器最新版本基本上都支持了 CSS Grid Layout，下图是 caniuse 上的支持情况：

caniuse

有些浏览器旧版本的已经实现但是没有默认开启（chrome < 57，firefox < 52）则需要通过下面的方式手动设置开启：

chrome 在地址栏输入“chrome://flags”，找到"experimental web platform features"开启
firefox在地址栏输入"about:config"，找到"layout.css.grid.enabled"开启
总结
上面只是 grid 布局的简单使用，实际上 grid 布局十分强大，使用起来也十分方便，未来将会是布局的主力军，
但是目前由于兼容问题暂时不建议在生产环境中使用，不过我们相信很快就可以见识到 grid 布局的强大威力了。

参考资料
A Complete Guide to Grid:   https://css-tricks.com/snippets/css/complete-guide-grid/#prop-align-items
CSS Grid Layout:    https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Grid_Layout
```
#### 第十七节：浏览器如何渲染 HTML & CSS
```
我们现在已经知道，使用 HTML & CSS 可以搭建出一个漂亮的 Web 页面。

那么浏览器到底是如何使用我们的 HTML & CSS 渲染成我们在屏幕上所看到的页面呢？

虽然具体渲染过程很复杂，但是还是可以将其分为几个关键路径，如下：

处理 HTML 标记并构建 DOM 树
处理 CSS 标记并构建 CSSOM 树
将 DOM 与 CSSOM 合并成一个渲染树
根据渲染树来布局，以计算每个节点的几何信息，再将各个节点绘制到屏幕上
构建 DOM 树
首先浏览器渲染页面前会根据 HTML 结构构建成对应的 DOM 树。

以下面的 HTML 代码为例：

<html>
  <head>
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <link href="style.css" rel="stylesheet">
    <title>Critical Path</title>
  </head>
  <body>
    <p>Hello <span>web performance</span> students!</p>
    <div><img src="awesome-photo.jpg"></div>
  </body>
</html>
其 DOM 树生成的流程如下图：



转换： 浏览器从磁盘或网络读取 HTML 的原始字节，并根据文件的指定编码（例如 UTF-8）将它们转换成各个字符。
令牌化： 浏览器将字符串转换成 W3C HTML5 标准规定的各种令牌，例如，“”、“”，以及其他尖括号内的字符串。
每个令牌都具有特殊含义和一组规则。

词法分析： 发出的令牌转换成定义其属性和规则的“对象”。
DOM 构建： 最后，由于 HTML 标记定义不同标记之间的关系（一些标记包含在其他标记内），创建的对象链接在一个树数据结构内，
此结构也会捕获原始标记中定义的父项-子项关系：HTML 对象是 body 对象的父项，body 是 paragraph 对象的父项，依此类推。
整个流程的最终输出就是我们这个简单页面的文档对象模型 (DOM)，如下图：



CSSOM
在浏览器构建上面的 DOM 时，在文档的 head 部分遇到了一个 link 标记，该标记引用一个外部 CSS 样式表：style.css。
由于预见到需要利用该资源来渲染页面，它会立即发出对该资源的请求，并返回以下内容：

/* style.css */

body { font-size: 16px }
p { font-weight: bold }
span { color: red }
p span { display: none }
img { float: right }
与处理 HTML 时一样，我们需要将收到的 CSS 规则转换成某种浏览器能够理解和处理的东西。
因此，我们会重复 HTML 过程，不过是为 CSS 而不是 HTML：

CSS 字节转换成字符，接着转换成令牌和节点，最后挂靠到一个称为“CSS 对象模型”(CSSOM) 的树结构内：

CSSOM 为何具有树结构？这是因为浏览器为页面上的任何对象计算最后一组样式时，都会先从适用于该节点的最通用规则开始
（例如，如果该节点是 body 元素的子项，则应用所有 body 样式），然后通过应用更具体的规则
（即规则“向下级联”）以递归方式优化计算的样式。

以上面的 CSSOM 树为例进行更具体的阐述。span 标记内包含的任何置于 body 元素内的文本都将具有 16 像素字号，并且颜色为
红色— font-size 指令从 body 向下级联至 span。不过，如果某个 span 标记是某个段落 (p) 标记的子项，则其内容将不会显示。

合并渲染树
接下来就是将 DOM 树与 CSSOM 树合并形成渲染树。

渲染树会网罗网页上所有可见的 DOM 内容，以及每个节点的所有 CSSOM 样式信息。



注：渲染树只包含渲染网页所需的节点，如display: none;的元素是不会出现在渲染树种的。

布局及绘制
有了渲染树，我们就可以进入“布局”阶段。

到目前为止，我们计算了哪些节点应该是可见的以及它们的计算样式，但我们尚未计算它们在设备视口内
的确切位置和大小---这就是“布局”阶段，也称为“自动重排”。

为弄清每个对象在网页上的确切大小和位置，浏览器从渲染树的根节点开始进行遍历。让我们考虑下面这样一个简单的实例：

<html>
  <head>
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <title>Critial Path: Hello world!</title>
  </head>
  <body>
    <div style="width: 50%">
      <div style="width: 50%">Hello world!</div>
    </div>
  </body>
</html>

以上网页的正文包含两个嵌套 div：第一个（父）div 将节点的显示尺寸设置为视口宽度的 50%；而里面内嵌的
第二个 div 将其宽度设置为其父项的 50%，即视口宽度的 25%。如下图：



布局流程的输出是一个“盒模型”，它会精确地捕获每个元素在视口内的确切位置和尺寸：所有相对测量值都转换为屏幕上的绝对像素。

最后，既然我们知道了哪些节点可见、它们的计算样式以及几何信息，我们终于可以将这些信息传递给最后一个
阶段：将渲染树中的每个节点转换成屏幕上的实际像素形成我们可见的页面。这一步通常称为“绘制”或“栅格化”。

注：执行渲染树构建、布局和绘制所需的时间将取决于文档大小、应用的样式，以及运行文档的设备：文档越大，浏览器需要
完成的工作就越多；样式越复杂，绘制需要的时间就越长（例如，单色的绘制开销“较小”，而阴影的计算和渲染开销则要“大得多”）。

参考资料
关键渲染路径:   https://developers.google.com/web/fundamentals/performance/critical-rendering-path/

```

#### 第十八节：重排与重绘
```
一个页面渲染完毕后，随着用户的操作，或者数据变化，网页还会进行重新渲染。
根据不同的触发条件，重新渲染分为两种情况：重排（reflow）和重绘（repaint）。

所有对元素视觉表现属性的修改，都会导致重绘（repaint）。比如修改了背景颜色、文字颜色等。

所有会触发元素布局发生变化的修改，都会导致重排（reflow）。比如窗口尺寸发生变化，删除、添加 DOM 元素，
修改了影响元素盒子大小的 CSS 属性如 width、 height、 padding 等。

通常情况下，重排的影响更大，重排会导致文档局部或全部的重新运算：重新计算元素位置，大小。
（改变一个元素的布局，可能会影响很多个元素的布局）

不管是重绘还是重排导致的重新渲染，都会阻塞浏览器。重新渲染的的过程中，JavaScript 会被阻塞，
用户的交互行为也会被卡住。复杂的 CSS 动画甚至会拖慢 JavaScript 的运行速度。

注：本文涉及到的 JavaScript 部分，可以先忽略，等以后学习了 JavaScript 再来查看。

导致重排和重绘的场景

CSS 属性改变
网站 CSS trigglers 列出了所有 CSS 属性对 layout （布局）、paint （绘制）的影响。
通过这个表，可以查到不同内核下，对 CSS 属性的修改会导致重绘、重排还是两者都会发生。

re-render

注：Composite （渲染层合并） 是 chrome 引入 GPU 加速带来的新概念。（相关信息可参看下面的参看资料）

对 CSS 属性进行修改，包括但不限于以下场景：

通过 display: none 隐藏 DOM 节点（导致重绘和重排）
通过 visibility: hidden 隐藏 DOM 节点 （导致重绘，因为它没有影响其它元素位置布局）
CSS 动画
通过 JavaScript 添加样式，修改样式
用户交互
对浏览器窗口进行缩放操作会导致重排
对 DOM 节点进行操作，添加、删除、更新 DOM 节点都会导致重排
光标 :hover 、进入文本输入框、修改浏览器的字体都会导致重排
最佳实践
所有的最佳实践都是围绕尽最大可能的降低重绘和重排的频率，来达到减少重新渲染的目的。

CSS 属性的读、写操作分开
浏览对 CSS 属性的连续修改做了优化，比如下面的连续修改两次 style，不会导致两次重新渲染：

div.style.color = 'blue';
div.style.marginTop = '30px';
上面代码只会进行一次重新渲染。但是如果写的不好，则会触发两次重新渲染，如下：

div.style.color = 'blue';
var margin = parseInt(div.style.marginTop);
div.style.marginTop = (margin + 10) + 'px';
上面代码对 div 元素设置背景色以后，第二行要求浏览器给出该元素的位置，所以浏览器不得不重新渲染然后得到该元素的位置。

除此之外，样式的写操作之后，如果有下面这些属性的读操作，都会引发浏览器立即重新渲染：

offsetTop/offsetLeft/offsetWidth/offsetHeight
scrollTop/scrollLeft/scrollWidth/scrollHeight
clientTop/clientLeft/clientWidth/clientHeight
getComputedStyle()
通过 class 或者 csstext 来批量更新样式
上面对通过对 style 对 CSS 属性一个一个修改，其实更好的方式应该是通过 class 来批量化。

// bad
var left = 10;
var top = 10;
el.style.left = left + "px";
el.style.top  = top  + "px";

// good 
el.className += " theclassname";

// good
el.style.cssText += "; left: " + left + "px; top: " + top + "px;";
其他方法
DOM 样式离线更新：尽量使用离线 DOM，而不是真实的网页 DOM 来改变元素样式。比如，操作 Document Fragment对象，
完成后再把这个对象加入 DOM。再比如，使用 cloneNode() 方法，在克隆的节点上进行操作，然后再用克隆的节点替换原始节点。

使用 display: none 进行样式批量更新：先将元素设为 display: none（需要1次重排和重绘），然后对这个节点进行100次操作，
最后再恢复显示（需要1次重排和重绘）。这样一来，你就用两次重新渲染，取代了可能高达100次的重新渲染。

善用 position：position 属性为 absolute 或 fixed 的元素，重排的开销会比较小，因为不用考虑它对其他元素的影响。
将元素设置为不可见：只在必要的时候，才将元素的 display 属性为可见，因为不可见的元素不影响重排和重绘。
另外，visibility : hidden 的元素只对重绘有影响，不影响重排。

减少样式的更新频率：使用虚拟 DOM 脚本库，比如 React 等。
调节 js 运行帧率：使用 window.requestAnimationFrame()、window.requestIdleCallback() 这两个方法调节重新渲染的频率。
慎用 table 布局：table 的单元格具有非常好的自适应特性，但是同时代价也很高，能不用就不用。如果非要使用 table ，
给 table 添加 table-layout: fixed 属性，这个属性的目的是让后面单元格的宽度由表头的宽度来决定——减少布局的计算量。

参看资料
网页性能管理详解:  http://taobaofed.org/blog/2016/04/25/performance-composite/

10 Ways to Minimize Reflows and Improve Performance
https://www.sitepoint.com/10-ways-minimize-reflows-improve-performance/

无线性能优化：Composite: http://taobaofed.org/blog/2016/04/25/performance-composite/

gpu-accelerated-compositing-in-chrome
http://www.chromium.org/developers/design-documents/gpu-accelerated-compositing-in-chrome


```



