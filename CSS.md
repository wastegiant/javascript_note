# CSS（Cascading Style Sheets)

- 对网页中的对象的位置进行像素级的精确控制，支持几乎所有字体字号样式，拥有对网页对象和模型样式的编辑能力，进行初步交互设计。

**运行流程**

1. 浏览器载入 HTML 文件（比如从网络上获取）。
2. 将 HTML 文件转化成一个 DOM（Document Object Model），DOM 是文件在计算机内存中的表现形式，下一节将更加详细的解释 DOM。
3. 接下来，浏览器会拉取该 HTML 相关的大部分资源，比如嵌入到页面的图片、视频和 CSS 样式。JavaScript 则会稍后进行处理，简单起见，同时此节主讲 CSS，所以这里对如何加载 JavaScript 不会展开叙述。
4. 浏览器拉取到 CSS 之后会进行解析，根据选择器的不同类型（比如 element、class、id 等等）把他们分到不同的“桶”中。浏览器基于它找到的不同的选择器，将不同的规则（基于选择器的规则，如元素选择器、类选择器、id 选择器等）应用在对应的 DOM 的节点中，并添加节点依赖的样式（这个中间步骤称为渲染树）。
5. 上述的规则应用于渲染树之后，渲染树会依照应该出现的结构进行布局。
6. 网页展示在屏幕上（这一步被称为着色）。



## CSS基本语法

- CSS有级联和继承性
- 在标签中同时使用id与class，因为class是全局属性，id是局部属性，会先渲染class再渲染id，最后显示id选择器的属性样式

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




### 选择器

- 使用选择器列表时，如果任何一个选择器无效 (存在语法错误)，那么整条规则都会被忽略

<img src="../../picture_typora/CSS/image-20230228163350932.png" alt="image-20230228163350932" style="zoom:80%;" />

选择-class 或者 id（单标签-独一无二）

```css
<p class="TYPE1" id="type">Hello world!</p>

<!--选择方式-->
1.元素选择器
p{//选择器
	color:red;//声明属性
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

5.伪类选择器
h1:hover { } //:hover伪类会在鼠标指针悬浮到h1元素上的时候选中这个元素
a:hover{ } //悬浮到a标签上选中它

6.运算符选择器
后代选择器 (以空格 分隔) 选择div中的所有p元素
子元素选择器 (以大于 > 号分隔）选择div中的子级p元素
相邻兄弟选择器（以加号 + 分隔）选择所有div后的第一个p元素
普通兄弟选择器（以波浪号 ～ 分隔）选择div后所有p元素
div p
{
  background-color:yellow; //所有div后的p元素
}

选择器可以多选，以逗号分隔
h1,h2,p.#i2,.class1{
    
}

```



### 盒模型

- margin：外边距
- border：边框
- padding：内边距

![CSS box-model](../../picture_typora/CSS/box-model.gif)



### 图像、媒体、表单处理

**图像大小处理**

```css
//max-width
.img{
    max-width:100%; //调整为最大宽度不超过盒模型
}

//object-fit
img{
    object-fit:contain; //填充盒模型-保持原比例
    object-fit:cover; //填充盒模型-裁剪
}
```





### 常见样式属性

- font-size：字体大小
- width：宽度
- background-color：背景颜色
- border：边框
- font-family：字体选择
- border-bottom：下边框样式
- color：颜色
- font-weight：字体粗细
- text-decoration：设置文本的修饰线外观



#### 边框属性

![image-20230228174549055](../../picture_typora/CSS/image-20230228174549055.png)

![image-20230228174512249](../../picture_typora/CSS/image-20230228174512249.png)



### @规则

> 一系列特殊规则，为css提供特殊表现

```css
body {
  background-color: pink;
}
//查看是否可以将媒体查询添加到 CSS 中，该查询将根据视口宽度更改样式。更改浏览器窗口的宽度以查看结果。
@media (min-width: 30em) {
  body {
    background-color: blue;
  }
}
```



## 样式表层叠

- CSS 规则的顺序很重要，当应用两条同级别的规则到一个元素的时候，写在后面的就是实际使用的规则。

有三个因素需要考虑，根据重要性排序如下，后面的更重要：

1. **资源顺序**
2. **优先级**
3. **重要程度**



**优先级：**!important > style(内联样式) > id > class  > 标签



**层叠优先**

```css
z-index: 1 //通过z-index设置为最顶层，层叠在页面最前
```





## 布局

### Display / Visibility

块级元素：占用全部行宽度，前后都是换行符

- /<h1>
- /<p>
- /<div>

内联元素：不强制换行

- /<span>
- /<a>

```css
h1{
    display:inline; //将h1元素更改为内联元素
}
span{
    display:block; //将span元素更改为块级元素
}
```



### 弹性盒子：flex布局

- flex元素具有继承性，子元素自动继承父元素成为flex布局

```css
display: flex;
```

![](../../picture_typora/CSS/flex_terms.png)

- **主轴**（main axis）是沿着 flex 元素放置的方向延伸的轴（比如页面上的横向的行、纵向的列）。该轴的开始和结束被称为 **main start** 和 **main end**。
- **交叉轴**（cross axis）是垂直于 flex 元素放置方向的轴。该轴的开始和结束被称为 **cross start** 和 **cross end**。
- 设置了 `display: flex` 的父元素（在本例中是<section>）被称之为 **flex 容器（flex container）。**
- 在 flex 容器中表现为弹性的盒子的元素被称之为 **flex 项**（**flex item**）（本例中是<article>元素。

```css
//flex布局的主轴默认方向为row行
section{
    display:flex; //默认为row排列
	flex-direction: column; //将flex项更改为column列排列
    flex-direction:row-reverse; //将flex项更改为行，但是反转start与end的位置
    flex-direction: column-reverse; //反转列的start与end位置
}
```



#### flex元素属性

> 你可能很少看到 `flex-grow`，`flex-shrink`，和 `flex-basis` 属性单独使用，而是混合着写在 [`flex`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex) 简写形式中。 `Flex` 简写形式允许你把三个数值按这个顺序书写 — `flex-grow`，`flex-shrink`，`flex-basis`。

- flex-basis：定义了该元素的**空间大小**（**the size of that item in terms of the space**），flex 容器里除了元素所占的空间以外的富余空间就是**可用空间** available space。该属性的默认值是 `auto` 。

- flex-grow：弹性填充并可按比例分配flex项
- flex-shrink：赋予不同的值来控制 flex 元素收缩的程度 —— 给`flex-shrink`属性赋予更大的数值可以比赋予小数值的同级元素收缩程度更大。



#### 设置flex项均匀分布

```css
justify-content: space-between;
```



#### 设置flex项多行分布

```css
ul {
  display:flex;
flex-wrap: wrap;
}
```



#### 设置flex项空间分布

- **垂直方向**

```css
.box {
            display: flex;
            align-items: flex-start;
          }
```

![image-20230228211311830](../../picture_typora/CSS/image-20230228211311830.png)

- **水平方向**

- ```css
    .box {
              display: flex;
              justify-content: flex-start;
            }
  ```

![image-20230228211512262](../../picture_typora/CSS/image-20230228211512262.png)



#### **避免flex项溢出**

```css
flex-direction: row;
flex-wrap: wrap;
//上面两项的缩写
flex-flow: row wrap;
```



#### **设置flex项的大小**

```css
//article中felx项等大平分
article {
  flex: 1;
}

//第三个flex项占2个单位，其余1个单位
article:nth-of-type(3) {
  flex: 2;
}

//每个flex项先预留200px空间，再让第三项分配
article {
  flex: 1 200px;
}
article:nth-of-type(3) {
  flex: 2 200px;
}

```



#### **设置flex项水平和垂直对齐**

```css
div {
  display: flex;
  align-items: center; //沿中间轴对称
  justify-content: space-around;
}
```



#### flex项排序

- 所有 flex 项默认的 [`order`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/order) 值是 0。
- order 值大的 flex 项比 order 值小的在显示顺序中更靠后。
- 相同 order 值的 flex 项按源顺序显示。所以假如你有四个元素，其 order 值分别是 2，1，1 和 0，那么它们的显示顺序就分别是第四，第二，第三，和第一。
- 第三个元素显示在第二个后面是因为它们的 order 值一样，且第三个元素在源顺序中排在第二个后面。

```css
button:first-child {
  order: 1;
}

你也可以给 order 设置负值使它们比值为 0 的元素排得更前面。比如，你可以设置“Blush”按钮排在主轴的最前面：
button:last-child {
  order: -1;
}

```



### 网格布局：Grid布局

> 一个网格通常具有许多的**列（column）\**与\**行（row）**，以及行与行、列与列之间的间隙，这个间隙一般被称为**沟槽（gutter）**。

<img src="../../picture_typora/CSS/image-20230301150433397.png" alt="image-20230301150433397" style="zoom:80%;" />

**定义网格**

```css
//display设置为grid网格
.container {
  display: grid;
  grid-template-columns: 300px 2fr 1fr; //fr表示当前可用空间(总空间-300px)的1个比例单位
  grid-template-rows: 100px; //设置网格行宽
}
```

#### **设置网格间隙**

```css
//使用 grid-column-gap (en-US) 属性来定义列间隙；使用 grid-row-gap (en-US) 来定义行间隙；使用 grid-gap (en-US) 可以同时设定两者

.container {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr;
    grid-gap: 20px;
}

```

#### 重复构建轨道组 - repeat()函数

```css
.container{
	display:grid;
	grid-template-colums:repeat(3,1fr); //repeat(重复次数，设置宽度)
	grid-gap:20px;
}
```

#### 显示网格-隐式网格 - minmax()函数

```css
//隐式网格只有在显式网格容纳不下的时候才会放置在里面
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr); //设置显式网格
  grid-auto-rows: minmax(100px, auto); //设置隐式网格，minmax(最小宽度，根据内容自动调整大小)
  grid-gap: 20px;
}
```

#### 自动多列填充

```css
//auto-fill设定自动确定重复次数
.container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-auto-rows: minmax(100px, auto);
  grid-gap: 20px;
}
```

#### 基于线放置网格的位置

![image-20230301151342137](../../picture_typora/CSS/image-20230301151342137.png)

> 网格有许多分隔线，第一条线的起始点与文档书写模式相关。在英文中，第一条列分隔线（即网格边缘线）在网格的最左边而第一条行分隔线在网格的最上面。而对于阿拉伯语，第一条列分隔线在网格的最右边，因为阿拉伯文是从右往左书写的。

我们根据这些分隔线来放置元素，通过以下属性来指定从那条线开始到哪条线结束。

- [`grid-column-start` (en-US)](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-start)
- [`grid-column-end` (en-US)](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-end)
- [`grid-row-start` (en-US)](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row-start)
- [`grid-row-end` (en-US)](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row-end)

这些属性的值均为分隔线序号，你也可以用以下缩写形式来同时指定开始与结束的线。

- [`grid-column`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-column)
- [`grid-row`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-row)

注意开始与结束的线的序号要使用`/`符号分开。

**备注：** 你也可以用 `-1` 来定位到最后一条列分隔线或是行分隔线，并且可以用负数来指定倒数的某一条分隔线。但是这只能用于显式网格，对于[隐式网格](https://developer.mozilla.org/zh-CN/docs/Glossary/Grid)`-1`不一定能定位到最后一条分隔线。

```css
header {
  grid-column: 1 / 3; //设置网格项列宽
  grid-row: 1;  //设置网格项行宽
}

article {
  grid-column: 2;
  grid-row: 2/4;
}

aside {
  grid-column: 1;
  grid-row: 2;
}

footer {
  grid-column: 1 / 3;
  grid-row: 1/3;
}

```





#### 基于区域块放置网格的位置

> 先定义好区域块的位置，然后给块赋予名字，再利用名字决定网格项放置

`grid-template-areas`属性的使用规则如下：

- 你需要填满网格的每个格子
- 对于某个横跨多个格子的元素，重复写上那个元素`grid-area`属性定义的区域名字
- 所有名字只能出现在一个连续的区域，不能在不同的位置出现
- 一个连续的区域必须是一个矩形
- 使用`.`符号，让一个格子留空

```css
.container {
  display: grid;
  grid-template-areas:
    "header header"
    "sidebar content"
    "footer footer";
  grid-template-columns: 1fr 3fr;
  gap: 20px;
}

header {
  grid-area: header;
}

article {
  grid-area: content;
}

aside {
  grid-area: sidebar;
}

footer {
  grid-area: footer;
}

```





## 浮动(待补充)



## 定位（待补充



## 继承

**可被继承属性：**

- color
- font-size
- font-family
- list-style
- cursor

**不可被继承属性**：

- width
- margin
- padding
- border
- background

**控制继承**

1. inherit：开启继承
2. initial：应用初始属性值
3. revert：将应用于选定元素的属性值重置为浏览器的默认样式，而不是应用于该属性的默认值。
4. revert-layer：将应用于选定元素的属性值重置为在上一个层叠层中建立的值。
5. unset：将属性重置为自然值，也就是如果属性是自然继承那么就是 `inherit`，否则和 `initial` 一样





## 函数

### calc()函数

> 计算函数

```css
.outer {
  border: 5px solid black;
}

.box {
padding: 10px;
width: calc(90% - 30px); //允许在css中进行计算
background-color: rebeccapurple;
color: white;
}

```





### 图像

- 元素是**块级**元素，意味着它占据了页面的空间并且能够赋予外边距和其他改变间距的值。而图片是**内联**元素，不具备块级元素的一些功能。所以为了使图像有外边距，我们必须使用 `display: block` 给予其块级行为。

```css
img {
  display: block;
  margin: 0 auto;
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



## 引入CSS文件

### src和href的概念与区别

六、src的概念

source（缩写），指向外部资源的位置，指向的内容将会应用到文档中当前标签所在位置。

七、href和src的区别

7.1 请求资源类型不同

（1）href 指向网络资源所在位置，建立和当前元素（锚点）或当前文档（链接）之间的联系。

（2）在请求 src 资源时会将其指向的资源下载并应用到文档中，比如 JavaScript 脚本，img 图片；

7.2 作用结果不同

（1）href 用于在当前文档和引用资源之间确立联系；

（2）src 用于替换当前内容；

7.3 浏览器解析方式不同

（1）若在文档中添加 ，浏览器会识别该文档为 CSS 文件，就会并行下载资源并且不会停止对当前文档的处理。这也是为什么建议使用 link 方式加载 CSS，而不是使用 @import 方式。

（2）当浏览器解析到 ，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行完毕，图片和框架等也如此，类似于将所指向资源应用到当前内容。这也是为什么建议把 js 脚本放在底部而不是头部的原因。

八、link和@import的区别

两者都是外部引用 CSS 的方式，但是存在一定的区别：

（1）link是XHTML标签，除了能够加载CSS，还可以定义RSS等其他事务；而@import属于CSS范畴，只可以加载CSS。

（2）link引用CSS时，在页面载入时同时加载；@import需要页面完全载入以后再加载。

（3）link是XHTML标签，无兼容问题；@import则是在CSS2.1提出的，低版本的浏览器不支持。

（4）link支持使用Javascript控制DOM改变样式；而@import不支持。


```css
<link href="lib/bootstrap.css">
<a href="www.goole.com">
```

