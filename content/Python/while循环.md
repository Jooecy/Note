---
title: while循环
date: 2020-04-24
weight: 6
description: Python的循环有两种，一种是`for...in`循环，依次把`list`或`tuple`中的每个元素迭代出来
categories:
- Python笔记
tags:
- while
- 循环
---

Python的循环有两种，一种是`for...in`循环，依次把`list`或`tuple`中的每个元素迭代出来，第二种循环是`while`循环，只要条件满足，就不断循环，条件不满足时退出循环。
### 使用while循环
下面的例子是使用`while`循环计算100以内奇数和：
```python
a = 0
b = 99
while b > 0:
	a = a + b
	b = b -2
print(a)
```
### 让用户选择何时退出
```python
message = ''
while message != 'q':
	message = input()
	if message != 'q':
		print(message)
```
上面的示例代码，在用户输入`q`是退出循环，否则将循环执行打印用户输入的操作。`if`语句使用户在输入退出指令`q`时，不至于将`'q'`打印出来。

### 使用标志
```python
active = True
message = ''
while active:
	message = input()
	if message == 'q':
		active = False
	else:
		print(message)
```
我们将条件测试都放在其他地方，`while`语句就只需要检查一个条件。从而可以使用程序更加的简洁易读。

### 使用break退出循环
`break`语句可以提前结束循环，例如上一个例子，可以这样改写：
```python
while True:
	message = input()
	if message == 'q':
		break
	else:
		print(message)
```

### 使用continue
在循环中可以使用`continue`语句跳过当次循环，并执行下一次循环。`continue`语句不会像`break`语句那样不再执行余下的代码。
```python
a = 0
while a < 10:
	a = a + 1
	if a % 2 == 0:
		continue
	print(a)
```
`break`语句可以在循环过程中直接退出循环，而`continue`语句可以提前结束本轮循环，并直接开始下一轮循环。这两个语句通常都必须配合`if`语句使用。

要特别注意，不要滥用`break`和`continue`语句。`break`和`continue`会造成代码执行逻辑分叉过多，容易出错。大多数循环并不需要用到`break`和`continue`语句，上面的两个例子，都可以通过改写循环条件或者修改循环逻辑，去掉`break`和`continue`语句。

### while循环处理列表和字典
`for`循环是遍历列表的有效方式，但不该在`for`循环中修改列表，例如移动元素的操作，因为这会导致Python无法跟踪其中的元素。然而使用`while`循环就可以在遍历时对列表进行修改。
### 在列表间移动元素
```python
l1 = [1,2,3,4]
l2 = []
while l1:
	l = l1.pop()
	l2.append(l)
print(l1)
print(l2)
```
输出：
```python
[]
[4, 3, 2, 1]
```
可见，列表`l1`中的元素已经移动到列表`l2`中了。

### 删除包含特定值的所有列表元素

```python
l = [1,2,1,3,1,4,5,1]
while 1 in l:
	l.remove(1)
print(l)
```
输出：
```python
[2, 3, 4, 5]
```
### 使用用户输入填充字典
```python
d = {}
active = True
while active:
	a = input('name')
	b = input('answer')
	d[a] = b
	c = input('是否继续？y,n')
	if c == 'n':
		active = False
for i,j in d.items():
	print(i,j)
```
我们让用户输入姓名和答案并将其存储在字典`d`中，然后询问用户是否继续，当用户输入`n`时，标志`active`为`False`，`while`循环结束，并打印结果。
