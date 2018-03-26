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

* jQuery属性选择：
1. `[ xx=yy ]`: 属性名称xx=yy的元素被选中
2. `[ xx^=abc ]`:属性名称xx中以abc为开头的元素被选中
3. `[ xx$=abc ]`:属性名称为xx以abc为结尾的元素被选中
4. `[ xx="aa bb cc" ]`:属性名称为aa bb cc元素被选中
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
### 常用方法：
```
addClass()    //添加一个class
removeClass()  //移除class
width()   //获取div的宽度 
innherWidth() //获取width+padding的长度
outerWidth()  //获取width+padding+border的宽度
outerWidth(true) //获取width+padding+margin+border的宽度
toggleClass()  //自动判断类里面是否有这个class，如果有删除，没有没有就自动添加。
show()   //显示相关信息
hide()   //隐藏相关信息
```
```
html:  <input type="button" value="button">
       <div>123</div>
js:
  var a=true;
  $('input').on('click',function(){
    if(a){
      ('div').show();
      a=!a;
    }else{
      ('div').hide();
      a=!a;
    }
  })
```
[show()/hide()实例演示](http://js.jirengu.com/hirazikoza/2/edit)
[toggle()实例演示](http://js.jirengu.com/yaxeripico/2/edit)

$()下的常用方法：
```
has()  //包含
filter() //筛选元素
not() //筛选的反义词
attr()  //设置元素的属性
next()  //下一个兄弟节点
prev() //上一个兄弟节点
find() //查找
eq() //更确切到某一个元素的下标，从0开始
```
上面我们知道has()和filter()的作用，现在我们来想一下他们的区别：<br>
`has()`是包含，就有筛选的作用，但是于筛选不同的是has()只能用于父级元素下的子级元素<br>
`filter()`则是没有那么多限制，直接去找父级元素<br>
[not、has、filter区别在线演示](http://js.jirengu.com/varibemohe/2/edit)<br>

`next()`和`prev()`都是指查找上一个元素或者下一个元素
下面提到的`find()`和`has()`有点相类似，`find()`查找的是父级元素下的子元素，所以这里要注意：`has() find() filter()`区别。

[next()、prev()、find()在线演示](http://js.jirengu.com/soyetiruba/2/edit)

`eq()`具体的是查找到某一个具体的元素，例如：
```
<ul>
  <li>123</li>
  <li>456</li>
  <li>789</li>
  <li>012</li>
</ul>  
js: $('li').eq(2).css('background','red')
//第3个li变色
```
`index()`一组元素的索引，可以查到当前元素在所有兄弟节点的中的位置
```
<ul>
  <li>123</li>
  <li>456</li>
  <li class="two">789</li>
  <li>012</li>
  
 js: console.log($('.two').index() ) //2
```


----
* DOM节点操作<br>
`first()`一般是选中一组元素中的第一个元素<br>
`last()`一般选中一组元素中的最后一个元素<br>
`slice(x,y)`截取一组元素中的某段元素,x表示开始的位置，y表示结束的位置-1<br>
`nextAll()`下面的所有节点都会被选中<br>
`preAll()`上面的所有节点都被选中<br>
`sibling()`找出元素的所有兄弟节点<br>
`children()`获取所有父级元素的子元素<br>
`find()`查找到某个具体的元素<br>
`parent()`获取父节点<br>
`parents()`获取当前元素所有的祖先节点<br>
`closest()`接收一个参数，找指定的一个最近的祖先元素<br>

[first()、last()、slice()实例演示](http://js.jirengu.com/ziwaniyove/2/edit)<br>
[find()、children()实例演示](http://js.jirengu.com/zoyozayaza/2/edit)<br>
find()相比较children()查找更加具体<br>
[parent()、parents()](http://js.jirengu.com/jacudovatu/3/edit)<br>
[closest()实例演示](http://js.jirengu.com/jacudovatu/3/edit)<br>
`closest()`接收一个参数，找到离它最近的一个元素的父级元素（也包括自己），如果父极元素没有这个参数，就会往祖先级查找.

* 节点操作：
  * 创建节点：<br>
`<''>` //例如创建一个div元素，可以这样：`('<div></div>')`
  * 节点操作:<br>
`append()`把元素添加到指定的节点里面，且是最后<br>
`prepend()`把元素添加到指定的节点的里面，且是最前<br>
`before()`把元素添加到指定的节点的前面<br>
`after()`把元素添加到指定的节点的后面<br>
当然也有`insertAfter(),insertBefore(),appendTo(),prependTo()`等操作符，意思是一样的，但是控制的元素是不一样的：主要是作用于开始的元素<br>
[append(),prepend(),before(),after()实例后面](http://js.jirengu.com/kumequtuwa/2/edit)<br>

  * remove() 删除某个节点<br>
  * clone()克隆某个节点<br>
[remove(),clone()实例演示](http://js.jirengu.com/magemihuwa/2/edit)<br>
克隆和删除有所不同，实际过程中删除进行的是剪切操作，克隆针对的是复制操作。<br>

  * index()索引值，代表的就是当前元素在所有兄弟节点中的排行位置
  [选项卡](http://js.jirengu.com/cikurufovu/2/edit)
```
html: 
<ul>
  <li>123<li>
  <li>123<li>
  <li id="abc">123<li>
  <li>123<li>  
</ul>

JS:console.log($('#123').index())    //2
```
当然，如果是这样：
```
  <div><span>123</span></div>
  <div><span>123</span></div>
  <div><span id="d">123</span></div>
  <div><span>123</span></div>
```
如果想查看`<span id="d">123</span>`在所有span元素中的位置，可以这样：
&ensp;&ensp;&ensp;`console.log($('#d').index('span'))`

----
* `on()`和`off()`<br>
说到这里我要介绍一下jQuery中点击事件的两种写法：
```
第一种：
$('div').click( function(){
    console.log('1');
})
第二种：
$('div).on('click' , function(){
   console.log('1');
})
```
这里的第二种好处是可以针对的是不止一种点击事件。举例说明：
```
$('div').on('click mouseover' , function(){
  console.log(123)         //鼠标移入会弹出123，鼠标点击也会弹出123
})
```
```
$('div').onclick({
  'click': function(){
    console.log(1);
  },
  'mouseover': function(){
    console.log(2);
  }
})
```
* `off()`关闭某个事件，注意这个关闭要加在到适当的地方，一般会加在事件完成以后之后，而不是在事件没触发就加在后面，这样是导致事件不会触发。<br>
```
$('div').on('click' , function(){
   console.log('1')}; 
      $('div')).off()       //如果()什么都不写是默认关闭所有事件，如果写了'click'就是关闭点击事件，或者别的事件
```
* `scrollTop()`获取屏幕滚动的距离<br>
eg：
```
  $(document).click(function(){
    alert( $(window).scrollTop() );
  })
```
点击某一个位置，弹出页面滚动的距离。

* jQuery中的遍历
 * each()
   * 回调函数的两个参数
   * this指向
   * return false

---

