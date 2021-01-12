---
title: 创建Django应用
date: 2021-01-11
weight: 2
description: 创建Django应用
categories:
- 项目
tags:
- Django
---
现在我们就可以在虚拟环境中创建Django项目了。
## 安装Django
使用如下命令安装Django最新版本：
```
(sxb_env) C:\Users\xiaoxi\Desktop\sxb_env>pip install django
```
## 创建Django应用
现在创建一个名为sxb的Django项目：
```
(sxb_env) C:\Users\xiaoxi\Desktop\sxb_env>django-admin startproject sxb
```
这时在虚拟环境`sxb_env`中会创建一个名为`sxb`的文件夹，这便是我们的Django项目文件夹。

进入sxb文件夹：
```
(sxb_env) C:\Users\xiaoxi\Desktop\sxb_env> cd sxb
(sxb_env) C:\Users\xiaoxi\Desktop\sxb_env\sxb>
```
接下来使用管理文件`manage.py`来创建第一个APP：
```
(sxb_env) C:\Users\xiaoxi\Desktop\sxb_env\sxb> python manage.py startapp webapp
```
`webapp`应用已经创建成功：
接下来我们就可以去编辑简单的应用模型了。
