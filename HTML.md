# 参考学习资源

1. https://www.w3school.com.cn/
1. [课程-KuangStudy](https://www.kuangstudy.com/course?cid=2)



# 前端理解

- 展示层 - 用户交互的最直接层次

> 浏览器网页的开发组成：`前端 <=> (数据交互) <=> 后台`
>
> 常见的手机 APP：`用户 <=> 终端/webview嵌H5 <=> (数据交互) <=> 终端后台 <=> 数据库 <=> 管理后台 <=> 管理前端 <=> 运营人员`

- 前端测试-设计一套适合不同用户浏览器界面与终端设备的页面



- 前端组成
  - HTML+CSS+JavaScript【Typescript-具备新开发特性语言】
  - CSS预处理器（SASS、LESS）
  - 原生JS开发（EMACScript-es6语法规范,采用webpack打包成es5)
  - 计算机基础 - 浏览器、网络协议、API接口等
  - 框架（jQuery、Angular、Vue、React、Axi) 、组件库(vue-element)、
  - <img src="D:\Program\picture_typora\image-20220907210823911.png"  style=zoom:70%></img>
  - 工程化、生态优化
  - 后端基础-Node.Js语言 [框架 - Express]





# HTML基础语法

### HTML简介

HTML 是用来描述网页的一种语言。

- HTML 指的是超文本标记语言 (**H**yper **T**ext **M**arkup **L**anguage)
- HTML 不是一种编程语言，而是一种*标记语言* (markup language)
- 标记语言是一套*标记标签* (markup tag)
- HTML 使用*标记标签*来描述网页





### HTML 文档 = 网页

网站是网页集合，网页是构成网站的基本元素，通常又图片、链接、文字、声音、视频等元素组成。

- HTML 文档*描述网页*
- HTML 文档*包含 HTML 标签*和纯文本
- HTML 文档也被称为*网页*

Web 浏览器的作用是读取 HTML 文档，并以网页的形式显示出它们。浏览器不会显示 HTML 标签，而是使用标签来解释页面的内容



### 使用浏览器打开HTML文件

例：

> [index.html是什么？怎么创建？ | w3c笔记 (w3cschool.cn)](https://www.w3cschool.cn/article/19800436.html)
>
> 文本超链接，指向对应.html文件路径

#### 常见浏览器内核：

<img src="D:\Program\picture_typora\image-20220716154307866.png" alt="20220716154307866" style=zoom:80%></img>



### Web标准

- 结构 - HTML 网页元素的整理和分类
- 表现 - CSS网页元素的版式、颜色、大小等
- 行为 -  Javascript网页模型的定义及交互的编写 





## HTML语法

- 多个空格以及代码行被视为一个空格
- “<p>开始标签  </p>结束标签 ，中间值做为属性”

- 不换行空格**&nbsp**  半角空格**&ensp**  全角空格**&emsp**
- 颜色
  - <img src="D:\Program\picture_typora\image-20220714172359896.png" alt="image-20220714172359896" style="zoom:60%;" />

-  超链接 "<a href/name="连接地址">超链接文本</a>"
- 图像标签“<img src="URL"//图像链接地址  align="TOP/bottom/middle/left/right"//图像位置   width="200" height="200"//图像大小   alt="替换文本" >”
- class与id元素
  - <img src="D:\Program\picture_typora\image-20220714175407364.png" alt="image-20220714175407364" style="zoom:70%;" />



## HTML 标签

HTML 标记标签通常被称为 HTML 标签 (HTML tag)。

- HTML 标签是由*尖括号*包围的关键词，比如 <html>
- HTML 标签通常是*成对出现*的，比如 <b> 和 </b>
- 标签对中的第一个标签是*开始标签*，第二个标签是*结束标签*
- 开始和结束标签也被称为*开放标签*和*闭合标签*



### 属性

例如：<script>标签拥有属性

- async：表示应该立即开始下载脚本，但不能阻止其他页面动作
- charset：使用src属性指定的代码字符集
- defer：表示脚本可以延迟到文档完全被解析和显示之后再执行
- integrity：
- src：表示包含要执行的代码的外部文件
- type：代替language，表示代码中脚本语言的内容类型，代码块的类型决定了解释方法和语法。如:text/javascript：application/javascript



### 常见标签

```html
<!--无序列表-->
<li></li>
```





## HTML示例代码

```html
<img alt="goole" src="/imgages/srpr/logo4w.png" width="275" height="95" /> <!--浏览器根据html向服务器请求png文件，

<!DOCTYPE html>  <!--说明该文档是一个HTML5文档，浏览器按照HTML5语法规则解析-->
<html>
    <head>
        <meta charset="UTF-8"> <!--描述文档的元数据-->
        <title>用户注册</title>
    </head>
    <body>
        <form action="use-register" method="post"> <!--form定义一个表单，用来接收用户输入-->
            <p>用户注册</p>
            <p> 姓名：<input type="text" name="name" size="15"> </p>
            <p>      
            兴趣：<input type="checkbox" name="hobby" value="sport">体育
                <input type="checkbox" name="hobby" value="read">阅读
            </p>
            <p>学历：<select name="education">
                <option value="bachelor">学士</option>
                <option value="master">硕士</option>
                <option value="doctor">博士</option>
                </select> 
            </p>
            <p><input type="submit" name="submit" value="提交">
               <input type="reset" name="reset" value="重置">
            </p>
        </form>
    </body>
</html>


```





# XML(可扩展标记语言)

- **HTML主要描述文档如何在浏览器中显示，XML主要描述数据的内容以及它们的结构关系**
- XML可与HTML互操作并可转换成HTML在Web浏览器上显示
- 具有可扩展性
- 具有更多的结构和语义
- 具有自描述性
- 数据和显示分离



### XTML(可扩展超文本标记语言)

- 将HTML做为XML的应用重新包装
- JavaScript代码必须指明type="text/javascript"

