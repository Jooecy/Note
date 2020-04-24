---
title: urllib库的使用
date: 2020-04-24
description: "`urllib`库是Python内置的`HTTP`请求库，它包含四个模块"
categories:
- Python笔记
tags:
- urllib
- 爬虫
---
`urllib`库是Python内置的`HTTP`请求库，它包含四个模块：



1. `request`：最基本的`HTTP`请求模块
2. `error`：异常处理模块
3. `parse`：工具模块
4. `robotparser`：识别`robots.txt`

使用`urllib`库，我们只需要关心请求的链接和需要传的参数是什么，以及设置请求头。不需要深入到底层去了解它。