# HTTP（超文本传输协议）入门
* URL简介
* DNS&hosts
* 请求
* 响应

----

## URL简介
* URI 俗称网址
* HTTP 两个电脑之间传输内容的协议
* HTML 超级文本，主要用来做页面跳转<br>
能让你访问一个页面，HTTP作用是你让你下载这个页面，HTML的作用是让你看懂这个页面<br>

URI:URL+URN(统一资源定位符+统一资源名称)，我们一般使用URL作为网址。<br>
URL:`https://www.baidu.com/s?wd=hello&rsv_spt=1#5`<br>
通过URL你可以确定一个唯一的网址<br>
协议：`https://`<br>
域名：`www.baidu.com`<br>
路径：`/s`<br>
查询参数：`?wd=hello&rsv_spt=1` &ensp;&ensp;//以？开始，以&链接<br>
锚点：`#5`<br>
顶级域名：`.com` &ensp; 二级域名：`baidu` &ensp;三级域名：`wwww`

---

## DNS:Domain Name System
* 输入域名
* 输出IP

nslookup baidu.com<br>
ping baidu.com&ensp;&ensp;&ensp;&ensp;//查看域名的IP地址的方法<br>
当然也可以设置固定IP访问域名地址：<br>
Mac电脑通过：`sudo vi /etc/host`设置指定域名地址<br>
`eg: 127.0.0.1 baidu.com`<br>
Windows电脑通过：修改host文件来进行设置<br>

----

## 请求
![请求和响应](https://i.loli.net/2018/03/19/5aaf2417d4da4.png)
`Server+Client+HTTP`<br>
21:FTP协议端口<br>
443:HTTS协议端口<br>
1080:代理服务器端口<br>
80:HTTP协议端口<br>
* 浏览器负责发起请求
* 服务器在80端口接受请求
* 服务负责返回内容（响应）
* 浏览器负责下载响应内容

HTTP作用就知道浏览器和服务器如何沟通

命令行实现下面的请求示例：<br>
* GET请求内容为：<br>
 `curl -s -v -H "abc:china" -- "https://www.baidu.com"`<br>
`-s`:不要显示进度<br>
`-v`:显示请求和响应<br>
`"abc:china"`:添加一个请求头<br>
` -- "https:www.baidu.com"`：要请求的网址<br>
* 大致图像：
![QQ图片20180319110243.png](https://i.loli.net/2018/03/19/5aaf28e69a9e6.png)
请求部分对应的意思：<br>
(1) 获取 根目录内容 使用HTTP协议1.1版本<br>
(2) ///<br>
(3) 使用curl，版本7.56.0发起的请求<br>
(4) 接受发送的请求<br>
(5) 请求头<br>

* POST请求内容：<br>
`curl -X POST -s -v -H "abc:china" --- "https://www.baidu.com"`<br>
结果与上述请求部分一致：唯一的区别就是第一句话的`GET`替换成了`POST`<br>

* POST带上传内容的请求：<br>
命令为：`curl -X POST -d "1234567890" -s -v -H "Frank: xxx" -- "https://www.baidu.com"`<br>

请求内容为：
```
POST / HTTP / 1.1
Host: www.baidu.com
User-Agent:curl/7.54.0
Accept: */*
Frank:xxx
Content-Length: 10
Content-Type: application/x-www-form-urlencoded

123456789
```
上传的长度为：10<br>
上传的格式为：application/x-www-form-urlencoded<br>

GET/POST 获取内容 /上传内容<br>

请求的格式：<br>
1&ensp;&ensp;  动词 路径  协议 版本<br>
2&ensp;&ensp;  key1: value1<br>
2&ensp;&ensp;  key2: value2<br>
2&ensp;&ensp;  key3: value3<br>
2&ensp;&ensp;  Content-Type: application/X-www-form-urlencoded<br>
2&ensp;&ensp;  Host: www.baidu.com<br>
2&ensp;&ensp;  User-Agent: curl/7.54.0<br>
3 <br>
4&ensp;&ensp; 要上传的数据

注意事项：
* 请求最多包含4部分，最少3部分，第四部分可以为空<br>
* 第三部分永远都是一个回车
* 动词可以是：GET / PUT / PATCH / DELETE /  HEAD / OPTIONS（获取、请求、上传更新、局部更新、删除）
* 这里的路径包含查询参数，但是不包含锚点
* 如果没有写路径，路径默认为 /
* 第二部分Content-Type实际为第四部分的格式

* 使用chrome发送请求：
1. 打开`Network`
2. 地址栏输入网址
3. 在NetWork点击，查看`requeset`,点击`view source`
4. 如果有请求的第四部分，那么在 FormData 或 Payload 里面可以看到

## 响应
第一个GET请求响应对应
```
    HTTP/1.1  200 OK
    Accept-Ranges: bytes
    Cache-Control: private,no-cache,pro-revalidate,no-transform
    Connection:Keep-Alive
    Content-Length: 2443
    Content-Type: text/html
    Date: Tue,10Oct 2017 09:14:05 GMT
    Etag: "5886041d-98b"
    Last-Modified:Mon,23 Jan 2017 13:24:25
    Pragma: no-cache
    Server: bfe/1.0.8.18
    Set-Cookie: BDDRZ=27315;max-age=86400;domain=.baidu.com ; path=/
```
第二个POST请求响应对应：
```
    HTTP/1.1 302 Found
    Connection: Keep-Alive
    Conetent-Length:17931
    Conetent-Type: text/html
    Date: Tue,10 Oct 2017 09:19:47 GMT
    Etag: "55d9749e-460b"
    Server: bfe/1.0.8.18
```
响应的格式：
1 &ensp;&ensp;  协议/版本号  状态码  状态解释
2 &ensp;&ensp;   key1:      value1
2 &ensp;&ensp;   key2:       value2
2 &ensp;&ensp;   Content-Length: 17931
2 &ensp;&ensp;   Content-Type: text/html
3 <br>
4 要下载的内容<br>
* 状态码：服务器对浏览器说的话
* 1xx
* 2xx
    * 200 访问成功
* 3xx
    * 301 永久性出现问题
    * 302 暂时性出现问题
* 4xx
    * 404 浏览器出现错误
* 5xx
    * 502 服务器出现错误

第二部分的Contet-Type标注了第4部分的格式
第二部分的Content-Type遵循MIME规范


