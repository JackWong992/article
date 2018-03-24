# Math对象&&数组&&Date
* Math对象
* 数组
* Date
## Math对象
Math对象是JS的内置对象，提供了一系列的数学常数和方法。<br>
Math对象只提供了静态的属性和方法，所以使用时不用实例化

## 方法
### round
Math.round用于四舍五入
```
Math.round(0.1)  //0
Math.round(0.5)  //1

```
它对于负值的运算结果与正值略有不同，主要体现对.5的处理：
```
    Math.round(-11) //-1
    Math.round(-1.5) //-1
```
* abs,max,min<br>
abs方法是返回参数值的绝对值
```
    Math.abs(1) //1
    Math.abs(-1) //1
```
max方法返回最大的参数，min方法返回最小的参数
```
    Math.max(2,3,4) //4
    Math.min(2,4,5) //5
```
* floor,ceil<br>
floor方法返回小于参数值的最大整数
```
    Math.floor(2.98) //2
```
ceil方法返回大于参数值的最小整数
```
    Math.ceil(3.7) //4
``` 
* pow , sqrt<br>
pow方法返回以第一个参数为底数，第二个参数为幂的指数值<br>
```
    Math.pow(2,2)   //4
    Math.pow(2,3)   //8
```
sqrt方法返回参数值的平方根，如果参数第一个值为负数，返回为NaN<br>
```
    Math.sqrt(4)  //2
    Math.sqrt(-4) //-4
```
* log,exp<br>
log方法返回以e为底的自然对数值<br>
```
    Math.log(Math.E) //1
    Math.log(10) //2.30258509299
```
* random<br>
该方法返回一个0-1的随机数
使用random得到一个8位的随机字符
```
function random(a,b) {
    return a+ Math.floor(Math.random()*(b-a))
}  //得到一位a-b的随机字符（不包括b）
```
```
function randomStr(len) {
    var dict="0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ"
    var str='';
    for(var i=0; i<len;i++){
        str+=dict[random(0,62)]
    }
    return str
}
```
使用random()得到一个随机的IP地址： 0.0.0.0 ~ 255.255.255.255<br>
```
    function randomIP(len){
        var arr=[]
        for(var i=0;i<4;i++){
            arr.push(random(0,256))
        }
        return arr.join('.')
    }

```
## 数组
数组的创建有三种：
1. 无参数构造函数，创建一空数组
`var a1=new Array()`<br>
2. 一个数字参数构造函数，指定数组的长度，创建指定长度的数组
`var a2 = new Array(5)`<br>
*创建了一个长度为5的数组*<br>
3. 带有初始化数组的构造函数，创建数组并初始化的参数数据<br>
`var a3= new Array(4,'hello',new Date())`<br>
 


