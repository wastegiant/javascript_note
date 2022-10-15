# JavaScript

> JavaScript是一种交互式编程语言。

- ECMA-62(es)是JavaScript的语言规范标准

|                    | JavaScript          |                       |
| ------------------ | ------------------- | --------------------- |
| （核心）ECMAScript | （文档对象模型）DOM | （浏览器对象模型）BOM |





![image-20220929185222266](D:\Program\picture_typora\image-20220929185222266.png)





## 基本语法

- ECMAScript中一切都区分大小写
- 标识符 - 驼峰式写法，第一个单词首字母小写，后面首字母大写 myCar
- 严格模式  - 在前面加上 "use strict" 开启



### 变量

- **规则**

> 1.变量名称由数字、字母、下划线、$组成
>
> 2.严格区分大小写
>
> 3.不能由数字开头
>
> 4.不能是保留字或者关键字
>
> 5.不要出现空格

#### var关键字

```JavaScript
var mess="hi"; //赋值mess为字符hi，但并未定义其是字符变量
mess=100; //合法

var mess="hi",
    found= false,
    num= 30; //采用逗号分隔定义多个变量
```

- var声明变量作用域在局部函数内，离开局部函数自动销毁
- 在函数内定义，忽略var 直接 mess="hi"，此时mess成为全局变量
- var可多次重复声明，且可进行提升，定义要求位置不严格



#### let声明

- 与var最主要的区别在于作用域不同，let采用的是块作用域，因此适用于for( )循环

```javascript
for(var i=0;i<5;i++){}
console.log(i);  //i=5，for循环内部i定义溢出

for(let i=0;i<5;i++){
    test(a);
    let a;  //错误，let不能自提升，var可以
}
console.log(i);  //i未定义，只在for代码块内有定义
```



#### const声明

- 行为与let类似，但是声明变量时需初始化，且此时改变量为常量，后续对其引用不允许再修改
- 作用域为块作用域
- 不能用于定义迭代变量，因为其会变化



### 数据类型

#### typeof操作符

- 用来返回判断变量类型

  ```javascript
  let mess="hi"
  console.log(typeof(mess));  //string
  console.log(typeof 95);  //number
  console.log(typeof (mess+100)) //number
  ```
  
  

#### undefined

- 所有声明未初始化的变量值都默认为undefined
- 变量声明时最好直接初始化，便于后续判断该变量是否声明



#### boolean

```javascript
let found=true; //TRUE，FALSE是标识符
let lost=false;

//布尔值转换函数
Boolean();
```

#### number

- 八进制 let num=070 //代表56
- 浮点数 1.2，.2 非浮点数1.0，1.

- 科学计数法 2.35e4 = 23500
- 浮点数精度不确定 0.1+0.2！=0.3
- NaN 表示“不是数值” "not a number"

```javascript

```



#### string



#### object

- 对象 初始化可赋值为NULL



#### function



#### symbol



### 数据类型转换

#### 数据转为数值

- Number(变量)
- parseInt(变量)
- parseFloat(变量)

```javascript
//字符串转换函数
Number("123") ->123

//将字符串转换为数值
parseInt("123abc") ->123

//将字符串转换为带浮点数
parseFloat("123.45abc") ->123.45
```



#### 数据转为字符串

- 变量.toString( )
- String(变量)
- 使用加法运算

```javascript
String(变量)
var a=123
var b=String(a)
console.log(a,b) ->123,'123'

变量.toString
var a=123
var b=a.toString()

加法运算,使用+拼接空字符即可将变量转化为字符串
var a=100
var b=a+""
console.log(a,b) -> 100,"100"
```



#### 数据转换为布尔Boolean

```JavaScript
Boolean(变量)
//在js中，只有''、0、null、undefined、NaN转换为false
//其他都转换为true（特殊：" "空格字符也算true）
```



### 数组

> 数组的本质是一个对象

#### 创建数组

```JavaScript
arr.unshift(a); //[a,1,2,3] 将a添加到数组头部

//字面量声明
var ageArr=[12,14,16]
var nameArr=["zhang","hong","lv"]
var student=[obj1,obj2]


//Array创建
var arr1=new Array(12,14,15,16)
var arr2=new Array(10)

```



#### 数组基本操作

```javascript
var arr1=[1,2,3,4]
arr1.length=3 //修改数组长度为3

//push方法 - 在数组最后追加元素，返回值为数组长度
var arr1=[1,2,3]
arr.push(4)
console.log(arr) //1,2,3,4

//pop方法 - 删除数组最后的元素，返回值为删除的元素
var res=arr.pop()
console.log(res) //4

//unshift方法 - 在前面追加元素，返回值为数组长度
var res1=arr.unshift("next")
console.log(arr) //1,2,3"next"

//shift方法 - 删除最前面的元素，返回值为删除的元素
var res2=arr.shift()

//splice(m,n)方法 - 从第m个位置开始删除n个元素,返回值是删除的元素
var res3=splice(2,1)

//splice（m,n,k,x) - 从第m个位置开始删除n个元素，同时加入k元素跟x元素
var res4=splice(2,1,"hong","kai")

//reverse()方法 - 将数组倒序排序
arr.reverse()

//sort()方法 - 内置排序算法
var arr4=[11,21,56,7,3]
1.直接调用 按照字符大小排序
arr4.sort()
console.log(arr4) //11,21,3,56,7

2.通过回调函数调用 return正序从小到大排序
arr4.sort(function(a,b){
    return a-b
})
console.log(arr4) //3,7,11,21,56

3.通过回调函数调用，return逆序从大到小排序
arr.sort(function(a,b){
    return b-a
})
console.log(arr4) //56,21,11,7,3


//concat()方法-拼接数组
var arr1=[1,2]
var arr2=[3,4]

var arr3=arr1.concat(arr2)

console.log(arr3) //1,2,3,4

//join()方法 - 将数组转化为字符串
arr.join("|") //将数组元素转换成字符串并用"|"连接


//slice()方法 - 截取数组元素
slice(a,b)方法 - 截取数组元素从a->b-1位置的元素
slice(a) - 从a->数组尾部位置的元素

//indexOf方法 - 查找数组中元素位置
var res =  arr.indexOf("a",2) //从第2个位置开始查找是否有a元素，有则返回其位置下标，没有返回-1


//foreach() - 遍历方法
var arr=["aaa","bbb","ccc","ddd"]
arr.forEach(function(item,index){
    console.log(item,index)
})

//map() - 映射方法，将数组中的每一项映射成return结果
var arr=["hong","kai","zhe"]
var arr1=arr.map(function(item){
    return "<li>"+item+"</li>"
})
console.log(arr1) //["<li>hong</li>","<li>kai</li>","<li>zhe</li>"]
doucument.write(arr1.join("")) //arr1直接元素采用空字符连接


//filter() 过滤方法，将return条件中成立的元素返回出来
var arr=[
    {
    name:"a",
    price:100
	},
    {
     name:"b",
     price:200
     },
	{
     name:"c",
     price:300
    }]

var arr2=arr.filter(function(item){
    console.log(item) //item将arr中元素当成对象并console输出
    return item.price>200
})
console.log(arr2) //{name:"c" price:300}


//every()方法 - 判断数组中每一项元素是否满足条件
var arr2=arr.every(function(item){
    return item>=90 //每一项都满足返回true，不满足返回false
})
console.log(arr2)

//some()方法 - 判断数组中是否有一项元素满足条件
var arr2=arr.some(function(item){
    return item>=90
})
console.log(arr2)


//find()方法 - 找到数组中满足的第一项元素
var arr2=arr.find(function(item){
    return item.grade===100
})

//reduce()方法 - 叠加数组元素
var arr=[1,2,3,4,5]
var arr2=arr.reduce(function(prev,item){
  return prev+item  //叠加，累加前一次reduce值（prev）与下一项元素值（item）
  return prev*item  //叠加，累乘前一次reduce值（prev）与下一项元素值（item）
    //以此类推
})
```



#### 数组去重

1. for循环+indexOf( )方法,开辟一个额外数组进行添加

2. 采用obj对象，数组元素当成i，在对象中添加obj[arr[i]]，重复的位置会覆盖

3. new Set 结构

   1. ```javascript
      var arr=[1,2,2,3,1,4,5]
      var set1=new Set(arr) //set1将arr转换为无重复的set结构
      consloe.log(set1) //1,2,3，4,5
      
      var arr1=Array.form(set1) //将set1结构转换为数组结构
      
      ```

      

### 字符串

>  字符串是一种特殊数组结构

- 字符串通过下标索引只读，不可修改



#### 常用方法

```javascript
//charAt() - 索引方法，返回对应的字符
var str="hong"
var str1=str.charAt(2)
console.log(str1) //n

//charCodeAt() - 索引对应字符编码，返回对应字符编码
var str1=str.charCodeAt(0)
console.log(str1) //输出对应ASCII码值

//toUpperCase() - 将所有小写字符转换成大写
//toLowerCase() - 将所有大写字符转换成小写

//substr(a,b) - 从a开始索引，截取b个长度字符
//substring(a,b) - 从a开始索引，到b位置结束不包括b
//slice(a,b) - 从a开始索引，b位置结束，b可以为负数

//replace(a,b) - 替换方法，将a字符替换成b字符
var str="abcd"
var str1=str.replace("a","*")
console.log(str1) //*

//split() - 定义分割字符，转换为数组


//indexOf() - 查找方法，查找字符在字符串内是否存在，存在返回索引位置，不存在返回-1
//lastIndexOf()  - 从后面进行字符查找，同indexOf

//trim() - 去掉首尾空格
//trimStart() trimLeft() - 去掉首空格
//trimEnd() trimRight() - 去掉尾空格


```



#### json格式字符串

- 后端与前端之间数据传递采用 json格式

- 将json格式通过JSON.oarse( )转换成obj对象格式
- 将obj格式通过JSON.stringify( )转换成json格式

```JavaScript
var str='{"name":"hong","age"=20}' //jason格式
var obj={name:"hong",age:20} //obj对象格式

```



###  数字Number

#### 常用操作

```javascript
//toFixed()方法 - 保留小数位数，遵循四舍五入，不足补0操作；返回值是字符串
var price=123.45678
console.log(price.toFixed(2)) //"123.46"

```

#### Math对象

```javascript
//random() - 返回0-1之间的随机值
Math.random()
var res=Math.floor(Math.random()*10) //0-10,不包含10
var res=Math.floor(Math.random()*(10+1)) //0-10,包含10
var res=Math.floor(Math.random()*10)+10 //10-20,不包含20
var res Math.floor(Math.random()*(10+1)) //10-20，包含20

//封装函数 - 实现随机min-max之间的数，不包含max
function getRandom(min,max){
    if(min>max){console.error("参数错误")	return}
    return Math.floor(Math.random()*(max-min)+min)
}


//round(a)- 四舍五入取整
Math.round()

//ceil向上取整 floor向下取整
Math.ceil()
Math.floor()

//abs取绝对值
Math.abs(-10.2)

//sqrt 开根号
Math.sqrt(25) //5

//pow(底数，指数) 指数值计算
Math.pow(3,3) //27

//max(a,b,c,d,e) 取参数最大值
Math.max(10,20,30) //30

//min(a,b,c,d,e) 取参数最小值
Math.min(10,20,30) //10

Math.PI//3.1415926
```





### 运算符

- **数学运算符**
  - +、- 、*、/、%

- **赋值运算符**
  - =、+=、-=、*= 、/= 、%=

- **比较运算符**

  ```javascript
  >=、<=、==、===、！= 、！== 、
  //== 比较符号两边的值是否相等，不管数据类型
  例如 1=='1' 两者相等
  
  //=== 比较符号两边的值和数据类型是否都相等
  例如 1==='1' 两者不相等
  为了防止传入字符串不能进行比较，可以先进行parseInt(x)进行转换
  
  ```



<img src="D:\Program\picture_typora\image-20220815171350367.png" style:zoom="80%">



![image-20221001130927869](D:\Program\picture_typora\image-20221001130927869.png)



### 函数

> 函数具有自提升，可以先使用后声明



#### 匿名函数

```javascript
//变量存储函数的值，该变量可以直接调用，相当于一个匿名函数
const func =function(a,b){
    return a+b;
}
func(1,2);

```

#### 箭头函数

```java
const f = (a,b) => {
	return a+b;
}
f(1,2);

//或者
const f = (a,b)=> a+b;
const f = a => a+2;
const f = () => 5;
```



#### 预解析

- 在所有代码执行之前，先对代码进行解释

- 将变量声明提到开头位置 
- 赋值函数不可以预解析提前（先使用后声明），声明式函数可以预解析提前

- **函数名与变量名冲突会报错，预解析是进行声明提升而不是执行提升，执行顺序还是按照代码出现顺序。**





#### 赋值式函数

```javascript
myFunc() //报错
var myFunc = function(){
	console.log("hello")
}
myFunc()
```



#### 声明式函数

```javascript
myFunc() //预解析，可正常执行
function myFunc(){
	console.log("hello")
}
```



### 对象

#### 创建对象

```javascript
<script>
    //1.直接创建对象
    var obj0={}
	var obj={
    name:"ky"  //key值
    "set+":"1234"
    age:100
	}
    
    //2.通过内置函数构造
    var obj2=new Object()
    obj2.name="ky"
	obj.age=20
<script>
```



#### 增删改查-对象

```html
<script>
    //增加对象属性
    var obj={}
    obj.name="ky"
    obj.age=20
    obj.location=shenzhen
    obj["name"]="change"
    
    //查找
    doucument.write("姓名是"+obj.name)
    
    //修改
    obj.age=200
    obj["name"]="change"
    
    //删除
    delete obj.name
    delete obj["name"]
    
</script>
```



#### 对象属性遍历

```javascript
for(var i in obj){
    //获取key
    console.log(i)
    //获取value
    console.log(obj[i])
    
    //循环输出到也页面
    document.write(i+":"+obj[i])
    document.write("<br>)
}
```





### 类型

- JavaScript内不区分整数型和浮点数型，默认使用浮点数形式表示

#### 数据类型

| 变量（let/var) | 解释                                                         | 示例 |
| -------------- | ------------------------------------------------------------ | ---- |
| String         | 字符串（一串文本）：字符串的值必须用引号（单双均可，必须成对）扩起来。 |      |
| Number         | 数字：无需引号。 包括科学计数法、各种进制数（0x十六进制，0八进制，0b二进制、浮点数 |      |
| Boolean        | 布尔值（真 / 假）： `true`/`false` 是 JS 里的特殊关键字，无需引号。 |      |
| Array          | 数组：用于在单一引用中存储多个值的结构。                     |      |
| Object         | 对象：JavaScript 里一切皆对象，一切皆可储存在变量里          |      |



### 输入输出

#### 输出

```javascript
document.write() //将内容写到HTML文档
window.alert() //弹出警告框
innerHTML //写入到HTML元素
console.log() //写入到浏览器的控制台
```



### 存储数据位置

- 复杂数据类型存储在堆区，其地址存储在栈区变量中
- 基本数据类型存储在栈区内存

<img src="D:\Program\picture_typora\image-20221003172824124.png" style:zoom="80%">



##### 拷贝

```JavaScript
var obj1={
    name="yiping"
    age=20
    location:sz
}
var obj2={}

//浅拷贝
obj2=obj1 //将obj1的地址赋值给obj2，此时两个对象指向同一个堆区地址

//深拷贝
for(var i in obj1){
    obj2[i]=obj[i]
}
obj2["name"]="hong" //此时修改obj2不会影响obj1中的值
```





### 注释

```javascript
/*注释*/
或者
//注释-注释
```



### <\noscript>标签

- 针对不支持JavaScript和需要关闭脚本功能的降级处理

  ```javascript
  <noscript>
  	<p>JavaScript不被支持时显示</p>
  </noscript>
  ```

  

## 属性

<script>标签拥有属性
- async：（异步执行）表示应该立即开始下载脚本，但不能阻止其他页面动作，即不用等js文件下载完再开始渲染页面
- charset：使用src属性指定的代码字符集
- defer：表示脚本可以延迟到文档完全被解析和显示之后再执行
- integrity：
- src：表示包含要执行的代码的外部文件
- type：代替language，表示代码中脚本语言的内容类型，代码块的类型决定了解释方法和语法。如:text/javascript：application/javascript





##   **添加JavaScript**

- 内部添加 通过<script> 标签</script>
- 外部添加 通过<script src="script.js"></script>
  - script.js文件本身只需要包含放在<script>代码块中间的JavaScript代码，此时页面会进行阻塞（包含下载文件的时间），从上到下顺序解释代码。
  - 且此时浏览器只执行src指向文件，不会再执行其余JavaScript代码。
  - src指向URL资源可以不遵循同源策略，即执行外部域的.js文件
- 内联JavaScript <button onclick="ceaatParagraph()"></button> (在一个函数后写入方法，然后引用，而不是统一写在外部文件或者直接在函数内定义方法)

> 注意：在<script>标签中，不能再出现形如"</script>"的内容，必须使用转义字符<\/script>代替

```java
<a href = "javascript:alert('弹出框');" >点击</a>
```



- 对于不推迟执行的脚本，浏览器必须解释完位于<script>元素中的代码，才能继续渲染，因此一般将其放到页面末尾，<body>标签最后方



## 文档模式

通过DOCTYPE切换文档模式，可以声明不同的css语法标准，决定网页以什么方式渲染

- 混杂（怪异）模式
  - 忽略文档开头的<! DOCTYPE>声明作为开关
- 标准模式（浏览器使用W3C标准解析渲染页面）



## 时间对象

- 标准时间：1970年1月1日 0:0:0



```javascript
//创建date时间对象
var date=new Date()

date对象常用方法
//getTime() - 时间戳，返回距离标准时间起至当前UTC时间的总毫秒数（不同时区不同）

//getFullYear()//获取当前年份

//getMonth() - 获取当前月份。月份是从0-11代表，例如：数字3代表4月

//getDate() - 获取当前是几号

//getDay() - 获取当前是星期几，周日0

//getHours() - 获取小时

//getMinutes() - 获取分钟

//getSeconds() - 获取秒

//getMilliseconds() - 获取毫秒


设置时间
//setMonth() setSeconds()
```

#### 倒计时

```javascript
setTimeout(function(){
          operate;
           },2000) //延时2000ms

setInterval(dunction(){
            
            },1000) //注册间隔定时器,1000ms执行一次

clearTimeout(time1)//清除延时定时器
clearInterval(time2)//清除间隔定时器

//样例
var targetDate = new Date("2022 / 11 / 11")

        function differTime(targetTime, currentTime) {
            var time = Math.ceil((targetTime - currentTime) / 1000) //将毫秒变成秒
            console.log(time)
            var day = parseInt(time / (60 * 60 * 24))
            var hour = parseInt(time % (60 * 60 * 24) / (60 * 60))
            var min = parseInt((time % (60 * 60) / 60)) /*先取余分钟后剩下多少秒，再除以一分钟60秒*/
            var second = parseInt(time % 60)

            var obj = {
                Day: day,
                Hour: hour,
                Min: min,
                Second: second
            }

            return obj
        }

        setInterval(function () {
            var currentDate = new Date()
            var sub = differTime(targetDate, currentDate)
            // document.write(`距离双十一还有${sub.Day}天${sub.Hour}小时${sub.Min}分钟${sub.Second}秒`)
            // document.write("<br>")

            box.innerHTML = `距离双十一还有${sub.Day}天${sub.Hour}小时${sub.Min}分钟${sub.Second}秒`

        }, 1000)

```



## 异步与同步

- 异步事件必须要等到同步事件处理完成后才能执行





## 事件

> 事件为网页添加真是的交互能力。可以捕捉浏览器操作并运行代码做为响应。





## BOM

> 浏览器对象模型（Browser Object Model)

- BOM的核心就是window对象，window对象内置浏览器操作

### 基本操作

#### 1.获取浏览器窗口大小

```javascript
window.innerHeight //高度

window.innerWidth //宽度
```

#### 2.浏览器弹出层

```html
<button id="btn">click</button>
<script>
    //警告框
	btn.omclick=function(){
        alter("弹出信息")
    }
    
    //询问框
    btn.onclick=function(){
        var res = confirm("请选择是或者否") //返回值为布尔类型
    }
    
    
   //输入框
    btn.onclick=function(){
        var res=prompt("请输入用户名") //返回值为字符串
    }
</script>

```

#### 3.浏览器地址信息

```html
<button id="btn">
    下一个页面
</button>
<button id="btn1">
    刷新
</button>
<script>
	btn.onclick=function(){ //点击button按钮后执行回调函数操作
        location.href="http://www.baidu.com" //地址栏变为改值
    }
    btn1.onclick=function(){
        location.reload() //刷新页面
    }
</script>

```

#### 4.浏览器常用事件

```javascript
//最后执行的事件
window.onload=function(){
	console.log("加载完成")
}

//窗口大小改变后执行
window.onresize=function(){
    console.log("resize")
}

//滚动事件，窗口滚动时执行
window.onscroll=function(){
    
}

//获取纵向滚动距离
window.onscroll=function(){
    console.log(document.documentElement.scrollTop||document.body.scrollTop) //滚动时-打印滚动页面距离,浏览器兼容html5以上采用documentElent,不兼容采用body
}

//获取横向滚动距离
window.onscroll=function(){
    console.log(document.documentElement.scrollLeft||document.body.scrollLeft) //滚动时-打印滚动页面距离,浏览器兼容html5以上采用documentElent,不兼容采用body
}

//页面跳转到指定位置
window.scrollTo({
    left:0,
    top:0
})

//浏览器打开新的标签页
window.open("www.baidu.com") //在新的页面中打开对应页面
//浏览器关闭当前页面
window.close()


```

#### 5.浏览器的历史记录

window中有一个对象叫history

```html
需要在有历史记录的情况下才可以执行前进与后退操作
<!--回退到上一页面-->
windows.history.back()
<body id="btn">
    回退
</body>
<script>
	btn.onclick()=function(){
        history.back()
    }
</script>

<!--前进到下一页面-->
windows.history.forward()

<!--跳转历史记录中的n个页面 -1代表回退1个，2代表前进2个-->
windows.history.go(n)

<!--存取值到浏览器，只能存字符串-->
locationStorage.setItem(key,value) //存
locationStorage.getItem(key) //取
locationStorage.removeItem(key) //删除一个值
locationStorage.clear() //删除所有浏览器中的值


<!--临时存储与永久存储-->
seesionStorage对象- 临时存储，方法与locationStorage一样，会话关闭则丢失
locationStorage对象 - 永久存储
```



#### 案例 - 记住用户名

```html
<div>
        用户名：
        <input id="username" type="text">

    </div>
    <div>
        密码：
        <input id="password" type="password">

    </div>
    <button id="login">登陆</button>
    <script>
        //获取用户名与密码存储到浏览器
        var uservalue = localStorage.getItem("username")
        var passvaule = localStorage.getItem("password")
		
        //设置用户名和密码框内值
        username.value = uservalue
        password.value = passvaule
		
        //点击登陆后取值
        login.onclick = function () {
            localStorage.setItem("username", username.value)
            localStorage.setItem("password", password.value)

            console.log(username.value, password.value)
        }

    </script>
```



## DOM

> 文档对象模型（Document Object Model）

- DOM的核心就是document对象
- 页面中的标签，我们通过js获取到以后，就把这个对象叫做DOM对象

### 基本操作

#### 1.获取标签元素

```javascript
//非常规 - html\head\body
document.documentElement
document.head
document.body

//常规标签
document.getElementById() //通过id获取
var items=document.getElementsByClassName()  //通过class获取
items[i-1] //class里第i个标签元素
Array.from(items) //转换成数组


document.getElementsByTagName("li")  //通过标签名获取

document.getElementsByName("name")  //通过给标签name属性获取

document.querySelector()  //返回遇到的第一个对象

document.querySelectorAll()  //返回所有查询的
```

#### 2.操作元素属性

```html
<div id="box" hong="hello">
    hello
</div>
<input type="text" value="hello" id="username">
<script>
	//元素自带属性||自定义属性（命名为data-xxx）
    //操作原生属性
    box.innerHTML="box内显示值"
    username.type="password" //通过id获取对象，从而改变对象的内部属性值
    
    //操作自定义属性
    box.setAttribute("hong","changeNum")
    box.getAttribute("hong")
    box.removeAttribute("hong")
    
    //html5后规定 自定义属性命名为 "data-xxx" 形式
    操作形式如下
    box.dataset //获取
    box.dataset.new="hello2" //设置new自定义属性为hello2
	delete box.dataset.new  //删除自定义属性new
    
</script>
```

#### 3.密码可视化

```javascript
var passInput=document.getElementById("password")
var eyeBtn=document.querSeletor("#eyebtn")

eyeBtn.onclick=dunction(){
    if(passInput.type==="password"){ //获取到password对象,如果其类型type为密码则改变为text可见
        passInput.type="text"
    }else{
        passInput.type="password"
    }
}
```

#### 4.全选框

```html
<body>
    <input type="checkbox" id="all">全选/全不选
    <div>
        <ul class="item">
            <li><input type="checkbox">商品1</li>
            <li><input type="checkbox">商品2</li>
            <li><input type="checkbox">商品3</li>
        </ul>
    </div>
</body>
<script>
    var oAll = document.querySelector("#all")
    var oitems = document.querySelectorAll(".item input")
    //console.log(oitems)
    oAll.onclick = function () {
        console.log(oAll.checked)
        for (var i = 0; i < oitems.length; i++) {
            oitems[i].checked = oAll.checked
        }

    }

    for (var i = 0; i < oitems.length; i++) {
        oitems[i].onclick = function () {
            var count = 0
            for (let j = 0; j < oitems.length; j++) { //for参数写错会死循环
                if (oitems[j].checked) count++
            }
            if (count === oitems.length) {
                oAll.checked = true
            } else {
                oAll.checked = false
            }
        }
    }
</script>
```

#### 5.操作元素文本内容

```javascript
box.innerHTML="box_content"  //能够完整获得html内容并解析

box.innerText="<h1>box_content" //只获取文本 不解析更安全

```

#### 6.渲染页面

```
P82
```







## Es6标准

- 字符串可采用 `` 符号,内部可以采用${ }进行特殊解析

```javascript
var name="hong"
var str=`my name is ${name} ${10+20}`
document.write(str) //my name is hong 30
```

