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




```
#### 8.	函数的方法
```




```
#### 9.	函数的属性
```




```
#### 10.	函数是 first class
```




```
#### 11.	闭包 closure
```




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

