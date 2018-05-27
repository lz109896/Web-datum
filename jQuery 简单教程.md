1.	jQuery 简介
```
全球的访问量最高的1万个站点中，有65% 的站点中都使用了 jQuery 。不用为繁琐的原生jQuery 烦恼，
使底层操作变得容易，是一个开源的 js库，封装了很多功能，直接调用，大幅度精简代码

```
2.	引入 jQuery
分为本地的 jQuery 文件和内容分布式网络 CDN 。
```





```
3.	jQuery 中的 $
jQuery 下载地址：https://jquery.com/

jQuery 是一个函数,$ 是jQuery 的别名
$ === jQuery

$()--->jQuery 对象   类数组带有额外方法

$ : 包括方法 $.ajax、$.extend、$.each ......










4.	选择器
```
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
5.	遍历 DOM 元素
主要是: .parent()、parents()、.eq（）、.eq()、.siblings()、.children()、.find、....






6.	添加和移除 DOM 元素



7.	jQuery 事件监听



8.	 [资料] 事件代理



9.	[资料] jQuery 隐式迭代和链式调用




10.	jQuery 体系和文档
