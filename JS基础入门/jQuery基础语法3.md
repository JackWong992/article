# jQuery基础语法3：class相关的操作

---
* addClass()
* removeClass()
* toggleClass()
* show()/hide()
* 节点操作
* eq()

### class的相关操作
* addClass()

故名思议，动态的为元素添加一个class。
```
    <div class="box1">box</div>

    $('div').addClass('box2')
```
* removeClass()

删除元素的一个class
```
    <div class="box1">box</div>

    $('div').removeClass('box1')
```
* toggleClass()

动态的为元素添加或删除一个元素，如果元素含有这个类就执行删除操作，如果没有就执行添加操作
```
    <div class="box name">box</div>

    $('div').toggleClass('box') //删除操作
    $('div').toggleClass('age') //没有这个类，执行添加操作
```

--- 

### show()/hide()

`show()/hide()`显示、隐藏操作：
```
    <input type="button" value="点击"> 
    <div> div</div>

    $('input').click(function(){
        var btn=true
        if(btn){
            $('div').show()
        }else {
            $('div').hide()
        }
        btn=!btn
    })
```
与CSS区别：
```
    <input type="button" value="点击"> 
    <div> div</div>

    $('input').click(function(){
        var btn=true
        if(btn){
            $('div').css('display','none')
        }else {
            $('div').hide('display','block')
        }
        btn=!btn
    })
```
这种写法与上面的写法虽然表面上来看实现的效果都是一样的，但是在实际工作中还是推荐`hide()/show()`的写法，如果是要针对的元素是行内元素，用第二种写法就会改变它的样式，所以这里不推荐第二种写法。

---

### 节点的操作
* pre()&ensp;&ensp;&ensp;  //上一个
* next()&ensp;&ensp;&ensp;//下一个
* preAll()&ensp;&ensp;&ensp;//上面所有
* nextAll()&ensp;&ensp;&ensp;//下面所有
* siblings()&ensp;&ensp;&ensp;//所有兄弟节点

```
    <div>div</div>
    <p>p</p>
    <h1>h1</h1>
    <h1 class="sc">secondly</h1>
    <span>span</span>

$('div').next().css('color','red') //p变红
$('p').pre().css('color','green') //div变绿
```
前面提到了方法函数化，我们也知道了元素的取值和设置。在这里节点的相关操作也有一种类似于取值的功能，不过在这里执行的是筛选功能：
```
    $('p').sibilings('.sc').css('color','yellow')
```
可以看到这里的`h1`颜色不会发生变化，而`secondly`的颜色变黄

---

### eq()下标
在jQuery中的`eq()`相当与原生JavaScript中数组的下标，一般我们说道下标的时候都是想实现对一组元素中的某一个元素的实现效果
```
    <ul>
        <li>1</li>
        <li>2</li>      //变红
        <li>3</li>
        <li>4</li>
    </ul>

    $('li').eq(1).css('background','red')
```
