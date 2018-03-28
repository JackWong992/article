# 01_CSS为什么那么难学？
* css不正交
* css也是易学
### css历史
在CSS出现之前，网页如果写样式是什么样？
```
<body bgcolor="yellow">
    <h1><center><font color="red">大标题</font></center></h1>
</body>
```
这种控制起来比较麻烦完全不符合软件开发人员的设计思想，这时候CSS就横空出现了
包括：选择器，颜色，字体<br>
CSS出现了样式分离的思想:
1. 在页面的顶部加入：`<style type="text/css"></style>`
2. 在页面中外部引入：`<link src="./xx.css">`

为了区分电脑显示的样式和打印的样式，CSS还做了这样的努力：
`<link src="./xx.css' media="print">`</br>
这句话的意思是说：只有在打印状态下才会显示`link`的样式,否则则不显示！

CSS早起出现是满足于用户需要的要求，而不是自己独特的思想：<br>
如果你要颜色: `color:red; / background-color: red;`<br>
如果实现图文混排：`float: left/right;`<br>
如果需要绝对定位：`position: absolute`<br>

## CSS不正交
1. margin上下合并<br>
解决方法：<br>
* 兄弟元素之间加入：`<div style="border-top:.1px solid"></div>`
* 兄弟元素之间加入:`<div style="display:table;"></div>`
* 兄弟元素之间加入:`<div style="display:flex;"></div>`

2. display和小圆点
```
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>    
</ul>
```
去除小圆点的方法：`li{ display: block;}`

3. `position`可以改变`display`的属性值
```
html:
<div class="parents">
    <div class="chid">内联元素</div>
</div>
CSS:
.parents {
    background: red;
    height: 100px;
    position: relative;
}
.child {
    display: inline;
    border:1px solid ;
    position: absolute;
    bottom: 0;
    right: 0;
}
```
通过上面的代码我们都可知道：child为内联元素，但是如果给他设置了position值就会改变它的display，这更加体现了CSS的不正交，为什么设置了position会改变display的值呢？<br>

4. `float`可以影响`inline`
```
html: 
<div class="parent">
    <div class="float">浮动元素</div>
    <div class="child">浮动元素</div>
</div>
.parent{
    height: 100px;
    background:red;
}
.float {
    background: rgba(0,0,0,.2);
    width: 100px;
    height: 60px;
    float: left;
}
.child {
    width: 300px;
    height: 50px;
    background: white;
}
```
## CSS也是易学的
1. 背套路即可应付日常工作
    * 水平居中
    * 垂直居中
2. 巧用工具
    * CSS 3 Generator<br>
如果我想实现布局应该：<br>
![image.png](https://upload-images.jianshu.io/upload_images/6071779-c43ed40d8321dc20.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<br>
如果你想实现居中：<br>

![image.png](https://upload-images.jianshu.io/upload_images/6071779-6d5c40d5aefa9183.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
