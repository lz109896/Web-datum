#### 第一节：JavaScript 引言
HTML 和 CCS 都是不叫简单的，JavaScript 才是重点

#### 第二节：认识 JavaScript
```
JavaScript :目前主流浏览器上唯一支持的脚本语言，简写JS；JS ：可以用来修改页面样式和内容、制作工具、游戏、其他
可以运行在服务器端，还能嵌入式

ECMAScript 语言基础：包括变量，循环，条件
DOM 文档对象模型： 可以操作HTML。
BOM ：浏览器对象模型，可以获取浏览器的信息，改变浏览器的行为 


```
#### 第三节：JavaScript 引入
```
<!DOCTYPE html>
<html Lang="en">
<head>
    <meta charset="utf-8">
    <title>Javascript 引入 </title> 
</head> 
<body>
    <button id="helloBtn">点击弹出消息框</button>
    <button id ="byebtn" onclick="bye();点击弹出消息框</button>   ：不要用，很简单很老的写法
    <script type="text/javascript" src="hello.js"></script>      ：外链
    <script type="text/javascript">                              
        function bye() {
            alert("bye");
        }
     </script>                                                  ：以上五行<script.....</script>是内嵌
</body>
</html>
```
script ：的属性有src、alert

#### 第四节：注释
```
// 这是单行注释

/*
这是多行注释
这是多行注释
这是多行注释
*/
多行注释也可以这样：
/*
*这是多行注释
*@paaram.....@paaram:是属于文档注释，可以看扩展资料
*这是多行注释
*/

```
#### 第五节：[资料] JSDoc 注释规范

##### 什么是 JSDoc
```
JSDoc 是一个根据 JavaScript 文件中注释信息，生成 JavaScript 应用程序或模块的API文档的工具。
你可以使用 JSDoc 标记如：命名空间，类，方法，方法参数等。从而使开发者能够轻易地阅读代码，
掌握代码定义的类和其属性和方法，从而降低维护成本，和提高开发效率。
```
##### JSDoc 注释规则
```
JSDoc注释一般应该放置在方法或函数声明之前，它必须以/ **开始，以便由JSDoc解析器识别。
其他任何以/*，/***或者超过3个星号的注释，都将被JSDoc解析器忽略。如下所示：

/**
* 一段简单的 JSDoc 注释。
*/
```
##### JSDoc 的注释效果
```
假如我们有一段这样的代码，没有任何注释，看起来是不是有一定的成本。

function Book(title, author) {
    this.title=title;
    this.author=author;
}
Book.prototype={
    getTitle:function(){
        return this.title;
    },
    setPageNum:function(pageNum){
        this.pageNum=pageNum;
    }
};
如果使用了 JSDoc 注释该代码后，代码的可阅读性就大大的提高了。

/**
 * Book类，代表一个书本.
 * @constructor
 * @param {string} title - 书本的标题.
 * @param {string} author - 书本的作者.
 */
function Book(title, author) {
    this.title=title;
    this.author=author;
}
Book.prototype={
    /**
     * 获取书本的标题
     * @returns {string|*} 返回当前的书本名称
     */
    getTitle:function(){
        return this.title;
    },
    /**
     * 设置书本的页数
     * @param pageNum {number} 页数
     */
    setPageNum:function(pageNum){
        this.pageNum=pageNum;
    }
};
```
##### @constructor 构造函数声明注释
@constructor 明确一个函数是某个类的构造函数。

##### @param 参数注释
```
我们通常会使用 @param 来表示函数、类的方法的参数，@param 是JSDoc中最常用的注释标签。
参数标签可表示一个参数的参数名、参数类型和参数描述的注释。如下所示：

/**
 * @param {String} wording 需要说的句子
 */
function say(wording) {
  console.log(wording);
}
```
##### @return 返回值注释
```
@return 表示一个函数的返回值，如果函数没有显示指定返回值可不写。如下所示：

/*
 * @return {Number} 返回值描述
 */
 ```
##### @example 示例注释
```
@example 通常用于表示示例代码,通常示例的代码会另起一行编写，如下所示：

/*
 * @example
 * multiply(3, 2); 
 */
 ```
##### 其他常用注释
```
@overview 对当前代码文件的描述。
@copyright 代码的版权信息。
@author <name> [<emailAddress>] 代码的作者信息。
@version 当前代码的版本。
```
更多参考
如果想了解更多的 JSDoc 注释的内容，可参考下面的链接。

JSDoc 文档  :http://usejsdoc.org/index.html


#### 第六节：变量
```




```
#### 第一节：[资料] 关键字和保留字
#### 第一节：数据类型引言
#### 第一节：数据类型简介
[练习] 填入 typeof 的正确结果
#### 第一节：Number 类型
[练习] 哪些可以用数据类型展示
#### 第一节：String 类型
[练习] 字符串拼接
#### 第一节：[资料] Number 类型与 String 类型之间的转换
#### 第一节：Boolean 类型
[练习] 找出 Boolean 运行结果
#### 第一节：Null 和 Undefined 类型
[练习] 判断 Undefined 和 Null 的说法
#### 第一节：Object 类型
[练习] 新建一个对象
#### 第一节：数组简介
[练习] 创建一个书单
#### 第一节：数组的简单方法
[练习] 对书单进行操作
#### 第一节：[资料] 数组的常用方法
#### 第一节：函数
[练习] 摄氏度华氏度转化
#### 第一节：[资料] 函数表达式和函数声明的区别
#### 第一节：作用域
[练习] 判断是否全局作用域
#### 第一节：算术运算符
[练习] 使用算术运算符
#### 第一节：赋值运算符
[练习] 使用赋值运算法
#### 第一节：比较运算符
[练习] 使用比较运算法
#### 第一节：逻辑运算符
[练习] 使用逻辑运算符














