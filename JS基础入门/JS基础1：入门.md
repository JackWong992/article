# JavaScript入门基础
---
* 标识符
* 命名规范
* 变量&ensp;&ensp;>&ensp;&ensp;变量提升
* 语句
* 注释
* 浏览器渲染原理&ensp;&ensp;>&ensp;&ensp;白屏
* 加载异步
* 基本调试

### 标识符
所谓的标识符就是指变量、函数、属性的名字，或者函数的参数。
标识符书写的规则：
1. 不能出现关键字
2. 首字母不可以出现数字
3. 后面可以是`数字、下划线、$`

---

### 命名规范
1. 使用具有实际意义的单词（例如：getXX，postXX）
2. 推荐你使用驼峰的写法（首字母小写，后面单词首字母大写），当然也可以是匈牙利写法
3. 变量尽量使用名词，方法函数最好以动词开始，常量全部使用大写字母，函数创建对象首字母要大写
```
    var firstName;
    var IsSmall;
    var PI;
    var Max_Count;
    function getName(){}
    function Person(){}
```
---

### 变量
在JavaScript中变量是用来保存值的占位符，定义变量的时候要使用`var`运算符，后面要跟随标识符
```
    var a;
    var b;
    var message;
```
JavaScript是一种弱类型的语言，不同与C,Java声明或者定义一种变量必须要指定变量的类型，而在JavaScript中一个变量可以保存任何类型的数据。
#### 变量的提升
JavaScript引擎的工作方式是，先解析代码，获取被声明的变量，然后在一行行的运行。实际的含义是：所有被声明的语句都会被提升到作用域的头部，这就是变量的提升。
```
    var a=1
    var b=2

    console.log(a)
    console.log(b)
```
实际工作流程：
```
    var a             //undefined
    var b             //undefined  
    a=1
    b=2
    console.log(a)     //1
    console.log(b)     //2
```
例如：
```
    var a=100
    var b=200
    
    console.log(a)   //100
    console.log(d)  // undefined

    var d=100
```

---

### 语句
在JavaScript中`var a=1;`这样我们可以称之为语句
1. 语句以`;`为结束，当然如果你不写`;`也不会报错
2. 一行中可以出现多个语句

---

### 注释
在JavaScript中注释可以有三种方式（多行，单行）
1. 单行注释 //
2. 单行注释 \<!-- 
3. 多行注释  /* */
4. 单行注释 -->

*需要注意的是，第四种注释需要写在一行的开头，否则就会被当成运算符（自减 大于）*

---

### 浏览器渲染的原理
JavaScript是客户端脚本语言

网页=html+css+JavaScript<br>
HTML：网页元素内容<br>
CSS： 控制网页元素的样式<br>
JavaScript： 实现网页功能或者效果<br>

渲染大致过程：
* 解析HTML标签，构建DOM树
* 解析CSS标签，构建CSSOM树
* 把DOM和CSSOM组合成渲染树（render tree）
* 在渲染树的基础上进行布局，计算每个节点的几何结构
* 把每个节点绘制到屏幕上

![](https://i.loli.net/2018/04/03/5ac2db598bcf9.png)



### 白屏问题
如果把样式放在底部，对于IE浏览器来说，在某些场景下（新窗口打开）页面会出现白屏，而不是内容逐步实现<br>
如果使用@import标签，即使CSS引入link，并且放在头部，也可能出现白屏。
* 所以应该将JavaScript放在底部（</body>之前）
1. 脚本会阻塞后面内容的实现
2. 脚本会阻塞其后组件的下载

对于图片和CSS，在加载时会并发加载（如一个域名下同时加载两个文件）但在加载JavaScript的时候，会禁用并发<br>
阻止其他内容加载，所以把JavaScript放在页面的顶部也会出现白屏现象

---

### 加载异步
```
    <script src="script.js"></script>

    <script async src="script.js"></script>

    <script defer src="script.js"></script>
```
* 没有`defer`和`async`，浏览器会立即加载并执行指定的脚本
* 有`async`,加载和渲染后续文档元素的过程将和`script.js`的加载与执行并行进行
* 有`defer`加载后续文档元素的过程中和`script.js`的加载并行进行<br>

defer: 脚本迟到文档解析和显示后执行，有顺序<br>
async：不保证顺序<br>

---

### 基本调试
* alert()
* console.log()
* debugger
* 二分法

推荐使用`console.log()`,不会直观的影响你的观察效果<br>
不推荐使用`alert()`,会影响用户体验<br>
二分法其实也是`console.log()`的一种延伸  <br>