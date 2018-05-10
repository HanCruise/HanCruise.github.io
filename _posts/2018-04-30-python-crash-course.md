---
layout: post
title:  "python crash course 笔记"
categories: python
tags:  python 笔记
author: HanCruise
---

* content
{:toc}

#### 注释
1. 井号 #
通常用来注释代码行
_comment.py_
```
# coding:utf-8
# 向大家问好
print("Hello Python people!")
```
2. 文档字符串 """..."""
通常用来注释文档交代文档功能，及函数、类。
_comment.py_
```
"""add comments"""
print("Hello Python people!")
```




#### 常用方法  
1. 切换大小写的三个方法：title()/upper()/lower()
三个方法均不改变原字符串的值，可用来生成新字符串或显示。
_name.py_
```
name = "ada lovelace"
print(name.title())
print(name.upper())
print(name.lower())
```
_result:_
```
Ada Lovelace
ADA LOVELACE
ada lovelace
```
2. 添加或删除空白
添加空白常用：_空格space_/_制表符\t_/_换行符\n_
删除空白常用三个方法：rstrip()/lstrip()/strip()
这些方法可删除由前三种方法产生的空格
_blank_add_delete.py_
```
# add blank
print("Languages:\n\tPython\n\tC\n\tJavaScript")

# python 中 print 自带换行，此处打印空使其换一行
# 若如c使用 print('\n') 则会换两行，小技巧。
print('')

"""delete blank"""
favorite_language = '  python  '
print(favorite_language)

# 删除字符串末尾空白
print(favorite_language.rstrip())

# 删除字符串开头空白
print(favorite_language.lstrip())

# 删除字符串头尾空白，中间不能
print(favorite_language.strip())
```
_result:_
```
Languages:
	Python
	C
	JavaScript

  python
  python
python
python
```

#### 数字
1. 乘方
```
>>> 3 ** 2
9
>>> 3 ** 3
27
```
2. 整数
需要注意的是除法，python3 如下：
```
>>> 3 / 2
1.5
```
python2 的规则此处与 c 更接近，如下：
```
>>> 3 / 2
1
```
3. 浮点数
运算结果包含的小数位数是不确定的，一般为近似值，但足够精确，
此由计算机存储机制导致。
```
>>> 0.2 + 0.1
0.30000000000000004
>>> 3 * 0.1
0.30000000000000004
```
#### 列表操作
1. 访问元素
_motorcycles.py_
```
motorcycels = ['honda', 'yamaha', 'suzuki']
print(motorcycles)
print(motorcycles[0])
print(motorcycles[0].title())
print(motorcycles[-1])
motorcycles[0] = 'ducati'
print(motorcycles)
```
_result:_
```
['honda', 'yamaha', 'suzuki']
honda
Honda
suzuki
['ducati', 'yamaha', 'suzuki']
```
2. 添加元素
append()/insert()
_motorcycles.py_
```
motorcycles = ['honda', 'yamaha', 'suzuki']
print(motorcycles)
motorcycles.append('ducati')
print(motorcycles)
motorcycles.insert(0, 'bmw')
print(motorcycles)
```
_rusult:_
```
['honda', 'yamaha', 'suzuki']
['honda', 'yamaha', 'suzuki', 'ducati']
['bmw', 'honda', 'yamaha', 'suzuki', 'ducati']
```
3. 删除元素
del	删除任意位置列表元素
pop()	删除任意位置列表元素并返回，无参时默认删除表尾元素
remove()	根据值删除元素
```
motorcycles = ['honda', 'yamaha', 'suzuki']
print(motorcycles)

del motorcycles[0]
print(motorcycles)

motorcycles.insert(0, 'honda')
del motorcycles[1]
print(motorcycles)

motorcycles.insert(1, 'yamaha')
poped_motorcycle = motorcycles.pop()
print(motorcycles)
print(poped_motorcycle)

motorcycles.append('suzuki')
motorcycles.remove('honda')
print(motorcycles)
```
_result:_
```
['honda', 'yamaha', 'suzuki']
['yamaha', 'suzuki']
['honda', 'suzuki']
['honda', 'yamaha']
suzuki
['yamaha', 'suzuki']
```
4. 组织列表
sort()	方法，对列表永久性排序
sorted()	函数，对列表进行临时排序
_cars.py_
```
cars = ['bmw', 'audi', 'toyata', 'subaru']
print(cars)
print(sorted(cars))
print(sorted(cars, reverse=True))

print(cars)
cars.sort()
print(cars)
cars.sort(reverse=True)
print(cars)
```	
_result:_
```
['bmw', 'audi', 'toyata', 'subaru']
['audi', 'bmw', 'subaru', 'toyota']
['toyota', 'subaru', 'bmw', 'audi']
['bmw', 'audi', 'toyata', 'subaru']
['audi', 'bmw', 'subaru', 'toyota']
['toyota', 'subaru', 'bmw', 'audi']

```
5. 倒着打印列表
reverse() 方法，反转列表元素的排列顺序
_cars.py_
```
cars = ['bmw', 'audi', 'toyota', 'subaru']
print(cars)
cars.reverse()
print(cars)
```
_result:_
```
['bmw', 'audi', 'toyota', 'subaru']
['subaru', 'toyota', 'audi', 'bmw']
```
6. 表长
len() 函数，统计列表元素的个数
```
>>> cars = ['bmw', 'audi', 'toyota', 'subaru']
>>> len(cars)
4
```
7. 列表解析
快速生成列表
_squares.py_
```
squares = [value**2 for value in range(1, 11)]
print(squares)
```
_result:_
```
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
8. 切片
处理列表的部分元素
_players.py_
```
players = ['charles', 'martina', 'michael', 'florence', 'eli']
print(players[0:3])
print(players[1:4])
print(players[:4])
print(players[2:])
print(players[-3:])
```
_result:_
```
['charles', 'martina', 'michael']
['martina', 'michael', 'florence']
['charles', 'martina', 'michael', 'florence']
['michael', 'florence', 'eli']
['michael', 'florence', 'eli']
```
切片的用途：
操作列表部分元素
列表复制
```friend_foods = my_foods[:]```



#### 常用函数
1. str()
将非字符串值表示为字符串
_birthday.py_
```
age = 23;
message = "Happy " + str(age) + "rd Birthday!"
print(message)
```
_result:_
```
Happy 23rd Birthday!
```
2. range()
生成一系列的数字
格式：range(x1, x2)
结果：x1, x, ... x2-1，不会生成x2
_numbers.py_
```
for value in range(1, 5):
	print(value)
```
_result:_
```
1
2
3
4
```
3. list()
将结果转换成列表
_numbers.py_
```
numbers = list(range(1, 6))
print(numbers)
```
_result:_
```
[1, 2, 3, 4, 5]
```
4. min()/max()/sum()
处理数字列表的几个函数，参数为列表名，输出相应元素
```
>>> digits = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> min(digits)
0
>>> max(digits)
9
>>> sum(digits)
45
```
5. items()/keys()/values()
用于字典遍历的三个函数
items()		用于遍历键值对
keys()		用于遍历键
values()	用于遍历值
_user.py_
```
user_0 = {
	'username': 'efermi',
	'first': 'enrico',
	'last': 'fermi',
	}

for key, value in user_0.items():
	print("\nKey: " + key)
	print("Value: " + value)
```
_result:_
```
Key: username
value: efermi

Key: first
value: enrico

Key: last
value: fermi
```
_favorite_languages.py_
```
favorite_languages = {
	'jen': 'python',
	'sarah': 'c',
	'edward': 'ruby',
	'phil': 'python',
	}

for name in favorite_languages.keys():
	print(name.title())
print('')
for name in sorted(favorite_languages.keys()):
	print(name.title())
print('')
for language in sorted(favorite_languages.values()):
	print(language.title())
```
_result:_
```
Jen
Sarah
Edward
Phil

Edward
Jen
Phil
Sarah

c
python
python
ruby
```
6. input()
input() 将输入解读为字符串
_parrot.py_
```
message = input("Tell me a number, and I'll repeat it back: ")
print(message)
```
_result:_
```
>>> Tell me a number, and I'll repeat it back: 1
1
```
7. int()
将数字的字符串表示转换为数值表示
```
>>> age = input("How old are you? ")
How old are you? 21
>>> age = int(age)
>>> age >= 18
True
```
8. set()
找到列表中独一无二的元素，并使用这些元素来创建一个集合
_favorite_languages.py_
```
favorite_languages = {
	'jen': 'python',
	'sarah': 'c',
	'edward': 'ruby',
	'phil': 'python',
	}

print("The following languages have been mentioned:")
for value in set(favorite_languages.values()):
	print(value.title())
```
_result:_
```
The following languages have been mentioned:
Ruby
Python
C
```
