## 1.	Node 引言
```JS
前面的课程中讲解过出于性能考虑将多个 .js 文件打包为一个 .js文件，减少浏览器的请求。
减少js的体积，将js 的代码压缩，作为软件工程师，不需要每次都手动去做，所以需要一个工具。
这个工具可以自动读取某个目录下的所有js文件，并且可以打包成一个可以发布到线上的js文件，就OK了。但涉及本地文件的读写操作
JS 是无法调用本地文件的，浏览器运行环境只能调用API：BOM 、DOM，无法调用本地文件的

java  python 是在本地电脑或者服务器操作的，可以调用本地文件的

JavaScript 可以运行在电脑或者服务器进行操作的？ Node.js
Node.js 是服务端的 JavaScript 运行环境
本地或者服务器运行 JS 代码
Node.js 是 JavaScript 的运行环境，既不是 JavaScript 的库和框架，也不是另外一门语言。
Node.js 可以调用很多本地或者服务器的接口，可以用来开发 Web 服务器或者本地应用，这是我们课程里面讲到了。
Node.js 运行环境是服务器，而不是浏览器，不需要考虑浏览器兼容问题。

```
![](https://raw.githubusercontent.com/lz109896/Web-datum/26225a54652ca39c2ad27c426ebae233fba8c7d6/Node%E5%BC%95%E8%A8%80.png)

## 2.	Node 安装
```JS
下载地址:https://nodejs.org/en/download/
稳定版带LTS, 最新版本是另外一个


怎么检查是否安装成功？
打开命令行提示符，输入：node -v
会看到版本号，如果与你下载的版本一致，那就说明安装成功
并且说明可以在本地电脑运行Node.js 代码，输入：node,就会出现一个尖括号，

到 Node.js 官网 下载安装包，然后打开安装包按指引一步步安装。注意 Mac 和 Windows 的安装包是不一样的，
不过官网会根据你的操作系统在首页显示对应的安装包，所以大家只要选择对应的版本点击下载就可以了。
安装完成之后，在命令行输入 node -v 看下是否有对应 Node.js 版本号，如果有就说明安装成功。
命令行输入 node 命令进入 node 运行环境，可以输入我们熟悉的 JavaScript 代码，
输入 .exit 或者连按2次 Ctrl + C 退出 node 环境

安装 nodejs 时，也会安装另外一个软件
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/26225a54652ca39c2ad27c426ebae233fba8c7d6/Node%20%E5%AE%89%E8%A3%85.png)

## 3.	NPM
```JS
NPM 类似淘宝网的管理平台

为了更好的管理上传结合下载使用，NPM 就要制定一个规范
比如在 jquery 在包的根目录下添加一个package.json 的文件，通过 json 格式去描述包的信息：包的名字、包的版本号、关键字，更好的管理和识别

初学者一般关注下载，很少关注上传
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/26225a54652ca39c2ad27c426ebae233fba8c7d6/NPM%201.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/26225a54652ca39c2ad27c426ebae233fba8c7d6/NPM%202.png)
```
安装 jquery 的命令：npm install jquery
安装成功会有 nade_modules 的目录，会有 jquery 的包

使用包的命令：var $ = require('jquery');

```
## 4.	命令行工具
```JS
uglify-js -g 压缩代码， 是安装在全局的，不是安装在某个项目下的，
可通过命令行查看安装情况 ：npm i(install 的简写) uglify-js -g
工具的用法帮助命令： uglifyjs -h
查看版本：uglifyjs -v

https://www.npmjs.com/package/uglify-js
```
安装好了，现在进行压缩
![](https://raw.githubusercontent.com/lz109896/Web-datum/26225a54652ca39c2ad27c426ebae233fba8c7d6/%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%B7%A5%E5%85%B7.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/26225a54652ca39c2ad27c426ebae233fba8c7d6/%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%B7%A5%E5%85%B71.png)


## 5.	运行 Node.js 代码

读文件
```JS
var fs = require('fs');
fs.readFile('./index.js', 'utf-8', function(err, data) 
  console.log(data);
});
  
```
```JS

/*辗转相除法求最大公约数: 
*/
function gcd(numberl, number2) { 
  var remainder 0;
  do {
    remainder  number1% number2;
    number1 = number2;
    number2 = remainder;
  )while(remainder !== 0);
  return numberi;
}

KEVINKUANG-MB0: run_nodejs kevinkuangs clear

输入：node app.js 就回车可以自动运行文件了
```
写文件

```JS
var fs = require('fs');
fs.readFile('./index.js', 'utf-8', function(err, data) 
  fs.writeFile('./index.copy.js', data)data); function(err) { 
  if (!err) 
      console.log( 'Write file succcess');
      }
    });
});
  
```
```JS

/*辗转相除法求最大公约数: 
*/
function gcd(numberl, number2) { 
  var remainder 0;
  do {
    remainder  number1% number2;
    number1 = number2;
    number2 = remainder;
  )while(remainder !== 0);
  return numberi;
}

KEVINKUANG-MB0: run_nodejs kevinkuangs clear

输入：node app.js 就回车可以自动运行文件了

````
删除注释

```JS
var fs = require('fs');
fs.readFile('./index.js', 'utf-8', function(err, data) 
  var newData = data.replace(/\/\*[s\S]*\*\//. '');
  fs.writeFile('./index.copy.js', data)data); function(err) { 
  if (!err) 
      console.log( 'Write file succcess');
      }
    });
});
  
```













