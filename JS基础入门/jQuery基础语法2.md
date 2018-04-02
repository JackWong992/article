# jQuery基础语法2:获取元素和设置元素
* 元素的赋值与获取
* 属性的选择操作
* jQuery中的链式操作
* 命名规范
* 集合的长度
```
 原生： 
    oDiv.innerHTML
    oDiv.innerHTML='hello world'
```

前面提到方法函数化，在这里可以理解为如果我们没有传参的话默认就是获取，如果传参的话就是赋值。当然这种想法不一定是对的，只是便于理解。
```
    oDiv.html()   //获取
    oDiv.html('hello world') //设置

    $('#div').css('color')  //取值
    $('#div').css('color','red') //设置（赋值）
```
在这里是设置还是获取取决于设置的参数来决定的。
当然也可以自定义的设置元素的属性
* attr()
```
    $('.div').attr('title')  //获取：xiaoming
    $('.div').attr('title','xiaohong') //设置 title：xiaohong
```
* val()是设置元素的基础值
```
    $('.div').val('abc')  //设置元素的value：abc
    $('div').val() //获取元素的value值为abc
```
但是`val()`使用起来比较鸡肋，只能设置val相关属性，就没有`attr`用起来比较强大
```
<input type="text" value='123'>
<input type="text" value='456'>

    $('input').val()   //123
```
*要注意的是，多元素进行取值的时候取得是第一个元素的值*

---

### 属性的选择操作
属性的选择方式：
*  &ensp; `[ ]`
*  &ensp; `[a=b]`
*  &ensp; `[a^=b]`
*  &ensp; `[a$=b]`
*  &ensp; `[a*=b]`

```
    <input value="123_111" type="text">
    <input value="123_111" type="text">
    <input value="2" type="text">
    <input value="456_111" type="text">
    
    $('input[value]')
    $('input[vallue=123_111]')
    $('input[value^=123]')
    $('input[value$=111]')
    $('input[value*=2]')
```
选中`input[value]`的元素<br>
选中`value=123_111` 的元素<br>
选中以`value=123`为开头的值<br>
选中以`value=111`为结尾的值<br>
选中含有`value=2`的值<br>

---

### jQuery的链式操作
在jQuery对于某一个元素可以触发多次事件或者行为我们称之为链式操作。<br>
例如：`$().css().html().click()`<br>
上述行为首先选中了元素，接着设置了css属性，然后获取到了`html`的内容，最后触发了点击事件<br>
*要注意的是链式操作针对的都是设置元素的某些值，如果你想获取某些元素使用链式操作实现不了*

---
### 命名规范：
变量名默认加入`$`,默认是使用了jQuery。与原生要分别开。
```
    var $text=$('.text')

    var $pre = $('#pre')
```

--- 
### 集合的长度
获取集合的长度在jQuery提供了两种方法：
* size()
* length()
 * $()获取得到的都是一个结合
```
    <div class="active">111</div>
    <div >222</div>
    <div >333</div>

    $('div').length //  3    
```