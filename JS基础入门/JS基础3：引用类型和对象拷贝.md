# JS基础3：引用类型和对象拷贝
* 引用类型
* 简单类型和复杂类型之间的存储
* 内存图
  * 经典面试题&垃圾回收 
* 对象拷贝

## 引用类型
* 基本类型:(数值，布尔值，null，undefined)指的是保存在栈内存中的简单数据段；
* 引用类型值：(对象，数组，函数，正则)：指的是那些保存在栈内存中的对象，变量中保存的实际只是一个指针，这个指针执行内存中的另一个位置，由该位置保存对象
### 简单类型和复杂类型之间存储：
* 简单类型存在`stack（栈）`
* 复杂类型存在于`Heap(堆)`，将地址存入`stack`<br>
要注意的是：对于复杂类型来说，存入的`stack地址`和`Heap`之间的关系是引用。<br>
其中简单数据类型的代表有：number,null,undefined,symbol,boolean<br>
复杂数据类型的代表有：object(array,function,正则表达式)<br>
string比较复杂不做研究,既可以是栈内存也可以是堆内存<br>
### 内存图
![image.png](https://upload-images.jianshu.io/upload_images/6071779-5c865f5fd901112d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
var a={name:'a'}
var b=a
b.name='b'
a.name=?
```
![image.png](https://upload-images.jianshu.io/upload_images/6071779-f4b39b5af513cdda.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
var a={name:'a'}
var b=a
b=null
a.name=?
```
![image.png](https://upload-images.jianshu.io/upload_images/6071779-48ee2a0353ca6782.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
#### 经典面试题
```
var a={n:1};
var b=a;
a.x=a={n:2}

alert(a.x);?
alert(b.x);?
```
![image.png](https://upload-images.jianshu.io/upload_images/6071779-d19d94eb1b35c35c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 垃圾回收机制<br>
如果一个对象没有被引用，它就是垃圾，就将被回收
![image.png](https://upload-images.jianshu.io/upload_images/6071779-deba44bbca2d3eb0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
var fn=function(){}
document.body.onclick = fn

fn=null
function(){} 是不是垃圾？
```
![image.png](https://upload-images.jianshu.io/upload_images/6071779-50e2090a6db6db4e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 对象拷贝
浅拷贝VS深拷贝
```
var a=1
var b=a
b=2
// a=1 b=2
```
* b的改变并不会影响a的变化，这种现象就叫深拷贝<br>
对于所有的基本类型，进行简单的赋值都是深拷贝现象<br>
对于复杂类型，来说：<br>
```
 var a={
     name:'a';
 }
 var b=a;
 b.name='b'
 a.name //结果也是'b'
```
* 这种b的改变影响了a的变化，这种现象就叫浅拷贝