
## 1：CSS 动画简介
```
分为两种补间动画（transition 动画）和帧动画（ animation 动画）

transition 动画：只需要定义开始和结束状态，补齐中间，浏览器会自动补齐中间的状态：称为：补间动画
animation 动画：可以利用关键帧做出复杂的帧动画
```
## 2：transition 动画
```
背景，位置

transition 包括以下属性
transition-property          属性
transition-duration          持续时间
transition-timing-function   功效
transition-delay             延迟时间

transition-property  并不是所有的属性都支持动画的，以下的是不支持的
background-image:(a.png ->b.png)  从A 图片到B 图片是没有动画的
float:(none ->left)               float 是不支持动画
width/height:(auto ->10px)        开始值auto 改为结束 10px 是没有动画的，但是10px 改为100px，才有动画
disply:(nane ->block)             没有动画
visibility:(hidden ->visible)     没有动画
position:(staticn ->absolute)     没有动画
```

## 3.[资料] 动画必备属性 transform

##### 概述
```
transform 本意是变形，变换之意，在 CSS 中使用该属性可对元素进行移动（translate）、旋转（rotate）、
缩放（scale）、倾斜（skew）等效果。因其有着各种特效及优良的性能，所以成为动画的标配。

在学习之前，我们可以简单欣赏下几个案例：

transform 简单 demo  :http://coding.imweb.io/demo/p3/transform/transform.html
flip card  : https://3dtransforms.desandro.com/3d-transform-functions
Cube - show sides  :https://3dtransforms.desandro.com/cube
```
##### 二维（2D）变换

##### translate
```
其语法为：transform: translate(tx[, ty])。其中 tx 表示 x 方向偏移，ty 表示 y 方向偏移，如果 ty 没有指定值则为0。

还可以分拆为：transform: translateX(tx) 或 transform: translateY(ty)。

简单示例如下（虚线框表示原先位置）：

.box {
    transform: translate(50px, 30px);
}


注：tx，ty 如果为百分比值的话，其参考计算的是元素本身的宽和高，而不是父元素的宽和高。所以经常使用该方法设置定位居中，
代码如下：

.demo {
  position: absolute;
  top: 50%; /* 父元素高度的一半位置 */
  left: 50%; /* 父元素宽度的一半位置 */
  transform: translate(-50%, -50%); /* 元素本身的一半宽、高 */
}
```
##### scale  缩放比例
```
其语法为：transform: scale(sx[, sy])。其中 sx 表示 x 方向的缩放比例，sy 表示 y 方向的缩放比例，
如果 sy 没有指定值则与 sx 相等。

同样也可以分拆为：transform: scaleX(sx) 和 transform: scaleY(sy)

简单示例如下：

.box {
    transform: scale(1.2);
}

```
##### rotate
```
其语法为：transform: rotate(angle)。angle 表示顺时针角度。

简单示例如下：

.box {
    transform: rotate(15deg);
}

```
##### skew
```
其语法为：transform: skew(ax[, ay])。其中 ax 表示 x 方向的顺时针角度，ay 表示 y 方向的顺时针角度，
如果 ay 没有指定值则 y 方向没有倾斜。

简单示例如下：

.box {
    transform: skew(30deg);
}

```
##### 复合变换
```
上面几个变换，都可以自由组合形成更复杂的复合变换。

简单示例如下：

.box {
    transform: translate(30px) rotate(10deg) skew(0, 5deg);
}


以上所有示例在线查看地址： transform 简单 demo
```
##### 变换中心点
```
默认上面所有的变换都是以元素的中心位置为参考原点的，不过我们可以通过属性 transform-origin 来改变参考原点。

其语法为：transform-origin: ox oy。其中 ox 表示 x 方向的位置，可使用 left、right、center、<length>、<percentage>，
oy 表示 y 方向的位置，可使用top、bottom、center、<length>、<percentage>。如果只传入一个值，则另一个值默认为 50%

简单示例如下（在线 demo）：

.box {
    transform: rotate(15deg);
}
.box-origin-top-left {
    transform-origin: left top;
}
.box-origin-right {
    transform-origin: right; /* 设置一个值，则另一个为50% */
}
.box-origin-px {
    transform-origin: 200px 80%;
}


```

##### trasform 2D 的本质 —— 矩阵变换
```
上面我们已经简单了解了 transform 2D 的基本语法，接下来简单探讨下 transform 2D 的本质。

transform 2D 除了以上的四种基本语法（translate、rotate、scale、skew）外，还有一个矩阵语法，如下：

transform: matrix(a, b, c, d, e, f);
上面 matrix(a, b, c, d, e, f) 的形式用矩阵符号表示，是这样的：

图一

需要注意的是，第三行是固定的，都是 0,0,1 ，所以 CSS 语法中省去了这一行。
因为涉及到 x、y 及旋转，所以二维变换需要三个变量来表示。

下面我们具体以实例了解下矩阵是如何用来表示变换的，以上面的 translate 为例：

.box {
    transform: translate(50px, 30px);
}
上面 css 代码的意思是说，把所有点都相对于 原点 （通过 transform-origin 指定，默认为中心点），
往 x 正方向平移 50px，往 y 正方向平移 30px。用数学表达式表示就是：

transform-13

这里 tx = 50px ，ty = 30px。稍微变换一下，x' 和 x，y 都相关，写成如下的形式：

transform-14

把两行的x、y系数取出来，再补充一行（为什么多了一行？为了运算方便，看下图也许就清楚了），得下面的语法形式—— 矩阵运算：

transform-14

那么，变换的本质是什么？就是把一组 (x, y) 通过算术运算，变为新的坐标 (x',y') ，刚好 矩阵
这种数学工具就可以用来描述这种数学变换。通用的二维矩阵变换就是：

图二
```
##### 常见的二维变换
```
上面公式的最左边的矩阵，通常是如下几种基本形式组合而成：
```
![二维变换](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/047726115d5d13adc62c83cc6705bcfc487d84a7/%E5%8A%A8%E7%94%BB.png)
```
如果每个变换，都用 matrix 语法来表示，要写很多参数，显然这样是不合理的。所以有了四个基本的简化写法：
```
![简化写法](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/047726115d5d13adc62c83cc6705bcfc487d84a7/%E5%8A%A8%E7%94%BB1.png)

##### 三维（3D）变换
```
3D 变换大概有如下几种使用方法：

transform: translate3d(12px, 50%, 3em);
transform: translateZ(2px);
transform: scale3d(2.5, 1.2, 0.3);
transform: scaleZ(0.3);
transform: rotate3d(1, 2.0, 3.0, 10deg);
transform: rotateX(10deg);
transform: rotateY(10deg);
transform: rotateZ(10deg);
transform: perspective(17px);
transform: matrix3d(1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0, 10.0, 11.0, 12.0, 13.0, 14.0, 15.0, 16.0);
3D 变换的复杂性及可以创造的特效远超 2D 变换。由于篇幅有限且深入掌握的话需要一定的想象力，这里就做不详细介绍了。

推荐两篇高质量入门文章如下：

CSS3 3D transform变换:
http://www.zhangxinxu.com/wordpress/2012/09/css3-3d-transform-perspective-animate-transition/

Intro to CSS 3D transforms
https://3dtransforms.desandro.com/

参考资料
CSS3 Transform
Advanced CSS3 2D and 3D Transform Techniques
transform | MDN
深入浅出CSS Transform
线性代数拾遗（三）：线性变换以及矩阵的意义
理解CSS3 transform中的Matrix(矩阵)
understanding-the-css-transforms-matrix
transformmatrix
css3-matrix-transform-for-the-mathematically-challenged

```
## 4：缓动函数

![缓动函数](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/047726115d5d13adc62c83cc6705bcfc487d84a7/%E5%8A%A8%E7%94%BB2.png)
![缓动函数](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/047726115d5d13adc62c83cc6705bcfc487d84a7/%E5%8A%A8%E7%94%BB3.png)
```
transition-timing-function   功效(又叫缓动函数，是一个过渡效果)
缓动函数速查表
http://cubic-bezier.com/#.17,.67,.83,.67

cubic-bezier
https://easings.net/zh-cn
```


## 5：animation 动画, 是可控制的

![animation 动画](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/047726115d5d13adc62c83cc6705bcfc487d84a7/%E5%8A%A8%E7%94%BB4.png)
```
    animation-name: circleRun;                没有这个属性就不会动画了  ，
                                              通过关键字 @keyframes定义的 circleRun，第几帧时定义位置变化
    animation-duration: 2s;                   动画的持续时间，当改为1S时，动画加快
    animation-timing-function: ease;          
    animation-delay: 0s;                      延迟开始时间，设置的时间值越大，开始时间越久   
    animation-iteration-count: infinite;      动画执行的次数， infinite 指的是无限执行，无限循环的，
                                              改为2，只执行2次，回归到原位   
    animation-direction: normal;              normal 重复路径执行，改为alternate 先顺路径执行，后反路径执行      
    animation-fill-mode: none;                第六节：animation-fill-mode 解析
    animation-play-state: running;            动画的状态，当animation-duration改为 5秒，动画在运行时，
                                              把状态改为paused 更清晰看到，动画暂停5秒了

以上代码简写为：
animation: circleRun 2s ease infinite;



```

## 6：animation-fill-mode 解析
```
animation-fill-mode 保持最后一帧的状态


    animation-name: circleRun2;
    animation-delay: 2s;
    animation-fill-mode: backwards;   backwards决定动画的初始位置
    animation-play-state: paused;



```
## 7：关键帧语法解析
```
@keyframes定义的 circleRun
表示动画执行到33% 时的状态位置在哪里
表示动画执行到66% 时的状态位置在哪里
表示动画执行到100% 时的结束状态位置在哪里

form：表示0%
to: 表示100%

```
![关键帧语法](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/047726115d5d13adc62c83cc6705bcfc487d84a7/%E5%8A%A8%E7%94%BB5.png)
![关键帧语法](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/047726115d5d13adc62c83cc6705bcfc487d84a7/%E5%8A%A8%E7%94%BB6.png)
## 8：transiton 动画和 animation 动画的异同

![画的异同](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/047726115d5d13adc62c83cc6705bcfc487d84a7/%E5%8A%A8%E7%94%BB7.png)



## 9：常见 CSS 动画库

##### 常见 CSS 动画库
```
自从 CSS3 有了动画功能，从此 Web 页面就迈进“忽如一夜春风来，千页万页动画开”的盛况。
所以 CSS 动画除了是炫技之选更是一项基本技能，当然也就有无数前辈为之呕心沥血总结经验了。
这里我们站在巨人肩上，为大家推荐一些常见且十分好用的 CSS 动画库，既可以用来学习也可用来提高工作效率。
```
Animate.css
```
Animate.css 是最早的也是目前最流行和最易于使用的CSS动画库之一，其包含了60多款不同类型的 CSS 动画
如晃动、闪动、淡出淡出效果等，如果你想快速的使用各种 CSS 动画特效的话，你可以选择它。

创作者：Daniel Eden
发行：2013年
当前版本：3.5.2
人气：GitHub上有40000+的star
未压缩大小：72kB
GitHub：https://github.com/daneden/animate.css

```
Magic CSS3 Animation
```
Magic CSS3 Animations 是一个特殊效果的 CSS 动画库，你可以免费用于你的 Web 项目，简单的引用 CSS 样式：magic.css 
或 magic.min.css （压缩版）即可。该项目提供了一个特别酷的演示应用程序。与 animate.css 相比，
Magic CSS3 Animation 的大小适中，它的特色动画，如魔法效果，愚蠢的效果和炸弹效果十分出众和特别。

创作者：Christian
发行：2014年
当前版本：1.1.0
人气：GitHub上有4700+的star
未压缩大小：20.5kb
GitHub：https://github.com/miniMAC/magic

```
Hover CSS
```
Hover.css 是一个 CSS 动画库，专为您的网站中的按钮和其他 UI 元素而设计。它具有非常好的2D转换，以及许多其他精心制作的动画。

创作者： Ian Lunn
发行：2013年
当前版本：2.1.1
人气：GitHub上有16000+的star
未压缩大小：100+kb
GitHub：https://github.com/IanLunn/Hover

```
Effeckt
```
Effeckt.css 是一个集合了众多新鲜而又实用的的 CSS/jQuery 动画效果，这些都适用于网站或是移动 APP 的网页，
比如一些 AJAX 弹出框动画、菜单动画、图片标题展示等等，这些特效动画都能给你的网站提升一定用户体验，而且简单实用。

创作者：paulirish
发行：2013年
当前版本：0.5.0
人气：GitHub上有10900+的star
GitHub：https://github.com/h5bp/Effeckt.css

```
Single Element CSS Spinners
```
在页面中，我们时常需要使用 gif 图片来实现比较炫酷的 loading 动画。Single Element CSS Spinners是一个
CSS螺旋加载动画的集合。使用Single Element CSS Spinners 来替代 gif 来实现螺旋加载动画，不仅减少了请求图片的次数，
同时还能够通过代码来灵活地修改动画的参数。

创作者：Lukehaas
发行：2014年
当前版本：1.0.0
人气：GitHub上有4700+的star
未压缩大小：10kB
GitHub：https://github.com/lukehaas/css-loaders


注：一般不建议全部拿来使用，而是使用哪个动画效果就拷贝对应的样式。

```
## 10：[资料] 动画性能优化

##### 动画性能优化

CSS3 动画给 Web 的用户体验带来了巨大提升，本文将尝试从浏览器渲染的角度，来解析动画优化的原理及其技巧。
为大家提供一些动画性能优化的参考。

##### 60fps 与设备刷新率
目前大多数设备的屏幕刷新率为60fps（Frame per Second），即每秒60帧。因此，如果在页面中有一个动画或渐变效果，
或者用户正在滚动页面，那么浏览器渲染动画或页面的每一帧的速率也需要跟设备屏幕的刷新率保持一致，
即每一帧要在16毫秒（1S/60 = 16.66ms）之内完成。如果无法完成，由于帧率的下降会导致内容在屏幕上抖动。
此现象通常称为卡顿，会对用户体验产生负面影响。

##### 浏览器渲染
在讲性能之前，我们需要先对浏览器渲染页面有一个基础的理解。

##### CSS 图层
浏览器在渲染一个页面时，会将页面分为很多个图层，图层有大有小，每个图层上有一个或多个节点。需要注意的是，
如果图层中某个元素需要重绘，那么整个图层都需要重绘（关于重绘下面会讲到）。

##### 渲染过程
```
简单来说，浏览器的渲染过程其实就是将页面转换成像素显示到屏幕上，大致有如下几个步骤：

Javascript操作： 一般来说，我们会使用 JavaScript 来实现一些交互操作。比如用往页面里添加一些元素，切换显示隐藏等

style 样式计算： 该过程根据 CSS 选择器，获取每个元素匹配的 CSS 样式并计算其最终应用样式

Layout 布局：该过程计算元素要占据的空间大小及其在屏幕的位置。网页的布局模式意味着一个元素可能影响其他元素，
例如 <body> 元素的宽度一般会影响其子元素的宽度以及树中各处的节点，因此对于浏览器来说，布局是经常发生的

Paint 绘制：本质上就是填充像素的过程。包括绘制文字、颜色、图像、边框和阴影等。也就是绘制元素所有的可视效果

Composite 渲染层合并：在每个层上完成绘制过程之后，浏览器会将所有层按照合理的顺序合并成一个图层，然后显示在屏幕上

如果我们需要提高动画的性能，需要做的就是减少浏览器在动画运行时所需要做的工作。当 CSS 在进行动画时，其不同属性值引起的改变，
重新渲染可能会有三种执行路径：

A：layout -> paint -> composite
B：paint -> composite
C：composite
很明显，最短路径的 C 动画性能是最高的，所以我们在使用动画的时候就得考虑使用什么属性，以尽量减少执行路径。
```
##### 动画属性
CSS 的属性大致分为三类：布局类（layout），绘制类（paint），合成类（composite）。

##### 重排（reflow）
```
由元素的布局类属性改变所触发的行为过程，我们称为 reflow，也叫做 relayout（重新布局）。
当某个节点 reflow 时会重新计算节点的尺寸和位置，还可能会引起其它节点的 reflow。

该系列属性的改变，会执行路径 A 进行重新渲染，所以性能是最差的。（这充分说明，重排会引起重绘）
```
###### 触发重排的属性
```
盒子模型相关属性会触发重布局：

width
height
padding
margin
display
border-width
border
min-height
```
```
定位属性及浮动也会触发重布局：

top
bottom
left
right
position
float
clear
```
```
改变节点内部文字结构也会触发重布局：

text-align
overflow-y
font-weight
overflow
font-family
line-height
vertival-align
white-space
font-size
```
##### 重绘（repaint）
```
由绘制类属性改变触发节点重新绘制其可视效果的过程，我们称为 repaint。

该系列属性的改变，会执行路径 B，所以性能一般。

触发重绘的属性
修改时只触发重绘的属性有：

color
border-style
border-radius
visibility
text-decoration
background
background-image
background-position
background-repeat
background-size
outline-color
outline
outline-style
outline-width
box-shadow
上面的属性由于不会修改节点的大小和位置，因此不会触发重排，其只是改变了节点内部的渲染效果，所以只会进行重绘以下的步骤。
```
##### composite
```
目前只有两个属性属于 composite 类：

transform
opactiy
该系列属性的改变，会执行路径 C，所以性能最佳。

如果想了解更多 CSS 中会影响 Layout、Paint 和 Composite 的属性，可参考：CSS Triggers。
https://csstriggers.com/
```
##### 优化技巧
###### 减少动画元素
```
减少动画元素，是动画性能
优化中首先需要完成的。通过审查页面动画 DOM 元素结构，去除不必要的动画元素，
减少元素的数量，相应地会减少布页面局和绘制的时间。
```
###### 尽量使用 fixed、absolute 定位
对于动画元素，尽量使用用 fixed、absolute 定位方式，避免影响到其他节点重排。

###### 尽量只改变transform和opacity
能用 transform、opacity 优先使用，其属性的改变不会发生重排和重绘。如位移操作的，可以使用translate 来实现，
渐隐渐现效果可以使用 opacity 属性来实现。

###### 恰当开启硬件加速效果
```
对动画元素应用transform: translate3d(0, 0, 0)、will-change: transform 等来开启硬件加速。
通常开启硬件加速可以让动画变得更加流畅。但这里需注意，在不需要的时候需去掉避免过多的内存消耗。

transform: translate3d(0, 0, 0);

transform: translateZ(0);

will-change: transform;
更多阅读
渲染性能
```















