#### 1.	流行的几个框架
```
qunit （不建议使用，jQuery 御用框架。只考虑浏览器的兼容性）：jQuery  、Browser
mocha （中庸的库，没有特色，没有短板） ：Node & Browser  、expressjs
jasmine （历史悠久，比较流行，很多有名的库用它）：JsUuit演化而来 、Node & Browser 、vuejs
karma （搭配其他框架使用，凌驾于框架的库之上）： Not A FrameWork  、A Test-Runner
facebook /jest：Facebook、React、Koa、零配置、内置代码覆盖率、强大的Mocks

```
#### 2.	Jest 入门
```


```
![]()


#### 3.	Jest 基本概念梳理
```
安装 ：npm i jest -save-dev
运行 ：jest  npm jest
零配置 :**test.js  


Test Suits : 测试套件   每个文件
Test Group : 分组      descripe()
Test Case  : 测试用例    test()
Assert    : 断言    expect()



```
#### 4.	Jest 配置
```


```
![]()

#### 5.	Jest Matchers
```
取反：not

```



#### 6.	测试 DOM
```




```
#### 7.	测试 DOM 原理
```
1.jest 可以做DOM 操作，是因为内置了JSDOM
2.JSDOM 是一个模拟浏览器环境，一个负责任的工程师，肯定回去真实环境（浏览器）中测试。
3.需要在 node 上运行
4.如果可以的话，Chrome headless 是比 JSDOM 更好的选择

在真实环境中测试也有解决方案，如 Vuejs 就是 jasmine+karma的方案，没错，关键就是这个 karma，它会捕获你
机器上的浏览器并自动运行测试代码，体验不错，大家可以尝试下。

Chrome headless 

Chrome headless 是真实的 Chrome ，就差 UI 界面了，自然而然它的效果比 JSDOM 之类的模拟库要好的多，不知道
后续 Jest 会不会内置 Chrome headless 。当然，你们可以 fock Jest 的仓库，将这个功能 PR 过去，你可以的。

```
#### 8.	测试 Tab 组件
```




```
#### 9.	测试异步流程
```




```
#### 10.	Jest Mocks
```




```
#### 11.	Jest Mocks 实战
```
1.Mocks 可以擦除函数的实际实现来测试代码之间的链接
2.Mocks 可以捕获对函数的调用
3.manual_mocks 用来 mock 依赖的模块，放置在相应 __mocks__ 目录下
4.使用 mopck function,可以查看函数的调用次数，以及入参情况

```
#### 12.	测试 React 组件入门
```




```
#### 13.	代码覆盖率
```
代码覆盖率其实是一个非常容易理解的概念，就算没有这些概念、框架，按照正常的思路，我们也会带得出
行覆盖率、
语句覆盖率、
函数覆盖率、
分支覆盖率。



```
#### 14.	代码覆盖率实战
```




```
#### 15.	因为测试，所以专业
```




```
