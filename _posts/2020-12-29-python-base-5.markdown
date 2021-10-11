---
layout: post
title: 【Python基础5】数据类型-列表
date: 2020-12-29 05:20:23 +0800
category: Python 
---



Python中的数据结构是通过某种方式组织在一起的数据元素的集合，这些数据元素可以是数字、字符、甚至可以是其他数据结构，在Python中最基本的数据结构是序列（列表和元组），序列中的每个值都有对应的位置值，称之为索引，第一个索引是 0，第二个索引是 1，依此类推。

创建一个列表，只需要用逗号分隔的不同的数据项然后用方括号括起来即可，如下：
```python
list1=['Google','BaiDu','Bing']
list2=[1,2,3,4,5,6]
list3 = ['Chrome', 'FireFox',1,2]
```
列表的遍历
```python
lst = ['a','b','c','d']
for i in lst:
    print(i)
```
## 1.列表函数
### 1.1 list函数
#### 描述
list() 方法用于将元组或字符串转换为列表。

如果对字符串赋值后想要改变字符串中的某个值，因为字符串不能像列表一样可更改，如果想更改可以利用list函数

#### 语法
```python
list(seq)
```
- seq -- 要转换为列表的元组或字符串。
#### 返回值
返回列表

#### 实例
```python
s='Hello Ptthon'
lst = list(s)
lst[7] ='y'
s = ''.join(lst)
print(s) 
# 返回
'Hello Python'
```

### 1.2 len函数
#### 描述
返回列表元素个数
#### 语法
```python
len(list)
```
- list -- 要计算元素个数的列表
#### 实例
```python
list1 = ['Chrome','FireFox','Edge']
print(len(list1))
# 返回
3
```

### 1.3 max函数
#### 描述
返回列表元素中的最大值
#### 语法
```python
max(list)
```
- list -- 要返回最大值的列表。
#### 实例
```python
list1 = [7,8,2,4,3,1]
print(max(list1))
# 返回
8
```

### 1.4 min函数
#### 描述
返回列表元素中的最小值。
#### 语法
```python
min(list)
```
- list -- 要返回最小值的列表。
#### 实例
```python
list1 = [7,8,2,4,3,1]
print(min(list1))
# 返回
1
```

## 2.列表方法
### 2.1 append
append方法用于在列表末尾追加新的内容
```python
lst=['Chrome','FireFox','IE']
lst.append('Edge')
print(lst)
# 返回
['Chrome', 'FireFox', 'IE', 'Edge']
```
### 2.2 count
count方法用于统计某个元素在列表中出现的次数
```python
lst=[1,2,5,2,8,2,6]
print(lst.count(2))

# 返回
3
```

### 2.3 extend
extend用于在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）。
```python
lst1 = [1,2,3]
lst2 = [4,5,6]
lst1.extend(lst2)
print(lst1)
# 返回
[1, 2, 3, 4, 5, 6]
```
此操作和列表相加操作差不多，但是追加操作改变原有列表，而相加不改变原有列表
```python
lst1 = [1,2,3]
lst2 = [4,5,6]
print(lst1+lst2)
# 返回
[1, 2, 3, 4, 5, 6]
print(lst1)
# 返回
[1, 2, 3]
```

### 2.4 index
index() 函数用于从列表中找出某个值第一个匹配项的索引位置。
```python
lst=[1,2,5,2,8,2,6]
lst.index(2)
# 返回
1
```

### 2.5 insert
insert() 函数用于将指定对象插入列表的指定位置。
```python
lst =['Chrome','FireFox']
lst.insert(1,'Edge')
# 返回
['Chrome', 'Edge', 'FireFox']
```

### 2.6 pop
pop() 函数用于移除列表中的一个元素（默认最后一个元素），并且返回该元素的值。
```python
lst =['Chrome', 'Edge', 'FireFox']
lst.pop(1)
# 返回
'Edge'
```

### 2.7 remove
remove() 函数用于移除列表中某个值的第一个匹配项。
```python
lst =['Chrome','Chrome', 'Edge', 'FireFox']
lst.remove('Chrome')
# 返回
['Chrome', 'Edge', 'FireFox']
```

### 2.8 reverse
reverse() 函数用于反向列表中元素。
```python
lst =['Chrome', 'Edge', 'FireFox']
lst.reverse()
# 返回
['FireFox', 'Edge', 'Chrome']
```
### 2.9 sort
sort() 函数用于对原列表进行排序，如果指定参数，则使用比较函数指定的比较函数。
```python
lst =[3,8,2,5,7,1]
lst.sort()
# 返回
[1, 2, 3, 5, 7, 8]
```
### 2.10 clear
clear() 函数用于清空列表
```python
lst =[3,8,2,5,7,1]
lst.clear()
# 返回
[]
```
### 2.11 copy
copy() 函数用于复制列表
```python
lst =[3,8,2,5,7,1]
lst2 = lst.copy()
print(lst2)
# 返回
[3, 8, 2, 5, 7, 1]
```

## 3.列表基本操作
列表可以使用所有适用于序列的标准操作，比如索引、切片、连接和相乘，更有趣的是列表是可以修改的，也就是定义的列表内容可以根据需求修改。
### 3.1 改变列表：列表赋值
在列表中要给指定的元素赋值时，需要指定列表中某个元素的索引值
```python
lst =[1,2,2,4,5]
# 改变列表中第二个元素的内容
lst[2]=3
print(lst)
# 返回
[1, 2, 3, 4, 5]
```
**注意：不能为一个索引不存在的元素赋值**

### 3.2 删除列表元素
若要删除列表中的元素，直接利用del删除即可
```python
browsers =['chrome','firefox','ie','edge']
# 删除过时的ie
del browsers[2]
print(browsers)
# 返回
['chrome', 'firefox', 'edge']
```
del语句还能用于删除其他元素，也可以用于变量的删除操作

### 3.3 切片赋值
切片：变量[start:end:step]
- start的默认值是按照step方向上的第一个元素
- end的默认值是按照step的方向上的最后一个元素
- step的默认值是1
```python
browsers =['chrome','firefox','ie','edge']
# 取前三个浏览器
browsers[0:3]
# 返回
['chrome', 'firefox', 'ie']
#如果第一个索引是0，还可以省略
browsers[:3]
# 返回
['chrome', 'firefox', 'ie']
# 切边支持倒数切片，取后三个浏览器
browsers[-3:]
# 取ie浏览器
browsers[-2:-1]
```
在Python中对序列或者列表的切片操作是一个很强大的特性，切片赋值会显得更强大，例如：

```python
heroes =['乔峰','段誉','慕容复']
# 把慕容复换成虚竹
heroes[-1] = '虚竹'
print(heroes)
# 返回
['乔峰', '段誉', '虚竹']
```
从上可知，程序可以一次为多个元素赋值，在切片赋值时，可以使用与原来序列不等长的序列将切片替换，例如：

```python
name = list('perl')
name[1:] = list('ython')
print(name)
# 返回
['p', 'y', 't', 'h', 'o', 'n']
```
切片赋值还可以在不需要更改原有列表任何内容的情况下进行新元素插入

```python
heroes =['乔峰', '段誉', '虚竹']
heroes[1:1]=['段正淳','段延庆']
print(heroes)
# 返回
['乔峰', '段正淳', '段延庆', '段誉', '虚竹']
```
同理也可以通过切片操作来删除列表中的元素，同样也支持负数切片操作

```python
heroes =['乔峰', '段正淳', '段延庆', '段誉', '虚竹']
# 段正淳和段延庆不配为英雄，将其删除
heroes[1:3]=[]
# 返回
['乔峰', '段誉', '虚竹']

# 负数切片操作
heroes[-4:-2]=[]
print(heroes)
# 返回
['乔峰', '段誉', '虚竹']
```

