# CSS（Cascading Style Sheets)

- 对网页中的对象的位置进行像素级的精确控制，支持几乎所有字体字号样式，拥有对网页对象和模型样式的编辑能力，进行初步交互设计。

## CSS基本语法

### **添加CSS样式表**

1. 外部样式表 - CSS保存在.css文件中、在HTML文件中使用<link>引用

   ```html
   <link href="css/style.css" rel="stylesheet" type="text/css"/>
   ```

   

2. 内部样式表 - 将CSS放在<style>标签里

   ```css
   <style type="text/css">
   	h1{color:#f00}
   	body{background-image:url(images/bg.gif)}
   </style>
   ```

   

3. 内联样式表 - 仅影响一个元素、在HTML元素的style属性中添加

   ```css
   <p style="color:#0000ff">该段落以蓝色显示</p>
   ```

   

选择-class 或者 id（单标签-独一无二）

```html
<p class="TYPE1" id="type">Hello world!</p>

<!--四种选择方式-->
1.元素选择器
p{
	color:red;
}

2.类选择器
.TYPE1{//选择所有class=“TYPE1”的类
	color:red;
}
h1.TYPE1//选择TYPE1中的h1元素
<h1 class="TYPE1">h1标签内部内容</h1>
<p class="TYPE1">p标签内部内容</p>

3.id选择器 //id不能以数字开头
#type{
	color:red;
}

4.通用选择器
*{
	text0-align:center;
	color:bule;
}
```



### 颜色

<img src="D:\Program\picture_typora\image-20220719220625558.png" style="zoom:80%" />



**CSS规则集（rule-set）由选择器和声明块组成:**

<img src="D:\Program\picture_typora\image-20220724150404044.png" style="zoom:60%"/>

- 选择器指向您需要设置样式的HTML元素
- 声明块包含一条或多条用分号分隔的声明
- 每条声明都包含一个CSS属性名称和一个值，以冒号分隔
- 多条CSS声明用分号分隔，声明块用{}扩起



