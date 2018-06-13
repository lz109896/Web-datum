#### 1.	cover 代码被删除事件
```
自己的电脑登录了账号，未退出，点击某连接，黑客通过我自己的电脑进行转账攻击
```
#### 3.	CSRF 基本原理
```
跨站点伪造请求
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/80bf81848c66c84ebf12f1565bf9774cf15ef070/CSRF%20%E5%9F%BA%E6%9C%AC%E5%8E%9F%E7%90%86%201.png)

#### 4.	CSRF 防御
```
针对伪造请求一般是用户不知情情况下发出的，我们一般会在关键操作增加验证码
针对伪造请求一般是从别的网站发出的，可以通过验证请求的 referer 来防御
最后，伪造请求可以成功的最主要还是因为我们的参数是可预测的，攻击者可以通过分析我们的请求，
伪造相应的参数进行攻击，所以我们最好最常用的方式还是让每个请求都带上服务器返回的，不可预测的参数，
这也就是我们说的 anti CSRF token。
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/80bf81848c66c84ebf12f1565bf9774cf15ef070/CSRF%20%E9%98%B2%E5%BE%A1%201.png)

#### 5.	CSRF 防御实操
![](https://raw.githubusercontent.com/lz109896/Web-datum/80bf81848c66c84ebf12f1565bf9774cf15ef070/CSRF%20%E9%98%B2%E5%BE%A1%202.png)
```
1.XSS 和 CSRF 可以配合一起攻击，相互之间是有影响的
2.XSS 可以在原网站中插入脚本，直接发出伪造请求
3.正因为 CSRF 伪造的请求可以通过 XSS 在原网站发出，所以 referer 验证已经失效了，另外，XSS 插入的脚本甚至
可以直接获取或者间接算出服务器返回给你的 token，也就是说 token 验证也有可能会失效
4.前面 CSRF 配合 XSS，会使得CSRF 防御失效，所以我们的防御措施要全面，缺少一环都有可能成为黑客的攻击的入口。
```
#### 6.	XSS 与 CSRF 的结合
```
不断传播的XSS + CSRF 攻击
```
![](https://raw.githubusercontent.com/lz109896/Web-datum/80bf81848c66c84ebf12f1565bf9774cf15ef070/XSS%20%E4%B8%8E%20CSRF%20%E7%9A%84%E7%BB%93%E5%90%88%201.png)

#### 7.	XSS 蠕虫
![](https://raw.githubusercontent.com/lz109896/Web-datum/80bf81848c66c84ebf12f1565bf9774cf15ef070/XSS%20%E8%A0%95%E8%99%AB%201.png)

#### 8.	XSS 蠕虫演示
```

XSS 蠕虫本质上就是 XSS + CSRF 结合的攻击方式，它利用的是社交网络等网站的用户创造内容的特点以及方便传播，
扩大攻击的影响范围。只要做好站点的安全防御，把 XSS 和 CSRF 的防范好了，就可以防止 XSS 蠕虫的出现。

```
