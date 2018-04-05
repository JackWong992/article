# JS入门基础2： 数据类型，运算符，运算符优先级，流程控制语句

* 数据类型分类
* 运算符
* 运算符优先级
* 流程控制语句

---

### 数据类型分类
JavaScript的语言的每一个值，都属于某一种数据类型。<br>
在js的内部，所有的数字都是以64位浮点数形式储存，即使整数也是这样<br>
在JavaScript中的数据类型一共有七种：
* 数值(number)：整数和浮点数
* 字符串（string）：字符串组成的文本
* 布尔值(boolean)：true(真)和false(假)两个特定的值
* undefined：表示未定义或者不不存在的值
* null：表示空缺，既此处应该有一个值，但是目前为空 
* object： 各种值的组合
* symbol： 目前暂时不做详细研究
```
    var num = 123;
    var str = 'xiaoming';
    var boo = true;
    var isUndefined;
    var n = null;
    var arr = [1,2,3]
    var fn = function(){
        console.log('1')
    }
    var obj = {
        name: 'xiaoming',
        age: '18'
    }
```
上述变量严格来分又分为简单数据类型变量和复杂数据类型变量。<br>
简单数据类型变量：`number`，`string`，`boolean`<br>
复杂数据类型变量： `object`<br>
其中复杂数据类型变量又分为三种：
* 狭义的对象
* 数组 `[]`
* 函数 `fuction(){}`
* 正则表达式  `var reg = /ye/`

其中在JavaScript中有三种方法可以判断一个值具体是什么类型：
* `typeof` 运算符
* `instanceof` 运算符
* `object.prototype.toString`方法

typeof运算符可以返回一个值的数据类型，
原始类型：<br>
`typeof` 123   // number<br>
`typeof` '123'  // string<br>
`typeof` true  // boolean<br>
复杂数据类型：
`typeof` function  //'function'<br>
`typeof` object  //'object'<br>
`typeof` window  //'object'<br>
`typeof` {}   //'object'<br>
`typeof` []  //'object'<br>
`typeof` null  // object<br>
上面我们可以看到当`typeof`碰到比较棘手的`object`处理起来就比较麻烦了，因为当碰见`[]`,`{}`返回的都是`object`<br>
所以这时候我们需要了解`insatanceof`<br>
区分数组和对象：
```
    var a = []
    var o = {}

a instanceof Array   //true
o instanceof Array   //false
```
区分于`null`和`undefined`区别：<br>
其实`null`和`undefined`是有历史渊源的，早期的设置为后来的使用存在了`bug`，首先从类型判断来说，`undefined`返回的结果是`undefined`，`null`则返回的结果是`object`，从值的意义来说，`null==undefined`<br>
所以对于`undefined`和`null`可以这么理解：
`null`表示值为空，既此处的值现在为空，典型的用法：
* 作为函数的参数，表示该参数的参数没有一个任何内容的对象
* 作为对象原型链的终点

---

### `undefined`表示不存在的值，就是此处目前不存在任何值，典型的用法是：
* 变量被声明了，但没有赋值时，就等于`undefined`
* 调用函数时，应该提供的参数没有提供，该参数等于`undefined`
* 对象没有赋值的属性，该属性的值为`undefined`
* 函数没有返回值时，默认返回`undefined`
```
    var i  //undefined
    
    function f(x){
        console.log(x)
    }
    f()   //undefined
    
    var o = new Object()
    o.p //undefined

    var x = f()
    x //undefined
```

---

### `boolean`:只有真和假两个状态，真的关键字用true表示，假的关键字用false表示<br>
会返回布尔值的运算符：
* 两元逻辑运算符: `&&`  , `||`
* 前置逻辑运算符: `!`
* 相等于算符: `=== ` &ensp;&ensp;`!==`&ensp; `==`  &ensp;&ensp;  ` !=`
* 比较运算符:`>` &ensp;&ensp;`>=`&ensp;&ensp;  `<`&ensp;&ensp; `<=`

5种转换为false的类型：
* `0`
* `NaN`
* `''`
* `undefined`
* `null`

*这5种false值将伴随我们JS学习的整个生涯，所以要死记。*

---

### `number`:JavaScript的数字类型和其他语言有所不同，没有整形和浮点数的区别，统一都是number类型：
可以表示十进制，八进制，十六进制：
```
    var a =10
    var b = 073  
    var c = 0xf3  
```
对于浮点数而言：
1. 浮点数的数字包含小数点，前面的0可以省略
2. 对于极大或者极小的数字可以使用科学计数法：`var a =3.1e5`
3. 浮点数的最高精度是17位，但是在计算的时候精度不如整数
```
    1-0.9     //0.09999999999999998
    0.1+0.2   //0.30000000000000004
```
NaN含义是Not a number，表示非数字，NaN和任何值都不相等，包括自己<br>
判断一个数字是否是`NaN`，可以选择`isNaN()`方法

`Infinity`表示无穷，表示两种场景，一种是一个正的数值太大，或者是一个负的数字太小，无法表示，还有一种是非0除以0

与数值相关的全局方法：
1. `parseInt()`   //字符串转换为整数
2. `parseFloat()` //字符串转换为浮点数

对于parseInt来说，如果头部有空格，空格会自动去除。
例如：`parseInt('   123') //123`<br>
字符串转换为整数的过程中会一个个字符的转换，遇到不能转换的字符会停止不在进行下去，返回已经转好的字符串。<br>
如果遇到第一个不能转换的字符串，会返回`NaN`<br>
`parseInt()`默认状态下是转换为10进制，当然你也可以指定转换的进制，例如：`parseInt(100,8)`,如果第二个数字不是2,8,16，结果会是`NaN`,如果是`null`,`undefined`会默认忽略。

---

### String
多行书写字符串，单行输出字符串的方法：
1. ` \`连接
```
    var string = 'long\
                long\
                long\
                String';
```
2. `+`连接
```
    var string= 'long'+
                'long'+
                'long'+
                +'string'
``` 
另一方面字符串也可以直接被当做是数组，例如：
```
    var s='hello'
    s[0] //'h'
    s[1] //'1'

那么：'hello'[0]  //'h'
```
因为字符串与数组的相似支出仅此而已，所以，严格意义上来说是无法改变字符串中的单个字符的。
同样，字符串也有`length`属性，且是无法改变的。

最后JS还有两种原生base64转码相关的方法：
1. `btoa()` 转换为base64编码
2. `atob()` base64编码转换为原来的值
```
    var str = 'xxcc30'

    btoa(str)    //eHhjYzMw

    atob(eHhjYzMw) //xxcc30
```
一般对用于个人的信息编码，主要是为了恶意爬虫爬自己的信息<br>
*注意的是这两种原生的方法不支持中文的编译*


---

### `Object`对象就是一种无序的数据集合，由若干个‘键值对（key-value）’构成，key是对象的属性，value可以是任何JS的类型，也可以是对象：
```
    var obj = {
        name:'abc',
        age: 2
    }
```
Object的属性读取的两种方式：
```
    obj.name
    obj['name']
```
如果键名不符合标识符的命名条件，且也不是数字，则必须加上引号：
```
    var obj = {
        1P:'helloworld'
    }  // 错误
    var obj  = {
        '1p':'helloworld'
    } //正确
```

如果一个属性的值还是对象，那么就可以形成链式引用
```
    var o1 = {};
    var o2 = { bar: 'hello' }

    o1.foo = o2;
    o1.foo.bar //'hello'
```
对象`o1`的属性`foo`指向对象`o2`，就可以链式引用`o2`的属性

---
### 运算符
运算符不同的含义，例如`+`:
```
    1+1 = 2
    
    1+'1' = 11
    
    obj = {a : 1 , b : 2 }
    obj+3 //[object Object]3

    obj = {
        a: 1,
        b: 2,
        valueOf: function(){
            return 100;
        }
    }
    obj+ 3 // 103

```
* 当符号两边都是数字，执行加法运算
* 当符号两边有一遍是字符串时，执行字符串连接的操作
* 在参数有对象的情况下调用`valueOf`或者`toString`
* 只有一个数字参数时，返回其正数值

比较运算符<br>
比较运算符比较两个值，然后返回一个布尔值，表示是否满足比较条件。
* `==`&ensp;&ensp;相等
* `===`&ensp;&ensp;严格相等（先比较类型，在比较具体的值）
* `!=`&ensp;&ensp;严格不相等
* `<`&ensp;&ensp;小于
* `<=`&ensp;&ensp;小于等于
* `>`&ensp;&ensp;大于
* `>=`&ensp;&ensp;大于或等于 
