
## 第一章 问答题
```
1.发明 Java 语言的原因是什么?发明Java语言的主要贡献者是谁?
答：  因为语言无法满足人们的需求，因为C语言是针对特定的芯片将源码程序编译为机器码，不同的芯片不一定能运行成功，很麻烦
也就是说不能跨平台，能运行在A平台未必能在B平台使用，不能运行于各种操作系统。
     主要贡献者是james Gosling


2.“Java 编译器将源文件编译生成的字节码是机器码”,这句话正确吗?
答：错误，为了保持它跨平台的特性,java源文件先编译成一种中间码,在运行的时候再实时编译成目标平台的机器码
java编译后的是字节码。
字节码，为java源代码编译完成后，由JVM转换成的文件，可以在任何装有JVM的系统上，转化相应的机器语言。
机器码：即机器语言，表示的就是运行字节码文件后的二进制序列。


3.Java 应用程序的主类必须含有怎样的方法?
答：包含main方法
public static void main(String args[]){
}
称为该应用程序的主类


4.“Java 应用程序必须有一个类是 public类”,这句话正确吗?
答：错误，Java 源文件必须有一个类是 public类


5.请叙述Java源文件的命名规则。
答：1.若源文件中有多个类，那么只能有一个类是 public 类。
2.若有一个类是 public 类，那么源文件的名字必须与这个类的名字完全相同，扩展名是 .java 。
3.若源文件没有 public 类，那么源文件的名字只要与某个类的名字相同，扩展名是 .java 就可以了。


6.源文件生成的字节码在运行时都加载到内存中吗?
答：不一定，动态随需要运行才加载

```
#### 7.怎样编写加载运行 Java Applet的简单网页。
```
答：？？？
C:\Documents and Settings\Administrator>appletviewer
用法：appletviewer <options> url(s)
其中，<options> 包括：
  -debug                  在 Java 调试器中启动 applet 小程序查看器
  -encoding <encoding>    指定由 HTML 文件使用的字符编码
  -J<runtime flag>        向 Java 解释器传递参数
-J 选项不是标准选项，如有更改，不另行通知。
网页就是HTML，嵌入Object标签就可以

8.JDK1.6编译器使用-source参数的作用是什么?- source参数的默认取值是什么?
答：-source参数的作用是约定字节码适合java的平台,默认取值是1.6


9.参照例1-1编写一个Java应用程序,程序能在命令行输出“早上好, Good Morning"

public class Hello {
    public static void main(String[] args) {
        System.out.println("早上好,Good Morning");
    }
}

```


## 第二章 问答题
```
1.什么叫标志符?标志符的规则是什么?
概念：用来标志类名、变量名、方法名、类型名、数组名、文件名的有效字符序列称为标志符

java语言规定标志符由字母、下划线、美元符号和数字组成，并且第一个字符不能是数字
1.标志符由字母、下划线、美元符号和数字组成，长度不受限制
2.第一个字符不能是数字字符
3.标志符不能是关键字
4.标志符不能是 true 、false 和 null .
5.标志符中的字母是区分大小写的

2.什么叫关键字?请说出5个关键字。
关键字就是java 语言中已经被赋予特定意义的一些单词，他们在程序上有着不同的用途，不可以把关键字作为名字来用
class、public、static、void、extends、double

3.Java的基本数据类型是什么?
 整数类型：byte，short，int，long
 浮点类型：float，double
 字符类型：char
 布尔(逻辑)类型：boolean
```

#### 4.下列哪些语句是错误的?
````
int x=120；
byte b=120；
b=x；

答：b=x，错；应修改为：b(byte)=x；

```
#### 5.下列哪些语句是错误的?
```
float x=12.0；
float y=12;
double d=12；
y=d;

答：y=d，错；应修改为：y(float)=d
```

6.下列两个语句的作用是等价的吗?
char x=97；
char x='a'；


7.下列 System. out. printf语句输出的结果是什么?
int a=97:
byte bl=(byte)128



```
