---
title: requests高级用法
date: 2020-04-24
weight: 16
description: requests的高级用法包括如：文件上传、Cookies设置、代理设置、会话维持、超时设置等。
categories:
- Python笔记
tags:
- requests
---

requests的高级用法包括如：文件上传、Cookies设置、代理设置、会话维持、超时设置等。
## 文件上传
```python
import requests


files = {'file':open('logo.png','rb')}
r = requests.post('http://httpbin.org/post',files=files)
print(r.text)
```
首先创建一个表示文件的字典：files，它的键为file，值为使用open()函数`'rb'`模式打开的待上传文件。之后在post方法中传递参数files,值为files字典。

## Cookies
