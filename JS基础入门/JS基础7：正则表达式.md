# JS中的正则表达式`RegExp()`
正则都是用来操作字符串的

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

    alert( str.match(re))  //[1]
```