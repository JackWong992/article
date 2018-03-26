# jQuery基础语法2
* wrap(),wrapAll()包装对象
## wrap(),wrapAll()
用于元素的包装对象，可以想象成在元素的外边套上一个你想要的盒子<br>
```
    $('span').wrap('<div>');
```
[`wrap()`与`wrapAll()`区别](http://js.jirengu.com/wugawavepi/2/edit)<br>
* wrapInner()内部元素包装<br>
* unwrap():删除包装，相当于删除父节点<br>
//这里要注意的unwrap是不会删除body的
[`wrap`的实例操作](http://js.jirengu.com/mexayafano/1/edit)

### `get()`把jQuery转成原生JS
```
html: <div>aaa</div>
Js: 
alert( $('div').get(0).innerHTML);
```
转换成原生的时候需要注意是`get()`转换的是一个结合，即使是一个单独的元素也要加上下标。<br>
`eq()`与`get()`都是指代集合，`eq()`与`get()`不同的是：get后面可以接原生JS代码，而eq则只能接jQ的代码。<br>