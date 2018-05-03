#1、 什么是Markdown ？
    Markdown是一种轻量级且易于使用的语法，用于在GitHub平台上设计所有形式的文字。
    Markdown是一种在网络上设置文本样式的方法。控制文档显示；将单词格式化为粗体或斜体，添加图像以及创建列表只是我们使用Markdown可以执行     的一些操作。大多数情况下，Markdown只是常规文本，其中包含一些非字母字符。例如：#、*。
    
#2、例子：使用Markdown很容易让一些文字变得粗体而其他词语变得斜体。甚至可以链接到谷歌！
#3、标题和行：结构化文件：
    a、不同级别的标题组织可以使用#开始行来创建标题，对于不同的标题大小，可以使用“#”直至“######；编号列表1.2.3.、或使用*、或使用—
    
    b、引用某人，可以再该行之前使用“>”字符
    c、有内联代码块，可以用反斜杠包装
    d、长的代码块，你可以缩进四个空格
    e、GitHub还支持所谓的代码屏蔽，它允许多行不缩进：
```
if (isAwesome){
  return true
}
```
   f、使用语法高亮显示，请使用以下语言：
```javascript
if (isAwesome){
  return true
}
```
   g、引用并链接到别人。如果想对某人发表评论，可以用@符号给他们的名字加上前缀：嘿@kneath  - 爱你的毛衣！
   h、可以使用表情符号！
   i、可以嵌入照片，首先要有图片链接，如：（https://octodex.github.com/images/yaktocat.png）
   
   
#语法指南
   开头：
# This is an <h1> tag
## This is an <h2> tag
###### This is an <h6> tag
   
   重点：
*This text will be italic*
_This will also be italic_

**This text will be bold**
__This will also be bold__

_You **can** combine them_
   
   有序：
1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b
   
   无序：
* Item 1
* Item 2
  * Item 2a
  * Item 2b
   
   图片：
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)

   链接：
http://github.com - automatic!
[GitHub](http://github.com)

   引用文字：
As Kanye West said:

> We're living the future so
> the present is our past.

   内联代码：
I think you should use an
`<addr>` element here instead.

   语法高亮显示：
```javascript
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
```
   以下是没有语法高亮显示的Python代码示例：
def foo():
    if not bar:
        return True
        
    任务列表：
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item

     表：可以通过组合单词列表​​并用连字符-（第一行）分隔它们，然后用管道分隔每个列来创建表格|：
 
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column

     在存储库中发布引用：任何引用问题或拉取请求的号码都会自动转换为链接。
 #1
mojombo#1
mojombo/github-flavored-markdown#1

    删除线
任何包含两个撇号（如~~this~~）的单词都会被划掉。

   
