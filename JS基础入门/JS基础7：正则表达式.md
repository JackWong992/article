# JS中的正则表达式`RegExp()`
正则都是用来操作字符串的

正则表达式使用场景：
 * 批量提取/替换有规律的字符串
 * 在各种高级文本编辑器的使用
 * 在各类办公软件（office）中使用
 * 在各种开发语言中使用(c#/java/js/Perl/PHP)
 * 用户输入的合法性验证（IP地址，特殊订单号要求）
 * 模块引擎的标签库开发
 * 网络爬虫（抓取机器人）的开发
 * 批量文本的高效处理

---
前置知识（转义字符）：
* \s&ensp; 空格
* \S&ensp; 非空格
* \d&ensp; 数字
* \D&ensp; 非数字
* \w&ensp;  字符(字母，数字，下划线)
* \W&ensp;  非字符

---
正则表达式的常用方法：
* `test`

text:正则去匹配字符串，如果匹配成功就返回真，如果
匹配失败就返回假<br>
```
    var str ='abcdefg'
    var re=/b/
    alert(re.test(str)) //true
```

* `search`

search:正则去匹配字符串，如果匹配成功，就返回匹配成功的位置，如果失败就不会-1<br>
```
    var str ='abcde'
    var re = /c/

    console.log(str.search(re))      //1
```
*正则中是默认区分大小写，如果想要区分大小写需要在正则的最后加入标识符`i`*
```
    var str='abcde'
    var re=/c/i

    console.log(str.search(re))       //1
```

* `match`

match:正则去匹配字符串，如果匹配成功就返回匹配成功的数组，如果匹配不成功，就返回null
```
    var str ='haj123sdk54hask'
    var re = /\d/

    alert( str.match(re))  //[1]
```
显然只得到一个1并不是我们想要得到的结果，我们要匹配字符串str中的所有数字才可以<br>
*正则中默认：正则匹配成功就会结束，不会继续匹配，如果想要全部匹配需要引入全局g*
```
    var str ='haj123sdk54hask'
    var re = /\d/g

    alert( str.match(re))  //[1,2,3,5,4]
```
如果想要匹配两个或者三个数字为一个元素：
```
    var str = 'haj123sdk54hask'
    var re=/\d\d/g

    alert( str.match(re) ) //[12,23,54]
```
如果想要尽可能的匹配多的数字应该引入量词的概念，后面会接着介绍到，这里只是演示
```
    var str='haj123sdk54hask'
    var re=/\d+/g

    alert( str.match(re) ) //[123,54]
```