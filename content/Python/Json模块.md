---
title: Json模块
date: 2020-04-24
weight: 10
description: 很多时候，我们需要保存用户提供的信息，一种简单的方式时通过模块json来存储数据。
categories:
- Python笔记
tags:
- json.load()
- json.dump()
---


很多时候，我们需要保存用户提供的信息，一种简单的方式时通过模块json来存储数据。

> JSON格式最初是为了JavaScript开发的，但随后成了一种常见格式，被众多编程语言采用。

### 使用json.dump()存储数据

使用`json.dump()`可以轻松的存储数据，`json.dump()`接受两个参数：要存储的数据以及可用于存储数据的文件==对象==，很多时候在提供第二个参数时，都会错误的提供了文件名称，而不是文件==对象==，例如：


```python
import json
username = '111'
with open('name.json','w') as name_obj:
    json.dump(username,name.json)
```
这时，就会报错：


```python
NameError: name 'name' is not defined
```
原因是我们错误向`json.dump()`传入了参数`name.json`，这并不是要存储数据的文件==对象==，应该传入参数`name_obj`。

```python
import json
username = '111'
with open('name.json','w') as name_obj:
    json.dump(username,name_obj)
```

同时，也要注意在使用`json.dump()`存储数据时，函数`open()`需要传递参数`'w'`，以便获得写入权限。

### 使用json.load()读取数据

同样的，使用`json.load()`时，传入的也是文件==对象==：

```python
import json

with open('name.json') as name_obj:
    username_tmp = json.load(name_obj)
print(username_tmp)
```
输出：
```python
111
```

