### JS基础以及一些小的案例实现
---

1. 数据类型：
number,string,boolean,object,null,undefined,symbol<br>
* 检测数据类型的方法：typeof , instanceof ,Object.prototype.toString<br>
typeof的返回值：number,string,boolean,undefined,object,function(一种变量只存放一种数据类型)<br>
```
    typeof 123  //number
    typeof true //boolean
    typeof 'hello'  //string
    typeof f(){}  //function
    typeof {}   //object
    typeof null //object
    typeof undefined //undefined
    typeof /ss/ //object
    typeof []   //object
```
判断是否是函数：
```
    function isFunction(val) {
        return typeof val ==='function'
    }      //  true表明是函数 false表明不是函数
```
上述实例中，我们都知道{} ， null ，/ss/ ,[]的返回值都是对象，但是我们怎么区分数组和对象呢？<br>
我们可以记住检测数据类型的第二种方法：instanceof
例如：
```
    var o=[];
    var a=[];

    o instanceof Array //false
    a instanceof Array //true
```
### null 和 undefined 区别<br>
首先：null === undefined
对于null和undefined，可以大致这样理解：
null 表示空值，即该处的值现在为空。典型的用法是：
* 作为函数的参数，表示该函数的参数是一个没有任何内容的对象
* 作为对象原型链的终点
undefined表示不存在的值，就是此处目前不存在任何值，用法：
* 变量被声明了，但是没有赋值，就等于undefined
* 调用函数时，应该提供的参数没有提供，该参数等于undefined
* 对象没有赋值属性，该属性值为undefined
* 函数没有返回值时，默认返回为undefined
### Boolean
布尔值代表'真'和'假'两个状态，'真'用关键字true表示，'false'用关键字false表示。布尔值只有两个值：true / false<br>
下面运算符会返回布尔值：
* 两元逻辑运算符：&&（And）, ||(Or)
* 前置逻辑运算符：!(Not)
* 相等运算符： === , !== , == , !=
* 比较运算符：> , >= ,< ,<=
### 浮点数
数值转换8,10,16进制<br>
要注意两个：<br>
`0.1+0.2=0.3000000000000004`<br>
`1-0.9=0.09999999999998`<br>
两个特殊值：Infinity(无穷大) / NaN<br>
5个false值：NaN，'',undefined,0,null<br>

JavaScript中对象又分为：简单对象和复杂对象<br>
简单对象包括：<br>
复杂对象包括：object <br>
对象（object）有细分为：独义的对象（object），数组（array)，函数（function），正则表达式（regexp）<br>
### 对象object
对象，就是一种无序的数据集合，由若干个‘键值对’（key-value）构成，key我们称对象的属性，value可以是有任何JavaScript类型，甚至可以是对象：<br>
    `var obj ={ name:'xiaoming' , age:2};`<br>
object读取的两种方式：<br>
`obj.name / obj['name']`

---

2. 变量类型的转换<br>
字符串转换为数字：parseInt(),parseFloat()<br>
parseInt()和parseFloat()使用区别：<br>
（1）忽略字符串前面的空白字符，找到第一个非空白字符<br>
（2）如果第一个字符不是“-”或者数字则返回为NaN<br>
（3）如果是继续解析，直到非数值模式为止<br>
（4）0开头当做八进制，0x开头当做16进制 <br>
example:
```
    parseInt('blue'); //NaN
    parseFloat('-23Abs'); //-23
    parseInt('0xf1'); //241
    parseInt('101',2); //5 将101转换为2进制的数字
```
检测NaN的方法：isNaN()<br>
NaN!==NaN  NaN+number=NaN<br>
隐式类型转换<br>
==先把两边东西转为一样的类型，然后在比较<br>
=== 不转换，直接比较<br>
-直接就是数字减法转换<br>
’+‘： 1. 字符串相加 2. 数字相加<br>
’-，*，/‘只有数学含义<br>
注释：<br>
单行注释： //<br>
多行注释： /* */<br>

--- 

变量作用域：<br>
局部变量：定义在一个函数里，只能在这个函数里使用<br>
全局变量：不定义在函数里面，在任何地方可以使用<br>
闭包：子函数可以使用父函数的局部变量<br>
```
function aaa(){
	var a=1;
	function bbb(){
		alert(a);
	}
}
```
---
### 运算符
JS中的运算符<br>
+-*/%：加，减，乘，除，取模<br>
取模的实例：隔行换色，秒转时间<br>
赋值：=，+=，-=<br>
逻辑： &&与 ||或 ！非<br>
运算符优先级：括号<br>
有些操作符对不同的数据类型有不同的含义：<br>
例如：+<br>
* 在两个操作数都是数字的时候，会做加法运算
* 在两个参数都是字符串或者有一个参数是字符串的情况下会把另外一个参数转换为字符串做字符串拼接
* 在参数有对象的情况下会调用valueOf()或者toString()方法
* 在只有一个字符串参数的时候会尝试将其转换为数字
* 在只有一个数字参数的时候返回其正数值<br>
在计算的过程中算术运算符优先级要注意：<br>
例如：`var a=1; var b=2; consloe.log(a+++b)`<br>
### 位于运算符：
* 或运算符：符号 | 表示两个二进制中有一个为1，则结果1，否则为0<br>
* 与运算符：符号& 表示两个二进制中有两个为1结果为1，否则为0<br>
* 否运算符：符号~，表示将一个二进制为变成相反值
* 异或运算：符号为^ 表示两个二进制中有且仅有一个为1时，结果为1，否则为0；<br>
* 左移运算符：<<
* 右移运算符：>>
* 带符号位的右移运算符：符号为>>>
```
1 & 2 :
0000000000000001
0000000000000010       //0
1 | 2 :
0000000000000001
0000000000000010       //3
```
---

程序流程控制：<br>
判断：if switch<br>
循环：while for do...while<br>
跳出：break，continue<br>
真/假: true,非零数字,非空字符串,非空对象<br>
       NaN，'',undefined,0,{}<br>
switch(变量/值){<br>
	case 值1：... break;<br>
	case 值2：... break;<br>
	case 值3：... break;<br>
	default: ...<br>
}<br>

---

### 变量提升
JavaScript引擎工作方式是：先解析代码，然后获取所有声明的变量，在一行行的运行。<br>
这样造成的结果是：所有的变量的声明语句，都是被提升到代码的头部，这就叫做变量提升。<br>
例如：var a=3;<br>
var b="ok";<br>
在js引擎中是这样操作的：<br>
先找到一个a变量，初始化的值为undefined，然后在找到一个b的变量初始化值为undefined<br>
接着第二步，赋值。给a变量赋值为3，b变量赋值为字符串ok<br>

---
### 函数传参（函数传递参数）
```
fn(100)
function fn(a){ alert(b)  }    //a=100

fn(100,'px')
function fn(a ,b){alert( a+b) }     // 100px
```
函数传递参数： 参数=JS的数据类型：number，string，boolean，undfined，null，symbol，object
当然你也可以这样做：
```
fn( function(){ alert(1) } )
function fn(abc){
  abc();          //1
 }
```
例子：
```
function fn2(lol){
  lol(100)
 }
fn2( function(a){ alert( a ) } )
```
1.传参，lol指的是function(a){alert( a )}
2. 代入，执行lol这个函数代入为100，执行得到结果为100
注意：执行有名字的函数的时候不需要带括号
例如：
```
function fn4(){ alert(4) }
function fn3( fn ){
  fn();
}
fn3( fn4 )   //4
```
当然，参数的传递也可以是对象：
例如，我们平时在控制台输出可以使用`console.log(1)`
```
 function fn(w,d){
            w.onload=function(){
                d.body.innerHTML=123;
            }
        }
        fn(window,document);
```
函数传参重用代码：
1、尽量保证HTML代码结构一致，可以通过父极选取子元素
2、把核心的主程序实现，用函数封装起来
3、把每组里不同的值找出来，通过传参实现

---
### JS作用域
什么是作用域？
域：空间，范围，区域...
作用：读、写

for循环二维数组：
---
```
---
for (var i=0; i<arr.length;i++){
    for(var j=0; j<arr[i].length;j++){
       console.log(arr[i][j])
 }
}
```
JS中所有用到class的地方都必须换成className

---

### this 
指的是调用当前方法（函数）的那个对象。
### 自定义属性
```
HTML：
<input type="btton" value="按钮">
JS：
var oBtn = document.getElementsByTagName('input');
oBtn[0].abc="123";
console.log(oBtn[0].abc); // 123
```
JS可以为任何HTML元素添加任意自定义属性。
在JS中背景，color，相对路径都不能作为判断条件。
获取自身递增数字及匹配数组内容：
地址：http://js.jirengu.com/vudenelaxu/2/edit

---
