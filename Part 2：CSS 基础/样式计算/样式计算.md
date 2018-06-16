#### 第一节：样式的继承与层叠
```
样式的继承







```
#### 第二节：样式优先级
```
选择器优先级
important(最高，不建议使用)-->style-->id选择器-->类选择器-->元素选择器-->*-->浏览器默认-->继承（最低）

```
```
值的计算
通过前面的学习，我们知道了一个元素的样式可能来自三个部分：

继承自父级元素的样式
元素的浏览器默认样式
元素自己声明的样式
而最终应用的样式就是这三个部分通过一套复杂的计算体系得到的。

应用值
我们把最终应用的样式称之为应用值（used value）。

如果元素本身声明了样式，那么我们的应用值将采用元素声明的样式，这点我们没有什么问题了。
但是如果元素没有声明该样式呢，它究竟用什么值来当做最终的应用值？

这就得回到我们的 CSS 属性定义了。

每个 CSS 属性在定义的时候都指出了该属性是默认继承的还是默认不继承的（本文下面附加了些常见的继承属性及非继承属性）。
这就决定了如果元素没有声明该样式，怎么得到最终的应用值：

如果属性是默认继承的，则取父元素的同属性的应用值（computed value）。
通过该方式得到的值我们称之为继承值（inherit value）
如果属性是默认不继承的，则取该属性的初始值（initial value）
这样，除应用值外，我们又有了两种新值，它们分别为继承值（inherit value）和初始值（initial value）。

继承值
为了进一步说明继承值，我们举个简单的例子来说明下，代码如下：

<p class="red" style="color: red;"><span>我继承了父元素的红色</span></p>
我们给<p>元素设置了文本颜色为红色，<span>没有任何设置。

在计算<span>元素的最终颜色时，因为该元素本身没有声明color属性，且由于color属性属于默认继承类型的，
所以会取父元素color属性的应用值（红色）。这样<span>通过父元素继承过来的值就是红色，
而最后的应用值用得就是该继承值。

当然我们还可以通过显式设置color属性的值为继承值，如color: inherit;。

注：inherit关键字用于显式地指定继承性，可用于继承性/非继承性属性。

初始值
每个属性都会有一个默认的初始值，如width属性的初始值为auto，font-size的初始值为medium。

初始值针对不同类别的属性具有不同的含义：

对于继承属性, 初始值只能被用于没有指定值的根元素（HTML）上
对于非继承属性 ,初始值可以被用于任意没有指定值的元素上
在CSS3中允许使用initial关键词明确的设定初始值。如font-size: initial;就是使用初始值。

其余值
除了上面的三种值之外，其实还有几种值的概念，如指定值（Specified value）、计算值（computed value）等等，
具体可参看：Assigning property values, Cascading, and Inheritance。（如果你能理解过来，那当然最好了，
如果实在理解不了，可以先忽略，以后慢慢的自然就懂了）

附
默认没有一个官方地址查看所有的继承属性或非继承属性，不过可以单独查看某个属性是否属于继承或非继承属性，
如在 MDN 的参考手册中查看color属性，在“是否是继承属性”那一栏就写了“yes”，截图如下：



常见继承属性
文本相关属性都可以继承

color、font、font-family、font-size、font-style、font-variant、font-weight、
text-decoration、text-transform、letter-spacing、word-spacing、white-space、
word-break、overflow-wrap、line-height、direction、text-indent、text-align、text-shadow

列表相关属性

list-style-image、list-style-position、list-style-type、list-style

表格相关属性

border-collapse、border-spacing

visibility 和 cursor

常见非继承属性
盒模型相关属性

margin、border、padding、height、min-height、max-height、width、min-width、max-width、box-sizing

布局类属性

display、overflow、position、left、right、top、bottom、z-index、float、clear、table-layout、vertical-align

系列类

background 系列、transform 系列、transtion 系列、animation 系列、flexbox 系列、grid 系列

```
#### 第二节：CSS 重置
```
normalize (属于纠正)

h1 {
    margin: 0.67em 0;
}
不是想要的

```
```
Eric Meyer's "Reset CSS"2.0 （属于清零）

h1 {
    margin: 0;
}

一竿子打死
```
```
normalize.css + 部分清零
```
```
浏览器兼容
首先浏览器有很多种，每种浏览器会存在一定的差异，其次每个浏览器都有不同的版本，
版本之间也存在必然的差异，而我们做出来的页面则需要各个浏览器以及不同版本表现一致，所以必然存在兼容问题。

一般来说兼容问题我们可以分两步走：第一步是确定浏览器是否支持，第二步是如果表现不一致，怎么去修复。

浏览器是否支持
技术总是在不断改进和发展的，新的东西一出来，那老的一些版本浏览器可能就不支持了。就如我们手机的发展，
总不能让以前的功能机安装我们智能机的 APP 吧。

一般来说，由于技术的不断改进和发展，大概存在以下几种问题：

新技术在老版本的浏览器总是不支持的（如ie8以下对 CSS3 支持几乎是空白）
由于新技术刚出现时，可能还没有完全定稿标准化，所以各个新浏览器一般都是先试探性的使用前缀的办法使用
同样的技术在不同的浏览器上可能表现也不一样。
对于这些问题，我们可以查阅 Can I use ，里面提供了各种浏览器支持情况。

以 CSS 的 flexbox 为例，我们在搜索框输入关键词”flexbox”，下面就显示了其对应的浏览器支持情况，
为了更加清楚了解，还可以点击图表左上角的按钮“show all”展开更多浏览器版本查看。


在查阅 Can I use 的时候，我们可以看到有些版本的右上角标有-符号，这就标识该版本得使用前缀，
目前我们常见的前缀有-webkit（webkit内核浏览器）、-ms（ie/edge）、-moz（火狐浏览器）

这里以圆角（border-radius）为例说明下前缀用法（当然现在圆角已经不需要写前缀了）：

.box {
    -webkit-border-radius: 5px; /* webkit内核浏览器（chrome、safari） */
    -moz-border-radius: 5px; /* 火狐浏览器 */
    border-radius: 5px; /* 标准语法 */
}
注：我们课程中的所有的代码都不会考虑前缀问题，但是不用担心，后面的自动化构建课程中，
我们会介绍使用 autoprefix 来自动处理这些前缀问题。

如何针对修复
如果问题出现了，我们怎么针对某些浏览器进行特定的修复而不影响到其他正常的浏览器。

这个时候就可以参考各个浏览器hack详细，里面提供了针对各种浏览器单独写样式的很多方法
（不一定所有办法都可以，但是你可以挑选一个可以的）

以修复 IE6、7 不兼容 inline-block 为例，我们挑选一条如下在属性前面加*的修复：

最终代码如下：

.inline-block {
    display: inline-block;
    *display: inline;
    *zoom: 1;
}

```
