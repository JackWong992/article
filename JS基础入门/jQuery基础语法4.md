# jQuery基础语法4：节点的选择与节点的操作
---
* 节点的选择
  * (子)节点的选择
  * (父)节点的选择

* 节点的相关操作
  * 创建节点
  * 插入节点
  * 删除节点
  * 复制节点

* 元素索引值

---

### (子)节点的选择：
* `first()`&ensp;&ensp;&ensp;//选择第一个元素
* `last()`&ensp;&ensp;&ensp;//选择最后一个元素
* `slice()`&ensp;&ensp;&ensp;//选择截取的元素（起始位置，结束位置+1）
* `children()`&ensp;&ensp;&ensp;//选择元素下的子元素
* `find()`&ensp;&ensp;&ensp; //查找元素下的特殊子元素
```
<ul>
  <li>1</li>
  <li>2</li>
  <li class='a'>3</li>
  <li>4</li>
  <li>5</li>
</ul>

$('li').first().css('background','red')
$('li').last().css('background','#ccc')
$('li').slice(1,4).css('fontSize','35px')
$('ul').children().css('padding','8px')
$('ul').find('.a').css('border','1px solid ')
```
第一个`li`元素背景变红<br>
最后一个元素的背景变灰色<br>
第2个元素至第4个元素字体变成`35px`<br>
所有元素的内边框大小为`8px`<br>
含有`.a`的元素有`1px`边框<br>

这里看起来`find()`和`children()`区别不是很大，但是`find`使用起来更加具体灵活，我不推荐使用`children`推荐你使用`find`,`find`针对的元素更加具体，而`children`则针对的是一个集合

---
### (父)节点的选择
* `parent()`&ensp;&ensp;&ensp;获取父级元素的节点
* `parents()`&ensp;&ensp;&ensp;获取所有祖先元素的节点
* `closest()`&ensp;&ensp;&ensp;查找指定的一个最近的祖先元素(包含自己)

前两种都比较容易理解，`parents()`在实战的过程中比较少见，因为难控制在<br>
`closest()`使用的就较多
```
    <li><div>aaa<span>span</span></div></li>

    $('span').closest('li').css('background','red')
```
要注意的是closest()这个方法必须要接受一个参数，这样才能生效，而且其查找的是指定的祖先级节点这一点使用起来比较多。

--- 

### 节点的操作
原生的JS创建节点是怎么样的：<br>
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;
`document.creatElement('div')`<br>
显然使用起来比较麻烦，而在jQuery中实现是这样的：
* $('\<xx>\</xx>')&ensp;&ensp;&ensp;创建一个元素

这里要注意的是在jQuery中选择一个节点是这样的：`$('div')`,所以是选择一个节点还是创建一个节点在这里要注意分辨清楚

* `append()` 将元素添加到指定的节点里面且是最后
* `prepend()` 将元素添加到指定的节点里面且是最前面
* `before()` 将元素添加到指定的节点（外面）的前面
* `after()`  将元素添加到指定的节点的（外面）的后面
```
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
    </ul>        
var $li = $('<li>hello</li>') 
var $lii = $('<li>world</li>') 
var $liii = $('<li>4</li>')
var $lie = $('<li>5</li>')
$('ul').append($lii) //ul下最后一个元素有li元素内容为world
$('ul').prepend($li) //ul下最上面一个元素有li元素内容为hello
$('ul').before($liii) //ul前面有元素li内容为4
$('ul').after($lie) //ul后面有元素li内容为5 
```
---

### 删除节点和克隆节点
* `remove()`&ensp;&ensp;删除节点
* `clone()`&ensp;&ensp;克隆节点
```
    <ul>
        <li>1</li>
        <li>2</li>
        <li>1</li>
    </ul>

 $('ul').remove()  //执行删除操作    
```
这是执行的删除节点操作，执行起来比较简单，没有原生的JavaScript那么麻烦，上面提到的插入节点或者是创建节点其实都是剪切的操作，不是复制的操作。<br>
举个例子来说，如果我们针对一个元素执行了`append()`的操作，然后在对这个元素执行`prepend()`的操作，结果是只有最后有这个元素，其实仅执行一次剪切操作。

* `clone()` 克隆节点
```
    var $div = $('div').clone(true) //参数救赎可以复制之前的操作行为
    
    $div.appendTo($('span'))
```
[具体实例演示](http://js.jirengu.com/zaceg/3/edit)

---
* `index()`&ensp;&ensp;&ensp;查找元素的索引值
代表的是当前元素在当前所有兄弟节点的排列位置
1. 第一种用法： 兄弟中的排行
```
    <li>1</li>
    <li>2</li>
    <li class="ac">3</li>
    <li>4</li>
    <li>5</li>
    
console.log($('.ac').index())  //2
```
2. 第二种用法：筛选后的排行<br>
例如想要得到`span`元素的排行应该怎么做呢？
```
    <div><span>1</span></div>
    <div><span>2</span></div>
    <div><span class="ac">3</span></div>
    <div><span>4</span></div>
    
$('.ac').index('span') //查找当前元素在所有span元素中的排行位置  2
```

[实例演示：写一个选项卡](http://js.jirengu.com/hukew/1/edit?html,js,output)