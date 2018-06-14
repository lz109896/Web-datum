## 1.准备工作

* [HTML 入门](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML)
* [HTML 元素参考 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element)
* [HTML 参考手册 | w3school](http://www.w3school.com.cn/tags/)

## 2.创建链接

#### 实例
```html
从一个页面转到另一个页面就是Web的魅力所在，而这之间的跳转正是通过<a>元素链接来完成的。

现在就让我们也来创建一个链接，让其跳转到”腾讯课堂”，代码如下：

<a href=“https://ke.qq.com”>腾讯课堂</a>
```
#### 知识讲解
HTML 中的 <a>元素 (或HTML锚元素, Anchor Element) 用于定义一个超链接到其他网络页面或文件，页面内的某个位置，电子邮件地址或其他任何URL。

#### 页面跳转
当其用于页面之间的跳转时主要有三个常用属性，分别为：
* title：指链接标题，一般与内容文字一样。鼠标滑过时暂停一会，会有个title提示效果，
* href：指定链接的目标地址（如果暂时不能确定目标地址可先用#表示）
* target：定义打开窗口方式，默认是当前窗口打开，有四种取值，分别为：
  * _self：当前窗口打开，此值为默认值
  * _blank：新窗口打开（该值是使用最多的）
  * _parent：表示在当前框架的父框架打开（一般用于iframe中，先不用了解，以后再说）
  * _top：表示顶层框架打开（一般用于iframe中，先不用了解，以后再说）
  
#### 页面内跳转
我们先打开一个有页面内跳转的页面：JavaScript秘密花园:https://bonsaiden.github.io/JavaScript-Garden/zh/

滚动鼠标到底部，发现其就是一篇文章。然后点击右边的导航试试，发现只要一点击，中间的内容就会定位到对应导航的内容部分，这其实就是页面内跳转。

仔细看下其地址栏的，你会发现只有后面的“#xxxx"部分发生变化
```html
当<a>元素用于页面内的锚点跳转时，应该先为该页面设置一些锚点，而定义锚点有两种办法：

通过<a>元素的name属性来定义，如：<a name="anchor-name">name属性的值就是锚点的名称</a>
通过其他元素的id属性来定义，如：<div id="anchor-name">id属性值可以作为锚点的名称</div>
设置好了锚点之外，就可以通过<a>元素链接到该锚点位置，其href取值为“# + 锚点名称”，示例如下:

<a href="#anchor1">锚点链接一</a>
<a href="#anchor2">锚点链接二</a>

<div>
    <div>我这里有很多内容...</div>
    <!-- 使用a的name属性定义锚点 -->
    <a name="anchor1">点击锚点链接一，会跳到我这里</a>
    <div>我这里有很多内容...</div>
    <!-- 使用元素的id属性定义锚点 -->
    <p id="anchor2">点击锚点链接二，会跳转到我这里</p>
</div>
```
#### 电子邮件
```html
当其用于邮件链接时，href属性的值为“mailto: + 邮件地址”，示例如下：

<a href="mailto:xuyc_brother@foxmail.com”>发送邮件给我</a>
```
#### 题目
```html
创建一个链接，点击新窗口打开 IMWeb 官网，链接地址为“ http://imweb.io/ ”。

答案：
<a href="http://imweb.io/" target="_blank">IMWeb学院</a>
```

## 3.创建图片
网页中的图片除了用<img>元素创建外，还可以使用CSS的背景图的形式表现

#### 知识讲解
首先<img>元素没有闭合标签，这点一定要记得。

除此之外，<img>元素还有几个重要属性如下：
* src：必备属性，表示图片地址
* alt：必备属性，如果图片加载失败将会显示该内容
* width：可选属性，用于设置图片的宽度，如width="400"
* height：可选属性，跟width类似，用于设置图片的高度，如height="300"
然后在实际页面中，有些图片还是个链接，点击图片会跳转到其他页面，那究竟是怎么回事呢？

其实无非是把图片放在了<a>元素里面当做了内容，如下代码，即可产生一个图片链接：
```html
<a href=“https://www.lagou.com/jobs/1715898.html” target=“_blank”>
    <img src=“http://coding.imweb.io/img/p1/img-2.png” alt=“imweb 前端招聘了”>
</a>
```
最后，更多关于< img >元素知识可参看：< img >:https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a

#### 题目
创建一个图片链接，要求如下：

* 图片地址为“ http://coding.imweb.io/img/img-style.png ”

* 加载失败的提示文字为“IMWeb学院”

* 宽度为“200px”

* 链接地址为“ http://imweb.io/ ”，新窗口打开链接
```html
参考答案
本题主要考察了图片与链接的结合使用，在实际项目中是非常常见的，相信你可以拿下！

<a href="http://imweb.io/" target="_blank">
    <img src="http://coding.imweb.io/img/img-style.png" alt="IMWeb学院" width="200">
</a>
```


## 4创建列表
#### 实例
排行榜其实就是个列表,排行榜是有序的，还有一种无序的不分先后顺序的
文章标签分类就属于无序列表
除此之外，我们还有很多可以用列表表示的东西，如网站的导航，人物头像列表等等。

现在就让我们来创建一个列表，代码如下：
```html
<ul>
    <li><a href=“#”>首页</a></li>
    <li><a href=“#”>全部课程</a></li>
    <li><a href=“#”>精选合辑</a></li>
    <li><a href=“#”>学团</a></li>
</ul>
```
#### 知识讲解
关于列表主要有以下三点需要注意：
* 列表分为有序列表和无序列表两种，分别为< ol >和< ul >元素
* 无论有序还是无序，其直接子元素都只能是< li >
* 列表可以嵌套，如< li >里面的内容如果是< ul >的话就形成了嵌套
 
更多关于列表知识可参看：
[ol](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/ol) 
[ul](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/ul)
[li](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/li)

#### 题目
创建一个无序列表，三个列表项内容如下：

* 言语理解与表达
* 判断推理
* 常识判断

```html
参考答案
这里我们创建的是一个无序列表，所以使用<ul>元素。

<ul>
    <li>言语理解与表达</li>
    <li>判断推理</li>
    <li>常识判断</li>
</ul>

```
## 5.创建表格
#### 知识讲解
每个表格由行与列组成的。< table >表示表格，< tr >表示行，< td >为单元格，< th >表示表头的单元格，每行可以由多个单元格组成，
每一个单元格就是一列。如下是一个简单的两行四列的表格：
```html
<table>
    <tr>
        <th>1月</th>
        <th>2月</th>
        <th>3月</th>
        <th>4月</th>
    </tr>
    <tr>
        <td>31天</td>
        <td>28天</td>
        <td>31天</td>
        <td>30天</td>
    </tr>
</table>
```
我们看到第一行的< tr >里面的直接子元素并不是< td >，而是< th >，这是因为我们第一行是表头，用< th >表示更合适。

当然为了更清楚的区别表头和内容部分，还可以使用< thead >包裹表头的< tr >，< tbody >包裹所有内容的< tr >，除此之外还可以为table添加一个标题< caption >如下：
```html
<table>
    <caption>五险一金缴纳</caption> <!-- table 标题，table里面第一个元素 -->
    <thead> <!-- 使用 thead 包裹表头行 -->
        <tr>
            <th>缴纳项目</th>
            <th>个人缴纳</th>
            <th>单位缴纳</th>
        </tr>
    </thead>
    <tbody> <!-- 使用 tbody 包裹内容 -->
        <tr>
            <td>养老</td>
            <td>8%</td>
            <td>14%</td>
        </tr>
        <tr>
            <td>医疗</td>
            <td>2%</td>
            <td>6.2%</td>
        </tr>
        <tr>
            <td>失业</td>
            <td>1%</td>
            <td>2%</td>
        </tr>
        <tr>
            <td>工伤</td>
            <td>0%</td>
            <td>0.4%</td>
        </tr>
        <tr>
            <td>生育</td>
            <td>0%</td>
            <td>0.5%</td>
        </tr>
        <tr>
            <td>公积金</td>
            <td>14%</td>
            <td>14%</td>
        </tr>
    </tbody>
</table>
 ```
在线预览上面的效果：table demo（为了好看，加了一些CSS样式，可以先不用了解）:http://coding.imweb.io/demo/p1/table.html

基本常用的table就这么简单，更多可参看： < table >（页面下面有其相关元素参考）:https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/table

#### 题目

创建一个成绩单表格，如下：

姓名	| 语文	| 数学	| 英语
 --- | --- | --- | ---
小明	| 89	| 90	| 93
小红	| 95	| 91	| 98
小兰	| 88	| 98	| 90

```html
参考答案
虽然现在表格的使用频率比较少，不过对于数据类型的内容，表格仍是不二之选。相对来说表格涉及到的标签比较多一点，
但是多写写也就熟悉了。

<table>
    <thead>
        <tr>
            <th>姓名</th>
            <th>语文</th>
            <th>数学</th>
            <th>英语</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>小明</td>
            <td>89</td>
            <td>90</td>
            <td>93</td>
        </tr>
        <tr>
            <td>小红</td>
            <td>95</td>
            <td>91</td>
            <td>98</td>
        </tr>
        <tr>
            <td>小兰</td>
            <td>88</td>
            <td>98</td>
            <td> 90</td>
        </tr>
    </tbody>
</table>
```
## 6.创建表单

我们常见的登录，搜索，写博客，发表评论都是表单的一种，这么说就熟悉了吧

#### 知识讲解

（特别注意：form表单所涉及到的知识特别多，先大概了解有这些东西，使用的时候再去查看相关文档即可，以后练习多了，自然就熟悉了。）
表单元素本身是指< form >，不过它也有一个更广泛的概念，指构成表单的所有元素。

首先就< form >元素本身来说，主要有两个属性（暂时不用细究，到后面我们还有详细说明）：
* action：表示表单数据所提交到的处理地址（如果不知道处理地址，可先用#表示）
* method：表示提交内容的方式，默认取值为 get，可以设置为 post


接下来将会简单介绍几种form表单常用元素。在介绍表单常用元素之前，先说下一般它们都通用的几个属性：

* name：表示字段名称
* value：表示字段值（最后提交的表单数据就是所有的字段值）
* disabled：表示字段是否禁用，该属性可以不用设置值，加上该属性即表示禁用
* readonly：表示字段是否只读，该属性可以不用设置值，加上该属性即表示只读


更多可参考：

form W3school:http://www.w3school.com.cn/tags/tag_form.asp

form MDN（页面下面有其相关元素参考）:https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/form

表单属性浅析:http://blog.mingsixue.com/it/HTML-form-attribute.html


下面正式介绍一些常用的表单元素，里面涉及到的所有的示例皆可  在线预览:http://coding.imweb.io/demo/p1/form.html

#### < input >元素
< input >元素跟< img >元素一样，不需要闭合标签。除了上面说到的通用属性外，其常见属性如下：

* type：必备属性，常见取值如下：
  * text：文本输入框
  * password：密码输入框
  * search：搜索框
  * number：数字输入框
  * radio：单选按钮
  * checkbox：复选框
  * hidden：隐藏域（页面不可见，用来保存数据等）
  * file： 上传文件
  * button：普通按钮
  * submit：提交按钮
  * reset：重置按钮
* placeholder：如为输入框时，可设置该属性，在输入框中灰色显示提示信息

简单示例如下：
```html
<!-- 文本输入框 -->
<input type="text" name="username">
<!-- 文本输入框提示信息 -->
<input type="text" name="username" placeholder="用户名">
<!-- 搜索框 -->
<input type="search" name="search" placeholder="搜索">
<!-- 数字输入框 -->
<input type="number" name="age" placeholder="只能输入数字">
<!-- 密码输入框 -->
<input type="password" name="pwd" placeholder="密码">
<!-- 单选框 -->
<input type="radio" name="sex" value="man">男
<!-- 复选框 -->
<input type="checkbox" name="hobby" value="music">音乐
<!-- 隐藏域 -->
<input type="hidden" name="other-data" value="用户不可见数据">
<!-- 上传文件 -->
<input type="file" name="file">
<!-- 普通按钮 -->
<input type="button" name="button" value="普通按钮">
<!-- 提交按钮 -->
<input type="submit" name="submit" value="立即加入">
<!-- 重置按钮 -->
<input type="reset" name="reset">
```
更多 input 请参考：

input W3school:http://www.w3school.com.cn/html/html_form_attributes.asp 

input MDN:https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input


#### < textarea >元素
 
用于多行文本输入，如上面的新浪微博截图中的发表微博就是个多行文本输入框，我们常用的评论输入框也是这个。

可以通过 cols 和 rows 属性来规定 textarea 的尺寸，不过等我们学了 CSS 之后，更好的办法是使用 CSS 的 height 和 width 属性来控制其尺寸。

简单示例如下：
```html
<textarea rows="5" cols="30" placeholder="请输入评论"></textarea>
```
更多 textarea 请参考：

textarea W3school：http://www.w3school.com.cn/tags/tag_textarea.asp

textarea MDN：https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/textarea

#### < select >元素
 
用于创建选项菜单，默认只能选择一个值，可通过设置属性multiple="multiple"来实现多选（很少很少使用多选）。

其选项为< option >元素，常用有两个属性：
* value：表示选中该选项的值。
* selected： 表示默认选中。

简单示例如下：
```html
<!-- 单选且有默认选中值 -->
<select name="tag">
  <option value="html" selected>HTML</option>
  <option value="css">CSS</option>
  <option value="js">JS</option>
</select>
<!-- 多选 -->
<select name="tags" multiple="multiple">
  <option value="html">HTML</option>
  <option value="css">CSS</option>
  <option value="js">JS</option>
</select>
```


更多 select 请参考：

select W3school：http://www.w3school.com.cn/tags/tag_select.asp
select MDN:https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/select

#### < button >元素
< button >元素用来定义按钮，跟 input 定义的按钮不同，这个是有闭合标签的。简单示例如下：
```html
< button >我是个普通按钮< /button >
 ```
同样也可以通过设置 type 属性来实现提交按钮和重置按钮，不过不建议这么做。
```html
<!-- 下面的两种方式不建议使用 -->
<button type="submit">提交按钮</button>
<button type="reset">重置按钮</button>
```
一般对于提交与重置按钮，我们建议使用 input 来定义，对于普通按钮可以使用 button。

更多 button 请参考：
button W3school:http://www.w3school.com.cn/tags/tag_button.asp

button MDN:https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button

#### < label >元素
<label>元素用于关联表单元素的标题，可直接包裹表单元素，也可以通过设置其 for 属性关联到表单元素的 id 属性，这样点击 label 标题上关联的表单元素就可以自动获取焦点，提升用户体验。

简单示例如下：
```html
<!-- 包裹表单元素 -->
<label>用户名：<input type="text"></label>

<!-- 使用for属性关联表单元素的id属性 -->
<label for="username">用户名：</label><input type="text" id="username">
```
更多 label 请参考：

label W3school:http://www.w3school.com.cn/tags/tag_label.asp

label MDN:https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/label
更多参考
更多关于表单元素知识请参考：HTML5中的表单元素；https://www.jianshu.com/p/1be42a9dda69

题目
创建一个登录表单，包括用户名、密码、下次自动登录、登录按钮（为了练习不同的元素，这个按钮我们采用 button 元素。但实际情况下，一般采用 input 元素，设置其 type 属性为 submit），用户名和密码需要使用 placeholder 属性提示


```html
参考答案
表单还是比较复杂的，尤其 <input> 元素的各种 type 属性就够好好理理了。这里我们只是简单的实现了一个登录表单，
为了让每行有点间隔，我们可以使用 <p> 元素，等以后我们学了 CSS 这些间距什么的就可以交给它了。

<form action="#">
    <p><input type="text" name="username" placeholder="用户名"></p>
    <p><input type="password" name="pwd" placeholder="密码"></p>
    <p><input type="checkbox" name="remember">下次自动登录</p>
    <p><button>登录</button></p>
</form>
```
