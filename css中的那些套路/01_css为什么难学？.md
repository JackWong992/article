# 01_CSS为什么那么难学？
* css不正交
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

2. 