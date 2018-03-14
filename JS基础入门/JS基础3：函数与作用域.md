# JavaScript的函数与作用域
----
函数是什么？
函数是指一个特定的代码块，可能包含多条语句，可以通过名字来供其他语句调用执行函数包含的代码语句。

## 函数声明的三种方式：<br>
1. 构造函数（不推荐）<br>
函数是对象的一种，我们可以通过其构造函数，使用new来创建一个函数对象<br>
`var sayHello = new Function("console.log('hello world!');");
2. 函数声明<br>
使用function关键字可以声明一个函数
```
//函数声明
function sayHello(){
    console.log('hello')
}
//函数调用
sayHello()
```
*声明可以不放到调用的前面*<br>

3. 函数表达式
```
var sayHello = function(){
    console.log('hello');
}
sayHello()
```
*声明必须放到调用前面*<br>

----

### 参数<br>

1. 单个参数：
```
function add(name){
    console.log('hello'+name)
}
add('world!')
```
2. 多个参数:
```
function abc(name,age,sex){
    console.log('姓名'+name);
    console.log('年龄'+age);
    console.log('性别'+sex)
}
abc('小明',16,'男性')
```
3. arguments<br>
在函数内部，你可以使用arguments对象获取到该函数的所有传入参数
```
function manAttributes(name,age,sex){
    console.log(name);
    console.log(age);
    console.log(sex);
    console.log(arguments);
}
```
arguments是一个伪数组，它的原型链直接指向的是object。<br>
### 重载
```
C语言的重载范例：
int sum(int num1 , int num2){
    return num1+ num2;
}
float sum(float num1, float num2){
    return num1 + num2;
}
sum(1,2);
sum(1.5 , 2.4);
```
在JavaScipt中没有重载的概念，如果这样写后面的函数会把前面的覆盖掉。<br>
但是在JS中可以模拟重载的效果：就是做if判断.例如下面这样：
```
function  abc(name,age,sex){
    if(name){console.log(name)}
    if(age){console.log(age)}
    if(sex){console.log(sex)}
}
abc('xiaoming')
abc('xiaoming',16)
abc('xiaoming',16,'man')
```
### 返回值
函数执行以后希望得到一个结果供别人使用，可以通过return来实现
```
 function sum(a ,b){
     a++;
     b++;
     return a+b;
 }
 var result = sum(2,3);
 console.log(result);
```
*1. 如果不写return结果一样会有返回值，不过结果undefined，<br>2.函数在执行的过程中，只要遇到return就会立即结束退出函数体。<br>3.不要混用console.log和return，console.log的在控制台输出你的结果，然后返回一个undefined* 
### 声明前置<br>
var 和 function的声明前置
在同一个作用域下，var声明的变量和function声明的函数会前置
```
console.log(a) //undefined
var a=3;
console.log(a) //3
sayHello();
function sayHello(){
    console.log('hello')
}
```
执行顺序：<br>
(1)var a / function sayHello(){} <br>
(2)a=3 , sayHello('hello')<br>
### 函数表达式
```
console.log(fn) //undefined
fn(); //报错
var fn=function(){}
```
函数表达式和var一个变量没有什么区别，是先有再用的。

### 参数重名
```
function fn(fn){
    console.log(fn);
    var fn=3;
    console.log(fn);
}
fn(10)
```
执行顺序：<br>
fn=10 ->console.log(10)->10<br>
fn=3 ->覆盖fn=10，执行console.log(3) ->3<br>
最终结果：// 10 3 
```
function fn(fn){
    //var fn=10 这是一个隐含的变量
    var fn
    
    fn=10
    console.log(fn)
    fn=3
    console.log(fn)
}
```
----

## 作用域<br>
在JS中只有函数有作用域，没有块作用域<br>
```
function fn(){
    var a=1;
    if(a>2){
        var b=3;
    }
    console.log(b);
}
fn()
console.log(a);
```
结果： <br>
fn() //undefined<br>
console.log(a) //"Reference Error : a is not defined"

### var 
1. 声明一个已经存在的变量
```
 function fn(){}
 var fn
 console.log(fn)

 var a=1
 var a
 var a
 console.log(a)
```
var 重复声明一个已经存在的变量，原值不变。<br>
这里你要注意的是：声明的是存在的变量，不是前面的参数名覆盖。<br>
只要我们的调用是在声明之后的我们都可以说是正常的。

### 函数的递归
* 自己调用自己

求n！阶乘
```
    function factorial(n){
        if(n===1)
            return n;
        else (n!==1)
            return n*factorial(n-1)
    }
    factorial(n)
```
求1+2+...+n的值<br>
```
 function sum(n){
     if(n===1){
         return 1;
     }
     return n+sum(n-1)
 }
 sum(10)
```
### 立即执行函数表达式
正常写法：
```声明： function abc(){},调用：abc()```<br>
这样看来，我们的调用是多了abc，于是我就想了一种简便的方法：<br>
声明+调用：`function abc(){}()`
后来查阅资料得知：声明的后面多了一对括号，会被JS默认为奇怪的符号，不会被识别。
所以正确的写法是：
```
(function (){
    console.log(balabalabala)
    })()
```
声明要实现加一对括号，JS会承认这是一个结果，然后执行后面的调用。<br>
而且这样写的好处是隔离作用域，保护局部变量不被污染<br>
当然，还有其他写法：
1. 逗号操作表达式<br>
` , function fn3(){};`
2. 数组操作表达式<br>
`[function fn2(){}]`
3. 感叹号操作表达式<br>
`!function(){ console.log(111)}()`<br>
### 练习题：
```
fn();
var i=10;
var fn=20;
console.log(i);

function fn(){
    console.log(i);
    var i=99;
    fn2();

    console.log(i);
    function fn2(){
        i=100;
    }
}
```
