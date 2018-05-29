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
如下面的代码,在这个函数内部，有三个私有变量 param、privateVariable、 privateFunction。在函数内部可以访问到这几个变量，但在函数外部则不能访问他们。

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

我们可以在函数的内部创建一个闭包，那么闭包通过自己的作用域链也可以访问这些变量。而利用这一点，我们就可以创建用于访问私有变量的公有方法。

我们也把有权访问私有变量和私有函数的公有方法称为特权方法。

如下面的代码，publicMethod 就是特权方法。在创建 MyObject 的实例后，除了使用特权方法 publicMethod 这一途径外，没有其他的办法可以直接访问来访问私有变量 privateVariable 以及私有函数 privateFunction。

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




```
#### 13.	构造函数的不足之处
```




```
#### 14.	原型 prototype
```




```
#### 15.	原型详解
```




```
#### 16.	原型、构造函数和实例
```




```
#### 17.	共享的缺陷
```




```
#### 18.	构造函数结合原型
```




```
#### 19.	 [资料] 经典的面向对象
```




```

