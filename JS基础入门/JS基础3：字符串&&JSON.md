# 字符串和JSON
* 字符串
* JSON

## 字符串
字符串就是零个或者多个排在一起的字符，放在单引号或者双引号之间<br>
```
'abc'  "abc"        //表示的意思是一样的
```
字符串的内部可以是单引号，也可以是双引号<br>
* 转义
`"hello "world"`
如果这样输入JS会默认将world给去掉，但是这里我们可以使用转义来实现`hello " world` ,使用`" hello \"world  "`<br>
左侧为转义，右侧为实际效果：
```
    "hello\'world"      -> hello'world
    "hello\"world"      -> hello"world
    "hello\tworld"      -> hello  world
    "hello\nworld"      -> hello  （换行）  world
```
* 字符串默认是一行，不能写在多行

### 字符串的长度计算,连接,截取，查找，大小写
`var str ='hello'`<br>
* 获取字符串的长度：`str.length`
* 获取字符串的第一个字符：`str[0]`
* 获取字符串的最后一个字符：`str[str.length-1]`
* 获取字符串x个字符：`str.charAt(x-1)`
* 获取字符串x个字符的ASCII码：`str.charCodeAt(x-1)`

1. 字符串的截取
`var str="hello world"`<br>
`var sub= str.subStr(x,y)`&ensp;&ensp;//起始位置，截取的长度<br>
`var sub= str.subString(x,y)`&ensp;&ensp;//起始位置，结束的位置（从0开始）<br>
`var sub=str.slice(x,y)`&ensp;&ensp;//起始的位置，结束的位置（可以为负数）
2. 字符串的查找
``
