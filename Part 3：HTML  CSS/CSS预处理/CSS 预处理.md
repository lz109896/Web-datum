## 1：预处理简介
```CSS
网站复杂度日益加深
CSA语法能力不够
就产生了CSS预处理器，增强语法能力。

流行的预处理器：sass、less、stylus
都只是语法形式上不一样而已，功能都一样
都有嵌套、变量、mixin、循环、逻辑&运算....

```
## 2：嵌套
```CSS
嵌套是 sass 最常用的功能特性

&：并符号  ：指的是有两个同样的层级嵌套时的简写

```
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/497f025fc749233bd61311f2530aa6520f5c3da5/%E5%B5%8C%E5%A5%971.png)
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/497f025fc749233bd61311f2530aa6520f5c3da5/%E5%B5%8C%E5%A5%972.png)
## 3：变量
```CSS
$ : 美元符号是一种标识符

```
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/497f025fc749233bd61311f2530aa6520f5c3da5/%E5%8F%98%E9%87%8F1.png)

## 4：mixin
```CSS
mixin  :混入类
就是将常用的一段代码，抽象为@mixin，需要使用时，就可以直接调用

```
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/497f025fc749233bd61311f2530aa6520f5c3da5/mixin%201.png)
## 5：循环
![](https://raw.githubusercontent.com/oqq5518/Liao-Zhou/497f025fc749233bd61311f2530aa6520f5c3da5/%E5%BE%AA%E7%8E%AF.png)
## 6：[资料] Sass 资源参考
```CSS
Sass 作为目前最受欢迎的 CSS 预处理器，学习参考资源也是非常的多，语法入门其实也比较简单，常用的我们都已经介绍过了，
更深入的了解可以参考如下教程：

Sass 官网：http://sass-lang.com/
Sass 中文文档：http://sass.bootcss.com/docs/sass-reference/
Sass 相关教程：http://www.w3cplus.com/blog/tags/302.html
```
#### Sass 安装与编译
```CSS
对于新手来说，Sass 的安装与编译是必然会遇到的一个大问题，一不小心就会让你心灰意冷。不过没关系，耐心点，
前人都已经准备好了一摞经验。

ruby sass

首先，Sass 是用 ruby 写的，所以你可以使用 ruby 来编译。
具体的安装与编译可参考：Sass 安装
这里的主要问题是因为国内网络墙得比较厉害，所以一般安装过程都不会那么顺利。这时就可以选择翻墙，
或者使用淘宝RubyGems镜像安装等
注：因为 ruby 的编译速度实在不怎么的，所以在项目中我们一般选择下面的 libsass。

libsass

libsass 是一个用 C 语言实现的 Sass 解析器。特点是简单、速度快而且易于集成。但是 libsass 只是一个库，
并不能直接使用，如果要实际使用还需要一个外壳来进行包装，如PHP，Node等
对于前端来说，优先选择的当然是用 Node 包裹的 node-sass。
同样由于网络被墙，使用 npm 安装 node-sass 失败率也会非常高，这时你可以选择翻墙，或者自己手动下载对应的
node sass binaries放到对应的目录中。
注：以后我们介绍构建时会介绍如何配置自动化 node-sass 编译，对于大项目来说，该方案才是最优选择。
```
#### 其他编译
编辑器编译：一般来说，编辑器都会有相应的 Sass 编译插件，或默认就自带了 Sass 编译功能

在线编译：Sass meister:https://www.sassmeister.com/

图形化编译工具：Koala:http://koala-app.com/index-zh.html

构建自动化编译：node-sass:http://sass-lang.com/libsass

注：如果你是一个完全的前端新手，建议使用 Koala 或编辑器插件来编译或直接在线编译。等学完了构建课程之后，
就可以随便选择你喜欢的方式进行编辑。


## 写在 HTML & CSS 课程结束
```CSS
首先，恭喜你完成了 HTML & CSS 的所有课程，相信经过这一段时间的学习，你应该有过思索问题时的抓耳挠腮，也有解决完
问题后的满心欢喜，遇到过一些难越的坎，也收获了不少技能点。而这段痛并快乐的旅程正是你作为程序员身份的一个新的开始。

虽然我们已经非常尽力的把知识解构呈现给你，但这肯定不是 HTML & CSS 的所有，更多知识及实践还需要自己多摸索学习，
毕竟知识是无穷的，技术是不断的发展的，要成为一个高手还是需要时间和恒心来磨砺的。

下面补充些内容，作为我们 HTML & CSS 课程的最后的收工。

知识图谱
首先对我们学过的知识进行一个简单的图谱总结，以方便大家系统认识及查漏补缺：

![]()

由于 CSS 脑图图片比较大，可新窗口打开图片或查看
CSS 脑图高清版:http://naotu.baidu.com/file/d2e931b2d0ae2add59e6b49903736725?token=48f0609ca3107975。



CSS 标准、支持及未来
然后在整个课程中，我们模糊了 CSS2 与 CSS3 的界限，而是统一称为 CSS，也很少刻意去说兼容的问题，这是因为 CSS3 已经
出来很多年了，浏览器的发展也非常迅猛，所有的不兼容都是暂时的，最终我们将迎来空前的繁盛。

从 CSS3 开始 CSS 属性是按照功能模块来分开开发的，每个模块开发完毕就会进入下一个版本，这样持续更新迭代发展，而整个
CSS 的大版本还是一致保留在 3 这个阶段，所以不存在 CSS4，但是存在某个模块版本的4，5，6...

CSS Working Group Editor Drafts:https://drafts.csswg.org/
CSS3 test:http://yisibl.github.io/css3test/
Can I use:http://caniuse.com/
Houdini：也许是你从未听过的在CSS领域最令人兴奋的发展:https://www.w3ctech.com/topic/1735
```
#### CSS 规范

如果你有一些代码洁癖，或者进入某个团队，然后发现大家的代码风格各不相同，维护代码时一团乱麻，这个时候一份统一的规范
就很有用了。规范相对来说比较灵活，各个团队可以根据自己团队制定不同的规范，下面是一些规范推荐：

推荐大家使用的CSS书写规范、顺序:http://www.shejidaren.com/css-written-specifications.html

[译]谷歌 HTML/CSS 规范:https://segmentfault.com/a/1190000007023192

CSS编码规范:https://github.com/fex-team/styleguide/blob/master/css.md

#### 个人经验与推荐
常逛站点
CSS Weekly:https://css-weekly.com/

CSS Trick:https://css-tricks.com/

Smashing magazine:https://www.smashingmagazine.com/

Sitepoint:https://www.sitepoint.com/

codrops:https://tympanus.net/codrops/

MDN:https://developer.mozilla.org/zh-CN/

W3cplus:http://www.w3cplus.com/

Codepen（在线编辑代码工具）:https://codepen.io/

#### 个人重构经验
HTML 整站结构设计:http://imweb.io/topic/55e1d253771670e207a16bb2

HTML 结构的拆与合:http://imweb.io/topic/55ea599844d58914555d5e57

CSS 设计中的不变与可变:http://imweb.io/topic/55eb092244d58914555d5e5a

class 命名方法:http://imweb.io/topic/5623c25734764b2c16769749

sheral 移动端重构:https://github.com/imweb/sheral

重构优秀教程合集:https://github.com/marvin1023/mark

#### 书籍推荐
```
《CSS 权威指南》：本书内容主要是 CSS2，虽然 CSS3 部分只涉及了一些选择器，但是对于基础、原理什么的讲解得非常好，非常值得入门。
《图解 CSS3》：本书是 w3cplus 站长所写，由于 CSS3 的发展比较快，所以书中有些内容都已经过时，不过最近作者正在升级更新第二版，建议到时入手。
《CSS揭秘》：本书是集 CSS 经验技巧的大成之作，里面有作者的各种经验及感悟，非常值得入手。
《响应式Web设计：HTML5和CSS3实战（第2版）》：看书名就知道是讲响应式的，对响应式理解不是很深的可以入手。
《SVG 精髓》：从入门到精通，全方位涵盖 SVG 技术，你值得拥有。目前最新版本为第二版。
```
