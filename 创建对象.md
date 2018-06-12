#### 1.	我们要开发游戏
```
游戏开发和面向对象
对象、继承、作用域

```
#### 2.	对象和实例
```
红色杯子

抽象：同一类型的可以装水，用手拿的杯子
抽象的叫做对象：

具体：物体红色的长的 可以装水的杯子
具体的叫做实例
```
#### 3.	引言
```
属性  名称   价钱   颜色  规格

创建对象不是简单的声明就可以了

创建很多同一类型的的杯子，需要怎么做？ 不是数组，不能复制粘贴重复冗余的代码
有哪些方法呢？
```
#### 4.	工厂模式
```
目的：用简单的方式来快速创建一系列相似的对象

以下是一个工厂内模式：
function createBottle(name,price,isKeepWarm) {
    return {
      name: name,
      price: price,
      isKeepWarm: isKeepWarm    
    };
}

var bottle = createBottle('太空杯', 49, false);
var bottle2 = createBottle('bottle', 49, true);
var bottle3 = createBottle('bottle', 59, true);

bottle ?    怎么证明我是一个 bottle ？
```
```
function createPerson(name, age, sex) {
  return {
    name: name,
    age: age,
    sex: sex,
    sayHello: function() {
      console.log(this.name);
    }
  };
}
```

#### 5.	再说说函数
```

属性： name   length   prototype

function createBottle() {
  内部有 arguments  this
} 

方法： bind()  call()  apply()

```
#### 6.	函数的 arguments
```
function createBottle(name,price,isKeepWarm) {
    return {
      name: name,
      price: price,
      isKeepWarm: isKeepWarm    
    };
}

简写为：
function createBottle() {
    return {
      name: arguments[0],
      price: arguments[1],
      isKeepWarm: arguments[2]    
    };
}
```
```
arguments 
是一个对象，类数组（不是真的数组），有length 属性
不要滥用，影响代码的可读性
非常适合动态参数的场景





```
#### 7.	函数的 this
```
dom.addEventistener('click',function() {
    console.log(this);
},false);

this  : 执行环境  （前端代码--》浏览器--》操作 windows 系统，这就是一个执行环境）
```
```
window.name = 'jero';
var o = {
    name:'henry'
};
function sayName() {
    console.log(this.name);
}

sayName();
o.sayName = sayName;
o.sayName();

如果你的函数在全局作用域执行，通常都会执行 windows 对象
如果作为对象的方法（o.sayName();），this 执行环境通常都会指向对应的对象
this 不是定义的时候确定的，只有当它调用的时候最终才知道他指向哪里！

sayName();    结果是：jero
o.sayName();  结果是：henry
```
#### 8.	函数的方法
```
函数的方法: bind、call、apply

o.sayName = sayName.bind(windows);  结果是：jero
bind：可以改变函数 this 的指向

sayName.call(o);
call：可以改变函数 this 的指向 o.

sayName.apply(o,[1.2]);
call 和 apply 看似一样，传参是不一样的；apply 只接受传参是数组


```
#### 9.	函数的属性
```
name、length、arguments.length、prototype

name : 函数名
length： 形参的个数
prototype : 是一个属性，是一个对象，是实现继承的重要属性

length、arguments.length  :
区别：length 依然是固定的，在声明的时候就确定了个数。
arguments.length ： 根据调用的函数传进来的参数个数决定的


```
#### 10.	函数是 first class

数据类型：是跨语言的，不仅是在 JS 里面
 * First  Class :  可以作为函数的参数和返回值，也可以赋给变量
 * Second Class ： 可以作为函数的参数，但不能从函数返回，也不能赋给变量
 * Third Class  ： 不能作为函数的参数
```
var add = function(a,b) {
    return a + b;
};


简写: var add = new function('a','b','return a + b;');  (这种函数的声明方式不推荐)
'return a + b;'   函数体
'a','b'      参数
```
```
实际项目中的  回调函数：

[1,2,3].sort(function(a,b) {
    return a < b;
});
```
```
function createScope(member) {
    return function() {
        return member;
    }
}

var gethenry = createScope('henry');
gethenry();

var getJero = createScope('Jero');
getJero();

体现一种思想：不可修改的变量  （私有变量，创建私有变量的方法时闭包）

```
#### 11.	闭包 closure
```
闭包：是指有权访问另外一个函数作用域中的变量的函数，也可以理解为有数据的函数
函数作用域、函数：只有这两种同时出现才能产生闭包



function foo() {
    var a = 'test';      ----------
    function bar() {      这里面是闭包范围
        console.log(a);       
    }                   -----------
    bar();
}
foo();

bar 函数可以访问父函数作用域中的 a 变量

```
```
function foo() {
    var a = 'test';      ----------
    function bar() {      这里面是闭包范围
        return a;         可以形成私有变量和作用域
    }                   -----------
    return bar;
}
var bar = foo();
bar();

```
```
function wait(message) {
    setTimeout(function() {
        console.log(message);
    },1000);
}

wait('hello,closure');

message  可以访问父函数中的 message
```
```
(function() {
    var doc = document;
    var util = {
        byId: function(id) {
            return doc.getElementById(id);     
        };   
    };
    windows.Util = Util;
})();
Util.byId('hahah');

立即执行函数，在声明的时候就执行了；调用匿名函数(function()，在后面的括号中 })(); 立即执行

byId 可以访问 doc 变量，这也是闭包
```
```
闭包非常常用尤其是在第三方的库中

(function() {
    var doc = document;
    var util = {
        byId: function(id) {
            return doc.getElementById(id);     
        };   
    };
    windows.jQuery = Util;
})();
jQuery.byId('hahah');

```
##### 创建一个私有变量
```
如果我们需要隐藏一些不应该被直接修改的数据，我们需要使用到私有变量和特权方法。那么什么是私有变量和特权方法呢？
```
###### 什么是私有变量？
```
对于私有变量，我们需要理解下面的两句话：

任何在函数中定义的变量，都可以认为是私有变量。因为不能在函数外部访问这些变量。
私有变量包括函数参数，局部变量以及在函数内部定义的其他函数。
如下面的代码,在这个函数内部，有三个私有变量 param、privateVariable、 privateFunction。在函数内部可以
访问到这几个变量，但在函数外部则不能访问他们。

function MyObject(param) {
  var privateVariable = 20;
  function privateFunction(){
      return true;
  }
}
// 在函数外部无法直接访问到私有变量和方法
```
###### 创建特权方法来访问私有变量
```
那么，我们如果需要访问私有变量时，可以怎么做呢？

我们可以在函数的内部创建一个闭包，那么闭包通过自己的作用域链也可以访问这些变量。
而利用这一点，我们就可以创建用于访问私有变量的公有方法。

我们也把有权访问私有变量和私有函数的公有方法称为特权方法。

如下面的代码，publicMethod 就是特权方法。在创建 MyObject 的实例后，除了使用特权方法 publicMethod 这一途径外
，没有其他的办法可以直接访问来访问私有变量 privateVariable 以及私有函数 privateFunction。

function MyObject(param) {
  var privateVariable = 20;
  function privateFunction(){
      return 10;
  }
  // 特权方法
  this.publicMethod = function(){
      privateVariable ++;
      return privateFunction();
  }
}
```
```
/*
* 题目:
* 完善工厂函数 createPerson，需要完成以下要求：
* 1.保存传入参数 name 到一个私有变量中
* 2.函数返回一个对象，且对象带有一个方法 getName，用于返回对象的私有变量 name 的值
*/

function createPerson(name) {
  // 保存参数name
  var privateName = name;
  return {
    // 创建一个 getter 方法来获取私有变量 name 的值
    getName: function() {
      return privateName;
    }
  };
}
```
#### 12.	构造函数
```
var bottle = createBottle('太空杯',49,falise);
怎么证明我是一个 bottle ？
```

构造函数：
* instanceof
* Bottle
* new 操作符
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%201.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%202.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%203.png)

#### 13.	构造函数的不足之处
* 实例与构造函数可以通过 instanceof 来判断他们之间的关系
* 构造函数跟工厂模式一样，都做到了代码复用
* 构造函数是通过将参数和方法都赋值给 this 的方式创建对象, 不是不足之处
* 构造函数每次创建实例的时候都会创建相同逻辑的函数作为对象的方法，这是构造函数的不足之处
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E4%B8%8D%E8%B6%B3.png)

#### 14.	原型 prototype
```
原型是函数的一个属性，是一个对象
非要在 JS 里面找一个特色，那就是原型

```
#### 15.	原型详解

* constructor
Object.prototype.constructor    的原型是Object


* 读写

__proto__: Object  :浏览器里面下划线的意思就是指向原型，代码里面一定不要这样指向原型，测试和演示调试的时候可以使用
可以共享原型，利用读写解决浪费内存的原型



* isPrototypeOf


![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%8E%9F%E5%9E%8B%E8%AE%B2%E8%A7%A3%201.png)

![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%8E%9F%E5%9E%8B%E8%AE%B2%E8%A7%A3%202.png)

#### 16.	原型、构造函数和实例
```
原型是函数的一个属性，是一个对象
如果函数作为构造函数使用，那么这个构造函数的所有实例，都共享这个原型对象

通过 naw 操作符可以生成实例
Bottle.prototype指向原型 prototype
constructor 指向 Bottle
实例化以后__proto__属性指向原型 prototype
也可以通过 isPrototypeOf 关联到 prototype

```
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E5%AE%9E%E4%BE%8B%201.png)
```
通过构造函数生成实例对象时，会自动为实例对象分配原型对象。每一个构造函数都有一个 prototype 属性，
这个属性就是实例对象的原型对象。

原型对象上的所有属性和方法，都能被派生对象共享。

因此本道题目，考察如何使用 prototype 来设置共享的方法，避免所有实例对象都设置相同的属性和方法导致对系统资源的浪费。

具体参考代码如下：

/*
* 题目:
* 使用 Prototype 来创建一个 Person 类， 需要完成以下要求：
* 1、在构造函数 Person 的 prototype(原型) 上增加下面的共享属性：
*   1.1、在原型上增加属性 `name` 值为 'Jonny'
*   1.2、在原型上增加属性 `friends` 值为 ['Cover', 'Kevin']
* 2、在构造函数 Person 的原型上增加共享方法 sayHello
*/
function Person(name){
}
// 设置原型
Person.prototype = {
  constructor: Person,
  name: 'Jonny',
  friends: ['Cover', 'Kevin'],
  sayHello: function() {
    //...
  }
};
需注意的是在上面的代码中，我们将 Person.prototype 设置为一个新创建的对象。会导致 Person.prototype 对象
原来的 constructor 属性不再指向 Person, 这里可以像上面那样，特意的把 constructor 设置为 Person 。
```
#### 17.	共享的缺陷
```
数据的污染
原型创建对象的时候就不能传参，主要缺陷是共享缺陷，
对象的属性和方法都挂在构造函数的原型上，通过函数共享原型，这是原型的生成方式

有共享问题通常情况是不同变量指向相同的引用类型的数据，一旦该数据的属性被修改了，则指向该数据的变量的值都会受到影响。
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%85%B1%E4%BA%AB%E7%BC%BA%E9%99%B7.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%85%B1%E4%BA%AB%E7%BC%BA%E9%99%B7%201.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%85%B1%E4%BA%AB%E7%BC%BA%E9%99%B7%202.png)


#### 18.	构造函数结合原型

实例上的属性覆盖原型上的属性，
```

/*
* 题目:
* 使用构造函数结合原型创建一个 Person 类, 需要完成以下要求：
* 1、使用构造函数创建一个 Person 类
* 2、每个生成的实例都有独立的属性 name，且属性值通过传入的参数进行设置
* 3、每个生成的实例都有独立的属性 friends，且属性值通过传入的参数进行设置
* 4、在构造函数 Person 的 prototype 上增加共享方法 sayHello
*/

function Person(name, friends){
  this.name = name;
  this.friends = friends;
}
// 增加原型方法 sayHello
Person.prototype.sayHello = function() {
```

![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E7%BB%93%E5%90%88%E5%8E%9F%E5%9E%8B1.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E7%BB%93%E5%90%88%E5%8E%9F%E5%9E%8B2.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E7%BB%93%E5%90%88%E5%8E%9F%E5%9E%8B3.png)

#### 19.	 [资料] 经典的面向对象

##### 经典的面向对象
```
这里所说的“经典的面向对象”，是有“类”这个概念的面向对象，比如 Java ，它就有“类”的概念。有接触过 Java 
的同学很容易就能理解，没有接触过 Java 的同学也不要慌，我这就来说说。

面向对象这个概念，实在是太像我们的世界。

说道“人”，Person ，大家肯定是想到一个鼻子，两个眼睛，是一个宽泛的概念，可以让你想到任何人。

所以“人”，是一个抽象，它描述一个特定类别的东西，一类动物。

“动物”也是一类抽象，从字面意思理解，“动物”是能动的生物，和“植物”区分开来。

人是动物，你我是人，也是动物。

但是，“你我”又有区别，虽然都是人，但我叫 jero ，你叫刘德华，我很帅，你却更帅。在“人”这个大的类别下，
你我是两个不同的实体，两个不同的对象，你我都是具象化的人，是一个具体的概念。

看到了吗，类这个字眼都加粗了，因为这是面向对象的一个重要概念。

class Animal {
    constructor(legs) {
        this.legs = 2;
    }
}

console.log(new Animal(2)); // { legs: 2 }
上面就是 Animal class 了，非常的简单，也很抽象，但是，我们 new 了一下之后，就具体化了，我们 new 了一个两条腿的动物。

好吧，我想大家还是更容易接受人的例子。

class Person {
    constructor(name) {
        this.legs = 2;
       this.name = name;
    }
}

console.log(new Person('刘德华')); // { legs: 2 }
上面就是 Person class 咯，Person 只是抽象，对吧，但是我们给他一个名字“刘德华”，他就是活生生的人咯，这就是实例化。

“类”是抽象，其实这个“类”就是分门别“类”里的“类”。“对象”和“实例”，现在如果你们区分不了，可以混用，就是“类”实例化的产物。

好咯，再看代码：

function Person(name) { // 这个 Person 就是类
    this.name = name;
    this.legs = 2;
}

console.log(new Person('刘德华')); // 活生生的人，就是实例
虽然 JS 里面没有类的概念，但我们还是习惯叫“类”，而且不同的“类”有时候是有关系的，比如“人”是“动物”，这个时候，
“人”就是子类，“动物”就是父类，也挺容易理解。

好吧，就讲到这，不理解的同学，多想想就行。

最后说一句，上面的 class Person 代码，也是 JS 代码，ES6 新增了类的语法，创建对象更容易了，大家可以看看。

类
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Classes

Class 的基本语法
http://es6.ruanyifeng.com/#docs/class

```

