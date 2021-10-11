---
layout: post
title: 【Python基础9】列表元祖字典集合的区别
date: 2020-12-29 09:20:23 +0800
category: Python 
---


列表、元组、字典和集合都属于Python3中的标准数据类型。这些数据类型彼此略有不同，因此了解代码使用哪种数据类型对于提高代码的质量和效率非常重要。我们来看看。
## 列表
列表是一个有序的可重复的可变对象集合，可以使用方括号[]将值放入其中，列表中的值是有序且可更改的，可以在一个列表中放置多种数据类型，如数字、字符串和布尔值。

```python
list_of_shoes = ["Adidas", "Reebok", "Nike"]
```
要访问列表中的值，必须使用索引号，例如我们向访问列表中的第二个值，我们需要使用索引号1(计算机从0开始计数)，如下：
```python
>>> list_of_shoes[1]
'Reebok' # 输出
```
同时也可以修改列表中的值，比如要修改列表中的第三项：
```python
>>> list_of_shoes[2] = 'Asics'
>>> list_of_shoes
['Adidas', 'Reebok', 'Asics'] # 输出
```
## 元组
元组是一个有序的可重复的不可变的对象集合，它使用小括号()来输入值。
```python
tup=('香蕉','苹果','葡萄')
```
与列表相比的主要区别是元组是不可变的，这意味着元组中的值不能更改、添加或删除
```python
>>> tup=('香蕉','苹果','葡萄')
>>> tup[2] = '西瓜'
# 抛出异常
Traceback (most recent call last):
  File "<input>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
```


## 字典
字典是无序的、无索引的键值对集合，使用大括号{}将键值放入其中，键是数据的输入，值是要使用的实际数据
```python
my_dictionary = {
  "age": 24,
  "location": "Tokyo",
  "favorite_food": "ramen"
}
```
可以使用键访问字典中的值
```python
>>> my_dictionary["age"]
24 # 输出
```
还可以使用键修改字典中的值：
```python
>>> my_dictionary["age"] = 31
>>> my_dictionary["age"]
31 # 输出
```

##  集合
集合是一种无序、无索引的数据类型，使用大括号{},这意味着不能使用索引号访问里面的数据
```python
games = {"战地", "堡垒之夜", "使命召唤"}
```
要访问集合中的数据必须使用for循环：
```python
games = {"战地", "堡垒之夜", "使命召唤"}
for x in games:
    print(x)

# 输出
堡垒之夜
使命召唤
战地
```
集合中的值不能更改，但可以使用add()和remove()添加和删除



## 总结

|  数据类型         | 是否可变  | 是否重复 |  是否有序 |  定义符号 |
|  :--:           | :--:     | :--:   | :--:    | :--:    |
| 列表(list)       | 可变      |可重复    |有序    |[]   |
| 元祖(tuple)      | 不可变    |可重复    |有序    |()    |
| 字典(dictionary) | 可变      |可重复    |无序    |{key:value}    |
| 集合(set)        | 可变      |不可重复    |无序    |{}或([])   |

