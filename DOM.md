#### 1.	DOM 简介
```
Document Object Model

JS通过 DOM 修改样式，新增删除元素-->渲染成界面
htnl 树-->DOM 树-->渲染成界面

DOM 是针对HTML 文档的一个API应用程序编程接口

```
#### 2.	DOM 节点
```
node  是一个对象：（nadeName,nodeType,parenNode,childNodes...）
      方法：appendChild(),inserBefore()...
十二种类型;DOCUMENT_NODE,  ELEMENT_NODE,  TEXT_NODE,  DOCUMECT_FRAGMENT_NODE.....

小技巧：直接打印对象的属性：例如：console.dir(document)
元素节点：document.body

node （节点）是一个对象，可以通过它的属性 parentNode 访问它的父节点，可以通过 childNodes 属性获取它的子节点。
可以回忆下我们视频里的 node 树。
html 树会被浏览器构建成 DOM 树，DOM 树就是一个一个的节点构成，这些节点都是对象，有访问父、子的属性，当然还有其他大量的属性。

```
#### 3.	常用节点类型
```


```
#### 4.	常用节点类型之 Node 接口
```


```
#### 5.	常用节点类型之 Document
```


```
#### 6.	常用节点类型之 Element
```



```
#### 7.	常用节点类型 之 Text
```
 Text 类型用调试工具其实很难选到的，只能选一个节点


```
```
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
```
#### 8.	DOM 查找

```
查找所有的 div 元素 ：document.getElementsByTagName('div')
查找更具体的元素，比如腾讯课堂的logo 标签:document.querySelector('.header-index-logo')
```
```
常用的查找 API：
document.getElementByID（）
[document | Element].getElementsByClassName()  不兼容老版浏览器，兼容i8以上
[document | Element].getElementsByTagName()
[document | Element].querySelector()
[document | Element].querySelectorAll()  比较通用，强大
```
```
getElementById(ID) 根据 id 属性的值来获取元素，获取一个元素
getElementsByClassName(CLASS) 获取所有 class 属性的值为 CLASS 的元素
getElementsByTagName 根据标签名来获取元素，会选中多个元素
querySelector 和 querySelectorAll ，根据指定 CSS 选择器来获取元素，第一个获取一个，第二获取多个元素
```
#### 9.	DOM 新增和删除
```
createElement(tag) 创建元素
createTextNode(content) 创建文本节点
appendChild(element) 新增节点到父元素的末尾
insertBefore(element, target) 新增节点到 target 元素的前面





```
#### 10.	新增 DOM 示例
```


```
#### 11.	使用 fragment 新增 DOM
```



```
#### 12.	删除 DOM 示例
```



```
#### 13.	property 和 attribute
```





```
#### 14.	DOM 修改样式
```


```
#### 15.	DOM 修改内容
```
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
#### 16.	DOM 遍历
```






```
#### 17.	DOM 遍历示例
```





```
