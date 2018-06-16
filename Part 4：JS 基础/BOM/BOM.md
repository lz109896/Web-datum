#### 1.	BOM 和 DOM
```
BOM :浏览器对象模型，JS通过BOM 访问浏览器相关的信息，对浏览器进行交互，获取宽高，改变当前窗口的地址

DOM ：文档对象模型，JS通过DOM 改变HTML的树结构，HTML树的节点进行增删改查
```
#### 2.	BOM 简介
```
Browser Object Model :浏览器对象模型

location: 链接相关，地址栏相关
navigator： 客户端信息，什么浏览器，什么操作系统
history： 用户的访问记录

window（视窗，窗口的意思） 包括了上面的三个属性

```
#### 3.	window 对象
```
window <---global<---ECMAscript

global  全局作用域
变量----->window 对象的属性：凡是不再其他作用域的变量，都是window 对象的属性
函数----->window 对象的方法：凡是不在其他作用域的函数，都是window 对象的方法
window 对象  是个兜底的对象，会将所有游离，独立的变量和函数放在window 的属性上
```
```
系统对话框
alert
confirm
prompt

例如：
window.alert('hello?')
console.log();

var result =window.confirm('hello?')
console.log(result);

var result =window.prompt('hello?')
console.log(result);
```
#### 4.	location 对象
```
1.最有用的对象之一
2.提供了文档相关的信息

location 可以直接访问

location.href :返回的是链接

location.href = 'https://ke.qq.com';  跳转到其他页面
location.assign（'https://ke.qq.com'）    也是跳转语句，不常用

location.host   返回的是域名

location.pathname    返回的是域名后面的地址路径

location.reload();   刷新当前页面，

location.reload(true);   不从浏览器缓存，直接从服务器拉全新的资源

以上信息可以直接在浏览器调试工具中 console 输入 location 即可看到这些属性和方法
```
```
下面是location属性名的说明：

属性名	            例子	                                      说明
hash	        "#contents"	         返回URL中的 hash（#号后跟零或多个字符），如果URL中不包含散列，则返回空字符串
host	        "ke.qq.com:80"	     返回服务器名称和端口号（如果有端口号才列出）
hostname	    "ke.qq.com"          返回不带端口号的服务器名称
href	        "https://ke.qq.com/course/list?mt=1001&st=2004"	返回当前加载页面的完整URL。
pathname	    "course/list"	       返回URL中的目录和（或）文件名
port	        "8080"	             返回URL中指定的端口号。如果URL中不包含端口号，则这个属性返回空字符串
protocol    	"http:"	             返回页面使用的协议。通常是http:或https:
search	      "?mt=1001&st=2004"	 返回URL的查询字符串。这个字符串以问号开头
```
#### 5.	navigator 对象
```
userAgent  ：浏览器的用户代理字符串

platform  : 浏览器所在系统平台

navigator.userAgent   **必须记住，最常用
navigator.platform    


```
#### 6.	history 对象
```
浏览器的后退按钮和前进按钮

从窗口被打开的那一刻算起，保存着用户上网的记录。

length      历史记录的数量
go()        跳转到指定历史记录
forward()   前进
back()      后退

window.history 对象在编写时可不使用 window 这个前缀。
为了保护用户隐私，对 JavaScript 访问该对象的方法做出了限制。
一些方法：

history.go(index)  - 接受一个整数作为参数，移动到该整数指定的页面，比如go(1)相当于forward()，go(-1)相当于back()
history.back()     - 移动到上一个访问页面，等同于浏览器的后退键
history.forward()  - 移动到下一个访问页面，等同于浏览器的前进键

```
