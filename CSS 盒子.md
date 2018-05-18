
#### 第一节：盒模型相关属性详解
margin  （与padding属性原理一样）

```
.box-1 {
    margin-top: 10px;
    margin-righe: 20px;
    margin-bottom: 10px;
    margin-left: 30px;
}
```
太麻烦了，以下是简写：
```
.box-1 {
    margin: 10px 20px 10px 30px;
}

顺时针，上(top)右(right)下()bottom左(left)。

如果值全部是 10px：
.box-1 {
    margin: 10px;
}
```
border
```
border-width
border-style
border-color

.box-1{
    border:1px solid #ccc;
}


.box-1{
    border-color: #f00 #ccc #ccc; /*  top、left和right、bottom    */
    border-width: 2px 1px; /*  top和bottom、left和right    */
    border-style: solid; /*   all   */   
}


    border-top ----------> 包括：border-top-width 、 border-top-style 、  border-top-color
    border-righe
    border-bottom
    border-left
```

#### 第二节：元素的显示隐藏
```
display
1.所有的后代元素都隐藏
2.好像这个元素不存在
（点击后，下面的内容顶上去了，自己原有的内容都消失了）

visibility
1.元素的大小不变，可理解为透明（点击后，自己原有的内容都消失了，但是下面的内容没有顶上去了）
2.子元素设为 visibility visible ，则该子元素（内容）依然可见，弹出的信息消失了
3.设置visibility hidden 展现后代元素

overflow
1.规定了当内容元素溢出父容器时的展现形式
2.设置hidden，裁剪内容，使用滚动条来显示或直接显示超出部分
3.设置overflow auto，出现滚动条
```
#### 第三节：背景
```
background-image: 背景图片
background-color:背景颜色
background-repeat: 背景图片平铺方式
background-position: 背景图片定位
background-size: 背景图片大小
background: 背景简写

.box {
    height: 400px;
    background-image: ulr('bg.jpg');
    background-color:#e8e8e8e8;
    background-repeat: no-repeat;
    background-position: center center;
    background-size: 100px 100px;
}

实际工作都是简写的,精简自己代码：

.box {
    height: 400px;
    background：ulr('bg.jpg') #e8e8e8e8 ound-no-repeat center center/100px 100px;
}


图片介绍
图片作为网页必不可少的一部分，在网页中占据着非常重要地位。一般来说，有以下两种方式来使用图片：

通过 img 元素直接使用
通过 background-image（背景图片）的形式使用
这两种形式的区别在于，前者一般具有实际含义（如产品图片，相册图片等），而后者一般用于装饰效果。

图片初步了解
目前网页中常用的图片大概有如下几种格式，它们有着各自的显著特点，被应用在各种不同的场景：

jpg/jpeg：由于其色彩还原度比较好，所以一般色彩丰富的图片均采用该格式，如宣传图、产品图、相册图等等。
（其实我们相机拍出来的照片就是该格式的）
png：由于其对透明度的良好支持，所以一般用于透明图片，如 logo 图、图标图等
gif：由于其对动画的支持，所以一般用来实现动效图片，如 loading 加载动画、一些搞笑图片等
除了这三种图片格式外，还有 ico 格式和 webp 格式：

ico 格式属于图标文件，主要用于网址前面的标识图标，如腾讯课堂及 IMWeb 前端学院的图标
webp 格式是由 google 研发的图片格式，它既具备高压缩率，又具备透明度以及动画的特性。
目前各个大互联网公司都有在使用该格式，其带来的效果也非常显著。
但是该格式有个明显的缺陷：目前浏览器端只有 google 浏览器支持。
参考资料
JPEG 图像
GIF 图像
PNG 图像
WebP 探寻之路
WebP相对于PNG、JPG有什么优势？
图片优化
通过HTTP Archieve统计显示，图片内容已经占到了互联网内容总量的65%左右。如下图（时间为 2017-03-15）:



如此多的图片，当然占用了很多流量及时间，所以从性能优化的角度看，图片绝对是优化的热点和重点之一。
由于图片优化篇幅太长，这里就不再展开介绍了，下面推荐一些图片优化的极佳资料以供参考：

Web性能优化：图片优化
前端图片优化机制
图片优化
```
#### 第四节：雪碧图（CSS Sprite ）
```
background-position
例如：background-position: -60px 0;
```
#### 第五节：渐变背景——————线性

![1](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/6920e7271c5c3b65ae51fecc147a835c585d2fa4/%E7%BA%BF%E6%80%A7%E6%B8%90%E5%8F%98.png)
![2](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/6920e7271c5c3b65ae51fecc147a835c585d2fa4/%E7%BA%BF%E6%80%A7%E6%B8%90%E5%8F%981.png)
![3](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/6920e7271c5c3b65ae51fecc147a835c585d2fa4/%E7%BA%BF%E6%80%A7%E6%B8%90%E5%8F%982.png)
![4](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/6920e7271c5c3b65ae51fecc147a835c585d2fa4/%E7%BA%BF%E6%80%A7%E6%B8%90%E5%8F%983.png)
![5](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/6920e7271c5c3b65ae51fecc147a835c585d2fa4/%E7%BA%BF%E6%80%A7%E6%B8%90%E5%8F%984.png)
![6](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/6920e7271c5c3b65ae51fecc147a835c585d2fa4/%E7%BA%BF%E6%80%A7%E6%B8%90%E5%8F%984.png)

#### 第五节：渐变背景——————径向
![1](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/0101f55a7d47e8a396c367dff29af713742ab603/%E5%BE%84%E5%90%911.png)
![2](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/0101f55a7d47e8a396c367dff29af713742ab603/%E5%BE%84%E5%90%912.png)
![3](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/0101f55a7d47e8a396c367dff29af713742ab603/%E5%BE%84%E5%90%913.png)
![4](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/0101f55a7d47e8a396c367dff29af713742ab603/%E5%BE%84%E5%90%914.png)
![5](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/773c0fbbc41db27931bac0df487c3751ddaf4156/%E5%BE%84%E5%90%915.png)
![]()
![]()












