#### 第一节：选择器概述

![选择器](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/187812eefb1562f5e09fd649fa6a41d8e8eea026/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20180517172213.png)


#### 第二节：基本选择器
![基本选择器](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/ad5c86c825d1e2a2c91fdba310e4a377552e8f27/%E5%9F%BA%E7%A1%80%E9%80%89%E6%8B%A9%E5%99%A8.png)

#### 第三节：选择器分组(*重要)
![选择器分组](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/a0fdbc958d713ed47b6426f655f8cf0d26f03eec/%E9%80%89%E6%8B%A9%E5%99%A8%E5%88%86%E7%BB%84.png)


#### 第四节：关系选择器

![关系选择器](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/313f37e8654df0fd9d876967e20a5ceaf5087d82/%E5%85%B3%E7%B3%BB%E9%80%89%E6%8B%A9%E5%99%A8.png)

#### 第五节：伪类选择器
![伪类选择器](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/10a6ca868f8068b7e978ed811e9a7a01cbaf65c9/%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8.png)

![伪类选择器1](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/a891ad942ebf45f372cee4dfd18042057666fff5/%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A81.png)

![伪类选择器练习题](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/5c0533080349ff47ac93d6b48150eb99a0fee561/%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8%E7%BB%83%E4%B9%A0%E9%A2%98.png)

#### 第六节：伪元素选择器

![伪元素选择器](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/03fd7f6df1b91bbca342c4c78380b177d80ba20c/%E4%BC%AA%E5%85%83%E7%B4%A0%E9%80%89%E6%8B%A9%E5%99%A8.png)

##### 注：除了视频中的四个伪元素选择器外，其实还有一个 ::selection 表示选中的伪元素选择器。
```
更多伪元素的使用可参考：
https://developer.mozilla.org/zh-CN/docs/Web/CSS/content

伪元素：http://coding.imweb.io/demo/p2/selector-pseudo-element.html
学习web开发：https://developer.mozilla.org/zh-CN/docs/learn
```

#### 第七节：选择器指南
```
选择器是 CSS 中一个非常重要的知识块。总得来说，大体分为五大类：
基本选择器，关系选择器，伪类选择器，伪元素选择器，属性选择器。
前面4个我们已经说过了，这里先补充下属性选择器。
```
属性选择器
```
前面我们讲元素的时候已经说过，可以用一些属性来表示元素的一些特征。现在我们就可以利用这些特征来选中该元素，
如类选择器及id选择器，其实都是利用属性 class 和 id 的值构造起来的选择器，这可以视作 class 和 id 属性的
一种特殊待遇，而其他的属性就得按部就班来了。

总得来说，属性选择器搭配比较自由，既可以根据属性来选，也可以根据属性值来选，还可以根据部分属性值来选，具体规则如下：
选择器	描述
[attribute]	用于选取带有指定属性的元素
[attribute=value]	用于选取带有指定属性和值的元素
[attribute\^=value]	匹配属性值以指定值开头的每个元素
[attribute$=value]	匹配属性值以指定值结尾的每个元素
[attribute*=value]	匹配属性值中包含指定值的每个元素
[attribute~=value]	用于选取属性值中包含指定词汇的元素
[attribute|=value]	用于选取带有以指定值开头的属性值的元素，该值必须是整个单词

下面我们使用这四个 a 元素来具体实践下：
<a href="https://ke.qq.com" target="_blank">腾讯课堂</a>
<a href="css-basic.pdf" >CSS学习文档</a>
<a href="css.png" >CSS 脑图</a>
<a href="http://imweb.io" title=“IMWeb”>IMWeb学院</a>

要求如下：
选中 title 属性链接
选中新窗口打开的链接（可在后面添加一个icon，以区分其他链接）
选中不同的文件类型链接（可在后面添加对应的图标，以表示资源类型）
选中绝对路径链接

对应的选择器如下：
/* 选中 title 属性链接 */
a[title] {}

/* 选中新窗口打开的链接 */
a[target="_blank"] {}

/* 选中 pdf */
a[href$=".pdf"] {}

/* 选中 png */
a[href$=".png"] {}

/* 选中绝对路径链接 */
a[href^="http://"],
a[href^="https://"] {}

选择器参考手册
一下讲了这么多选择器，估计一时半会是消化不了的。不过没关系，我们可以慢慢来，
视频可以多看几次，也可以先有个印象继续学习后面的内容，然后再回过头来消化消化。
同时这里也为你找了一些非常具有参考价值的选择器文档，可以方便你学习查阅。

首先是W3school的选择器参考，归类很详细，非常适合入门学习：
http://www.w3school.com.cn/css/css_selector_type.asp

CSS 元素选择器
CSS 类选择器详解
CSS ID 选择器详解
属性选择器详解 | W3School
CSS 后代选择器
CSS 子元素选择器
CSS 相邻兄弟选择器
CSS 伪类
CSS 伪元素
或者直接参考选择器手册：

选择器参考手册 | MDN（点击相应的选择器为英文链接，可以在地址栏中将 en-US 换成 zh-CN 即可）
https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Selectors

CSS 选择器 | 菜鸟教程
http://www.runoob.com/cssref/css-selectors.html

选择器参考手册 | W3School
http://www.runoob.com/cssref/css-selectors.html

Selectors Level 3 | W3（官方参考手册，英文版）
Selectors Level 4 | W3（第四代选择器草稿）
选择器优化
现在我们知道了选择器有很多种，但是对于浏览器来说，解析每种选择器所耗费的时间并不是一样的。
所以当我们使用选择器的时候也有必要了解如何才能写出最优选择器。

选择器效率
根据网站效率专家 Steve Souders 指出，各种 CSS 选择器的效率由高至低排序如下

id选择器（#myid）
类选择器（.myclassname）
标签选择器（div,h1,p）
相邻选择器（h1 + p）
子选择器（ul > li）
后代选择器（li a）
通配符选择器（*）
属性选择器（a[rel="external"]）
伪类选择器（a:hover,li:nth-child）
以下面的 p 元素为例：

<p id="test" class="red">我用来测试选择器的优化</p>
我们可以通过很多种方法去选中它，如p，.red，#test，[class="red"]等等。但是如果按照执行效率来说，
id选择器是最佳的，其次是类选择器，然后是元素选择，最后才是属性选择器。

选择器解读顺序
一般来说，在具体的项目中，HTML 结构都比较复杂，所以关系选择器使用非常的普遍。对于关系选择器来说，
我们的阅读习惯是从左到右，但是浏览器解读选择器，遵循的原则是从选择器的右边到左边读取。

如对于选择器.list .item .item-tt，浏览器先找的是.item-tt，然后继续向父级元素寻找.item，
再找.list，这样才完成了最终的选择器匹配。

所以如果路径链越短，效率也就相应有所提高。这里建议选择器的层级最多不要超过4层，
如.demo .list .item .item-tt .tt-link就有5层了，可根据实际情况考虑缩短为4层以内，
如.demo .item-tt .tt-link

参考资料
如何提升 CSS 选择器性能
https://www.jianshu.com/p/268c7f3dd7a6

CSS选择器的优化
https://www.w3cplus.com/css/css-selector-performance

Efficiently Rendering CSS
https://css-tricks.com/efficiently-rendering-css/

```


