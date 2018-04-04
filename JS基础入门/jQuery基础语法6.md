# jQuery基础语法6：循环，包装，转换
* `each()`
* 包装对象`wrapper()`
* 转换原生的方法`get()`
---
* `each()`

### 循环
在jQuery中循环遍历使用`each()`,相当于原生JS中的for循环
```
   <li></li>       //0
   <li></li>       //1
   <li></li>       //2
   
$('li').each(function(i,elem){
    $(elem).html(i)
})
```
`each()`接收一个函数，函数里有两个参数`i和element`<br>
这里的`i`代表的是原生`for`循环中的`i`，`elment`相当于原生中的元素<br>
这里用`return false`代替`break`

---

### jQuery中的包装对象
* `wrap()`
* `wrapAll()`
* `wrapInner()`
* `unwrap()`
```
    <span>span</span>
    <span>span</span>
    <span>span</span>

$('span').wrap('<div>')
$('span').wrapAll('<div>')
$('span').wrapInner('<div>')
$('span').unwrap('div')
```
这样的结果会发现每个`<span>`标签外面都有一个div标签.<br>
给所有的元素加入一个`div`,这里针对的是`span`元素,如果在`span`元素中有一个非`span`元素那么这个元素就会被剪切出div<br>
在元素的内部包含一个`div`<br>
去除元素的包含元素，相当于删除元素的父级节点,同时body元素是不可能被删除的<br>
[wrap的实例演示：普通用户和管理员](http://js.jirengu.com/pihiv/1/edit?html,js,output)

----

jQuery转原生JS方法
* `get()`&ensp;&ensp;&ensp;把jQuery转换成原生JS
```
    <div>aa</div>

$('div').get(0).innerHTML  //aa
```
使用`get()`将jQuery转换为原生的JS，这里需要注意的是转换成原生的结果是一个集合，所以如果想要获得原生需要在`get()`方法里面传入一个参数，参数就是需要转换的下标

那么为什么要将jQuery转换成原生的JS呢？<br>
事实上，我们想要获取元素的文本内容实际高度就要使用原生JS
```
 jQuery:   console.log($('#l').height())
 JS: console.log($('#l').get(0).scrollHeight)
```

---

