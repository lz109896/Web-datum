#### 1.	画图利器 Canvas
```
开发理念，设计思想

定义游戏，清晰、快捷

以前的HTML绘图能力太弱，使用画图利器 Canvas，能绘制出复杂的图形


```
#### 2.	认识 Canvas 元素
```
实现射击小游戏，可以有flash 、js + dom、 Ccnvas ，三种方法
Canvas 是HTML5 提供的新标签，（画布元素）

var myCanvas = document.getElementById('Canvas');
var context = myCanvas.getContext('2d');

xy轴坐标
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/1876bf178957623029b3d98df507f390d264d7d6/%E8%AE%A4%E8%AF%86Canvas%20%E5%85%83%E7%B4%A0.png)
#### 3.	矩形
```
截图，简化怪兽跟飞机都是矩形

context.fillRect(x,y，宽，高)；  绘制的是实心矩形
context.strokeRect(x,y，宽，高)；绘制的是空心矩形

```
```
var canvas = document.getElementById('canvas');
var context = canvas.getContext('2d');

context.fillRect(10,10,20,20);
context.strokeRect(10,200,200,200);

```
#### 4.	线条 (路径)
```
绘制线条
context. beginPath       告诉 Canvas 要开始绘图了       
context. moveTo         调用 moveTo 来移动画笔的笔触
context. lineTo             设置路径需要经过的位置
context. closePath               自动闭合路径
context. fill /  context. stroke    绘制路径
```
```
var canvas = document.getElementById('canvas');
var context = canvas.getContext('2d');

context.beginPath();
context.moveTo(20,50); 
context.lineTo(150,200);
context.lineTo(20,200);
context.closePath();
context.stroke();

context.beginPath();
context.moveTo(180,140); 
context.lineTo(230,200);
context.lineTo(180,200);
context.closePath();
context.fill();
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/1876bf178957623029b3d98df507f390d264d7d6/%E7%BA%BF%E6%9D%A1.png)

#### 5.	 [资料] 绘制圆弧
##### 绘制圆弧
```
讲解下如何在 canvas 画布上 绘制圆弧和圆形。
相对矩形来说，绘制圆弧则更为复杂。绘制圆弧需要确定圆心的坐标，圆弧的角度以及绘制圆弧的绘制方法等等。
```
##### context.arc()
```
在 Canvas 中我们可以使用 context.arc() 的方法来创建圆弧路径。简单来说，在 Canvas 中，创建一条圆弧路径是从
与圆心(x, y)距离为一个半径且角度为开始角度的位置开始，最后停在离圆心(x, y)距离为一个半径且角度为结束角度的位置上。

context.arc(x, y, radius, startAngle, endAngle, anticlockwise);
参数说明：

```
![](https://raw.githubusercontent.com/lz109896/Web-datum/1876bf178957623029b3d98df507f390d264d7d6/%E7%BB%98%E5%88%B6%E5%9C%86%E5%BC%A7.pngg)
```
x: 圆的中心的 x 坐标
y: 圆的中心的 y 坐标
radius: 圆的半径
startAngle: 圆弧的开始角度
endAngle: 圆弧的结束角度
anticlockwise: 可选的参数，规定应该逆时针还是顺时针绘图，默认值为 false
```
##### 弧度表示角度
```
这里需要注意的是，在 Canvas 中表示圆弧的开始角度和结束角度都是以弧度来表示的，而不是使用角度来表示。

举个例子: 360度使用弧度来表示则是 2π (pi 的两倍)弧度。
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/1876bf178957623029b3d98df507f390d264d7d6/%E7%BB%98%E5%88%B6%E5%9C%86%E5%BC%A7%202.png)


```
我们可以通过下面的公式进行换算。

var degree = 1; // 表示 1°
var radians = degree * (Math.PI / 180); // 0.0175弧度
```
##### 绘制圆弧路径
```
接下来让我们尝试绘制一个圆弧，如下图：
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/1876bf178957623029b3d98df507f390d264d7d6/%E7%BB%98%E5%88%B6%E5%9C%86%E5%BC%A7%203.png)
```
具体代码如下：

// 开始创建新路径
context.beginPath();
// 创建一个半圆圆弧
context.arc(250, 250, 200, 0, Math.PI, false);
// 调用 stroke 绘制该路径
context.stroke();
```
##### 绘制部分圆
```
接下来让我们尝试绘制一个部分圆形填充图形，如下图：

// 开始创建新路径
context.beginPath();
// 创建一个圆弧
context.arc(250, 250, 200, 0, 0.75 * Math.PI, false);
// 填充该圆弧
context.fill();
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/1876bf178957623029b3d98df507f390d264d7d6/%E7%BB%98%E5%88%B6%E5%9C%86%E5%BC%A7%204.png)
##### 绘制圆形
```
圆形实际上是由圆弧组成（首尾相连的圆弧便是圆形）,如果我们需要绘制下面的圆形：
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/1876bf178957623029b3d98df507f390d264d7d6/%E7%BB%98%E5%88%B6%E5%9C%86%E5%BC%A7%205.png)
```

具体代码如下：

// 开始创建新路径
context.beginPath();
// 设置开始角度为0，结束角度为 2π 弧度
context.arc(250, 250, 200, 0, 2 * Math.PI, false);
// 使用 fill 自动闭合圆弧路径，然后填充圆弧区域
context.fill();
```
##### 绘制圆角矩形
```
我们不仅可以使用 context.arc() 来绘制圆弧和圆形，我们还可以来绘制圆角矩形上的圆角。如下图为我们需要绘制一个圆角矩形：

```
![](https://raw.githubusercontent.com/lz109896/Web-datum/1876bf178957623029b3d98df507f390d264d7d6/%E7%BB%98%E5%88%B6%E5%9C%86%E5%BC%A7%206.png)

```
var x = 120; // 圆角矩形左上角横坐标
var y = 120; // 圆角矩形左上角纵坐标
var width = 250; // 圆角矩形的宽度
var height = 250; // 圆角矩形的高度
var radius = 50; // 圆角的半径

// 开始创建新路径
context.beginPath();
// 绘制左上角圆角
context.arc(x + radius, y + radius, radius, Math.PI, Math.PI * 3 / 2);
// 绘制顶边路径
context.lineTo(width - radius + x, y);
// 绘制右上角圆角
context.arc(width - radius + x, radius + y, radius, Math.PI * 3 / 2, Math.PI * 2);
// 绘制右边路径
context.lineTo(width + x, height + y - radius);
// 绘制右下角圆角
context.arc(width - radius + x, height - radius + y, radius, 0, Math.PI * 1 / 2);
// 绘制底边路径
context.lineTo(radius + x, height +y);
// 绘制左下角圆角
context.arc(radius + x, height - radius + y, radius, Math.PI * 1 / 2, Math.PI);
// 闭合路径 也可使用 context.lineTo(x, y + radius);
context.closePath();
// 设置绘制的颜色
context.strokeStyle = '#188eee';
context.stroke();

```
#### 6.	文本:http://coding.imweb.io/demo/p5/canvas-text.html
```
绘制文本:contex.fillText(text,x,y);   /   contex.strokeText(text,x,y);
```
```
var canvas = document.getElementById('canvas');
var context = canvas.getContext('2d');


context.fillText('fillText',200,100);
context.strokeText('strokeText',20,100); 

context.font = '60px 黑体';
context.strokeText('strokeText2',20,150);

```
#### 7.	给图形上色：http://coding.imweb.io/demo/p5/canvas-style.html
```
设置颜色：context.fillStyle = color;  /  context.strokeStyle = color; 

设置的颜色只会应用于在他之后定义的绘制的命令，如下代码：
```
```
必须符合CSS3 颜色值标准
以下fillStyle 的值均为‘红色’
context.fillStyle = "red";
context.fillStyle = "#ff0000";
context.fillStyle = "rgb(255,0,0)";
context.fillStyle = "rgb(255,0,0,1)";

```
```
var canvas = document.getElementById('canvas');
var context = canvas.getContext('2d');

context.fillStyle = "red";
//绘制填充的矩形
context.fillRect(50,50,160,160);

context.strokeStyle = 'rgb(0,255,0)';
//绘制矩形的描边
context.strokeRect(250,50,160,160);
//绘制三角形
context.beginPath();
context.moveTo(200,280);
context.lineTo(200,380);
context.lineTo(300,380);
context.fill();
```

#### 8.	修改线宽
```
修改线宽：context.lineWindth = number;
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/1876bf178957623029b3d98df507f390d264d7d6/%E4%BF%AE%E6%94%B9%E7%BA%BF%E5%AE%BD.png)
```
/*
* 题目:
* 根据题目要求设置图案的颜色和线宽
*/

var canvas = document.getElementById('canvas');
var context = canvas.getContext('2d');

// 绘制轮廓颜色为 'rgba(255, 122, 33, 0.5)' 且线宽为 10 的矩形轮廓
context.strokeStyle = 'rgba(255, 122, 33, 0.5)';
context.lineWidth = 10;
context.strokeRect(40, 20, 80, 80);


// 绘制填充颜色为 'green' 的矩形图形
context.fillStyle = "green";
context.fillRect(20, 120, 120, 60);

```
#### 9.	擦除 Canvas
```
context.clearRect(x,y,宽,高)；
对象左上角坐标： x,y
对象的宽,高

清除整个画布的描述是：
context.clearRect(0,0,canvas.width,canvas.height)；

```
![](https://raw.githubusercontent.com/lz109896/Web-datum/1876bf178957623029b3d98df507f390d264d7d6/%E6%93%A6%E9%99%A4canvas.png)
