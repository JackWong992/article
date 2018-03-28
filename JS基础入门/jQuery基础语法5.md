# jQuery中的运动
简单运动效果
* show()
* hide()
* toggle()<br>

复杂运动效果

* animate() 

## 运动的一些方法
* show()显示
```
    var btn=true;
    $('input').click(function(){
        if(btn){
            $('div').hide()
            btn=!btn
        }else(btn){
            $('div').show()
            btn=!btn
        }
    })
```
* hide()隐藏
* toggle()显示/隐藏的结合，点击一次隐藏，再点击显示<br>
如果使用了toggle()则不需要进行true判断了
```
    $('#input2').click(function(){
        $('#div2').toggle()
    })
```
这里的也可以对`hide()` `show()` `toggle()`的括号里面设置参数：`'fast'`，`'slow'`，`'normal'`来显示运动效果的快慢。<br>
* `fadeIn()` `fadeOut()` `fadeToggle()`与上述效果类似，只是添加了淡入淡出的效果。
* `slideDown()`,`slideUp()`, `slideToggle()`与上面的`hide`和`fadeIn()`不同的是一个是往上走，一个是往下降，效果类似。它们都可以设置时间。

### 复杂运动animate()
与上面不同的是，animate()接受的是复杂的运动效果。
比如：
animate()接受4个参数：
1. 第一个参数：对象{}去设置（目标）样式属性和值
2. 第二个参数：时间，默认是400ms
3. 第三个参数： 运动形式，只有两种：`swim`(默认：缓冲，慢快慢) 和`line`(匀速)
4. 第四个参数： 运动结束的回调
```
    $('#input1').click(function(){
        $('#div1').animate({
            width: 400,
            height: 300
        },2000,'linear'，function(){
            alert('1');
        })
    })
```
除了上述的写法，也还有另外一种写法：<br>
配置参数step的作用：<br>
》》duration easing complete
```
    $('#input1').click(function(){
        $('#div1').animate({
            width: 300
        },{
            duration: 1000,
            easing: 'linear',
            complate: function(){
                alert(123);
            }
        })
    })
```
这种运动效果也是支持链式运动的，也可以-delay()增加延迟实现。

### stop()
```
    $('input2').click(function(){
        $('#div1').stop();
    })
```
stop可以接受2个参数：
1. 默认情况下： 只会停止当前运动
2. 第一个参数：`stop(true)` 可以停止所有的运动
3. 第二个参数：`stop(true , true)` 可以停止到指定的（当前）目标点
4. 同时`stop()`还有一个清空队列的行为。<br>
`$('#div1').finish();`瞬间完成操作；


