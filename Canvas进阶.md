#### 1.	加载图像
http://coding.imweb.io/demo/p5/canvas-img.html
```
context.drawlmage(image,x,y,[宽度],[高度])
image: 要加载图片的对象
x,y： 加载图片的位置坐标
[宽度],[高度]  ：设置图片的尺寸，如果没有设置只会显示原始尺寸
```
```
var canvas = document.getElementById('canvas');
var context = canvas.getContext('2d');

var image = new Image();
image.src = 'http://coding.imweb.io/img/p5/plane.png';

image.onload = function () {
    context.drawImage(image,50,50);
    context.drawImage(image,150,50,60,100);
};

```
#### 2.	 [资料] 图像裁剪

##### 图像裁剪
```
前面我们讲到如何在 Canvas 中加载各种帅气酷炫的图像。但是有时候我们并不需要使用完整的图像，而只是图像的一部分内容，
这个时候我们就需要使用图像裁剪。图像裁剪是图片 PS 中经常使用到的一种技术，目的是为了突出我们图片的某个特定的区域。
接下来，让我们学习如何使用 Canvas 来裁剪我们的图像。
```
##### 还是 context.drawImage()
```
没错，你没看错，我们还是使用 drawImage 的方法。裁剪是 drawImage 方法的最后一种用法。

context.drawImage(image, source_x, source_y, source_width, source_height, x, y, width, heigh);
它总共涉及9个参数，具体如下：

image：源图像对象
source_x：源图像的裁剪区原点横坐标
source_y：源图像的裁剪区原点纵坐标
source_width：源图像的裁剪区宽度
source_height：源图像的裁剪区高度
x：在画布上绘制图像的原点横坐标
y：在画布上绘制图像的原点纵坐标
width：在画布上绘制图像的宽度
heigh：在画布上绘制图像的高度
上面所有参数的看起来可能比较抽象，可以通过结合下面说明图进行理解：



实例
接下来让我们尝试截取图片的中间部分，如下图：



相关代码如下：

<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>物体移动</title>
</head>
<body>
    <canvas id="canvas" width="500" height="500"></canvas>
    <script>
      var canvas = document.getElementById('canvas');
      var context = canvas.getContext('2d');

      var image = new Image();
      image.src = 'http://coding.imweb.io/img/p3/retina-pixel.jpg';
      image.onload = function () {
        // 加载图片后，边截取图片且缩放展示在画布左上角
        context.drawImage(image, 260, 260, 480, 480, 0, 0, 240, 240);
      }
    </script>
</body>
</html>




```
#### 3.	[资料] 认识 requestAnimationFrame

##### requestAnimationFrame

###### 动画原理简介
```
动画的基本原理是依靠人类具有视觉暂留的特性人的眼睛看到一幅画或一个物体后，在 1/24 秒内不会消失（即每秒钟至少
更换24张画面）利用这一原理，在一幅画（一帧）还没消失前播放下一幅画（下一帧），就会给人造成流畅的视觉变化效果。

如翻书动画，就是利用我们人的视觉暂留的特性的。

因此我们可以得出：如果我们需要实现动画，只需要设置定时不断地绘制下一帧的画面便可以了。
```
###### 早期动画循环
```
在 JavaScript 中我们可以使用 setTimeout 和 setInterval 来设置延时任务。
因此在很长时间以来，计时器一直都是 JavaScript 动画的最核心技术。
如下面的代码就是使用 setTimeout 方法来实现基本的动画循环：

function animate() {
    // 动画内容
    animation1();
    animation2();
    // 间隔100ms执行动画循环
    setTimeout(function () {
        animate();
    }, 100);
}
// 执行动画
animate();
```
###### 循环间隔 60Hz
```
早期的动画循环时候，最关键的问题是确定循环间隔的时长。一方面，循环间隔必须足够短，这样才能动画效果显得更平滑流畅；
另一方面，循环时隔还要足够长，这样才能确保浏览器有能力渲染产生的变化。我们知道大多数的显示器的刷新频率是 60Hz ，
即相当于在每秒钟中屏幕会重绘 60 次。因此最平滑动画的最佳循环间隔是 1000ms/60，约等于 16.7ms。
```
###### setTimeout 和 setInterval 问题
```
然后无论是 setTimeout 和 setInterval 都并不是十分精准。

我们知道 JavaScript 是一个单线程的解释器，在一定时间能只能执行一段代码。为了要控制代码的执行顺序，就需要通过一个
JavaScript任务队列 来进行管理控制（任务会按照添加到队列的顺序执行）。通过 setTimeout 和 setInterval 我们能够设
置延时多长时间把我们的代码任务添加到 JavaScript任务队列 中。如果当前任务队列是空的，那么添加的代码可以立即执行；
如果队列不是空的，则新添加的任务需要等到其前面所有的任务都执行完成才能执行。由于前面的任务到底需要多少时间执行完，
是不确定的，所以没有办法保证，setTimeout 和 setInterval 指定的任务，一定会按照预定时间执行。

如下面的代码：

setTimeout(animateTask, 1000 / 60);
// 耗时长的任务
longTimeTask();

上面代码的 setTimeout，我们制定 16.7ms 后运行 animateTask 任务。但是，如果由于后面的 longTimeTask 执行
（当前脚本的同步任务））非常耗时，即使过了 16.7ms 仍无法结束，那么延迟执行的 animateTask 就只有等着，只有等
到前面的任务都运行完，才能轮到它执行。

具体可阅读下 John Resig（jQuery 作者）的这篇文章 How JavaScript Timers Work。
https://johnresig.com/blog/how-javascript-timers-work/
```
###### requestAnimationFrame
```
由于 setTimeout 和 setInterval 的不精准问题，促使了 requestAnimationFrame 的诞生。 requestAnimationFrame
是专门为实现高性能的帧动画而设计的一个API，目前已在多个浏览器得到了支持，你可以把它用在 DOM 上的效果切换或者 Canvas
画布动画中。 requestAnimationFrame 并不是定时器，但和 setTimeout 很相似，在没有 requestAnimationFrame 的浏览器
一般都是用setTimeout模拟。 requestAnimationFrame 跟屏幕刷新同步（大多数是 60Hz ）。
如果浏览器支持 requestAnimationFrame , 则不建议使用 setTimeout 来做动画。
```
###### requestAnimationFrame 的兼容使用
```
下面是我们常规使用 requestAnimationFrame 的兼容写法，当浏览器不兼容的 requestAnimationFrame 时则通过使用
setTimeout 来模拟实现,且设定渲染间隔为 1000ms/60。

// 判断是否有 requestAnimationFrame 方法，如果有则模拟实现
window.requestAnimFrame =
window.requestAnimationFrame ||
window.webkitRequestAnimationFrame ||
window.mozRequestAnimationFrame ||
window.oRequestAnimationFrame ||
window.msRequestAnimationFrame ||
function(callback) {
    window.setTimeout(callback, 1000 / 30);
};
```
###### 使用 requestAnimationFrame 实现动画
```
使用 requestAnimationFrame 来实现一个物体来回移动的动画。

<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>认识Canvas</title>
</head>
<body>
    <canvas id="canvas" width="500" height="500" style="border: 1px solid #33"></canvas>
    <script>
        var canvas = document.getElementById('canvas');
        var context = canvas.getContext('2d');
        // 兼容定义 requestAnimFrame
        window.requestAnimFrame =
        window.requestAnimationFrame ||
        window.webkitRequestAnimationFrame ||
        window.mozRequestAnimationFrame ||
        window.oRequestAnimationFrame ||
        window.msRequestAnimationFrame ||
        function(callback) {
            window.setTimeout(callback, 1000 / 30);
        };

        // 绘制的圆的对象
        var circle = {
            x: 250,
            y: 250,
            radius: 50,
            direction: 'right',
            // 移动圆形
            move: function() {
                if (this.direction === 'right') {
                    if (this.x <= 430) {
                         this.x += 5;
                    } else {
                        this.direction = 'left';
                    }
                } else {
                    if (this.x >= 60) {
                         this.x -= 5;
                    } else {
                        this.direction = 'right';
                    }
                }
            },
            draw: function() {
                // 绘制圆形
                context.beginPath();
                // 设置开始角度为0，结束角度为 2π 弧度
                context.arc(this.x, this.y, this.radius, 0, 2 * Math.PI, false);
                context.fillStyle = '#00c09b';
                context.fill();
            }
        }
        // 动画执行函数
        function animate() {
            // 随机更新圆形位置
            circle.move();
            // 清除画布
            context.clearRect(0, 0, canvas.width, canvas.height);
            // 绘画圆
            circle.draw();
            // 使用requestAnimationFrame实现动画循环
            requestAnimationFrame(animate);
        }

        // 先画第一帧的圆，即初始化的圆
        circle.draw();
        // 执行animate
        animate();        
    </script>
</body>
</html>

```
#### 4.	JS 里的动画
```





```
#### 5.	动画循环

动画循环
* 初始化
* 动画循环（更新、清除、绘制）
* 结束动画循环
```
var canvas = document.getElementById('canvas');
var context = canvas.getContext('2d');

var monster = {
    x: 30,
    y: 50,
    size: 60
};

var image = new Image();
image.src = 'http://coding.imweb.io/img/p5/monster.png';
//图片加载完毕
image.onload = function () {
    context.drawImage(image,monster.x,monster.y,monster.size,monster.size);
    animate();
};
function animate() {
    if (monster.x > 445) {   ----- 判断是否超过界面，设置if 语句，设置 return ，结束动画循环
        return;
    }

    monster.x += 5;         ------- 不断的向右移动，monster往右不断增加 5px
    context.clearRect(0,0,canvas.width,canvas.height) ----- 清除上一次的整个画布
    context.drawImage(image,monster.x,monster.y,monster.size,monster.size); ----重新绘制
    requestAnimationFrame(animate);    -------- 循环执行 animate 函数，不断执行
};


```
#### 6.	[资料] 键盘事件处理

##### 键盘事件处理
```
在制作 PC 端的游戏的时候，我们经常需要监听键盘的事件，以便响应用户的键盘操作。
目前，对键盘事件的支持主要遵循的是 DOM0级。
```
##### 按键相关事件
```
键盘操作涉及下面三种事件：

keydown：当用户按下键盘上的任意键时触发，而且如果按住按住不放的话，会重复触发此事件。
keypress：当用户按下键盘上的字符键时触发，而且如果按住不放的，会重复触发此事件（按下Esc键也会触发这个事件）。
keyup：当用户释放键盘上的键时触发。
```
##### 按键过程
```
用户按下键盘上的字符键时

首先会触发 keydown 事件
然后紧接着触发 keypress 事件
最后触发 keyup事件
如果用户按下了一个字符键不放，就会重复触发 keydown 和 keypress 事件，直到用户松开该键为止。
```
##### 键码（keyCode）对照表
```
在发送 keydown 和 keyup 事件时，event 对象的 keyCode 属性中会包含一个代码，与键盘上一个特定的键对应。
如下图，为我们键盘键位的 keyCode 对照表：







例子：简单实现键盘控制物体移动
实现的基本原理如下：监听全局键盘操作事件，当用户按下某一按键时，返回对应的键值，
然后再根据键值判断用户按下了哪一按键，来控制物体上下移动的操作，效果如下：



<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>物体移动</title>
</head>
<body>
    <canvas id="canvas" width="500" height="500"></canvas>
    <script>
      var canvas = document.getElementById('canvas');
      var context = canvas.getContext('2d');
      var rect = {
        x: 100, // 矩形的 x 坐标
        y: 400, // 矩形的 y 坐标
        width: 100, // 矩形的宽度
        height: 100, // 矩形的高度
        step: 30 // 矩形移动的步伐
      }
      // 全局监听键盘操作的 keydown 事件 
      document.onkeydown = function(e) {  
        // 获取被按下的键值 (兼容写法)
        var key = e.keyCode || e.which || e.charCode;
        switch(key) {
          // 点击左方向键
          case 37: 
            rect.x -= 20;
            drawRect();
            break;
          // 点击上方向键
          case 38: 
            rect.y -= 20;
            drawRect();
            break;
          // 点击右方向键
          case 39: 
            rect.x += 20;
            drawRect();
            break;
          // 点击下方向键
          case 40: 
            rect.y += 20;
            drawRect();
            break;
        } 
      };
      function drawRect() {
        // 清除画布
        context.clearRect(0, 0, canvas.width, canvas.height);
        // 绘制矩形
        context.fillRect(rect.x, rect.y, rect.width, rect.height);
      }
      // 第一次绘制
      drawRect();
    </script>
</body>
</html>




```
#### 7.	[资料] 碰撞检测
```
碰撞检测
在实现 Canvas 游戏和动画中，往往需要解决物体相互碰撞的情况如。对于物体碰撞相关的问题，我们会在动画中采用 碰撞检测 来解决，以此实现更为逼真的动画。

碰撞检测关键步骤
碰撞检测需要处理经历下面两个关键的步骤：

计算判断两个物体是否发生碰撞
发生碰撞后，两个物体的状态和动画效果的处理
计算碰撞
只要两个物体相互接触，它们就会发生碰撞。

矩形物体碰撞检测
假设检测发生碰撞的物体是 矩形1 和 矩形2 时，我们只需检测 矩形1 的上下左右四侧的和 矩形2 是否存在着距离。我们可以看看下面的图：



我们可以看到 矩形2 和 矩形1 之间没有发生碰撞共有四种可能的情况：

矩形2的右侧 离 矩形1的左侧有一段距离
矩形2的左侧 离 矩形1的右侧有一段距离
矩形2的底部 离 矩形1的顶部有一段距离
矩形2的顶部 离 矩形1的底部有一段距离
当符合上面其中一种情况，则两个矩形没有发生碰撞。

因此通过逆向推导我们可以得出：当上面四种情况都不满足的时候，则代表两个矩形碰撞了。在代码中，我们可以这样写：

// 判断四边是否都没有空隙
if (!(rect2.x + rect2.width < rect1.x) &&
    !(rect1.x + rect1.width < rect2.x) &&
    !(rect2.y + rect2.height < rect1.y) &&
    !(rect1.y + rect1.height < rect2.y)) {
    // 物体碰撞了
}
圆形物体碰撞检测
假设发生碰撞的物体是 圆形 时，检测碰撞则变得比较复杂了，前面矩形所使用的碰撞检测，并不能判断圆形物体的情况。如下图的情况：



那么如何检测两圆是否碰撞了呢？这个时候又到了考验我们数理化的知识了。

检测两圆是否相交：当两个圆心之间的距离是否小于两个圆的半径之和。这是已经被证实的数学运算。如下图所示：



其中 dx 和 dy 分别表示两个圆之间的横坐标和纵坐标的差值。 即 dx = x2 - x1; dy = y2 - y1;

然后我们需要通过 勾股定理 计算两个圆心之间的距离。如下图：



因此我们碰撞检测的代码可以这样写：

var dx = circle2.x - circle1.x;
var dy = circle2.y - circle1.y;
var distance = Math.sqrt((dx * dx) + (dy * dy));
if (distance < circle1.radius + circle2.radius) {
  // 两个圆形碰撞了
}
前面讲解了怎么检测矩形和圆形是否碰撞，基本已经可以适用大部分场景。对于特殊的场景，则需要大家自己去思考如何检测了。

碰撞后的处理
当检测到碰撞后，则可以对碰撞的物体进行状态设置了，可以是相互毁灭，或者是反弹等。这里大家可以根据场景来决定。




```
#### 8.	[资料] 独自开启 Canvas 的旅途吧
```
独自开启 Canvas 的旅途吧 
到这里，Canvas 的教程已经基本结束了，掌声鼓励下自己吧。

到此为止你们所学的 Canvas 知识，已经能够满足接下来我们所要开发的项目——射击小游戏。

但事实上 Canvas 中还存在着许多强大的 API在我们课程中并没有涉及到。如果你对 Canvas 有着一股不能自拔的热情，你可以继续按着下面的知识点，独自地展开一段成为 Canvas 大牛的旅途吧！

更多知识点
这里列出 Canvas 其他的知识点，感兴趣同学们可以深入了解下。

保存和恢复绘画状态(save 和 store)
渐变
阴影
变形
合成
导出画布（getImageData）
像素处理常用接口
相关资料
下面是一些推荐的 Canvas 学习书籍。

《HTML5 CANVAS基础教程》
十分适合新手看的一本 canvas 书籍。



《HTML5 canvas开发详解》

是一本大而全的 canvas 书籍，覆盖的知识点比较多。如果希望全面了解 canvas 的可以看一下。



下面是一些推荐的学习 Canvas 的教程文章

Canvas 入门精通教程
HTML5 Canvas 学习笔记
Canvas API-阮一峰




```
