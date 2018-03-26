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
* `stopPropagation()`
* `preventDefault()`
* `return false`
