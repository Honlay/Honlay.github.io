---
layout: post
title: 【Python基础3】数据类型-数字
date: 2020-12-29 03:20:23 +0800
category: Python 
---



## Python3支持int、float、bool、complex(复数)

数字类型顾名思义就是用来存储数值的，需要记住的是如果改变了数字数据类型的值，将重新分配内存空间。
Python支持三种不同的数值类型：

- 整形(int)-通常被称为整形或整数，是正或负整数，不带小数点。Python3整形是没有大小限制的，可以当作Long类型使用，所以Python3没有Python2的Long类型
- 浮点型(float)-浮点型有整数部分和小数部分组成，浮点类型不精确存储，浮点类型也可以使用科学计数法表示(2.5e2=2.5*102=250)
- 复数(complex)-复数由实数部分和虚数部分构成,可以用a+bj或者complex(a,b)表示，复数的实数a和虚数b都是浮点型

### 示例：

```python
counter = 100     # 整形变量
distance = 100.0  # 浮点型变量
name ='小明'       # 字符串    
print(counter)
print(distance)
print(name)
```

## 数字类型转换

- int(x)将x转换为一个整数
- float(x)将x转换为一个浮点数
- complex(x) 将x转换到一个复数，实数部分为 x，虚数部分为 0
- complex(x, y) 将 x 和 y 转换到一个复数，实数部分为 x，虚数部分为 y。x 和 y 是数字表达式。

## 数值运算

和别的语言一样，数字类型支持各种常见的运算，不过Python的运算比别的大都数语言都更加丰富，此外还有大量丰富的方法提供更高效的开发
数值运算示例

```python
print(3 + 2) # 加法
print(5.2 -3 )# 减法
print(3 * 8) # 乘法
print(2 / 4) # 浮点数除法
print(2 // 4) # 整数除法
print(17 % 3) # 取余
print(2 ** 5) #乘方
```

