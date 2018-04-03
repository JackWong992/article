# jQuery基础语法3：class相关的操作

---
* addClass()
* removeClass()
* toggleClass()
* show()/hide()

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
* pre()
* next()