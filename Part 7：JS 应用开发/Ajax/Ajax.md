#### 1.	终于到了 Ajax
Asynchronous Javascript +XML JSON
```
Ajax 现在接口已很成熟，规范。 改变了前端开发的历史，他的出现 WEB 应用才更庞大和复杂，
因而促进前端开发岗位的形成；Ajax 涉及HTTP 

```
#### 2.	Ajax 的威力
```
iframe（框架，内嵌框架） :由于安全问题，性能问题已不再流行
Ajax：现在页面使用 Ajax 已经是的标配了，不需要全部刷新，暗中观察，暗中请求数据，更新页面，局部刷新。

```
#### 3.	需要一个本地服务器
```
服务器：PC 的主机类似、PC 也可以做服务器
提供HTTP 的服务器主要有：Nginx（搭配php、java常用）,Apache（搭配php搭档出现）,Tomcat（搭配java 搭档出现）
Nodejs ：也可以作为服务器，做本地的服务器常用,静态服务器
安装命令：npm install http-server -g
```
#### 4.	XHR
view-source:http://coding.imweb.io/demo/p7/ajax-xhr.html
```
Asynchronous Javascript +XML JSON
异步 :不等了，需要监听 readyState 这个属性
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/5a8572e99684954ed62e388418941cf71e244bf1/XHR%201.png)
```
function getData(callback) {
            var xhr = new XMLHttpRequest();

            xhr.onreadystatechange = () => {
                console.log('xhr after response', Object.assign(xhr));

                if (xhr.readyState === 4) {
                    callback(JSON.parse(xhr.responseText), xhr);
                } else {
                    console.log(xhr.status);
                }
            }

            xhr.open('get', 'data.json');
            xhr.send(null);
        } 
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/5a8572e99684954ed62e388418941cf71e244bf1/XHR%202.png)


#### 5.	[资料] JSON

##### JSON
```
前端新手对 JSON 的理解都是错误的。 — 让人头疼的小江

官网的第一句话：

JSON (JavaScript Object Notation) is a lightweight data-interchange format.

JSON 是一种轻量级的数据交换格式。JSON 是一种格式，而不是对象，所以别再说“这个 JSON 对象有问题”这种话。

var a = { // 这是一个对象字面量，和 JSON 无关
    "hello": "JSON"
};

var b = [ // 这是一个数组字面量，和 JSON 无关
    {
        "hello": "JSON"
    }
];

var c = '{"hello":"JSON"}'; // 这是一个字符串变量，和 JSON 有一点关系
{"hello":"JSON"}
这才是 JSON ，JSON 就是文本，和什么语言没有关系，JS 可以解析，自然 JAVA、Python 都可以解析，所以{"hello":function () {}}不是一个 JSON 是不是就很容易理解了，你这个 function放在 JAVA 里面算个什么回事？！

当然，它是有格式的文本，至于什么格式，看官网 http://json.org/ 就好了。

```
#### 6.	[资料] jqXHR

##### jqXHR
```
jqXHR 是一个对象，是 jQuery 中的 XHR 的对象，影响了一代人。

你辛辛苦苦的写了下面这个代码：

var xhr = new XMLHttpRequest();

xhr.onreadystatechange = () => {
    if (xhr.readyState === 4) {
        // todo
    } else {
        console.log(xhr.status);
    }
}

xhr.open('get', 'data.json');
xhr.send(null);
使用 jQuery 只用这样：

$.getJSON('data.json', function() {
    // todo
});
我想没人不喜欢这样写吧，具体可以参考 http://api.jquery.com/jquery.getjson/ 。所以很多人认为 Fetch 的出现就是受到 jQuery 的影响。

$.getJSON 是一个简写，jQuery 的 ajax 有更底层的接口：

$.ajax({
    dataType: 'json',
   url: 'data.json',
   success: function() {
        // todo
    }
});
别忘了我们的题目是 jqXHR ，所以接口什么的不多说，更详细的介绍可以参考这里：http://api.jquery.com/jQuery.ajax/ 。

给上面的代码赋个值：

const jqXHR = $.ajax({
    dataType: 'json',
   url: 'data.json',
   success: function() {
        // todo
    }
});
没错，所有的 jQuery ajax 返回值，不管是 ajax() 底层还是 getJSON() 高阶，都是返回 jqXHR 对象。

jqXHR 是原生 XHR 的封装，原生有的它都有，原生没有的，它也有。

The jqXHR objects returned by $.ajax() as of jQuery 1.5 implement the Promise interface, giving them all the properties, methods, and behavior of a Promise.

注意 Promise 字眼，Promise 是你们必须要掌握的东西，因为它是所有异步编程技术的基础，可以看看下面的参考资料。

而 Promise 带给 jqXHR 的变化，就是像下面这样写代码：

$.getJSON()
 .done((data) => { // todo })
   .done((data) => { // todo again })
    .fail((err) => { // if error })
这就是为什么要聊聊 jqXHR 。

向 jQuery 致敬。
```
##### 参考
JavaScript Promise迷你书（中文版）：https://www.gitbook.com/book/wohugb/promise/details
http://api.jquery.com/jQuery.ajax/#jqXHR

#### 7.	参数传递

![](https://raw.githubusercontent.com/lz109896/Web-datum/5a8572e99684954ed62e388418941cf71e244bf1/%E5%8F%82%E6%95%B0%E4%BC%A0%E9%80%92%201.png)


http://git.imweb.io/imweb-teacher/p7-ajax
```
1.git clone 这个项目到你本地
2.打开命令行切换到项目目录
3.执行npm i，会把所有依赖的包都下载下来
4.执行npm start，打开http://127.0.0.1:3000/查看效果

 
   // get 的参数直接拼在 url 的末尾
   xhr.open(type, urlMap[type] + (type === 'get' ? `?${data}` : '')); 
   // 模拟 post 请求，必须设置个请求头
      if (type === 'post') {
        xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
      }

      xhr.send(type === 'get' ? null : data);

get 和 post 的区别？

A. HTTP 协议并没有限定 GET/POST 请求参数的长度，长度限制一般都是由浏览器和服务器来决定，所以各浏览器和服务器都
不尽相同，详细数据可以查看这里：https://www.jianshu.com/p/512389822f8b
B. GET 参数更容易被查看、截断、替换等，相比 POST 来说不安全，当然 POST 也安全不到哪里去。
C. 构造 GET 参数的时候，总是会通过 encodeURIComponent 编码的，总是会，别忘了啊；POST 则不用。
D. GET 参数只能加在 URL 的末尾，POST 编码只要和服务器约定好就行了，至少有四种常见的编码，可以参考这里。
https://imququ.com/post/four-ways-to-post-data-in-http.html
```

#### 8.	同源策略
同源策略：same-origin policy
不同域的客户端脚本在没有明确授权的情况下，不能读写对方的资源

![](https://raw.githubusercontent.com/lz109896/Web-datum/5a8572e99684954ed62e388418941cf71e244bf1/%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5%201.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/5a8572e99684954ed62e388418941cf71e244bf1/%E5%90%8C%E6%BA%90%E7%AD%96%E7%95%A5%202.png)
```
A 同源策略的初衷就是安全，但是同源限制也意味着不能共享，这是有悖于互联网的初衷的，所以折中了一下，
  script image style等等资源都是可以跨域共享的。
B 如果二级域名相同，可以通过 JS 来提升域名。
   // 比如 www.qq.com 和 ke.qq.com 要通信，可以各自将域名提升为 qq.com 
   document.domain = 'qq.com'; //  双方都要设置
C cookie 自然不能跨域读取。比如登录态的识别就是依靠 cookie 。
  cookie 可以看这篇文章了解下 :http://bubkoo.com/2014/04/21/http-cookies-explained/

```
#### 9.	CORS
```
同源策略：same-origin policy
不同域的客户端脚本在没有明确授权的情况下，不能读写对方的资源
授权==》Cross-Origin Resource Sharing :跨域资源共享：基于 HTTP 协议实现的
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/5a8572e99684954ed62e388418941cf71e244bf1/CORS%201.png)
```
响应头没有 'Access-Control-Allow-Origin'  就不能跨域

origin 是每个页面的标配字段，发送数据到服务器

```
#### 10.	JSONP
```
JSONP: 是一种格式
JSONP with Padding 
<boby>
     

```
#### 11.	iframe 和 window.name
```
iframe：可以把另外的一个页面迁到我的页面中
window.name ：保留当前的值


```
#### 12.	借助 iframe 跨域
```
127.0.0.1:3001/a.html  获取数据             
127.0.0.1:3002/b.html  生产数据
127.0.0.1:3001/c.html  赋值给window.name
```
b.html 嵌入到 a.html ，a.html 借助 iframe 跨域，c.html的 window.name赋值给b.html，
b.html 生产完数据后，跳转c.html，最后跨域成功

#### 13.	借助 iframe 跨域实战
```
安装 http-server npm i http-server -g ，已安装的跳过
命令行中执行  http-server -p 3001
命令行中执行  http-server -p 3002
浏览器中打开 http://127.0.0.1:3001 观察
修改 a.html ，将注释的部分放出来，未注释的注释起来，刷新页面观察效果
http://git.imweb.io/imweb-teacher/p7-iframe
```
