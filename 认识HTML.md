#### 第一章：HTML 语法
##### 第一节：认识HTML
```
1.点离开任何网页，右击，都会出现显示“查看源代码”的选项。
```
##### 第二节：HTML 基础结构
```
<!DOCTYPE html>
<html>
<head>
    <title>基本HTML结构</title>
</head>
<body>
    <h1>我是一级标题</h1>
    <p>我是一段文本段落</p>
</body>
</html>

释义：
<!DOCTYPE html>  文档声明，告诉浏览器使用哪个HTML版本进行解析**千万不要忘记**
例如：<!DOCTYPE HTML PUBLIC"-//W3C//DTD HTML 4.01//EN""http://www.w3.org/TR/html4/stritct.dtd">

<html>
......
</html>
属于html 元素，顶级元素或根元素；只能包含 head 元素或者 body 元素

<head>
    <title>基本HTML结构</title>
</head>
属于<head> 元数据
例如：《word 文档》内容：标题、段落....
     元数据就是：文件名、创建时间、修改时间....

title：表示页面的名称是什么。还会显示在标签页的浏览器上<链接>

<body>
    <h1>我是一级标题</h1>
    <p>我是一段文本段落</p>
</body>
body元素:存放页面的内容

```
###### 深入了解 head 元素
```
<head>元素用于定义网页的常规信息和元数据，虽然在网页中不可见，但是也是非常的重要。
（该篇文档对于现在的你可能有点困难，可以先简单过下有个印象，等学完 p3 再回过头来查看）

总得来说其里面的子元素大概分为三类，分别是：
1.描述网页基本信息的，
2.指向渲染网页需要其他文件链接的，
3.各大厂商根据自己需要定制的。

网页基本信息
一个网页，首先得有个标题，就跟人有名字一样。除此之外，还可以根据实际需要补充一些基本信息。

文档标题（浏览器标签中显示的文本）：<title>深入了解 head 元素</title>
编码格式：<meta charset="utf-8">（你可能还看到 gb2312格式，不过不建议使用），
如果你的页面出现乱码，那一般就是编码格式不对
视窗设置：<meta name="viewport" content="width=device-width, initial-scale=1.0">
搜索引擎优化相关内容： <meta name="description" content=“帮助你深层次了解HTML文档结构”>
IE浏览器版本渲染设置：<meta http-equiv="X-UA-Compatible" content="ie=edge">
其他文件链接
一个完整的网页光有 HTML 结构是非常简陋的，就如一个毛坯房。有了结构之后，我们还需要加入样式与行为为网页增添色彩。

指向渲染网页
CSS 文件：<link rel="stylesheet" type="text/css" href="style.css">
JavaScript 文件：<script src=“script.js"></script>

厂商定制
比喻开启双核浏览器先河的360浏览器就定制了一个默认使用哪个内核来渲染页面，
可以设置为 webkit 内核、IE 标准，IE 兼容三种模式。代码分别为：

<meta name="renderer" content="webkit"> <!-- 默认webkit内核 -->     
<meta name="renderer" content="ie-stand"> <!-- 默认IE标准模式 -->
<meta name="renderer" content="ie-comp"> <!-- 默认IE兼容模式 -->
同样分享页面到QQ的聊天窗口，有些页面直接就是一个链接，但是有些页面有标题，图片，还有文字介绍。
为什么区别这么明显呢？其实就是看有没有设置下面这三个内容（具体参阅：腾讯移动WEB开发平台）。

<meta itemprop="name" content="这是分享的标题"/>
<meta itemprop="image" content="http://imgcache.qq.com/qqshow/ac/v4/global/logo.png" />
<meta name="description" itemprop="description" content="这是要分享的内容" />
还有IOS也定制了一些移动开发设置如下：

<meta name="apple-mobile-web-app-capable" content="yes" /> 
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<link rel="apple-touch-icon" href="touch-icon-iphone.png">
<link rel="apple-touch-startup-image" href="/startup.png">

```
