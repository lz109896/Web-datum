#### CSS 基础部分
##### 第一章：CSS 基础
###### 第一节：认识CSS
```
Cascading Style Sheets:层叠样式表
```
###### 第二节：CSS语法
```
h1{color:red;font-size:20px}

释义语法：
h1    是选择器
；    是分隔符
color:red 和 font-size:20px    是声明语句
color 和 font-size             是属性
red 和 20px                    是值

正确的写法：例如：
h1 {
    color: red;
    font-size: 20px;
}
```
##### 第三节：练习：
```
/*
文字颜色(color)为“white” 
字体大小(font-size)为“16px” 
背景色(background-color)为“red” 
宽度为(width)为“200px”
*/

p {
  width: 200px;
  color: white;
  font-size: 16px;
  background-color: red;
}
```
###### 第四节：CSS 注释
```
前面有讲过 HTML 的注释，不清楚的同学可以回去看下哦。
CSS 注释的作用也差不多，只是语法不同，其语法如下：

/* 这是一行单行注释 */

/*
这个注释分散
在多个行上面
*/
来看几个例子。

辅助阅读注释
/* logo 样式 */
.logo {
 width: 200px; /* 宽度200px */
}

单行代码注释
/* logo 样式 */
.logo {
 /* width: 200px; */
}

多行代码注释
/* logo 样式 */
.logo {
    width: 200px;
    /* height: 100px;
    position: relative;
    left: 10px;
    top: 40px; */
}
```
###### 第五节：HTML中引入CSS
```
深入了解样式引入
我们已经学习了行内、内嵌和外链三种方式来引入我们的 CSS 样式，这里我们再深入探讨下。
```
行内方式
```
通过给元素添加 style 属性来添加样式，如下：
<div style="color: red;">颜色为红色</div>
<div style="color: red;">颜色为红色</div>

它有一个很明显的缺点：只能改变当前标签的样式，如果想要多个元素都使用同一种样式，
每个元素都要添加一遍，这样不仅导致HTML代码冗长难以阅读，而且后期维护起来也非常艰难。

所以我们一般不会大量使用这种方式添加样式，只有在少量使用 js 改变样式的时候使用。
```
内嵌方式
```
通过在<head>元素中使用<style>元素来定义：

<head>
    <style type="text/css">
        div {
            color: red;
        }
    </style>
</head>
该方法有效解决了第一个行内方式的带来的多元素不能重用同一个样式的问题，但是同时又暴露出
了另一个问题：没有办法和其他页面共用，只能本页面使用。所以当多个页面需要引入相同的 
CSS 代码时，这样写会导致代码冗余，也不利于维护。

这种方式我们一般在写简单 demo 的时候或者在移动端追求性能优化时使用。
```
外链方式
```
通过在<head>元素中使用<link>元素来引入：

<head>
    <link rel="stylesheet" type="text/css" href="style.css">
</head>
这是我们网页最常见的也是最推荐的引入 CSS 的方式，具备良好的可维护性。并且如果多个页面共用一个
CSS 文件的话，一般只在第一次加载时需要下载，以后切换页面时根本不需要加载该文件（浏览器一般有缓存）。
```
导入方式
```
其实除了上面三种方式之外，还有第四种方法，就是@import导入的方式。这种方式呢建议只作为一个了解，
千万不要使用。

引入方式如下：

<style>
    @import url(style.css);
</style>
可以看到这个这个方式也是引用一个外部CSS文件，那么和上面的外链方式有什么区别呢？

范畴不同： <link> 属于 HTML 元素，通过其href属性来引入外部文件；而 @import 属于 CSS，所以导入语句应写在
CSS 中，要注意的是导入语句应写在样式表的开头，否则无法正确导入外部文件

兼容性差别： @import 是 CSS2.1 才出现的概念，所以如果浏览器版本较低，无法正确导入外部样式文件；
而<link>则没有任何兼容问题；

加载顺序不同：当 HTML 文件被加载时，<link>引用的文件会同时被加载，而 @import引用的文件则会等页面
全部下载完毕再被加载

js 修改支持：<link>支持使用JavaScript控制DOM改变CSS样式，@import不支持

总结
在实际网页中我们应尽量使用 <link> 标签导入外部 CSS 文件，避免或者少使用其他三种方式。
```
###### 第六节：引入对应的CSS练习
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>使用样式</title>
    <!--
        外链形式引入normalize.css
        链接地址为：https://necolas.github.io/normalize.css/6.0.0/normalize.css
     -->

    <!--
        内嵌形式样式,内嵌样式代码为下面
        h1 { color: red; }
        p { font-size: 20px; }
     -->
     <link rel="stylesheet" type="text/css" href="https://necolas.github.io/normalize.css/6.0.0/normalize.css">
     <style type="text/css">
        h1 {
            color: red;
        }
    </style>
    <style type="text/css">
        p {
            font-size: 20px;
        }
    </style>
</head>
<body>
    <h1>我用来测试h1元素的样式</h1>
    <p>我用来测试p元素的样式</p>
</body>
</html>
```
###### 第七节：CSS调试

打开调试工具
```
1.快捷键
windows:f12
mac:cmm+optim+i
2.右键菜单
页面空白处，点击检查
3.浏览器入口
浏览器右上角3个点，点击更多工具，点击开发者工具
```
HTML 调试
```
1.树结构
2.选中元素
3.修改
```
CSS 调试
```
1.查看样式
2.修改样式
3.新增样式
```




