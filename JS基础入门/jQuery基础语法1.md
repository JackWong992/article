# jQuery入门1：使用jQuery你需要知道的背景
--- 
* 前置知识
* 如何使用jQ
* 选择元素
* jQ方法函数化
* JavaScript与jQuery的关系
### 前置知识
熟悉HTML，CSS，JavaScript<br>
简单的了解一些控制台相关知识

---
### 如何使用jQuery
1. 下载至本地，直接引入
   * 官网：www.jQuery.com 
2. CDN引入
   * www.bootcdn.com(推荐使用)

---
### jQuery中如何选择元素
先来看看原生中如何选中元素的：
```
  var box = document.getElementById('box')
  var box = document.getElementsByTagName('box')[0]
  var box = document.getElementsClassName('box')[0]
```
总之看起来很麻烦，在来看看jQuery中是怎么使用的：
```
  $('div').css('background','red')
  $('#div').css('background','red')
  $('.div').css('background','red')  
```
其实在jQ中选择的元素有点类似与CSS中的选择元素，使用起来比较轻便。

---
### jQuery方法函数化
原生
```
  var oDiv = document.getElementById('div')
  oDiv.onclick = function(){
    alert(oDiv.innerHTML)
  }
```

jQuey
```
var oDiv = $('#div')  //获取元素，有点类似于函数调用
oDiv.click(function(){
  alert( oDiv.html() )
})
```

---

### JavaScript与jQuery的关系
```
  alert( oDiv.html() ) //纯jQuery写法
  alert( document.getElementById('div').innerHTML) //纯JS写法

  alert( oDiv.innerHTML)    //错误
  alert( oDive.getElementById('div1').html()) //错误  
```
* JavaScript与jQuery之间不能混写
* 函数中返回原生的this，选择元素需要加入`$()`

[颜色选择实例演示](http://js.jirengu.com/dohey/2/edit)
```
  var color =''
  
  $('span').click(function(){
    color = $(this).html()
  })

  $('div').click(function(){
    $(this).css('background',color)
  })
```

