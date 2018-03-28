# 事件
在jQuery中事件的操作都是绑定的形式,支持多事件写法<br>
* on()
* off()

---
## `on()`
打开事件<br>
有两种写法：<br>
1.  
```
$('div').on('click' , function(){
    alert('1');
})
```
2. 
```
$('div').click(fucntion(){
    alert('1')
})
```
第一种写法支持多事件写法。<br>
例如：<br>
```
$('div').on('click mouseover',function(){
    alert('1')
})`
```
### Event对象
* `pageX`/`pageY`
* `clientX` /`clientY`
* `which`
* `target`
* `stopPropagation()`  //阻止冒泡
* `preventDefault()`
* `return false`<br>

* `stopPropagation()`阻止冒泡时间的发生，不会受父级元素的影响发生变化。
```
  <div class="f">
    <div class="s">123</div>
  </div>  
css:
.f {
  background: red;
  width: 200px;
  height: 200px;
}
.s {
  background: green;
  width: 50px;
  height: 50px;
}
JS:
$('.f').click(function(ev){
  $('.f').css('fontSize','20px').css('color','white')
})
$('.s').click(function(ev){
  ev.stopPropagation();
})
```
首先在没有添加冒泡事件的情况下，点击子元素会发生变化。因为子元素在父级元素的包裹之下。
当添加了阻止冒泡事件以后，点击子元素状态不会发生变化。

`prevevtDefault()`表示阻止默认事件
`return false`表示既阻止默认事件，又阻止冒泡
实战过程中，解决冒泡点击事件绑定的方法：
```
    $('div').click(function(){
        $('span').off('click').click(function(){
            alert(1);
        })
    })
```

## 事件委托delegate()
```
$('ul').delegate('li','click',function(){
    $(this).css('background','red')
})
```
this指的是li，并不是ul。只是ul把事件委托给了li
当然也可以找到委托源，例如这样：
```
$('ul').delegate('li','click',function(ev){
  //  $(this).css('background','red')
  $(ev.delegateTarget).css('background','red')
})    
```
### trigger()主动触发事件
```
    $('#input').click(function(){
        var $li=$('<li>'+$('input2').val()+'</li>');
        $('ul').append($li);
    })
    $('#input2').keydown(function(ev){
        if(ev.which==13){
            $('#input1').trigger('click');
        }
    });
```
命名空间，相当于对主动触发指定了引导的方向：
```
    $('div').on('click',function(){
        alert(1);
    })
    $('div').on('click',function(){
        alert(2);
    })
    $('div').trigger()
```
我们上面说到了主动触发事件，但是这里的主动触发事件就不知道主动触发谁了，是弹出1，还是弹出2？或者说如果我们的需求是只弹出1，不弹出2，该怎么办？
引入了命名空间，在这里相当于给点击事件命名了：
```
    $('div').on('click',function(){
        alert(1)
    })
    $('div').on('click.abc',function(){
        alert(2)
    })
    $('div').trigger('click.abc')
```
引入了命名空间，这里就只会触发弹出2,1则不会弹出。

### 工具方法：
* $.type()&ensp;&ensp;   //比原生的typeof更强大
* $.isFunction() &ensp;&ensp;//判断是否是函数
* $.isNumeric()&ensp;&ensp; //判断是否是数字
* $.isArray()&ensp;&ensp;//判断是否是数组
* $.isWindow()&ensp;&ensp;//判断是否是window
* $.isEmptyObject()&ensp;&ensp;//判断是否是空数组
* $.isPlainObject()&ensp;&ensp;//判断是否是对象自变量
* $.extend()&ensp;&ensp;//对象的引用
```
 var a={
    name: 'hello';
 }
 var b={}
 $.extend(b,a,{age: 20});
 console.log(b);
 b.name="hi";
 alert(a.name)   //hello
```

### 工具方法
`$.proxy()` //修改this的指向<br>
```
    function show(){
        alert(this);
    }
    $.proxy(show , document)();
    //show的this是window，这里把document替换成window
```