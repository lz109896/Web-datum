## 1.	DOM 简介
```JS
Document Object Model ：文档对象模型

htnl 树-->DOM 树-->渲染成界面
Javascript 通过 DOM 修改样式，新增删除元素-->渲染成界面

DOM 是针对HTML 文档的一个API应用程序编程接口

```
## 2.	DOM 节点
```JS
node  是一个对象：（nadeName,nodeType,parenNode,childNodes...）
      方法：appendChild(),inserBefore()...
      
      有十二种类型;DOCUMENT_NODE,  ELEMENT_NODE,  TEXT_NODE,  DOCUMECT_FRAGMENT_NODE.....

小技巧：直接打印对象的属性：例如：console.dir(document)
元素节点：document.body

node （节点）是一个对象，可以通过它的属性 parentNode 访问它的父节点，可以通过 childNodes 属性获取它的子节点。
可以回忆下我们视频里的 node 树。
html 树会被浏览器构建成 DOM 树，DOM 树就是一个一个的节点构成，这些节点都是对象，有访问父、子的属性，当然还有其他大量的属性。

```
## 3.	常用节点类型

类型 | 常量 | nodeType | nodeName
---- | ----- | ------- | ------
Element类型 | ELEMENT_NODE | 1 | 元素的标签名
Text类型 | TEXT_NODE | 3 | #text
Document类型 | DOCUMENT_NODE | 9 | #document
DocumentFragment类型 | DOCUMENT_FRAGMENT_NODE | 11 | #document fragment

## 4.	常用节点类型之 Node 接口
http://coding.imweb.io/demo/p4/dom-node-type.html
```JS
常用节点类型实例

Node接口介绍
console.dir(Node) ：查看 function Node、 有定义的常量等等....

```
## 5.	常用节点类型之 Document
```JS
Document类型

console.dir(Documente) 
.Document 是抽象的文档
·不是 html 元素，可以访问到 html 
·挂靠各种常用的api

document.documentELement   =====这个是HTML元素
document.getELementsByTaaName ('ul') ====常用的API
document. createELement () ====常用的API
```
## 6.	常用节点类型之 Element
```JS

Element类型
.HTML元素
·属性
·创建/删除元素

选中元素后，在console 里面 使用 $0  ：快捷引用

创建元素 'class'
var div = document.createELement('div');
div.id = 'id';
div.className = 'class';
console.dir(div);

删除元素
操作步骤：选中一个要删除的元素
在控制台 Console 中打开
$0.parentNode. removeChild($0);
```
## 7.	常用节点类型 之 Text
```JS
Text 类型用调试工具其实很难选到的，只能选一个节点
console.dir($0) 
子元素就是文本节点


Text 是文本类型
.data和nodeValue
·创建文本节点

创建文本节点 : 2342
var.ext = document.createTextNode('2342');
text.data = 'change'; 
console.dir(text):
```

```JS
/**
 * 创建一个 p 元素，要求如下：
 *
 * 将其 id 属性设置为 first-element
 * 将其 title 属性设置为“我的第一个元素”
 * 将其赋值给变量 `myFirstElement`
 */

var myFirstElement = document.createElement('p');

myFirstElement.id = 'first-element';
myFirstElement.title = '我的第一个元素';

创建元素的方法只有 createElement(tagName) 一个，只此一家，别无分店。

既然元素也是节点的一种，所以它也是对象，给对象新增一个属性，用 . 操作符即可。

捎带提下，还有创建文本节点的方法 createTextNode(string) ，例：

var textNode = document.createTextNode('你的第一个文本节点！');
当然，这些方法还只是理论，后面我们会实践，将这些创建的节点塞到我们的文档中！
```
## 8.	DOM 查找

```JS
查找所有的 div 元素 ：document.getElementsByTagName('div')
查找更具体的元素，比如腾讯课堂的logo 标签:document.querySelector('.header-index-logo')
```
```JS
常用的查找 API：
document.getElementByID（）
[document | Element].getElementsByClassName()  不兼容老版浏览器，兼容i8以上
[document | Element].getElementsByTagName()
[document | Element].querySelector()                        是CSS选择器
[document | Element].querySelectorAll()  比较通用，强大      是CSS选择器


var id = document.getELementById('id'); //一个元素 
console.log(id);

var cls = document.getElementsByClassName('class');
console.log('class',cls); // HTML Collection多个元素 

var tag document.getElementsByTagName('Li');
console.log('tag', tag);

var qId = document.querySelector('#id');
console, log('qId', qId);

var qAllLi = document.querySelectorAll('Li');
console.log('qAllLi',qALLLi);

var qLi = document.querySelector('Li');
console.log('qLi',qLi);

```
```JS
getElementById(ID) 根据 id 属性的值来获取元素，获取一个元素
getElementsByClassName(CLASS) 获取所有 class 属性的值为 CLASS 的元素
getElementsByTagName 根据标签名来获取元素，会选中多个元素
querySelector 和 querySelectorAll ，根据指定 CSS 选择器来获取元素，第一个获取一个，第二获取多个元素
```

## 9.	DOM 新增和删除
```JS
createElement(tag) 创建元素
createTextNode(content) 创建文本节点
appendChild(element) 新增节点到父元素的末尾
insertBefore(element, target) 新增节点到 target 元素的前面
```JS
<!DOCTYPE html>
<html lang="zh-CN"> 
<head> 
      <meta charset="UTF-8"> 
      <title>DOM 的新增和删除</title> 
</head>
<body> 
      <h1>DOM 的新增和删除示例</h1> 
      <ul> 
            <li>新增一个元素</Li> ----在这行<li>之前插入元素insertBefore()
            <li>新增多个元素</li> 
            <li>删除一个元素</li> ----- removeChild()
            <li>删除多个元素</li> ----在这行</li>之后插入追加
      </ul>               |
</body>                 在最后面 追加  append Child()
</html>

直接操作 DOM 回导致浏览器反复渲染  

DocumentFragment:不在 DOM 树之内，看不到的，它是游离在 DOM 树之外，需要新增多个节点的时候，可以临时的存放到仓库中

1、文档片段,"轻量级"的节点 
2、nodeType = 11
3、nodeName = #document-fragment
4、作为仓库来使用

```

## 10.	新增 DOM 示例
```js
var h2 = document.createELement('h2');
var h2Text = document.createTextNode('OS列表');

h2.appendChild(h2Text);
document.body-appendChild(h2);

var ul = document.createElement('ul');
dcument.body.appendChild(ul);

var osList = ['mac','win','Linux'];
for (var i= 0, len = osList.length; i < len;i++) {
      var li = document.createElement('1i');
      var liText = document.createTextNode(osList[i]);
      li.appendChild(LiText);
      ul.appendChild(ti);
}
```

## 11. 使用 fragment 新增 DOM
```js
var osList = ['mac'.'win','Linux']; 
var frag = document.createDocumentFragment();
for (var i = 0, Len = osList.Length; i < len; i++) { 
      var li = document.createELement('li');
      var liText = document.createTextNode(osList[i]);
      li.appendChild(LiText);
      frag.appendChild(1i);
} 
ul.appendChild(frag);
```
## 12.	删除 DOM 示例
```js
var h2 = document.querySelector('h2');
document.body.removeChild (h2); -----删除单个

var 1i = document.querySelectorAll('li");
for (var i = 0, len = li.lenath;i < len; i++）{
      li[i].parentNode.removeChild(li[i]);
}                          ---------删除多个
```
## 13.	property 和 attribute
```js
<div class="content" style="color: red;"> 
      <a href="https://ke.qq.com/">腾讯课堂</a> 
</div>
class、style、href属于html 属性

```
```js
    { 
      nodeName
      .....
      className 
      style 
      childNodes: [
       {
        nodeName 
        href
      }
    ]
}

属性：property 
className、style 、href 属于特性：attribute

node.div
    |转换
    |——> node.a
```
```js
property 和 attribute 的区别
1.公认的attribute会映射到Property
2.读写方式
3.特别的值,如class, style等
```

## 14.	DOM 修改样式
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/1bd58238864f3ab662dc129ac51dc82c436d3292/DOM%20%E4%BF%AE%E6%94%B9%E6%A0%B7%E5%BC%8F%201.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/1bd58238864f3ab662dc129ac51dc82c436d3292/DOM%20%E4%BF%AE%E6%94%B9%E6%A0%B7%E5%BC%8F%202.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/1bd58238864f3ab662dc129ac51dc82c436d3292/DOM%20%E4%BF%AE%E6%94%B9%E6%A0%B7%E5%BC%8F%203.png)

## 15.	DOM 修改内容
```JS
通过 文本节点 修改内容

$0
<a href="http://ke.qq.com/">腾讯课堂</a> 
$0.childNodes
[text]
$0.childNodes[0l 
"腾讯课堂" 
$0.childNodes[0].data = '腾讯课堂就是好!';
"腾讯t就是好!;
```
```JS
通过 innerHTML 和 outerHTML 修改内容

$0
<li>innerHTML和outerHTML</Li>
$0.innerHTML = <ul><li>innerHTM</li><li>outerHTML</li></ul>';
<ul><li>innerHTML</li><li>outerHTML</li></ul>"


```JS
/**
 * 将其 id 属性更新为 update
 * 新增一个类名 new
 * 将其内容更新为 “我第一次修改元素的内容”
 */
var dom = document.getElementById('waiting');
var className = dom.className;

dom.id = 'update';
dom.className = className + ' new'; // 兼容所有浏览器，注意 'new' 前的空格
dom.innerHTML = '我第一次修改元素的内容';

```

## 16.	DOM 遍历
```JS
var domLi = document.getElementsByTagName('li');
for (var i = 0, len = domLi.length; i < len; i++) { 
      console.log (domLi [i]);
}


HTMLCollection : domLi  

length  : 动态集合
```
```JS
遍历动态集合，的时候 length 保存在局部变量里面

children

var domUl = document.getElementsByTagName ('ul') [0];
var domLi = domUl.children;
var newLi = null; 

for (var i = 0; i < domLi.length; i++) {
      newLi = document.createElement('li');
      domUl.appendChild(newLi);
console.log(i);
}
```
![]()

## 17.	DOM 遍历示例
```JS
遍历所有的li,所有的子元素都能访问到

function traversal(dom) { 
      var len = dom.length;
      var i= 0;
      var d= null:
      
      for (; i< len; i++) { 
            d= dom[i];
            console.log(d);
            if (d.children) {
            traversal(d.children); 
            }
      }
}        

traversal(document. querySelector('ul').children);
```
```JS
所有的文本节点都能打印出来
有换行符就会有文本节点，文本节点会自动拼接

function traversal(dom) { 
      var len = dom.length;
      var i= 0;
      var d= null:
      
      for (; i< len; i++) { 
            d= dom[i];
            console.log(d);
            if (d.children) {
            traversal(d.childNodes); 
            }
      }
}        

traversal(document. querySelector('ul').childiNodes);
```
![]()
