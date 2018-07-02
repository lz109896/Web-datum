## 1：JavaScript 引言
HTML 和 CCS 都是简单的，JavaScript 才是重点

## 2：认识 JavaScript
```CSS
JavaScript :目前主流浏览器上唯一支持的脚本语言，简写JS；
JS ：可以用来修改页面样式和内容、制作工具、游戏、其他
可以运行在服务器端，还能嵌入式

ECMAScript 语言基础：包括变量，循环，条件
DOM 文档对象模型： 可以操作HTML。
BOM ：浏览器对象模型，可以获取浏览器的信息，改变浏览器的行为 


```
## 3：JavaScript 引入
```CSS
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

## 4：注释
```CSS
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
## 5：[资料] JSDoc 注释规范

##### 什么是 JSDoc
```CSS
JSDoc 是一个根据 JavaScript 文件中注释信息，生成 JavaScript 应用程序或模块的API文档的工具。
你可以使用 JSDoc 标记如：命名空间，类，方法，方法参数等。从而使开发者能够轻易地阅读代码，
掌握代码定义的类和其属性和方法，从而降低维护成本，和提高开发效率。
```
##### JSDoc 注释规则
```CSS
JSDoc注释一般应该放置在方法或函数声明之前，它必须以/ **开始，以便由JSDoc解析器识别。
其他任何以/*，/***或者超过3个星号的注释，都将被JSDoc解析器忽略。如下所示：

/**
* 一段简单的 JSDoc 注释。
*/
```
##### JSDoc 的注释效果
```CSS
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
```CSS
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
```CSS
@return 表示一个函数的返回值，如果函数没有显示指定返回值可不写。如下所示：

/*
 * @return {Number} 返回值描述
 */
 ```
##### @example 示例注释
```CSS
@example 通常用于表示示例代码,通常示例的代码会另起一行编写，如下所示：

/*
 * @example
 * multiply(3, 2); 
 */
 ```
##### 其他常用注释
```CSS
@overview 对当前代码文件的描述。
@copyright 代码的版权信息。
@author <name> [<emailAddress>] 代码的作者信息。
@version 当前代码的版本。
```
更多参考
如果想了解更多的 JSDoc 注释的内容，可参考下面的链接。

JSDoc 文档  :http://usejsdoc.org/index.html


## 6：变量

是全局变量还是局部变量，取决于是否在 function 里面
function 里面使用 var 定义一个变量再给它赋值就是：局部变量；function 外面是访问不到的。
全局变量不使用 var 是可以全部访问到的。




![](https://github.com/oqq5518/Liao-Zhou/blob/dde205c13f243e0f3903efc3a440045c223d30b3/var%201.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/dde205c13f243e0f3903efc3a440045c223d30b3/var%202.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/dde205c13f243e0f3903efc3a440045c223d30b3/var%203.png)

## 7：[资料] 关键字和保留字
##### 关键字和保留字

在 javaScript 中，保留字和关键字不能够用作标识符，也就是不能用作变量或者函数的名称。

##### 关键字
```CSS
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


## 8：数据类型引言
```CSS
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
## 9：数据类型简介
```CSS
Number、String:属于基本数据类型
Null、Undefined :为空的意思
Boolean :布尔类型（是或否的意思）
Object:复杂数据类型，引用数据类型

typeof ：是操作符
typeof !1, !是反义操作符， !1的结果是 false，为布尔类型， 因此结果是 boolean
'true' 被引号括起来了，是一个字符串，所以结果是 string
变量定义 var a; 相当于 var a = undefined;, 结果是 undefined
```
![]()

## 10：Number 数字类型
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/number%201.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/number%202.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/e7a3d5f76e3872c4ea29a01c40c177f3176a33e3/number%203.png)
## 11：String 类型(字符串)
```CSS
String ： 可以拼接
空格、点号、只要出现的引号里面的都是长度

这些都是 String 字符串
var name = 'bottle';  ------单词
var type = '多彩保温杯'------中文
var brand = 'image';--------词组
var letter = 'a';   --------字母
var p = 'I am liaozhou.'----句子
var numStr = '11'; ---------数字


单引号，双引号必须成对出现的,推荐使用单引号
var name = 'bottle';   true
var name = "bottle";   true
var name = "bottle';   flase
var name = bottle;     flase

拼接字符串
var p = 'I am liaozhou.'
var first = 'Hello!';
console.log(first + p);  //'Hello! I am liaozhou.'
console.log(first + '' + p);  //'Hello! I am liaozhou.'

输出长度
var p = 'I am liaozhou.'
console.log(p.length);  //14

字符串索引:从0开始  
           “多彩保温杯茶杯” 
            0 1 2 3 4 5 6
 
var type ='多彩保温杯茶杯';
console.log(type[0]); //多
console.log(type [2]); //保
console.log(type. charAt(1)); // '彩'

```
## 12：[资料] Number 类型与 String 类型之间的转换

深入了解 Number 类型
```CSS
Number 类型作为 JS 的基本数据类型之一，被应用在程序中的各种场景，其重要性就如数字对于我们日常生活。
下面就让我们来一起深入了解下，为以后的“策马奔腾”做好铺垫。
```
定义方式
```CSS
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
```CSS
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
```CSS
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
```CSS
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
```CSS
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
```CSS
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
```CSS
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
## 13：Boolean 类型  (true、false)
```JS
这个杯子是否保温? 是  输出返回：true
今天有没有下雨?  否   输出返回：false

var flag = true;    // Boolean类型
var flag = "false";  // String 类型

你身高有180cm吗?
var height = 172;
console.log(height >=180);  //false

我的名字是不是liaozhou
var name = 'liaozhou';
console.log (name ==='liaozhou');  //true

!：是取反操作符
 console.log(!!1); // true 
 console.log(!1); // false
 console.log(!!0); // false 
 console.log(!!NaN); // false
 console.log(!!-3.14); // true
 console.log(!!''); // false 
 console.log(!!' '); // true 
 console.log(!!'0'); // true 
 console.log(!!'false'); // true

3 > 4: 是比较运算，结果是 Boolean 类型。
8 - 8: 运算结果是0，是 Number 类型。
'true': 用引号括起来的是字符串类型。
9 !== 9: 是否等于这些也是比较运算，结果是 Boolean 类型。
!'str': ! 是取反操作符, 会将后面的 'str' 字符串转成 Boolean 类型。
!8 - 1: ! 运算符比 - 运算符优先级高，所以上面算式等价于 (!8) - 1, 运算一步之后等价于 false - 1, 
false 在计算中等于0, 所以计算结果是 -1，类型是 Number。
这里涉及到运算符的优先级,活用调试工具。

```
## 14：Null 和 Undefined 类型
```
初始化变量是如果不赋值，变量的值是 undefined, 不是 null。
typeof null 的值是 object（对象）。
!!null 的值是 false。
Null 类型只有一个值 null, Undefined 也只有一个值 undefined。
```
![]()


## 15：Object 类型
```JS
bottle:
var name ='bottle';
var pric = 49;
var isKeepWarm = true;

写成JS语法
var bottle = {
    name: 'bottle', 
    price: 49, 
    isKeepWarm: true
}

上面就是对象的方法以及声明方式，对象字面量
{} 大括号是标识符，有{}的就是定义一个对象
isKeepWarm ：是 Key 合法字符
true : 是 Value 任意类型

console.log(bottle.name);    // 'bottle';  推荐这种写法
console.log(bottle['name']); // 'bottle';

写
bottle.name ='cup';
bottle.color ='blue';
console.log(bottle);
{
    name: 'cup',
    price: 49 
    isKeepWarm: true, 
    color: 'blue'
}

读
console.log(bottle['is keep warm']); // true
console.log (bottle.'is keep warm');---报错
console.log(bottle.is keep warm);------报错
```

## 16：数组简介
```JS
数组字面量描述方式例如：var bottles = ['绿','蓝','紫','红']   **推荐这种
或者 Array 构造函数：var bottles = name Array ['绿','蓝','紫','红']
```

##### 数组的读：
```JS
数组字面量 ： var bottles = ['绿','蓝','紫','红'] 
数组索引：                    0    1    2    3
console.log（bottles[0]）//'绿'
console.log（bottles[3]）//'红'
console.log（bottles[4]）//'undefined'    ** 当长度没有那么多，读取不到时，返回值是'undefined'
```
##### 数组的写：
```JS
数组字面量 ： var bottles = ['绿','蓝','紫','红']
bottles[1] = '黄'
console.log（bottles）; //['绿','黄','紫','红']
长度为1的数据变成了'黄'
```
##### 数组的长度：
```JS
数组字面量 ： var bottles = ['绿','蓝','紫','红']
console.log（bottles.length）; //4

改变数组的长度，给长度赋值，** 不建议这种方式改变数组的长度，其他语言没有这种写法
bottles.length = 5
console.log（bottles）; //['绿','黄','紫','红'undefined]

```
## 17：数组的简单方法

##### push 方法，在数组末尾增加数据
```JS
数组字面量 ： var bottles = ['绿','蓝','紫']
bottles.push('红');
console.log（bottles）; //['绿','蓝','紫','红']
console.log（bottles.length）; //4
```
##### pop 方法，在数组末尾去掉数据
```JS
数组字面量 ： var bottles = ['绿','蓝','紫','红']
bottles.pop();
console.log（bottles）; //['绿','蓝','紫']
console.log（bottles.length）; //3
```
##### shift 方法，在数组中，去掉前面的数据
```JS
数组字面量 ： var bottles = ['绿','蓝','紫','红']
bottles.shift();
console.log（bottles）; //['蓝','紫','红']
console.log（bottles.length）; //3
数组序号改变，索引也会改变
```
##### unshift 方法，在数组中，在前面增加数据
```JS
数组字面量 ： var bottles = ['绿','蓝','紫',]
bottles.unshift('红');
console.log（bottles）; //['红','蓝','紫','红']
console.log（bottles.length）; //4
数组序号改变，索引也会改变
```


## 18：[资料] 数组的常用方法
```JS
数组作为一种重要的数据类型，除了我们前面已经说到的 pop、push、shift、unshift 几个方法外，还有很多实用的方法也是我们的必备技能。

假设我们有一队人，我们要对其进行一些排序或筛选的操作（比喻按高矮排序，筛选女性等），我们都可以通过数组来进行操作。

注：这里更侧重讲解如何使用，至于详细方法请参考：数组 | MDN:https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array

抽出一些人,首先我们用数组定义该数据（为了简单起见，我们数据就不搞那么多）：

var aPerson = ['person1', 'person2', 'person3', 'person4', 'person5', 'person6']
```
##### slice
```JS
现在假设我们要抽取三个人，我们可以使用slice()方法来选取三个人，如下：

var aP3 = aPerson.slice(1, 4);
console.log(aPerson); // ['person1', 'person2', 'person3', 'person4', 'person5', 'person6']
console.log(aP3); // ["person2", "person3", "person4"]
该方法返回一个从开始到结束（不包括结束）选择的数组的一部分浅拷贝到一个新数组对象。原数组不会改变。

详细语法请参考：slice :https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/slice
```
##### splice
```JS
同样我们还可以使用splice()方法来选取，如下：

var aPerson = ['person1', 'person2', 'person3', 'person4', 'person5', 'person6']
var aP3 = aPerson.splice(1, 3);
console.log(aPerson); // ["person1", "person5", "person6"]
console.log(aP3); // ["person2", "person3", "person4"]
该方法通过删除现有元素或添加新元素来更改数组的内容。原数组会改变。

对于 slice 来说，splice 的功能会更强大点，其区别主要在于：

slice 不改变原数组，而 splice 则会改变
slice 的第二个参数为截至的索引值，而 splice 则表示要截取的个数
splice 还能用于增加元素，slice 则不可以
详细语法请参考：splice:https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/splice
```
##### concat
```JS
除了从队伍里抽出一些人出来，我们还可以把另外一个队伍和这个队伍合并成一个新队伍，如下：

var aPerson1 = ['person1', 'person2', 'person3', 'person4', 'person5', 'person6']
var aPerson2 = ['person7', 'person8', 'person9'];

var aPerson3 = aPerson1.concat(aPerson2);
console.log(aPerson3); // ["person1", "person2", "person3", "person4", "person5", "person6", "person7", "person8", "person9"]
concat() 方法用于合并两个或多个数组。此方法不会更改现有数组，而是返回一个新数组。

详细语法请参考：concat
```
##### 高矮排序
```JS
现在我们以高矮的形式定义一组数据，如下：
var aHeight = ['170', '165', '178', '183', '168', '175', '173'];
```
##### reverse
```JS
我们可以直接使用reverse()方法来实现倒序，如下：
aHeight.reverse();
console.log(aHeight); // ["173", "175", "168", "183", "178", "165", "170"]
该方法非常简单，没有任何参数，就是把数组的出现顺序调换下，第一个元素会成为最后一个，最后一个会成为第一个。一般也很少用到。
```
##### sort
```JS
比起 reverse() 来说，sort() 方法使用的地方就多了。我们先来个从矮到高的排序，如下：

aHeight.sort();
console.log(aHeight); // ["165", "168", "170", "173", "175", "178", "183"]
sort() 方法默认的排序是升序，如上代码可见。但是我们也可以传入一个函数，指定其排序方式，如现在让其以降序方式排列：

aHeight.sort(function(a, b){
    return b - a;
});
console.log(aHeight); // ["183", "178", "175", "173", "170", "168", "165"]
详细语法请参考：sort :https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/sort
```
##### 随机排序
```JS
除了正常的升序降序之外，其实我们还经常使用到随机排序，如我们的抢红包，棋牌游戏中的洗牌都是随机排序的应用。

在使用随机排序的时候，我们得使用到一个随机函数 Math.random()。
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/random
该函数返回一个浮点数, 其数字在范围[0，1)。

这样我们就可以使用该随机生成浮点数与0.5大小进行比较，那样结果可能大于或小于0，最后就得到了我们的随机排序。

// 第一次运行
aHeight.sort(function(){
    return 0.5 - Math.random();
});
console.log(aHeight); // ["183", "168", "175", "173", "170", "165", "178"]

// 第二次运行
aHeight.sort(function(){
    return 0.5 - Math.random();
});
console.log(aHeight); // ["170", "183", "175", "168", "173", "165", "178"]
因为是随机的，所以每次运行都会不一样，我们可以多运行几次试试。
```
##### 条件筛选测试
```JS
现在我们以肤色和年龄的的形式定义两组数据，如下（yellow 表示黄种人，white 表示白人，black 表示黑人）：

var aColor = ['yellow', 'black', 'white', 'white', 'yellow', 'yellow'];
var aAge = [19, 30, 25, 37, 18, 35];
```
##### 测试是否符合条件
```JS
every
every() 方法用于测试数组的所有数据是否都通过了指定函数的测试，如果通过返回 true，否则 false。

比喻判断是否所有人的年龄都大于20岁，如下：

var ageTest = aAge.every(function(item, index){
    return item > 20;
})

console.log(ageTest); // false
every 需要数组中的每个数据都满足该条件则返回 true，否则就是 false。

详细语法请参考：every
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/every
```
some
```JS
对应 every() 方法，还有一个 some() 方法，表示数组中只要有任何一个数据满足条件则返回 ture，如果一个数据都不满足则返回 false。

比喻判断是否有人的年龄都大于32岁，如下：

var ageTest2 = aAge.some(function(item, index){
    return item > 32;
})

console.log(ageTest2); // true
详细语法请参考：some
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/some

includes
includes() 方法用来判断当前数组是否包含某指定的值，如果是，则返回 true，否则返回 false。

比喻判断是否有35岁的人，如下：

var ageTest3 = aAge.includes(35);
var ageTest4 = aAge.includes(28);

console.log(ageTest3); // true
console.log(ageTest4); // false
```
##### 条件筛选
```JS
filter
比喻我要选取所有黄皮肤的人，如下：

var aYellow = aColor.filter(function(item, index) {
    return item === 'yellow';
})

console.log(aYellow); // ["yellow", "yellow", "yellow"]
该方法返回所有满足条件数据组成的数组。

详细语法请参考：filter
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter

让每个人都干点啥
forEach
forEach() 方法对数组的每个元素执行一次提供的函数，该方法没有返回值。

比喻过节的时候给每个人去老板那边领个红包，如下：

var aPerson = ['person1', 'person2', 'person3', 'person4', 'person5', 'person6']

aPerson.forEach(function(item, index) {
    console.log(item + '领取了 200 元红包')
})
详细语法请参考：forEach
```
#####  map
```JS
map() 方法创建一个新数组，其结果是该数组中的每个元素调用一个提供的函数。

比喻每个人的工资都增加 5000元，如下：

// 先构造一份工资数据
var aSalary = [8000, 7000, 1500, 9000, 22000];

var aNewSalary = aSalary.map(function(item, index) {
    return item + 5000;
})

console.log(aNewSalary); // [13000, 12000, 6500, 14000, 27000]

详细语法请参考：map
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map

其他
除了上面说的那些方法之外，还有一些常用方法，如 indexOf、join 等等，这里就不再一一说明了，具体可参考：数组 | MDN

总之，数组的方法一定要了如指掌，如果你实在记不住，那也必须知道有这么个东西，以后知道怎么查阅，因为平时做业务的时候处理数据就需要这些各种方法。


```
## 19：函数
```JS
var bottles = ['绿', '蓝','紫', '绿', '红', '紫', '绿', '红'];
function countBottles(color) {            -----------------
    var num = 0;
    for (var i= 0; i< bottles.length; i++) {        函数定义
        if (bottles [i] === color) { 
            num++;
         }             ------------------------------------
      }
       console. log(num);
 } 
 countBottles('绿'); //3  -------------------------> 函数调用
 countBottles("红'); //2
 countBottles('蓝'); //1
 countBottles('紫"); //2

function countBottles(color) {
......
}
return num
 关键字   函数名  （参数）{
函数体
}
返回值

```
```JS
函数声明
function countBottles(color) { 
    var num = 0;
    for (var i = 0; i < bottles.length; i++) {
        if (bottles[i] === color) { 
            num++;
        }
    }
    return num;
}
```
```JS
函数表达式
var countBottles = function(color) {
    var num = 0;
    for (var i = 0; i< bottles.length; i++) {
        if (bottles[i] == color) {
            num++;
        }
    } 
    return num;
}
```
```JS
// console.log(add(2, 1));
function add(a, b) {   //函數声明, 
    return a + b;
} 
console.log(add1(1, 2));   //没有声明, 
var add1 = function(a,b) {   //表达式!
    return a + b;
};
```
## 20：[资料] 函数表达式和函数声明的区别
```JS
函数声明与函数表达式的区别
前面我们已经说了两种定义函数的方式：函数声明与函数表达式。那么这两种方式有区别吗，还是一样的呢？下面我们来进一步探讨探讨。

下面我们定义了两个函数分别为 hello 和 hi，前者采用函数声明，后者采用函数表达式，然后再调用，如下：

function hello () {
    console.log('Hello the world');
}

var hi = function () {
    console.log('Hi, IMWeb');
}

hello(); // 'Hello the world'
hi(); // 'Hi, IMWeb'
上面的调用，我们都能得到正确的运行，并没有什么区别。但是如果我们把顺序掉下，先调用函数后定义函数，那么情况就会有点不一样了。如下：

hello(); // 'Hello the world'
hi(); // Uncaught TypeError: hi is not a function

function hello () {
    console.log('Hello the world');
}

var hi = function () {
    console.log('Hi, IMWeb');
}
从上我们可以看到，hello 函数可以照常运行，但是我们的 hi 函数就会报错了。
根据报错“Uncaught TypeError: hi is not a function”，我们知道 hi 不是 function 了，
那又是什么呢？我们继续使用 typeof 查看下：

console.log(typeof hello); // function
console.log(typeof hi); // undefined

function hello () {
    console.log('Hello the world');
}

var hi = function () {
    console.log('Hi, IMWeb');
}
function hello () {
    console.log('Hello the world');
}
var hi;

console.log(typeof hello); // function
console.log(typeof hi); // undefined

hi = function () {
    console.log('Hi, IMWeb');
}
通过 typeof 我们可以看到 hi 现在是个 undefined 了，这是为什么呢？

这是因为 JavaScript 解释器中存在一种变量声明被提升（hoisting）的机制，
也就是说变量（函数）的声明会被提升到当前作用域的最前面，即使写代码的时候是写在最后面，也还是会被提升至最前面。

这样上面的例子在执行的时候就成了这样的：

这样是不是一下就恍然大悟了。所以在实际开发的时候，一定要注意变量（函数）的声明会被提升到当前作用域的最前面

```
## 21：作用域
```JS
1.在函数内声明，前面有关键字 var， 都属于函数作用域下的
2.在函数外声明，属于全局作用域
3.在函数内声明，但是前面没有 var 关键字，也属于全局作用域
```
```JS
var bottles = ['绿', '蓝', '紫', '绿'];
function countBottles(color) { 
    var(num)= 0;
    for (var i=0; i < bottles.length; i++) { 
        if (bottles[i] === color) { 
            num++;
        }
    }
    console. log(num);
}
console. log (num); 

报错 ：ReferenceError: num is not defined
因为最后面的 num；在函数内声明的，在外面不能访问
```
```JS
全局作用域 :程序的任何地方可以访问

var bottles = ['绿', '蓝', '紫', '绿'];
    function scropExample() {
        name = 'Jero';
}
```
```JS
函数作用域 :函数内部才访问

function countBottles(color) { 
    var num = 0;
    for (var i = 0; i < bottles.length; i++) { 
        if (bottles[i] === color) { 
            num++;
        }
    } 
    console.log(num);
}
```
```JS
var name = 'bottle';
function scope() { 
    var num = 3;
    function innerScope() { 
        var color = 'blue';
        console.log num;  //3
} 
console.log(name);   // 'bottle' 
console.log(color);  //报错: color is not defined
}

总共3层作用域
name :一点隐私都没有，因为在最外面
num : 在作用域最里面都可以访问，但是在最外面不能访问到
color ：访问不到，它是最深的作用域了，只有自己访问自己了
```
## 22：算术运算符
```JS
算术运算符：
+ ：加
- ：减
* ：乘
/ ：除
% ：求余
++/--：自增/自减

//加减乘除 
var result = 7+3;  // result = 10
var result = 7-3;  // result = 4
var result = 7*3;  // result = 21
var result = 7/3;  // result = 2.3333333333333335
var result = 7%3;  // result = 1
```
```JS
1.使用了赋值运算符=
2.使用的为比较运算符==，并不是赋值运算符
3.使用了复合赋值运算符+=，这里 result += 6; 相等于 result = result + 6;
```

```JS
//普通自增加1 
var result = 1;
result = result+ 1;
//result = 2;
```

```JS
//前自增
var result = 1;
console. log(++result); // 2;
console. log (result); // 2;

先自增完毕，再运算整个表达式

```
```JS
//后自增
var result = 1;
console.log(result++); // 1;
console.log (result); // 2;

先运算完整个表达式,再进行自增

```

## 23：赋值运算符

推荐使用这种，代码的可读性比较好
```JS
//希望对result加4 
result = result + 4;

//对result减2
result = result -2;

//对result乘2
result = result * 2;

//对result除3
result = result / 3;

对result对4取模 
result = result % 4;

```
简写赋值运算
```JS

//使用赋值运算符 += 
result += 4;

//使用赋值运算符 -=
result -= 2;

//使用赋值运算符 *= 
result *= 2;

使用赋值运算符 /= 
result /= 3;

//使用赋值运算符 %= 
result %= 4;

```
## 24：比较运算符
```JS
比较运算符

>          大于
<          小于
>=         大于或等于 
<=         小于或等于 
== 或 ===  相等/严格相等 
!= 或! ==  不相等/严格不相等



4 大于 3            4>3  //true
3 小于 4            3<4  //true
5 大于或等于 4      5>=4  //true
4 大于或等于 4      4>=4  //true
3 小于或等于 4      3<=4  //true
4 小于或等于 4      4<=4  //true
4 等于4             4 = 4  //true
4 严格等于4                   4 === 4  //true
3 不等于4           3!=4  //true
                    3 !== 4 //true

```

```JS
'3'  ： 是字符串

使用相等 :先类型转换，再比较
//非严格相等,
3 == '3'  // true
3 != '3'  //false


使用严格相等 ： 不会进行类型转换  ***推荐使用
//严格相等
3 == '3' // false 
3 !== '3'  //true


```
## 25：逻辑运算符

```JS
!   (逻辑非)：非真即假，非假即真

!操作数       结果
!true        false
!false       true

```
```JS
&&  (逻辑与):只要一个为假，结果就是假

第一个操作数     第二个操作数     结果
true             true          true
true            false          false
false           true           false
false           false          false



//使用多重if实现多重条件并列
if (IsOpenLock1) { 
    if (IsOpenLock2) { 
        console.log('门开了');
    }
}


//使用逻辑与 
if (IsOpenLock1 && IsOpenLock2) { 
    console.log('门开了');
}
```
```JS
||  (逻辑或） ：只要一个为真，结果就是真

第一个操作数     第二个操作数     结果
true             true          true
true            false          true
false           true           true
false           false          false


//使用if...else if实现多重条件分支 
if (isErTong) { 
    console.log('糊牌");
} else if (isSanWang) { 
    console.log('糊牌");
}


//使用逻辑或 
if (isErTong || isSanwag) 
    console.log('糊牌');
}
```
















![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/4a3a11f770d84b3ccb4d88abe294a9b64fc7a1a8/%E9%80%BB%E8%BE%91%E8%BF%90%E7%AE%97%E7%AC%A6%201.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/4a3a11f770d84b3ccb4d88abe294a9b64fc7a1a8/%E9%80%BB%E8%BE%91%E8%BF%90%E7%AE%97%E7%AC%A6%202.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/4a3a11f770d84b3ccb4d88abe294a9b64fc7a1a8/%E9%80%BB%E8%BE%91%E8%BF%90%E7%AE%97%E7%AC%A6%203.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/4a3a11f770d84b3ccb4d88abe294a9b64fc7a1a8/%E9%80%BB%E8%BE%91%E8%BF%90%E7%AE%97%E7%AC%A6%204.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/4a3a11f770d84b3ccb4d88abe294a9b64fc7a1a8/%E9%80%BB%E8%BE%91%E8%BF%90%E7%AE%97%E7%AC%A6%205.png)
