# jQuery的基础语法
## jQuery好处
* 简化JS复杂操作
* 不再需要关心兼容性(jQuery2以后不支持IE6)
* 提供大量使用的方法
## jQuery设计思想：
* 选择网页元素
  * 模拟CSS选择元素
  * 独有的表达式选择
  * 多种筛选方法
* jQuery写法
  * 方法函数化
  * 链式操作
  * 取值赋值合体
* jQuery与JavaScript的关系
  * 可以实现共存，但是不能混用
----

### 引入：本地引入和CDN
  1. 本地引入：`<script src="./js/jQuery-x.x.x.min.js">`
  2. CDN->bootcdn.cn->jQuery

----
### jQuery的选择器
上面提到jQuery可以模拟css选择元素、独有的表达式选择、多种筛选方法，下面分别来模拟：
```
css选择元素：
<div class="chioce">hello world!</div>
<div class="chioce" id="two">hello world!</div>
<div id="three">hello world!</div>
<ul>
    <li title="header">你好</li>
    <li>你好</li>
    <li title="footer">你好</li>
</ul>    

js：
$('.chioce').css('background','red');
$('div').css('background','red');
$('#two').css('background','green')
$('li:odd').css('font-size','20px')
$('li').filter('[title=footer]').css('background','orange')
```
* css选择器：上述(js：1-3)代码中分别通过标签，id选择器，class选择器来控制改变元素的样式。
* 独有的表达式选择：上述中第二个li变色，这里要注意的是odd虽然表示的是奇数，但是实际过程中是从0开始，所以是第二个
* 多种筛选方法：js最后一句代码中通过filter选中最后一行title=footer控制改变颜色<br>
[在线案例演示](http://js.jirengu.com/himuvinose/3/edit)

----
### 方法函数化
在jQuery中，要把原生JS中的一些方法想象成一个函数。
```
<div id="div1">balabala小魔仙</div> 

js:
$('#div1').click(function(){
    console.log($(this).html()) //jQ的写法
    console.log(this.innerHTML)  //原生的写法
    console.log($(this).innerHTML)//错误的写法:不能将原生的jQ混着使用
})
```
* 链式操作：<br>

类似于原生的写法：
```
  var oDiv = $('#div1');
  oDiv.html('hello');
  oDiv.css('background','green');
  oDiv.click(function(){
      alert('123');
  })
```
链式操作：
```
 $('#div1').html('hello').css('background','green').click(function(){alert('123');})
```
----
* 取值赋值合体<br>
原生JS取值赋值：
```
oDiv.innerHTML = 'hello'; //原生赋值
console.log(oDiv.innerHTML)//原生取值
$('#div1').Html('hello'); //jQ赋值
alert($('#div1').html()); //jQ取值
```
当然也可以这样写：<br>
当写一个参数的时候是取值：`css('width')`<br>
当写两个参数的时候是赋值：`css('width' , '200px')`<br>
但是要主要的是，当选中一组元素的时候取值赋值得到的结果是不一样的：
```
<ul>
    <li>aaa</li>
    <li>bbb</li>
    <li>ccc</li>
    <li>ddd</li>    
</ul>

js: 
alert($('li').html());  
$('li').html('hello');
//只有aaa弹出，其余不变化
//全部的值都会变成hello
```
* 所以要注意：当选中一组元素的时候，取值是一组中的第一个
* 当选中是一组元素的时候，赋值是一组中的所有元素

----
$()下的常用方法：
```

filter()
attr()  //设置元素的属性
```
