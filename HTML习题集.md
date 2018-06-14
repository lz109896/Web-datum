## 1.准备工作

* [HTML 入门](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML)
* [HTML 元素参考 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element)
* [HTML 参考手册 | w3school](http://www.w3school.com.cn/tags/)

## 创建链接

### 实例
```html
从一个页面转到另一个页面就是Web的魅力所在，而这之间的跳转正是通过<a>元素链接来完成的。

现在就让我们也来创建一个链接，让其跳转到”腾讯课堂”，代码如下：

<a href=“https://ke.qq.com”>腾讯课堂</a>
```
### 知识讲解
HTML 中的 <a>元素 (或HTML锚元素, Anchor Element) 用于定义一个超链接到其他网络页面或文件，页面内的某个位置，电子邮件地址或其他任何URL。

### 页面跳转
当其用于页面之间的跳转时主要有三个常用属性，分别为：
* title：指链接标题，一般与内容文字一样。鼠标滑过时暂停一会，会有个title提示效果，
* href：指定链接的目标地址（如果暂时不能确定目标地址可先用#表示）
* target：定义打开窗口方式，默认是当前窗口打开，有四种取值，分别为：
  * _self：当前窗口打开，此值为默认值
  * _blank：新窗口打开（该值是使用最多的）
  * _parent：表示在当前框架的父框架打开（一般用于iframe中，先不用了解，以后再说）
  * _top：表示顶层框架打开（一般用于iframe中，先不用了解，以后再说）
  
### 页面内跳转
我们先打开一个有页面内跳转的页面：JavaScript秘密花园:https://bonsaiden.github.io/JavaScript-Garden/zh/

滚动鼠标到底部，发现其就是一篇文章。然后点击右边的导航试试，发现只要一点击，中间的内容就会定位到对应导航的内容部分，这其实就是页面内跳转。

仔细看下其地址栏的，你会发现只有后面的“#xxxx"部分发生变化
```html
当<a>元素用于页面内的锚点跳转时，应该先为该页面设置一些锚点，而定义锚点有两种办法：

通过<a>元素的name属性来定义，如：<a name="anchor-name">name属性的值就是锚点的名称</a>
通过其他元素的id属性来定义，如：<div id="anchor-name">id属性值可以作为锚点的名称</div>
设置好了锚点之外，就可以通过<a>元素链接到该锚点位置，其href取值为“# + 锚点名称”，示例如下:

<a href="#anchor1">锚点链接一</a>
<a href="#anchor2">锚点链接二</a>

<div>
    <div>我这里有很多内容...</div>
    <!-- 使用a的name属性定义锚点 -->
    <a name="anchor1">点击锚点链接一，会跳到我这里</a>
    <div>我这里有很多内容...</div>
    <!-- 使用元素的id属性定义锚点 -->
    <p id="anchor2">点击锚点链接二，会跳转到我这里</p>
</div>
```
### 电子邮件
```html
当其用于邮件链接时，href属性的值为“mailto: + 邮件地址”，示例如下：

<a href="mailto:xuyc_brother@foxmail.com”>发送邮件给我</a>
```
### 题目
```html
创建一个链接，点击新窗口打开 IMWeb 官网，链接地址为“ http://imweb.io/ ”。

答案：
<a href="http://imweb.io/" target="_blank">IMWeb学院</a>
```

## 2.创建图片
网页中的图片除了用<img>元素创建外，还可以使用CSS的背景图的形式表现

知识讲解
首先<img>元素没有闭合标签，这点一定要记得。

除此之外，<img>元素还有几个重要属性如下：

src：必备属性，表示图片地址
alt：必备属性，如果图片加载失败将会显示该内容
width：可选属性，用于设置图片的宽度，如width="400"
height：可选属性，跟width类似，用于设置图片的高度，如height="300"
然后在实际页面中，有些图片还是个链接，点击图片会跳转到其他页面，那究竟是怎么回事呢？

其实无非是把图片放在了<a>元素里面当做了内容，如下代码，即可产生一个图片链接：

<a href=“https://www.lagou.com/jobs/1715898.html” target=“_blank”>
    <img src=“http://coding.imweb.io/img/p1/img-2.png” alt=“imweb 前端招聘了”>
</a>
最后，更多关于<img>元素知识可参看：<img>。


## 3.创建列表


## 4.创建表格


## 5.创建表单
