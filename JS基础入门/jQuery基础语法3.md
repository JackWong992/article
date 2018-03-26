# 获取高度的宽度

----
* 获取元素的尺寸
* 与原生获取尺寸的区别/可视区尺寸和页面尺寸获取
* 滚动距离：`scrollTop`

----

### 获取元素的尺寸
下面介绍只以`width`为例（`height`不做介绍）<br>
* `width()`&nbsp;&nbsp; 获取元素的宽度（width）
* `innerWidth()`&nbsp;&nbsp;获取元素内部宽度=width+padding
* `outerWidth()` &nbsp;&nbsp;获取元素外部宽度=width+padding+border
* `outerWidth(true)`&nbsp;&nbsp;获取元素的宽度=width+padding+border+margin
### 设置元素的尺寸
例如设置元素的宽度为200px<br>
设置元素的宽度+padding=200px<br>
设置元素的width+padding+border=200px<br>
设置元素的width+padding+border+margin=200px<br>
```
$('div').width('200px');
$('div').innerWidth('200px');
$('div').outerWidth('200px');
$('div').outerWidth(200,true);
```
### 原生的JS获取尺寸
```
 $('div').get(0).offsetWidth()
```
不过获取尺寸来说原生的和jQ的有点区别是：原生的JS是获取不了隐藏元素的尺寸的，为jQ则是可以的。<br>
获取窗口可视区的尺寸：`$(window).width()`<br>
获取页面的实际尺寸：`$(document).width()`<br>

----

### scrollTop的理解
scrollTop可以理解为滚动的距离，其实学到这里的时候我是一直不理解滚动的距离是什么意思。<br>
后来我接触了越来越多才发现：滚动的距离=页面的高度-窗口的高度（`scrollTop==document.height()-window().height`）<br>
实际就是这样：
```
    $(document).scrollTop==$(document).height-$(window).height()
```
一般有的网站上可能不止出现一个滚动的页面，我们可以也可以通过对某个元素设置该属性(`$('div').scrollTop`)<br>
### `offset()`获取元素到`document`的真实距离
```
    $('div').offset().top //获取元素到页面顶部的距离
    $('div').offset().left //获取元素到document左边的距离
    $('div').offset().right //获取元素到页面右部的距离
```
这里的`offset().x`针对的只是`document`的距离，即使被设置的元素是被嵌套的，获取的也是到`document`的距离<br>
如果父元素发生了绝对定位，同样也是`失效`,只是获取到document的距离<br>

如果我们想获取子元素相对与父元素的距离或者相对元素的距离该怎么办？
这时候引入了`position()`属性。<br>
`$('.son').position().left`到相对元素的左边距离<br>
`$('.son').position().top`到相对元素的顶部距离<br>
`$('.son').position().right`到相对元素的右边距离<br>
*需要了解的是position对margin是失效的，如果一个子元素设置了margin那么position结果为0*<br>
当然也可以通过jQ中计算的方法来获取得到距离相对父级元素的值：<br>
例如：<br>
父（相对）元素到边界的距离：`$('.son').offsetParent().offset().left`<br>
子元素到边界的距离：`$('.son').offset().left`<br>
距离父元素的距离=子元素到边界的距离-父元素到边界的距离
[懒加载的实现](http://js.jirengu.com/wepemavibi/2/edit)
