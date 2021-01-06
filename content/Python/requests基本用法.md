---
title: requests基本用法
date: 2020-04-24
weight: 15
description: 基本的GET、POST请求方法 
categories:
- Python笔记
tags:
- requests
- 爬虫
---

基本的GET、POST请求方法 

### GET请求

`HTTP`中最常见的请求之一就是`GET`请求，用`requests`构建`GET`请求非常方便。

#### 使用requests.get()


```python
import requests
r = requests.get('https://baidu.com/')
print(type(r))
print(type(r.text))
print(r.status_code)
print(r.cookies)
print(r.text)
```
输出：


```python
<class 'requests.models.Response'>
<class 'str'>
200
<RequestsCookieJar[<Cookie BDORZ=27315 for .baidu.com/>]>
# 部分代码
<!DOCTYPE html>
<!--STATUS OK--><html> <head>
....
 </body> </html>
```
使用`requests.get()`方法，即可以`GET`方式请求网页。
- `status_code`属性获取`状态码`
- cookies属性获取`cookies`
- text属性获取`网页内容`
- `headers`属性获取`响应头`
- `url`属性获取`URL`
- `history`属性获取`请求历史`
- 等等......


如果GET请求需要附加额外信息，例如添加两个参数：

`r = requests.get('http://httpbin.org/get?name=joecy&age=24')`

如果写成这样未免太繁琐，这时可以利用params参数：

```python
import requests

data = {'wd':'我'}
r = requests.get('https://baidu.com/s',params=data)

print(r.status_code)
r.encoding = 'utf-8'
print(r.text)

```
> `r.encoding = 'utf-8'`  用于修改编码

输出了百度关于关键词“我”的搜索结果。


#### 抓取网页

抓取知乎发现页面：
```python
import requests

r = requests.get('https://www.zhihu.com/explore')

print(r.status_code)
r.encoding = 'utf-8'
print(r.text)
```



结果

```python

400
<html>
<head><title>400 Bad Request</title></head>
<body bgcolor="white">
<center><h1>400 Bad Request</h1></center>
<hr><center>openresty</center>
</body>
</html>
```
由于没有传递请求头，不能够正常抓取知乎发现页。

添加`headers`：


```python
import requests
headers = {
    'User-Agent':'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/68.0.3440.75 Safari/537.36'
}
r = requests.get('https://www.zhihu.com/explore',headers=headers)

print(r.status_code)
r.encoding = 'utf-8'
print(r.text)

```
这样就可以正常抓取了。

#### 抓取二进制数据

抓取一个网页页面，实际上返回的是一个`HTML文档`，图片、音乐、视频等二进制文件需要写入文件才可以获取到：

以抓取百度logo为例：


```python
import requests
headers = {
    'User-Agent':'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/68.0.3440.75 Safari/537.36'
}
r = requests.get('https://www.baidu.com/img/bd_logo1.png',headers=headers)


print(r.text)
print(r.content)

```


```
KaPq�����o�L !��B�;��|���wx��v��yk���5?�r�{(�(I��W.����KX����jsj�!:��{&�2{,�px��&9��^gRݩ�΍�p�p �p �� �p �p ��p ���5���B �=B�IEND�B`�

b'\x89PNG\r\n\x1a\n\x00\x00\x00\rIHDR\x00\x00\x02\x1c\x00\x00\x01\x02\x08\x03\x00\x00\x00\x82\x14\xfe8\
```

打印`r.text`时出现乱码，是因为在打印时，它将图片直接转换为`'str'`，所以乱码。
打印`r.content`时，打印出来的是`'b'`开头的`bytes`类型的数据。

接着我们保存图片：


```python
import requests
headers = {
    'User-Agent':'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/68.0.3440.75 Safari/537.36'
}
r = requests.get('https://www.baidu.com/img/bd_logo1.png',headers=headers)


with open('logo.png','wb') as f:
    f.write(r.content)

```
将二进制数据以*二进制写的形式*（`'wb'`）写入指定的文件（`logo.png`），就可以保存这个图片了。

同样的，视频和音频文件都可以这样保存。

### POST请求



使用`requests`实现`POST`请求一样很简单。

#### 使用requests.post()


```python
import requests

data = {
    'name':'joecy',
    'age':'24'
    }
r = requests.post('http://httpbin.org/post',data=data)
print(r.text)

```

#### 对比响应码

常见的响应码包括：

200、302、404、500等，我们经常需要通过响应码判断请求状态，requests内置了一个状态码查询对象：`requests.codes`：


```python
import requests

r = requests.get('https://baidu.com')
if r.status_code == requests.codes.ok:
    print("请求成功")
    
```
> 参考：[常见的返回码和查询条件](https://#/)




