#### 第一节：属性参考
```
CSS 属性也是一个非常庞大的知识体系，这里先介绍下一些基本的属性，方便我们入门练习，
后续将慢慢学习更多。如果你对某些属性不太了解，也可以直接参考文档：

CSS 参考 - CSS | MDN
https://developer.mozilla.org/zh-CN/docs/Web/CSS/Reference
CSS 参考手册 | W3school
http://www.w3school.com.cn/cssref/

如何阅读 CSS 属性值定义语法。
https://developer.mozilla.org/zh-CN/docs/Web/CSS/Value_definition_syntax

下面的前四个相关属性（字体，文本，列表，表格）需要自己多学习实践，如有不明白，
可以在上面的参考手册中查阅对应的资料（如需快速查找，可以在网页中使用ctrl+f快捷键，
打开搜索，输入下面的属性，点击搜索即可找到该属性）。之后的相关属性我们以后也会慢慢讲到，
你也可以先提前了解下。
```
![属性和值](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/oqq5518-photo-1/%E5%B1%9E%E6%80%A7%E5%92%8C%E5%80%BC.png)

字体相关属性
```
font-family：定义文本的字体，如：font-family: arial;
font-size：字体尺寸，如：font-size: 18px;
font-style ：字体样式，如：font-style: italic;
font-weight：字体的粗细，如：font-weight: bold;
```
文本相关属性
```
color：定义文字颜色，如：color: red;
line-height：设置行高，如：line-height: 1.5;
text-align：文本的水平对齐方式，如：text-aligin: center;
text-decoration：文本的装饰效果，如：text-decoration: underline;
text-indent：首行的缩进，如：text-indent: 2em;
text-shadow：文本的阴影效果，如：text-shadow: 0 0 5px #ff0000;
```
列表属性
```
list-style：在一个声明中设置所有的列表属性
list-style-image：将图象设置为列表项标记
list-style-position：设置列表项标记的放置位置
list-style-type：设置列表项标记的类型
上面的几个属性一般只作用于ul/ol、li元素重置的时候（其他时候几乎从来不用），
使用的时候也是使用第一个简写的形式（简写形式以后的课程将会详细介绍），如：

ul, ol {
    /* 第一个none表示image，outside表示position，第二个none表示type */  
    list-style: none outside none; 
}
```
表格属性
```
border-collapse：是否合并表格边框
border-spacing：相邻单元格边框之间的距离
table-layout：设置表格的布局算法

上面三个属性，只作用于 table 元素，其余元素都没有作用，如：
table {
    border-collapse:collapse;
    border-spacing: 0;
    table-layout: fixed;
}
```
盒子相关
```
盒子相关属性可以等到学完本章的“CSS 盒子”内容之后再来查阅。

盒子大小
主要是宽高及最小和最大宽高。

width
min-width
max-width
height
min-height
max-height
box-sizing
简单示例如下：

div {
    width: 200px;
    min-height: 400px;
}
盒子边框
每个元素都有四条边，你可以给任何一条边设置边框，分别为上（top）、右（right）、下（bottom）、左（left）表示，
而每个边框又包括宽度（width）、样式（style）及颜色（color）三个样式，这样组合起来就有很多属性了，
不过我们一般使用简写的模式来写。

border：简写模式，四边边框
border-width：边框宽度
border-style：边框样式，常用的为solid和dashed
border-color：边框颜色
border-top：上边框
border-right：右边框
border-bottom：下边框
border-left：左边框
这里来几个简单的例子，更详细的请参考各个属性文档。

p {
    /* 
    四边样式 
    1px为border-width
    solid为border-style
    #f00为border-color
    */    
    border: 1px solid #f00; 
}
div {
    border-top: 2px dashed #f00; /* 单边样式 */
}
span {
    border: 1px solid #ccc; /* 先定义四边样式 */
    border-top-color: #f00; /* 重新定义上边框的颜色 */
}
h1 {
    border: 1px dashed #999; /* 先定义四边样式 */
    border-width: 1px 2px; /* 重新边框的宽度 */
}
盒子内外边距
内边距为 padding，外边距为 margin，和 border 一样，也有四边可以设置，
分别为上（top）、右（right）、下（bottom）、左（left），同样我们一般也采用简写的形式。

margin
margin-top
margin-right
margin-bottom
margin-left
padding
padding-top
padding-right
padding-bottom
padding-left
简单示例如下：

h1 {
    margin-top: 0; /* 外边距上 */
    margin-bottom: 20px; /* 外边距下 */
}
p {
    margin: 0; /* 外边距 */
}
div {
    padding: 15px 20px; /* 内边距，15px为上下值，20px为左右值 */
    margin: 0 20px 30px; /* 外边距，0为上，20p为左右，30px为下 */
}
盒子背景
设置背景图片，背景颜色，图片位置及是否平铺等，一般也采用简写形式。

background：总的简写形式，包括了下面各个单条属性
background-color：背景色
background-image：背景图片
background-position：背景图片起始位置
background-repeat：背景图片平铺方式
background-size：背景图片大小
background-clip：背景图片绘制区域
background-origin：背景图片的定位区域
简单示例如下：

p {
    background: #f00;
}
div {
    background: url(logo.png) no-repeat #fff;
}
盒子显示隐藏
overflow：指定当内容溢出其块级容器时,是否剪辑内容，渲染滚动条或显示内容
visibility：是否可见
盒子其他
border-radius：圆角
box-shadow：阴影
空间位置相关
这一块涉及元素定位布局，第三章会详细讲解。

display
float
clear
position
top
right
bottom
left
transform
z-index
opacity
动画相关
同样这块我们也在第三章再具体介绍

transition
animation
```
####  第二节：单位
```
进一步探讨单位
CSS 中的单位有很多，这里主要介绍目前常用的及未来必备的几个单位。
```
px
```
px 是 pixels（像素）的缩写，是一种绝对单位，用于屏幕显示器上，传统上一个像素对应于计算机屏幕上的一个点，
而对于高清屏则对应更多。任何现代显示屏，不管是手机，平板，笔记本还是电视都是由成千上万的像素组成的，
所以我们可以使用这些像素来定义长度。

另外 CSS 将光栅图像(如照片等)的显示方式定义为默认每一个图像大小为“1px”。 一个“600x400”解析度的照片的
长宽分别为“600px”以及“400px”，所以照片本身的像素并不会与显示装置像素(可能非常小)一致，而是与 px 单位一致。
如此就可以将图像完整的与网页的其它元素排列起来。

下面我们使用 px 单位设置下元素的大小，如下：

.box {
 width: 200px;
 font-size: 16px;
}
```
%
```
%（百分比）应该是我们最好理解的单位了，这里就不多解释了，主要有一点需要注意：

如果对 html 元素设置 font-size 为百分比值，则是以浏览器默认的字体大小16px为参照计算的
（所有浏览器的默认字体大小都为 16px），如62.5%即等于10px（62.5% * 16px = 10px）。
```
em
```
em 也是一种相对单位，既然是相对单位，那么肯定有一个参照值。不过其参照值并不是固定不变的，而是不同的属性有不同的参照值。

font-size
对于字体大小属性（font-size）来说，em 的计算方式是相对于父元素的字体大小，1em 等于父元素设置的字体大小。
如果父元素没有设置字体大小，则继续往父级元素查找，直到有设置大小的，如果都没有设置大小，则使用浏览器默认的字体大小。

下面我们举几个简单的例子说明下：

.parent {
 font-size: 14px;
}
.child1 {
 font-size: 1em; /* 1em = 1*14px*/
}
.child2 {
 font-size: 1.5em; /* 1.5em = 1.5*14px */
}
/* 父级元素都没有设置大小的 */
.no-parent-font-size {
 font-size: 0.8em; /* 0.8em = 0.8*16px */
}
```
其他属性（border, width, height, padding, margin, line-height）
```
在这些属性中，使用em单位的计算方式是参照该元素的 font-size，1em 等于该元素设置的字体大小。同理如果该元素没有设置，
则一直向父级元素查找，直到找到，如果都没有设置大小，则使用浏览器默认的字体大小。

下面我们举几个简单的例子说明下：

p {
 font-size: 14px;
 width: 20em; /* 20em = 20*14px */
 padding: 1.5em; /* 1.5em = 1.5*14px */
}
/* 元素本身没有设置字体大小且父级元素也没有设置 */
.no-font-size {
 width: 40em; /* 40em = 40*16px */
 margin-bottom: 2em; /* 2em = 2*16px */
}
总之em的计算单位相对来说比较复杂，现在已经不建议使用，如果你要兼容的浏览器是现代浏览器的话，
那么可以使用下面要介绍的 rem 单位。
```
rem
```
和 em 一样，rem 也是一种相对单位，不过不一样的是 rem 是相对于根元素 html 的 font-size 来计算的，
所以其参照物是固定的。（rem的r就是表示root，虽然rem相对em进步了很多，但是由于是新技术，
不支持IE8以下（包括IE8）,不过幸喜的是移动端可以放心使用）

由于 rem 是基于跟元素 html 的 font-size 来计算的，所以如果改变 html 的 font-size 值，那么所有使用的
rem 单位的大小都会随着改变，这对于移动端适应各种屏幕大小来说还是有点作用的。

html {
 font-size: 625%; /* 相当于100px = 625% * 16px */
}
div {
 font-size: 20px; 
 width: 2rem; /* 2rem = 2 * 100px(根元素的font-size) */
 height: 4rem; /* 4rem = 4 * 100px(根元素的font-size) */
 padding: 0.1rem; /* 0.1rem = 0.1 * 100px(根元素的font-size) */
}
如果我们改变了 html 的 font-size 值，如设置为 80px，则相应的我们的 div 的 width，
height 和padding 大小也随着改变了。

相对于 em 来说，rem 只需要修改 html 的 font-size 值即可达到全部的修改，即所谓的牵一发而动全身。
```
vw, vh, vmin, vmax
```
最后要介绍的这四个单位属于 v 系单位，它们也是相对单位，是基于视窗大小（浏览器用来显示内容的区域大小）来计算的。

网页中我们很多时候都需要用到满屏，或者屏幕大小的一半等，尤其是移动端，屏幕大小各式各样，
而这个时候我们现有的单位就显得有点捉襟见肘，于是就诞生了这四个单位。

vw：基于视窗的宽度计算，1vw 等于视窗宽度的百分之一
vh：基于视窗的高度计算，1vh 等于视窗高度的百分之一
vmin：基于vw和vh中的最小值来计算，1vmin 等于最小值的百分之一
vmax：基于vw和vh中的最大值来计算，1vmax 等于最大值的百分之一
下面我们实例说明实现一个宽度为视窗宽度的 25%，高度为视窗高度 50% 的一个盒子：

.box {
 height: 50vh; /* 视窗高度的50% */
 width: 25vw; /* 视窗宽度的25% */
 background: red;
}
同样由于是新技术，还是有些浏览器不兼容，哪怕在移动端安卓4.3 以下也是不兼容，不过长远来说这也是必备的。
```
单位运算 calc 
```
除了设置以上的单位之外，我们还可以使用 calc 来进行单位运算，单位运算时可以使用各种单位进行加减乘除运算。

简单示例如下：

.box {
 height: calc(50vh - 20px); /* 50% 的视窗高度减掉20px */
 width: calc(100% / 3);  /* 三分之一的父容器宽度 */
 background: red;
}
可惜的是，calc 也存在兼容问题，详细介绍可参考：calc | MDN
https://developer.mozilla.org/zh-CN/docs/Web/CSS/calc

注：chrome 浏览器最小的字体为 12px，如果设置 10px 也会渲染成 12px 。
```
#### 第三节：颜色
```
CSS 颜色的使用
现在我们已经学会了一些基本的颜色使用，但是在实际工作中，我们还需要面对颜色有着更深入的了解，从而能更从容面对各种挑战。

颜色从哪来？
一般来说，你要装修房子的话，得先找装修公司设计个最终效果图，然后交给装修师傅，让他按照这个图来实现效果。

同样你做网页的时候，设计师也会给你一个最终的效果图，这个效果图可以是图片，也可以是 psd 的原稿，
甚至是 sketch 原稿。那么我们的文字或背景色就来自这个效果图。

这样我们就得需要一个取色工具来帮助我们从效果图上吸取所需取色。这里推荐几个（这种工具一搜一大把）：

马克鳗 - 设计稿标注、测量
RGB网页颜色在线取色器
ColorSchemer（for windows）
ColorZilla（浏览器插件）
除此之外，打开 photoshop 和 sketch 也可以完成取色。

如何定义颜色？
颜色关键词
首先，我们可以使用一些关键词来表示颜色，如 red，green，gray 等（默认浏览器支持 147 种关键词颜色：CSS 颜色名），
除此之外，还有两个关键词可用，分别是 transparent 和 currentColor。

transparent 从字面上就可以知道是透明；而 currentColor 关键字表示使用该元素 color 的计算值。
如果该元素设置了 color 颜色值，则使用该 color；如果该元素没有设置 color，则继承父级元素的 color。

实例如下：

/* transparent */
.transparent {
    border-color: transparent;
    color: transparent;
}
/* currentColor 使用场景一 设置了color */
.box {
    color: green;    
    border-color: currentColor; /* 使用color的颜色green */
}
/* currentColor 使用场景二 没有设置color 继承父级元素的color */
.parent {
    color: red;
}
.parent .child {
    border-color: currentColor; /* 使用来自parent的red */
}
rgb
表示使用红-绿-蓝模式来定义颜色。这其实就是我们说的十六进制（hex）和 rgb 函数两种形式。

十六进制
十六进制颜色表现形式为： #RRGGBB 和 #RGB

“#” 后跟6位十六进制字符（0-9, A-F）
“#” 后跟3位十六进制字符（0-9, A-F）
其中三位数的 RGB 符号是六位数的简写形式，当六位数满足两个 R，两个 G，两个 B 同时相等的时候，就可以进行简写。
如#ff0000、#336699、#cccccc，可省略为#f00，#369，#ccc，但是#ff0122（表示绿色的01不一样），
#3f3f3f（表示红色的3f不一样，同样表示绿色和蓝色也不一样）则不能省略。

rgb
rgb 函数表示为：rgb(red, green, blue)。每个参数 (red、green 以及 blue) 定义颜色的强度，
可以是介于 0 与 255 之间的整数，或者是百分比值（从 0% 到 100%）。

如rgb(255,0,0)表示红色，rgb(125,125,125)表示灰色。

rgba
在 rgb 的基础上，还可以添加一个 alpha 透明度表示半透明值，这样就构成了我 rgba，
其函数表示为：rgb(red, green, blue, alpha)，其中 alpha 参数是介于 0.0（完全透明）与 1.0（完全不透明）的数字。

如我们需要一个半透明的黑色作为遮罩层：background: rgba(0, 0, 0, 0.5) 。

hsl
除了使用红-绿-蓝的模式定义颜色之外，还可以通过 hue（色调）、saturation（饱和度）、lightness（亮度）模式定义颜色，
其语法为：hsl(hue, saturation, lightness) 。

Hue 是色盘上的度数（从 0 到 360） - 0 (或 360) 是红色，120 是绿色，240 是蓝色。Saturation 是百分比值；
0% 意味着灰色，而 100% 是全彩。Lightness 同样是百分比值；0% 是黑色，100% 是白色。
如红色使用 hsl 表示：hsl(0, 100%, 50%)

下面通过图来帮助理解下：





同样对于 hsl 也可以加入透明度来表示半透明色，这就是 hsla，语法为hsla(hue, saturation, lightness, alpha)，
alpha 取值同样为介于0.0到1.0的数字，如hsla(0, 100%, 50%, 0.7) 。

参考资料
- CSS | MDN
CSS 合法颜色值






































