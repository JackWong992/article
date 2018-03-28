# 工具方法
* $.parseJSON()
* $.parseHTML()
* $.parseXML()
* $.isXMLDoc()

---

### $.parseJSON()
将JSON类型的字符串，转换成真正的JSON数据 
```
var a='{
    'name':'xiaoming',
    'age':"18"
    }'
var json=$.parseJSON(a);
console.log(json) //{'name':'xiaoming','age',18}
console.log(json.name) //'xiaoming'
```
但是这里要注意的是：转换为JSON类型的字符春，只针对严格的JSON，也就是说key，value值必须是""包裹<br>

### $.parseHTML()
将HTML类型的字符串，转换为真正的JSON数据
```
    var a='<span></span><div>div</div>';
    var ss=$.parseHTML(a);
    console.log(ss) //[span,div]
```
返回得到的是一个数组[span,div]<br>
当然也可以将这个数组添加到页面中：
```
    console.log(ss)
    $('body').append(ss)   //span div
```