#### 1.	引言
```
在毛坯基础上，建自己的大厦
面向对象中，对象就是毛坯，拿过来，在它的基础上，扩展出自己想要的，功能最为强大的瓷器，这个过程就是继承
在已有的基础上扩展出自己的东西，就是继承
```

客运机和战斗机
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%BC%95%E8%A8%80.png)
#### 2.	什么是继承
```
继承可以使子类具有父类的属性和方法，而不需要重复编写相同的代码。

```
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E4%BB%80%E4%B9%88%E6%98%AF%E7%BB%A7%E6%89%BF.png)

#### 3.	原型链
```
目标：子类具有父类的方法和属性--》实例中找不到属性和方法--》去原型中去找--》父类的实例

父类的方法和属性--》父类的实例--》指向原型
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%8E%9F%E5%9E%8B%E9%93%BE1.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%8E%9F%E5%9E%8B%E9%93%BE2.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%8E%9F%E5%9E%8B%E9%93%BE3.png)

#### 4.	原型链继承的不足

1.constructor
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%8E%9F%E5%9E%8B%E9%93%BE%E4%B8%8D%E8%B6%B31.png)

2.属性共享问题

![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%8E%9F%E5%9E%8B%E9%93%BE%E4%B8%8D%E8%B6%B32.png)

3.参数
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%8E%9F%E5%9E%8B%E9%93%BE%E4%B8%8D%E8%B6%B33.png)

#### 5.	借用构造函数继承
![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%80%9F%E7%94%A8%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B01.png)
![](https://github.com/lz109896/Web-datum/blob/16058691bda3af220a3280d6758a2cf688fab0ed/%E5%80%9F%E7%94%A8%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B02.png)

#### 6.	组合继承
```
function Plane (color){                 -------------
    this.color = color;
}
Plane.prototype.fly = function() {      基础构造函数（父类）
    console.log('flying);
}                                      ---------------
function fighter(color) {
    Plane.call(this,color);       --------  借用构造函数继承实例属性
    this.bullets = [];
}
Fhter.prototype = new Plane();    --------  继承原型属性和方法
Fghter.prototype.constructor = Fghter;
Fghter.prototype.shoot = funceion() {
    console.log('biu biu biu);
}

```
```
组合继承
1.属性和方法都是从父类继承的（代码复用）
2.继承的属性是私有的（互不影响）
3.继承的方法都在原型里（函数复用）

```
#### 7.	组合继承的不足

![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/%E7%BB%84%E5%90%88%E7%BB%A7%E6%89%BF%E7%9A%84%E4%B8%8D%E8%B6%B3%20.png)

#### 8.	最佳实践
![]()
![]()
![]()
![]()
![]()

#### 9.	 [资料] ES6 中的继承

##### ES6 的继承
```
到目前为止，我们已经知道了 JS 中继承方式的最佳实践了，相信大家会有这样的疑惑：怎么感觉 JS 继承方式这么绕，又要借用构造函数，又要自己封装继承原型的函数。没错，你们的感觉是对的，大家也是这么觉得的，以至于后来有了很多 JS 继承的封装或者语法糖，比如现在比较火的 TypeScript 就是参照经典的面向对象对 JS 的类的声明和继承进行了封装。

幸运的是，ES6 标准已经将 经典的 class 声明类和继承的方式纳入标准了，前面经典的面向对象扩展资料中就有提到 ES6 中怎么声明类了，下面是使用 ES6 实现 Person 类。

//定义类
class Person {
    // 构造函数
    constructor(name) {
        this.name = name;
    }

    // 方法
    sayName() {
        console.log(this.name);
    }
}
在 ES6 中继承是通过 extends 关键字声明的，比如下面 Student 类继承了 Person 类

//定义类
class Student extends Person {
    // 构造函数
    constructor(name, grade) {
        super(name);
        this.grade = grade;
    }

    // 方法
    sayGrade() {
        console.log(`I am Grade ${this.grade}`);
    }
}
上面继承方式关键点其实就2个，一个是通过 extends 关键字声明继承关系，第二是在子类构造函数 constructor 中调用 super 函数，这其实就相当于我们的借用构造函数。要注意的点是 constructor 中 this 对象要 super 调用之后使用，不然会报错。具体原因可以看下面参考资料。

目前部分现代浏览器新版本已经实现对 ES6 中的 class 和继承的支持，但是注意在旧版本或者 IE 浏览器中是不支持的，所以使用的时候要注意，或者配合使用 Babel 等编译工具。


```
#### 10.	Node 和 Element

![](https://raw.githubusercontent.com/lz109896/Web-datum/16058691bda3af220a3280d6758a2cf688fab0ed/Node%20%E5%92%8C%20Element%20.png)

#### 11.	面向对象
```
面向过程是一个繁琐的过程，不易维护

面向对象，定义一个类，同时具有相同的方法创建对象，然后通过方法把所有的功能封装在一起

move 方法

封装和继承，减少重复，易于维护，方便扩展


```
