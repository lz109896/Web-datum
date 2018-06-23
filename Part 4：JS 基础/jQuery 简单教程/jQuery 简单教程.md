## 1.	jQuery 简介
```JS
全球的访问量最高的1万个站点中，有65% 的站点中都使用了 jQuery 。不用为繁琐的原生jQuery 烦恼，
使底层操作变得容易，是一个开源的 js库，封装了很多功能，直接调用，大幅度精简代码

```
## 2.	引入 jQuery
```JS
本地的 jQuery 文件
<script src="js/jquery.min.js"></script>.

内容分布式网络CDN1
//非压缩版
<script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.js"></script>       开发 

//压缩版 
<script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>   正式发布
```
示例
```JS

<IDOCTYPE html>
<html> 
<head> 
    <meta charset="UTF-8"> 
    <title>引入jQuery</title> 
</head> 
<body> 
    <h1>引入iQuery</hl>
    <p>https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js </p> 
    <script src="https://cdn.bootcss.com/jquery/3.2.1/iquery.min.js"></script> 
</body> 
</html>

$
function (a,b){return new r.fn.init(a,b)}
s. fn.jquery 
"3.2.1"
```
## 3.	jQuery 中的 $
```JS
jQuery 下载地址：https://jquery.com/

jQuery 是一个函数,$ 是jQuery 的别称
$ === jQuery

$()--->jQuery 对象   类数组带有额外方法

$(stirng)：传递参数
$('.footer');   //selector ,将类名为footer的元素转为jquery对象
$('<div></div>'); //是HTML text ,生成一个div的jquery对象

$(dom element) ：是dom 对象
//获取所有段落元素DOM.
var paragraphs = document.getElementsByTagName('p');
var $paragraphs = $(paragraphs); //将 DOM 转换为jQuery对象

//使用eq、get、索引
var $firstParagraph = $paragraphs.eq(0); // jQuery对象 
var firstParagraph = $paragraphs[0]; //DOM 
var secondParagcaph = $paragraphs.get(1); // DOM


$ : 包括方法 $.ajax、$.extend、$.each ......

```
## 4.	选择器
http://coding.imweb.io/demo/p4/jquery-selector.html
```JS
jQuery 选择器--实现-->CSS选择器

jQuery 选择器包括了：基本选择器、组合选择器、其他选择器

基本选择器包括：
$(tag): 按标签选择         例如：$('div');// 查找div 标签
$（.class）：按类名选择     例如：$('.footer');//查找类名为 footer 的元素
$(#id)： 按标签id选择       例如:$('#cat-tab');//查找标签id 为 cat-tab 的元素
$(*) ： 匹配所有元素         例如:$(*); //查找所有元素


组合选择器包括：
$(selector1,selector2) : 多元素选择器       例如：$('div,p');
$(selector1 selector2) : 后代元素选择器     例如：$('.footer p');
$(selector1 > selector2) : 子元素选择器     例如：$('.footer>p');
$(selector1 + selector2) : 毗邻元素选择器   例如：$('.footer + p');

其他选择器包括：
$(selector:first-child)  :  选取第一个子元素         例如：$('.footer:first-child');
$(selector:last-chlid)  :  选取最后一个子元素        例如：$('.footer:last-child');
$(selector:eq(index))  :  选取集合中第 index 个元素  例如：$('.item:eq(2)');
$(attribute=value)  :  选取属性值为 value 的元素     例如：$('[value=2]');


```
## 5.	遍历 DOM 元素
```JS
主要是最常用的这6种: .parent()、parents()、.eq（）、.eq()、.siblings()、.children()、.find、....

//获取父元素
$('#me').parent();
//获取所有父元素和祖先元素 
$('#me').parents();一个多个

//使用.eq()函数获取相应元素
$('#me').parents().eq(0); //获取爸爸 
$('#me').parents ().eq(1); //获取爷爷 
//使用.parents(selector)来精准查找 
$('#me').parents ('.fat);
$('#me').parents (.oldest');selector

//获取所有的兄弟元素
$('#me') . siblings();多个
//通过使用selector来精准查找
$('#me') . siblings ('.tall); selector 

//使用.children()获取子元素 
$('#grandPa').children();
//使用. find ('*')获取所有子孙元素
$('#grandPa').find('*');

//使用.find(selector)精准获取子孙元素
$('#qrandPa').find('.youngest');


              爷爷(grandPa)
       叔叔(uncle)          爸爸(father)
表弟(cousin)         大哥(brother)       我(me)$('#me')
             侄子(nephew)  侄女(niece)(.youngest)
```
## 6.	添加和移除 DOM 元素
http://coding.imweb.io/demo/p4/jquery-dom.html
```JS
append / appendTo 在被选元素的结尾插入内容
prepend / prependTo 在被选元素的开头插入内容
after /insertAfter 在被选元素乏后插入内容
before / insertBefore 在被选元素之前插入内容
```
演示
```JS
$(document. body). append('<div>哈哈哈</div>')
[body] 

s(document. body).prepend('<div>哈哈哈</div>')
[body]

$('<div>哈哈哈2</div>').prependTo(document. body)  
[div, prevobject: r.fn.init(1)] 

$('<div>哈哈哈2</div>'). appendTo(document. body)
[div, prevObject: r.fn.init(1)]

$('h1")
[hl, nl, hl, prevobject: r.fn.init(1)] 

$('h1').eq(0).after('<h2>呵呵呵</h2>') 
[h1, prevobject: r.fn.init(3)]

$('hi). eq(0).before('ch2>呵呵呵</h2>')-
[hi, prevobject: r.fn.init(3)]

$(<h2>呵呵呵2</h2>').insertBefore($('hi ).eq(0))
[h2, prevobject: r.fn.init(1)]
```
```JS
删除元素
$('#father').empty
$('#father')remove  (把自己都删除了)

选择 "#tree1" 的元素其 ".etc" 的子元素，这里使用 jQuery 的常用方法 remove 来去除元素
$('#tree1 .etc').remove();
选择 "#tree1" 的元素，这里使用 jQuery 的常用方法 after 来插入其兄弟元素 <div id="tree2"></div>
$('#tree1').after('<div id="tree2"></div>');
选择刚才插入的 "#tree2" 元素, 通过使用 jQuery 的常用方法 append 来插入子元素 ".item";
$('#tree2').append('<div class="item">tree2 子元素</div>');

$(document.body).append('<ch20s列表</h2><ub<li>mac</Lix<liwine/li></ub>');
[body]

```

## 7.	jQuery 事件监听
```JS
jQuery ：就是对原生JS的封装和对调用接口的优化，简化调用方式div

jQuery 事件包括：
触发事件的目标元素
触发的事件名称
事件触发时的回调
jquery 事件对象---> 封装原生事件对象：浏览器兼容、增加好用的属性和方法

$(触发事件目标元素).on(触发的事件名称, 事件触发时的回调);

$('#target')：事件的目标元素
on：事件监听函数,处理事件委托会比较方便的
functio：事件出发执行的回调callback
'click' ：监听的事件名称
event ：jquery事件对象

$('#target').on('click', function(event) {
    console. log( 'target'); // 被点击了
    $('body').css ('background', '#ffo');
}):


```
```JS
$('a")on('click', function(event) {
    console.loa(event.target); //获取触发事件的元素 
    event.preventDefault(); //阻止默认事件 
    event.stopPropagation(); //阻止事件冒泡
});


$('a').on('click', function(event) {
    console.log(event.target); //获取触发事件的元素 
    return false; //既阻止默认事件,且阻止事件冒泡
});
```
```JS
jQuery快捷方法click()

//使用快捷函数click 
$('#target').click(function(event) { 
    console.log('target');   //被点击了 
    $('body').css ('background','#ff0');
});


封装的其他事件类型，可以在官网去查查
focus()
blur()
keydown()

```
## 8.	 [资料] 事件代理

### 事件委托
```JS
一般来说我们要给某个元素绑定事件，都会直接绑定在该元素上，如下：

// 给 li 元素绑定点击事件
$('li').click(function() {
    console.log('你点击我了');
})
但是这种直接的处理会有以下问题：

通过 JS 新添加的 li 元素并没有该事件绑定，所以点击无效
元素如果比较多的话，比喻有200个 li ，那每个 li 都绑定一个事件，性能是非常低的
那么如何解决这些问题呢？这就是我们要说的事件委托（或叫事件代理）。

事件委托简单来说就是利用事件冒泡，只指定一个事件处理程序，用来管理某一类型的所有事件。

以一个 todo list 为例：

// 要点击的元素是 todo-item
// 但是我们把事件绑定在父元素 todo-list 上，实现事件委托
// html 结构为：ul#todo-list>li.todo-item*5

$('#todo-list').on('click', '.todo-item', function() {
    $(this).toggleClass('done');
})
以 jQuery 为例，所以我们看不到背后的本质，下面我们以一个原生的实现来说明下：

var todoList = document.getElementById("todo-list");

todoList.addEventListener("click", function (e) {
    var target = e.target;
    // 检查事件源 target 是否为 todo-item
    if (target && target.nodeName.toUpperCase() == 'LI' && target.classList.contains('todo-item')) {
        target.classList.toggle('done')
    } else {
        console.log('我不是 todo-item ');
    }
});
注：因为事件委托是依赖于事件冒泡的，所以没有事件冒泡的事件是不能使用事件委托的。

参考资料
实例分析JavaScript中的事件委托和事件绑定
javascript: 事件委托解析
事件委托
```
## 9.	[资料] jQuery 隐式迭代和链式调用

### jQuery 隐式迭代和链式调用
```JS
学过 jQuery 之后，一般是不太有人再愿意写原生 JS 的，甚至有段时间 jQuery 成了 JS 的代名词。原因无他，足够简单方便。
可在这简单方便的背后，可少不了两大功臣：隐式迭代和链式调用。
```
### 隐式迭代
```JS
对于原生 JS 来说，一般我们设置某类元素的样式，都得使用循环设置，而 jQuery 在使用的时候则无需考虑这点，简单示例如下：

// 设置 .primary 元素的文字颜色为 #188eee

// 原生 JS
var primary = document.getElementsByClassName('primary');
for(var i = 0, len = primary.length; i < len; i++) {
    primary[i].style.color = '#188eee';
}

// jQuery
$('.primary').css('color', '#188eee');
这是因为 jQuery 的方法内部存在隐式迭代，它会对匹配到的所有元素进行循环遍历，执行相应的方法；
无需我们再手动地进行循，方便我们使用。

除了隐式迭代外，jQuery 还提供了 each 方法，方便有需要的时候调用。比喻要对每个元素做不同的处理：

$("li").each(function(i){
   $(this).addClass('item-'+i);
 });
注：jQuery 还有一个全局的 each 方法，用于遍历对象或数组，具体可参考：$.each
```
### 链式编程
```JS
从前我们要对某个元素进行一系列操作，只能一个一个来，而 jQuery 提供了链式操作，操作起来简直是不能再爽，如下：

// 原始版
$('div').hide(); //隐藏页面上所有的div元素
$('div').text('new content'); //更新所有div元素内的文本
$('div').addClass("updatedContent"); //在所有的div元素上添加值为updatedContent的class属性
$('div').show(); //显示页面上所有的div元素

// 重写版，链式
$('div').hide().text('new content').addClass("updatedContent").show();

// 缩进版
$('div')
  .hide()
  .text('new content')
  .addClass("updatedContent")
  .show();
其原理就是每个方法的最后都返回了 this 对象，我们可以使用一份简单的代码演示下：

// 定义类
function Person(opt) {
    this.name = opt.name;
    this.age = opt.age
}

// 定义 getName 方法
Person.prototype.getName = function() {
    console.log(this.name);
    return this; // 返回 this 对象
}

// 定义 sayHello 方法
Person.prototype.sayHello = function() {
    console.log('hello the world');
    return this; // 返回 this 对象
}

// 新建一个叫 next 的 Person 类
var next = new Person({
    name: 'next'
});

// 链式调用 getName 和 sayHello 方法
next.getName().sayHello(); 
更多关于 jQuery 的源码分析可参考：jQuery源码分析系列:http://www.cnblogs.com/aaronjs/p/3279314.html

```
## 10.	jQuery 体系和文档
官网地址学习，下载版本

jquery 不只是一个库，是一个体系了，非常经典，学习他的设计思路
http://jquery.com/
