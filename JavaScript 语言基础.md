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


![](https://github.com/oqq5518/Liao-Zhou/blob/dde205c13f243e0f3903efc3a440045c223d30b3/var%201.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/dde205c13f243e0f3903efc3a440045c223d30b3/var%202.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/dde205c13f243e0f3903efc3a440045c223d30b3/var%203.png)

#### 第七节：[资料] 关键字和保留字
##### 关键字和保留字

在 javaScript 中，保留字和关键字不能够用作标识符，也就是不能用作变量或者函数的名称。

##### 关键字
```
ECMA-262 描述了一组具有特定用途的关键字,这些关键字可用于表示控制语句的开始或结束，或者用于执行特定操作等。
根据规定，关键字是语言保留的，不能用作标识符即用作变量名或函数名。
```
##### 下面是 ECMAScript 关键字的完整列表：

* break
* case
* catch
* continue
* default
* delete
* do
* else
* finally
* for
* function
* if
* in
* instanceof
* new
* return
* switch
* this
* throw
* try
* typeof
* var
* void
* while
* with
注意：如果把关键字用作变量名或函数名，可能得到诸如 "Identifier Expected"（应该有标识符、期望标识符）这样的错误消息。
在 javaScript 中，一些标识符是保留关键字，不能用作变量名或函数名。

##### 保留字
ECMA-262 还描述了另外一组保留字,有些保留字可能还没有任何特定的用途，但它们有可能在将来用作关键字。

##### 以下是ECMAScript规定的保留字：

* boolean
* abstract
* byte
*  char
* class
* const
* debugger
* double
* export
* enum
* extends
* final
* float
* goto
* implements
* import
* let
* int
* interface
* long
* native
* package
* private
* protected
* public
* short
* static
* super
* synchronized
* throws
* throws
* transient
* volatile

更多阅读
关键字和保留字-w3School  ：http://www.w3school.com.cn/js/pro_js_keywords.asp


#### 第八节：数据类型引言
```
编程不是为了编程而编程，是为了解决现实生活中的问题

以下属于数据类型,用JS来描述以下
名称：太空保温杯；太空保温杯就是字符串
产地：xxx
价格：xxx
供应商：xxx.xx
颜色：xxx
杯子：在JS被称为 对象
等等....

全部属于组合在一起就属于  数组了

```
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%202.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%201.png)
#### 第九节：数据类型简介


```
Number、String:属于基本数据类型
Null、Undefined :为空的意思
BOoolean :布尔类型（是或否的意思）
Object:复杂数据类型，引用数据类型
```
typeof ：是操作符
typeof !1, !是反义操作符， !1的结果是 false，为布尔类型， 因此结果是 boolean
'true' 被引号括起来了，是一个字符串，所以结果是 string
变量定义 var a; 相当于 var a = undefined;, 结果是 undefined


#### 第一节：Number 数字类型
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/number%201.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/number%202.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/number%203.png)
#### 第十节：String 类型(字符串)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/String%201.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/String%202.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/String%203.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/String%204.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/String%205.png)


```
String ： 可以拼接
空格、点号、只要出现的引号里面的都是长度
```
#### 第十一节：[资料] Number 类型与 String 类型之间的转换

深入了解 Number 类型
```
Number 类型作为 JS 的基本数据类型之一，被应用在程序中的各种场景，其重要性就如数字对于我们日常生活。
下面就让我们来一起深入了解下，为以后的“策马奔腾”做好铺垫。
```
定义方式
```
一般来说我们可以直接使用数值字面量格式来定义一个数字，如下：

var num1 = 15;
var num2 = 7;

console.log(typeof num1); // number
console.log(typeof num2); // number
```
数值类型
```
定义的数值可分为两种类型，分别为整数和浮点数。
```
整数
```
整数，可以通过十进制，八进制，十六进制的字面值来表示。（默认为十进值）

// 十进制
var intNum1 = 55; // 正数
var intNum2 = 0; // 0
var intNum3 = -3; // 负数

// 八进制
// 第一位必须是0，其余位的取值范围为0-7
// 无效的八进制会直接忽略前面的0，解析为十进制
var octalNum1 = 070; // 八进制的56（7*8 + 0）
var octalNum2 = 079; // 无效的八进制数，9超过了8进制数的范围，解析为79
var octalNum3 = 08; // 无效的八进制数，直接解析为8

// 十六进制
// 前两位必须是0x，其余位的取值范围为 0~9 或 A~F
var hexNum1 = 0xA; // 十六进制的10
var hexNum2 = 0x1f; // 十六进制的31（1*16 + 15）
在进行算数计算时，所有以八进制和十六进制表示的数值最终都将被转换成十进制的数值。

// 对前面定义的八进制和十六进制数值进行运算
console.log(octalNum1 + hexNum1); // 66
```
浮点数
```
浮点数其实就是我们通常所说的小数，所以一定有个小数点。简单示例如下：

var floatNum1 = 5.2;
var floatNum2 = 3.14;
浮点数所占据的内存空间是整数的两倍。如果小数点后只有零或没有数字，为了节省内存空间，则该小数会被转化为整数，如下：

var floatNum3 = 5.0; // 5
var floatNum4 = 2.; // 2
进行算术运算时，浮点数不如整数精准，所以一般不要使用浮点数进行计算，如下：

var floatNum4 = 0.1; 
var floatNum5 = 0.2; 

// 0.1 + 0.2 不等于 0.3
console.log(floatNum4 + floatNum5); // 0.30000000000000004
对极大极小的浮点数一般会采用e表示法，如下：

 var floatNum6 = 3.2e7；// 3.2×10（7次幂）
 var floatNum7 = 3.2e-7；// 3.2×10（-7次幂）
 ```
NaN
```
NaN 是 not a number 的简写，即非数字。它是一个特殊的值，这个数值用于表示一个本来要返回数值的操作数，
结果未返回数值的情况。

NaN 有两个不同寻常的特点：

任何涉及 NaN 的操作都会返回 NaN
NaN 值与任何值都不相等，包括本身。
console.log(NaN / 10); // NaN
console.log(NaN == NaN); // false
针对这两个特点，JS 提供了一个 isNaN()函数。该函数接受一个参数（可以是任何类型），
而函数会帮我们确定这个参数是否“不是数值”。

注：传递的参数会涉及数值转换的问题，例如“10”这个字符串就可以转换为 10，
但是“blue”这个字符串则无法转换为数字，所以 isNaN('blue') == true

console.log(isNaN(NaN)); // true
console.log(isNaN(10)); // false
console.log(isNaN("10")); // false，可以被转成数值 10
console.log(isNaN("blue")); // true
console.log(isNaN(true)); // false，可以被转成数值 1
```
数值转换
```
有三个函数可以把非数值转换为数值：Number()，parseInt()，parseFloat()。第一个可以用于任何数据类型，
后两个则专门用于把字符串转化为数值。

简单示例如下：

// Number()
// 转换规则比较复杂，可详细参考下面的资料
var numN1 = Number("Hello world!");  // NaN
var numN2 = Number(" ");  // 0 空字符串转为0
var numN3 = Number("000011");  // 11
var numN4 = Number(true);  // 1

// parseInt
// 忽略小数点
// 字符串会被转成数值
var numI1 = parseInt(22.5);   // 22
var numI2 = parseInt ("1234blue") ;  // 1234
var numI3 = parseInt (" ") ;   // NaN
var numI4 = parseInt("70");  //70（十进制数）
var numI5 = parseInt ("070") ;  // 56（八进制数）
var numI6 = parseInt ("0xA") ;  // 10（十六进制数）

// parseFloat
// 字符串会被转成数值
// 如果有多个小数点，则只取第一个，其余全部舍弃
var numF1 = parseFloat ("1234blue") ;  // 1234（整数）
var numF2 = parseFloat("0xA");   // 0
var numF3 = parseFloat("22.5");  // 22.5
var numF4 = parseFloat("22.34.5");  // 22.34
var numF5 = parseFloat("0908.5");   // 908.5
var numF6 = parseFloat("3.125e7");   // 31250000
详细介绍可参考：

JavaScript数值转换(非数值转换为数值)
parseInt
parseFloat
```
数值范围
```
由于内存的限制，JS 并不能保存所有的数值。那么其能表示的最大最小值到底是多少呢？我们可以使用 Number 
对象的 MIN_VALUE 和 MAX_VALUE 属性表示（很少很少用到，大概知道就可以，真要用的时候可以再查阅）：

Number.MIN_VALUE 为能表示的最小正数即最接近 0 的正数 (实际上不会变成 0)，它的近似值为 5 x 10-324。
Number.MAX_VALUE 为能表示的最大正数，它的近似值为 1.7976931348623157 x 10308
如果一个数值超过了最大能表示数值，则自动变成 Infinity 值（无穷数），我们可以使用 Number 对象的 isFinite() 
来判断一个数是否是有限数，如果非有限数则为无穷数。

console.log(Number.isFinite(56)); // true
console.log(Number.isFinite(Number.MAX_VALUE + Number.MAX_VALUE)); // false
更多 Number 对象的属性和方法可参考：Number 对象 | MDN
```
数学函数
```
回忆想想，我们上学的时候是不是学过很多处理数字的数学公式啊，那在 JS 中该怎么办？

不用慌，JS 中内置了一个 Math 对象，它具有数学常数和函数的属性和方法。

我们先来几个简单的例子：

// 函数返回一个数字四舍五入后最接近的整数值。
Math.round(3.4); // 3

// 函数返回一个随机浮点数, 范围在[0，1)
Math.random(); // 随机浮点数，每次都不一样

// 函数返回一个数的平方根
Math.sqrt(9); // 3

// 函数返回给定的一组数字中的最大值
Math.max(10, 20, 13, 18);   //  20

//sin 方法返回一个 -1 到 1 之间的数值，表示给定角度（单位：弧度）的正弦值。
// Math.PI 表示圆周率，一个圆的周长和直径之比，约等于 3.14159.
Math.sin(Math.PI / 2); // 1
更多 Math 对象可参考：Math 对象 | MDN


```
#### 第十一节：Boolean 类型
true

false

!：是取反操作符

![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/Boolean%201.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/Boolean%202.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/Boolean%203.png)

```
3 > 4: 是比较运算，结果是 Boolean 类型。
8 - 8: 运算结果是0，是 Number 类型。
'true': 用引号括起来的是字符串类型。
9 !== 9: 是否等于这些也是比较运算，结果是 Boolean 类型。
!'str': ! 是取反操作符, 会将后面的 'str' 字符串转成 Boolean 类型。
!8 - 1: ! 运算符比 - 运算符优先级高，所以上面算式等价于 (!8) - 1, 运算一步之后等价于 false - 1, 
false 在计算中等于0, 所以计算结果是 -1，类型是 Number。
这里涉及到运算符的优先级，虽然还没介绍，但不妨碍我们做题，是吧？活用调试工具。

```
#### 第一节：Null 和 Undefined 类型
```
初始化变量是如果不赋值，变量的值是 undefined, 不是 null。
typeof null 的值是 object。
!!null 的值是 false。
Null 类型只有一个值 null, Undefined 也只有一个值 undefined。
```





#### 第一节：Object 类型
```
有{}的就是定义一个对象



```
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














