---
title: if语句
date: 2020-04-24
description: "`if`语句可以检查程序的当前状态，本据此采取相应的措施。"
toc: true
categories:
- Python笔记
tags:
- if语句
---
`if`语句可以检查程序的当前状态，本据此采取相应的措施。
## if语句的简单示例
```python
a = ['joecy','wang']
for i in a:
    if i == 'joecy':
        print(i.title())
```
输出：
```python
Joecy
wang
```
在这个`for`循环中，`if`语句来检测，所遍历的元素是否为`joecy`，如果是，就对其使用方法`title()`。


## 条件测试
每条`if`语句的核心都是一个值为`True`或`False`的表达式，这种表达式被称为`条件测试`（`布尔表达式`）。例如`i = 'joecy'`，Python根据条件测试的值为`True`或`False`来决定是否执行`if`语句中的代码：

```python
>>> car = 'bwm'

#检查是否相等

>>> car == 'bwm' 
True
>>> car == 'Bwm'
False


#检查是否不相等

>>> car != 'audi' 
True


#比较数字

>>> a = 18
>>> a == 18
True
>>> a > 10
True
>>> a < 9
False
>>> a != 3
True

#使用and检查多个条件，条件同时成立为True
>>> car == 'bwm' and a == 18
True
>>> car != 'audi' and a == 18
True


#使用or检查多个条件，只要有一个条件成立就为True

>>> car == 'bwm' or a != 18
True


#检查特定值是否包含其中

>>> b = [1,2,3,4,6]
>>> 1 in b
True
>>> 5 in b
False


#检查特定值是否包含其中

>>> 5 not in b
True
>>> 3 not in b
False

```
## if语句
最简单的`if`语句只包含一个条件测试表达式和一个操作：
```python
if test:
    do something
```
例如：
```python
age = 18
if age >= 18:
    print('你已经长大了！')
```
### if-else语句
`if-else`语句用来在条件测试通过时执行一个操作，在不通过时执行另一个操作。
```python
age = 18
if age >= 18:
    print('你已经长大了！')
else:
    print('你还没有成年呢！')
```
### if-elif-else语句

但我们需要检查多个条件时，可使用`if-elif-else`语句，Python将只执行其中的一个代码块，它一次检查，直到遇到通过测试的条件。
```python
age = 12
if age < 4:
    print('无需购票')
elif age < 18:
    print('虽然没成年，但是得买票了。')
else:
    print('买票吧')
```

可根据实际情况使用`任意数量的elif代码块`。
有时候需要`省略else代码块`，使用`elif`代码块处理更有效。因`为else`语句，只要不满足任何`if`或`elif`中的条件测试，其中的代码块就会执行。同理很多时候我们也需要仅`舍弃elif语句和else语句`使用`if`语句来测试条件。
