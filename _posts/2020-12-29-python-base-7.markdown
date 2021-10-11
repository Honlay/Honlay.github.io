---
layout: post
title: 【Python基础7】数据类型-字典
date: 2020-12-29 07:20:23 +0800
category: Python 
---

Python中字典（dictionary）提供了一种灵活的访问和组织数据的方式

- 字典是另一种可变容器模型，且可存储任意类型对象。
- 字典的每个键值 key=>value 对用冒号 : 分割，每个对之间用逗号(,)分割，整个字典包括在花括号 {} 中
- 键必须是唯一的，但值则不必。
- 值可以取任何数据类型，但键必须是不可变的，如字符串，数字。

```python
>>> heroes ={'乔峰':'降龙十八掌','段誉':'六脉神剑','虚竹':'小无相功'}

>>> heroes
{'乔峰': '降龙十八掌', '段誉': '六脉神剑', '虚竹': '小无相功'}
# 乔峰的武功
>>> heroes['乔峰']
'降龙十八掌'
# 输出所有英雄（键值）
>>> heroes.keys()
dict_keys(['乔峰', '段誉', '虚竹'])
# 输出所有武功
>>> heroes.values()
dict_values(['降龙十八掌', '六脉神剑', '小无相功'])
# 输出字典长度
>>> len(heroes)
3
```

字典的遍历

```python
>>> heroes ={'乔峰':'降龙十八掌','段誉':'六脉神剑','虚竹':'小无相功'}
# 遍历可以使用keys() values() items()
for k,v in heroes.items():
    print(k,v)
# 返回
乔峰 降龙十八掌
段誉 六脉神剑
虚竹 小无相功
```
键一般是唯一的，如果键重复，最后一个键值对会替换前面的一个键值对，值没有唯一性要求

```python
>>> hero = {'name':'乔峰','age':'35','gender':'男','name':'段誉'}

>>> hero
{'name': '段誉', 'age': '35', 'gender': '男'}
```
值可以取任何类型，但键必须是不可变的，如字符串、数字或元组

```python
hero = {'name':'乔峰','age':'35','gender':'男',('kungfu1','kunfgu2'):('降龙十八掌','打狗棒法')}
```

## 1.访问字典的数据

把相应的键放入方括号中：

```python
>>> hero = {'name':'乔峰','age':'35','gender':'男','kungfu':'降龙十八掌'}
>>> hero['name']
'乔峰'
print(f"有一个{hero['gender']}英雄，他的名字是{hero['name']},今年{hero['age']}岁了！他会使用{hero['kungfu']}!")

# 返回
有一个男英雄，他的名字是乔峰,今年35岁了！他会使用降龙十八掌!
```
同样的，字典也可以用整数作为键，和列表的索引类似，只是字典的值是任何整数类型都可以，不必要从0开始，因为键值的数据类型是任意的。
```python
>>> ranking ={1:'乔峰',2:'虚竹',3:'段誉'}
print(f"武林中排名第一的是{ranking[1]}!")
# 返回
武林中排名第一的是乔峰!
```
因为字典是无序的，所以不能像列表那样切片。如果访问字典中不错在的键，将导致KeyError错误信息。这很像列表的越界信息：
```python
>>> ranking ={1:'乔峰',2:'虚竹',3:'段誉'}
>>> print(f"武林中排名第四的是{ranking[4]}!")
# 返回
Traceback (most recent call last):
  File "<input>", line 1, in <module>
KeyError: 4
```
## 2.修改字典元素
### 2.1 添加和更新字典数据
向字典添加新数据的方法是增加新的键值对
```python
>>> ranking ={1:'乔峰',2:'虚竹',3:'段誉'}
# 更新排名榜
>>> ranking[2],ranking[3] ='段誉','虚竹'
>>> ranking
{1: '乔峰', 2: '段誉', 3: '虚竹'}

# 新增排名榜第四名
>>> ranking[4] = '无崖子'
>>> ranking
{1: '乔峰', 2: '段誉', 3: '虚竹', 4: '无崖子'}
```

### 2.2 删除字典的元素
对字典元素的删除等单一删除也能将整个字典清空
```python
>>> ranking = {1: '乔峰', 2: '段誉', 3: '虚竹', 4: '无崖子'}
# 删除第四名
>>> del ranking[4]
>>> ranking
{1: '乔峰', 2: '段誉', 3: '虚竹'}
# 清空排名榜
>>> ranking.clear()
>>> ranking
{}
# 销毁排行榜
>>> del ranking
>>> ranking
# 因为排行榜已被销毁，所以抛出异常
'''
Traceback (most recent call last):
  File "<input>", line 1, in <module>
NameError: name 'ranking' is not defined
'''
```

## 3.字典的特性
字典的值可以没有限制的取任何python对象，既可以是标准对象也可以是用户自定义的对象，但是键不行
两个重要的点需要记住

**1.不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住。**
```python
>>> hero = {'name':'乔峰','age':'35','gender':'男','name':'段誉'}

>>> hero
{'name': '段誉', 'age': '35', 'gender': '男'}
```
**2.键必须不可变，所以可以用数字、字符串或元组充当，列表就不行**
```python
>>> hero = {['name']:'乔峰','age':'35','gender':'男'}
# 抛出异常
Traceback (most recent call last):
  File "<input>", line 1, in <module>
TypeError: unhashable type: 'list'
```
## 4.字典的函数
### 4.1 len()
len()函数用于计算字典元素个数，即键的总数
```python
>>> ranking = {1: '乔峰', 2: '段誉', 3: '虚竹', 4: '无崖子'}
>>> len(ranking)
4
```
### 4.2 str()
输出字典，以可以打印的字符串表示
```python
>>> ranking = {1: '乔峰', 2: '段誉', 3: '虚竹', 4: '无崖子'}
>>> str(ranking)
# 输出
"{1: '乔峰', 2: '段誉', 3: '虚竹', 4: '无崖子'}"
```
### 4.3 type()
返回输入的变量类型，如果变量是字典就返回字典类型
```python
>>> ranking = {1: '乔峰', 2: '段誉', 3: '虚竹', 4: '无崖子'}
>>> type(ranking)
<class 'dict'>
```

## 5.字典的方法
### 5.1 dict.clear()
删除字典内所有元素，clear()方法没有返回值
```python
>>> ranking = {1: '乔峰', 2: '段誉', 3: '虚竹', 4: '无崖子'}
# 清空排名榜
>>> ranking.clear()
print(f"排名榜上还有{len(ranking)}位英雄")
# 返回
排名榜上还有0位英雄
```

### 5.2 dict.copy()
返回一个字典的浅复制。
```python
ranking = {1: '乔峰', 2: '段誉', 3: '虚竹'}
ranking2 = ranking.copy()
print('新拷贝的字典为:',ranking2)
# 返回
新拷贝的字典为: {1: '乔峰', 2: '段誉', 3: '虚竹'}
#直接赋值和Copy的区别
hero = {'name':'乔峰','kongfu':['降龙十八掌','打狗棒法']}

hero2 = hero         # 浅拷贝：引用对象
hero3 = hero.copy() # 浅拷贝：深拷贝父对象（一级目录），子对象（二级目录）不拷贝，还是引用
# 修改数据
hero['name'] = '郭靖'
hero['kongfu'].remove('打狗棒法')

print(hero)   # 返回 {'name': '郭靖', 'kongfu': '降龙十八掌'}
print(hero2)  # 返回 {'name': '郭靖', 'kongfu': '降龙十八掌'}
print(hero3)  # 返回 {'name': '乔峰', 'kongfu': '降龙十八掌'}
```
实例中hero2其实是hero的引用，即别名，所以输出结果是一致的，hero3对父对象进行了深拷贝，不会随hero修改而修改，子对象是浅拷贝所以随hero的修改而修改，****即赋值会随父对象修改而修改，拷贝不会随父对象修改而修改****

### 5.3 dict.fromkeys()
创建一个新字典，以序列 seq 中元素做字典的键，value 为字典所有键对应的初始值。该方法返回一个新的字典
#### 语法：
`dict.fromkeys(seq[, value])`

- seq -- 字典键值列表。
- value -- 可选参数, 设置键序列（seq）对应的值，默认为 None。
```python
seq=('name','age','sex')
person = dict.fromkeys(seq)
print('新的字典为:',person)
# 返回 
新的字典为: {'name': None, 'age': None, 'sex': None}
person = dict.fromkeys(seq,10)
print('新的字典为:',person)
# 返回
新的字典为: {'name': 10, 'age': 10, 'sex': 10}
```

### 5.4 dict.get()
返回指定键的值
#### 语法
`dict.get(key, default=None)`
- key -- 字典中要查找的键。
- default -- 如果指定的键不存在时，返回该默认值。
```python
ranking = {1: '乔峰', 2: '段誉', 3: '虚竹'}
print(f"英雄榜排名第一的是{ranking.get(1)}")  # 返回  英雄榜排名第一的是乔峰
print(f"英雄榜排名第四的是{ranking.get(4,'NA')}")  # 返回   英雄榜排名第四的是NA
```

### 5.5 key in dict
如果键在字典里返回True,否则返回False
```python
ranking = {1: '乔峰', 2: '段誉', 3: '虚竹'}
if 1 in ranking:
    print('乔峰在英雄榜中')
else:
    print('乔峰竟然不在英雄榜中？')

# 返回  乔峰在英雄榜中
```

### 5.7 dict.items()
item() 方法以列表返回可遍历的(键, 值) 元组数组
```python
ranking = {1: '乔峰', 2: '段誉', 3: '虚竹'}
print(ranking.items())
# 返回  dict_items([(1, '乔峰'), (2, '段誉'), (3, '虚竹')])

# 遍历
heroes ={'乔峰':'降龙十八掌','段誉':'六脉神剑','虚竹':'小无相功'}
for k,v in heroes.items():
    print(f"{k}会{v}")
    
# 返回
乔峰会降龙十八掌
段誉会六脉神剑
虚竹会小无相功
```
### 5.8 dict.setdefault()
 setdefault() 方法和 get()方法 类似, 如果键不已经存在于字典中，将会添加键并将值设为默认值。

#### 语法
`dict.setdefault(key, default=None)`
- key -- 查找的键值。
- default -- 键不存在时，设置的默认键值。
```python
heroes ={'乔峰':'降龙十八掌','段誉':'六脉神剑'}
print(f"乔峰的武功为{heroes.setdefault('乔峰',None)}")  
# 返回 乔峰的武功为降龙十八掌
print(f"虚竹的武功为{heroes.setdefault('虚竹','小无相功')}")
# 返回 虚竹的武功为小无相功
print('新的字典',heroes)
# 返回 新的字典 {'乔峰': '降龙十八掌', '段誉': '六脉神剑', '虚竹': '小无相功'}
```
关于dict.get()和dict.setdefault()的区别是：当查找键值不存在的时候，dict.setdefault()会返回默认值并更新字典，添加键值，dict.get()只返回默认值，并不改变原来的字典

### 5.9 dict.update(dict2)
把字典参数 dict2 的 key/value(键/值) 对更新到字典 dict 里
```python
heroes1={'乔峰':'降龙十八掌','段誉':'六脉神剑'}
heroes2={'杨过':'黯然销魂掌','小龙女':'玉女心经'}
heroes1.update(heroes2)
print(heroes1)
# 返回 
{'乔峰': '降龙十八掌', '段誉': '六脉神剑', '杨过': '黯然销魂掌', '小龙女': '玉女心经'}
```
### 5.10 dict.values()
返回一个迭代器，可以使用 list() 来转换为列表，列表为字典中的所有值。
```python
heroes = {'乔峰': '降龙十八掌', '段誉': '六脉神剑', '杨过': '黯然销魂掌', '小龙女': '玉女心经'}
# 把武林中的牛逼武功放入一个列表中
lst = list(heroes.values())
print(lst)
# 返回
['降龙十八掌', '六脉神剑', '黯然销魂掌', '玉女心经']
# 再把所有武功用-连起来转成字符串
Konfugs = '-'.join(lst)
print(Konfugs)
# 返回
降龙十八掌-六脉神剑-黯然销魂掌-玉女心经
```

### 5.11 dict.pop
删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值。
#### 语法
`pop(key[,default])`
- key: 要删除的键值
- default: 如果没有 key，返回 default 值
```python
heroes = {'乔峰': '降龙十八掌', '段誉': '六脉神剑', '杨过': '黯然销魂掌'}
# 删除不属于天龙八部中的角色，并看看他会什么武功
print(heroes.pop('杨过'))  # 返回 黯然销魂掌
print(heroes)  # 返回  {'乔峰': '降龙十八掌', '段誉': '六脉神剑'}
```
### 5.12 dict.popitem()
随机返回并删除字典中的最后一对键和值。按照 LIFO（Last In First Out 后进先出法） 顺序规则，即最末尾的键值对。如果字典已经为空，却调用了此方法，就报出KeyError异常。
```python
heroes = {'乔峰': '降龙十八掌', '段誉': '六脉神剑', '杨过': '黯然销魂掌'}
print(heroes.popitem())  # 返回 ('杨过', '黯然销魂掌')
```



