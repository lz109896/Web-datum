#### 1.	React
```
jQuery 是非常经典的 JS 库，不流行了，React 的出现，延伸出很多东西

```
#### 2.	React 简介
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/React%20%E7%AE%80%E4%BB%8B%20.png)
```
React 是 JS 的一哥，是一个基于 JS 库构建用户 UI 界面（组件库的库）

1.首先，React 是一个 UI 库，通过使用 React，我们可以更方便直观地构建复杂的页面，这也是大部分 UI 库的目的。
2.React 最大的特点就是将页面结构进行组件化，根据页面结构划分出一个个组件，代码结构会更清晰，有利于我们开发和后期维护。
3.经过 React 组件化之后，因为相关逻辑的代码都放在一起了，而且组件间也很大程度上解耦了，我们可以很方便地复用组件。
4.React 本身只是个 UI 库，现在我们看到复杂庞大的 React 全家桶是在 React 的基础上衍生出的其他的库，通常跟 React 组合
在一起使用，React 本身是没有集成这些功能的。Redux因其简单易学体积小在短时间内成为最热门的前端架构。
```
#### 3.	搭建React 开发环境
```
操作步骤：
1.克隆代码： git clone http://git.imweb.io/imweb-teacher/react-todos
2.安装项目本身依赖：npm i
3.安装构建依赖: npm i babel-core babel-loader babel-preset-es2015 babel-preset-react --save-dev
4.安装 react：npm i react react-dom --save
5.配置构建命令，在 module 里的 rules 字段增加 babel 编译配置，修改后的 module 字段如下：
```
```js
module: {
    rules: [{
        test: /\.css$/,
        use: ['style-loader', 'css-loader']
    }, {
        test: /\.jsx?$/,
        exclude: /node_modules/,
        use: {
            loader: 'babel-loader',
            options: {
                presets: ['es2015', 'react']
            }
        }
    }]
}
```
```
6.运行构建：npm run dev
上面的操作重点其实就是添加 babel-loader，还有配置 babel 的 presets，按照上面一步步操作，就可以搭建 React 的开发环境了。
后面我们会在这个项目基础上用 React 做一个简单的 todolist 小应用。
```

#### 4.	JSX 函数与 render 函数
```
JSX 语法就跟HTML语法一样，class 被className 替代
JSX 文件都有 render ，是入口函数。，按照它的逻辑，可以看完这个代码
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/JSX%20%E5%87%BD%E6%95%B0%E4%B8%8E%20render%20%E5%87%BD%E6%95%B0%201.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/JSX%20%E5%87%BD%E6%95%B0%E4%B8%8E%20render%20%E5%87%BD%E6%95%B0%202.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/JSX%20%E5%87%BD%E6%95%B0%E4%B8%8E%20render%20%E5%87%BD%E6%95%B0%203.png)

#### 5.	组件化
```
html 标签   <input />    小写
自定义组件   <Input />    大写
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/%E7%BB%84%E4%BB%B6%E5%8C%96%201.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/%E7%BB%84%E4%BB%B6%E5%8C%96%202.png)

#### 6.	事件绑定
```
bind 的方法：改变作用域，并且将作用域指向传入对象

如果没有 .bind(this)， this就是 null

在 React 里面事件绑定是直接在标签属性中添加的，相比于原生的 addEventListener 的方式，这种方式比较方便且直观。
不过要明白的是这只是 React 封装的方式而已，其实际原理上也是通过 addEventListener 来添加事件绑定的。

```
#### 7.	列表渲染
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/%E5%88%97%E8%A1%A8%E6%B8%B2%E6%9F%93%201.png)


#### 8.	props
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/props%201.png)
```
this.props ：相当于参数

在 React 中，组件的配置参数都是通过 props 获取的，配置的参数可以是简单的字符串，也可以是对象，甚至是回调函数。

组件通过接收参数配置，这样既维护了组件本身的独立性，也可以增加组件的灵活性，更便于组件的复用。

```
#### 9.	state
```
state 是组件内部的数据，一些只需要组件内部控制的状态都可以在 state 中保存数据。

在 React 中，每次调用 setState 方法都会触发组件的重新渲染逻辑，这样就可以做到每当数据变化时，页面就会体现出来。
这种方式你可能会觉得每次都重新渲染整个页面，性能会有问题，但是实际上 React 通过 虚拟DOM 的方式来实现的。
http://www.alloyteam.com/2015/10/react-virtual-analysis-of-the-dom/
```
#### 10.	组件间通信
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/%E7%BB%84%E4%BB%B6%E9%97%B4%E9%80%9A%E4%BF%A1%201.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/%E7%BB%84%E4%BB%B6%E9%97%B4%E9%80%9A%E4%BF%A1%202.png)
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/%E7%BB%84%E4%BB%B6%E9%97%B4%E9%80%9A%E4%BF%A1%203.png)
http://cn.redux.js.org/
#### 11.	refs 和 DOM
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/refs%20%E5%92%8C%20DOM%201.png)
```
1.焦点处理，文本选择或媒体控制
2.控制 js 动画
3.使用依赖 DOM 第三方库

```
#### 12.	生命周期
```
render
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/462720a5fd8bdf835191f9426801252a28508725/%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%201.png)


#### 13.	 [资料] React 体系
```
React 的衍生
我们经常说的 React ，可以称为 React Core ，2011 年由 Facebook 工程师 Jordan Walke 创建，六七年时间过去了，React 现在是一个巨无霸。

React Core 有很大的变化，它进一步的分化出了 React Core、React DOM、React Server 。Core 不多说，React DOM 是用于浏览器，React Server
用于 Nodejs ，它的魔爪已经伸向了服务端，就是这个服务端渲染的特性被很多框架所借鉴，算是开启了一个时代。

围绕这个 React Core ，大批量的辅助库涌现了出来，典型的如 React Router、Redux ，生态越来庞大，于是又有了 ant-design 这些大而全的框架。

前端和服务端都被 React 占领，它还没有停歇，触角又伸向了 iOS 和 Android ，React-Native ，从此我们可以用 HTML CSS JS 写出手机端应用。

所以啊，在众多的库和框架当中，我们选择 React 介绍给大家。如果说前端是一个世界，那么 React 从这个世界衍生出了一个更为广阔的世界。
现在给大家开了一扇窗，如果喜欢，你们就要靠自己的双手开出一扇门了，努力！
```
一些资源

React 官网:https://reactjs.org/

官网翻译版:https://doc.react-china.org/

React.js 小书 :http://huziketang.mangojuice.top/books/react/

虚拟 Dom :http://www.alloyteam.com/2015/10/react-virtual-analysis-of-the-dom/

PropTypesv :https://doc.react-china.org/docs/typechecking-with-proptypes.html

高阶组件:https://doc.react-china.org/docs/higher-order-components.html



