---
layout: post
title: 【Python基础4】数据类型-字符串
date: 2020-12-29 04:20:23 +0800
category: Python 
---
创建字符串可以使用单引号、双引号、三单引号和三双引号，其中三引号可以多行定义字符串，Python中不支持单字符串类型，单字符串在Python中也是作为一个字符串使用
## 字符串的常见操作
```python
s='我要学Python'
# 切片
# 字符串索引取值范围 -len()到len()-1 越界会报错
s[0] , s[-1] ,s[3:] s[::-1] # '我'，'n'，'Python'，'nohtyP学要我'

# 替换，还可以使用正则表达式替换
s.replace('Python','C#') # '我要学C#'

# 查找 find()、index() 、rfind() 、rindex()
s.find('p') # 3 ，返回字符串第一次出现的位置
s.find('h',2) # 6 ,设定下标2开始查找
s.find('c') #-1 查找不到返回-1
s.rfind('p') # 3  返回字符串最后一次出现的位置(从右向左查找)，如果没有则返回-1
s.index('y') # 4,返回字符串第一次出现的位置
s.index('c') # 不同于find(),查找不到会抛出异常
s.rindex('P') # 3 返回字符串最后一次出现的位置，如果没有则抛出异常

# 转大小写, upper()\lower()\swapcase()\capitalize()\istitle()\isupper()\islower()
s.upper() # 我要学PYTHON
s.swapcase() # 我要学pYTHON 大小写互换
s.istitle() # True 
s.islower() #False

# 去空格 strip() lstrip() rstrip()
a = 'Hello Python '
a.strip() # 'Hello Python' 该方法只删除开头或是结尾的字符，不能删除中间部分
a.lstrip() # 'Hello Python ' 该方法只能截掉左边的空格或指定字符
a.rstrip() # Hello Python' 该方法只能删除字符串末尾的空格或指定字符

# 格式化
s1 = '%s %s' % ('Python', 3.8) # 'Python 3.8'
s2 = '{}{}'.format('Python',3.8,) # 'Python3.8' 推荐使用format格式化字符串
s3 = '{0}, {1}, {0}'.format('Python', 3.8) # 'Python, 3.8, Python'
s4 = '{name}: {age}'.format(age=21, name='小明') # '小明: 21'

```
以上是一些常见的操作
另外还有一点需要注意的是字符串编码，所有的Python字符串都是Unicode字符串，当需要将文件保存到外设或进行网络传输时，就要进行编码转换，将字符串转换为字节，以提高编码效率
```python
s='我要学Python'
print(s.encode()) #默认编码是UTF-8 输出 b'\xe6\x88\x91\xe8\xa6\x81\xe5\xad\xa6Python'
print(s.encode('gbk')) # 输出 b'\xce\xd2\xd2\xaa\xd1\xa7Python'
# deconde 将字节传唤为字符
print(s.encode().decode('utf-8')) #输出 我要学Python
print (s.encode('gbk').decode('gbk')) # 输出 我要学Python
```
## Python字符串的45个方法详解
Python中字符串对象提供了很多方法来操作字符串，功能相当丰富。必须进行全面的了解与学习，后边的代码才能更得心应手。
### 
#### 大小写转换
**1.capitalize()**

**描述**:将字符串的第一个字母变成大写，其余字母变为小写

**语法**：str.capitalize()

**示例**：

```python
s1 = 'i love python'
s1.capitalize() # 输出 'I love python'
s2 = 'i Love PYTHON'
s2.capitalize() #输出 'I love python'
```
**2.title()** 

**描述**:返回"标题化"的字符串,就是说所有单词都是以大写开始，其余字母均为小写

**语法**:str.title();

**示例**
```python
s = 'this is string example'
s.title()  #输出 'This Is String Example'
```
**3.swapcase()** 

**描述**:将字符串中大写转换为小写，小写转换为大写

**语法**:str.swapcase();

**示例**
```python
s = 'this is string example'
s.swapcase()  #输出 'THIS IS STRING EXAMPLE'
```
**4.lower()** 

**描述**:转换字符串中所有大写字符为小写

**语法**:str.lower();

**示例**
```python
s = 'Hello Python'
s.lower()  #输出 'hello python'
```
**5.upper()** 

**描述**:将字符串中的小写字母转为大写字母。

**语法**:str.upper();

**示例**
```python
s = 'Hello Python'
s.upper()  #输出 'HELLO PYTHON
```
**6.casefold()** 

**描述**:将字符串中的所有大写字母转换为小写字母。也可以将非英文 语言中的大写转换为小写.
**注意**：lower() 方法只对ASCII编码，也就是‘A-Z’有效，对于其他语言（非汉语或英文）中把大写转换为小写的情况只能用 casefold() 方法。

**语法**:str.casefold()();

**示例**
```python
s = 'Groß - α'
s.casefold()  #输出 'gross - α'
```

#### 字符串填充
**7.center()** 

**描述**:返回一个指定的宽度 width 居中的字符串，fillchar 为填充的字符，默认为空格。

**语法**: str.center(width , “fillchar”)

- width:指定字符串长度
- fillchr:要填充的单字符，默认为空格

**示例**
```python
s = 'python'
s.center(10)  #输出 '  python  '
s.center(10,'*') # 输出 '**python**'
```
**8.ljust()** 

**描述**:返回一个原字符串左对齐,并使用空格填充至指定长度的新字符串。如果指定的长度小于原字符串的长度则返回原字符串。

**语法**:str.ljust(width, fillchar) -> str 返回一个新的字符串
- width:指定字符串长度
- fillchr:要填充的单字符，默认为空格

**示例**
```python
s = 'Python'
s.ljust(10)  #输出 'Python    '
s.ljust(10,'*') # 输出 'Python****'
```
**9.rjust()** 

**描述**:返回一个原字符串右对齐,并使用fillchar(默认空格）填充至长度 width 的新字符串

**语法**:str.ljust(width, fillchar)
- width:指定字符串长度
- fillchr:要填充的单字符，默认为空格

**示例**
```python
s = 'Python'
s.rjust(10)  #输出 '    Python'
s.rjust(10,'*') # 输出 '****Python'
```

**10.zfill()** 

**描述**:返回长度为 width 的字符串，原字符串右对齐，前面填充0

**语法**:str.zfill(width)

**示例**
```python
s = 'Python'
s.zfill(10)  #输出 '0000Python'
```

#### 字符串编码
**11.encode()** 

**描述**:以指定的编码格式编码字符串。errors参数可以指定不同的错误处理方案。

**语法**:str.encode(encoding='UTF-8',errors='strict')
- encoding -- 要使用的编码，如: UTF-8。
- errors -- 设置不同错误的处理方案。默认为 'strict',意为编码错误引起一个UnicodeError。 其他可能得值有 'ignore', 'replace', 'xmlcharrefreplace', 'backslashreplace' 以及通过 codecs.register_error() 注册的任何值

**示例**
```python
s = '我要学Python'
s.encode(encoding='utf-8',errors = 'strict')  #输出 b'\xe6\x88\x91\xe8\xa6\x81\xe5\xad\xa6Python'

```
**12.decode()** 

**描述**:以 encoding 指定的编码格式解码字符串，默认编码为字符串编码。decode英文意思是 解码

**语法**:str.decode(encoding=‘utf-8’, errors=‘strict’)
- encoding -- 要使用的编码，如：utf-8,gb2312,cp936,gbk等。
- errors -- 设置不同错误的处理方案。默认为 'strict',意为编码错误引起一个UnicodeError。 其他可能得值有 'ignore', 'replace', 'xmlcharrefreplace', 'backslashreplace' 以及通过 codecs.register_error() 注册的任何值

**示例**
```python
s = '我要学Python'
s_utf8=s.encode(encoding='utf-8')  
s_utf8.decode(encoding='utf-8',errors = 'strict') # 输出 '我要学Python'

```

#### 字符串查找
**13.find()** 

**描述**:方法检测字符串中是否包含子字符串 str ，如果指定 beg（开始） 和 end（结束） 范围，则检查是否包含在指定范围内，如果指定范围内如果包含指定索引值，返回的是索引值在字符串中的起始位置。如果不包含索引值，返回-1。

**语法**:str.find(str, beg=0, end=len(string))
- str -- 指定检索的字符串
- beg -- 开始索引，默认为0。
- end -- 结束索引，默认为字符串的长度。

**示例**
```python
s1 = 'I love Python'
s2 = 'Python'
print(s1.find(s2))   #返回 7
print(s1.find(s2,5)) # 返回 7
print(s1.find(s2,8)) # 返回 -1

```
**14.rfind()** 

**描述**:返回字符串最后一次出现的位置，如果没有匹配项则返回-1。

**语法**:str.rfind(str, beg=0 end=len(string))
- str --  查找的字符串
- beg -- 开始索引，默认为0。
- end -- 结束索引，默认为字符串的长度。

**示例**
```python
s1 = 'I love Python'
s2 = 'Python'
print(s1.rfind(s2))   #返回 7
print(s1.rfind(s2,5)) # 返回 7
print(s1.rfind(s2,8)) # 返回 -1

```

**15.index()** 

**描述**:与find()方法一样，只不过如果str不在string中会抛出一个异常

**语法**:str.index(str, beg=0, end=len(string))
- str --  查找的字符串
- beg -- 开始索引，默认为0。
- end -- 结束索引，默认为字符串的长度。

**示例**
```python
s1 = 'I love Python'
s2 = 'Python'
print(s1.index(s2))   #返回 7
print(s1.index(s2,5)) # 返回 7
print(s1.index(s2,8)) # 抛出异常

```

**16.rindex()** 

**描述**:rindex() 方法返回子字符串最后一次出现在字符串中的索引位置，该方法与 rfind() 方法一样，可以规定字符串的索引查找范围[star,end)，只不过如果子字符串不在字符串中会报一个异常。

**语法**:str.rindex(str, beg=0 end=len(string))
- str --  查找的字符串
- beg -- 开始索引，默认为0。
- end -- 结束索引，默认为字符串的长度。

**示例**
```python
s1 = 'I love Python'
s2 = 'Python'
print(s1.rindex(s2))   #返回 7
print(s1.rindex(s2,5)) # 返回 7
print(s1.rindex(s2,8)) # 抛出异常

```

#### 字符串格式化

**17.format()** 

**描述**:Python2.6 开始，新增了一种格式化字符串的函数 str.format()，它增强了字符串格式化的功能。 format 函数可以接受不限个参数，位置可以不按顺序。

**语法**: format(value, format_spec)

**示例**
```python
"{} {}".format("hello", "python")    # 不设置指定位置，按默认顺序
'hello python'

"{0} {1}".format("hello", "python")  # 设置指定位置
'hello python'

"{1} {0} {1}".format("hello", "python")  # 设置指定位置
'python hello python'

# 也可以设置参数：
print("网站名：{name}, 地址 {url}".format(name="XRLoft", url="www.xrloft.com"))
'网站名：XRLoft, 地址 www.xrloft.com'

# 通过字典设置参数
site = {"name": "XRLoft", "url": "www.xrloft.com"}
print("网站名：{name}, 地址 {url}".format(**site))
'网站名：XRLoft, 地址 www.xrloft.com'

# 通过列表索引设置参数
my_list = ['XRLoft', 'www.xrloft.com']
print("网站名：{0[0]}, 地址 {0[1]}".format(my_list))  # "0" 是必须的
'网站名：XRLoft, 地址 www.xrloft.com'
```

**18.format_map()** 

**描述**:返回字符串的格式化版本。在Python3中使用format和format_map方法都可以进行字符串格式化，但format是一种所有情况都能使用的格式化方法，format_map仅使用于字符串格式中可变数据参数来源于字典等映射关系数据时才可以使用。

**语法**:  str.format_map(mapping) -> str 返回字符串
-  mapping 是一个字典对象

**示例**
```python
People = {"name": "john", "age": 33}
"My name is {name},iam{age} old".format_map(People) # 返回 'My name is john,iam33 old'
```

#### 解决判断问题
**19.endswith()** 

**描述**:用于判断字符串是否以指定后缀结尾，如果以指定后缀结尾返回 True，否则返回 False。可选参数 "start" 与 "end" 为检索字符串的开始与结束位置。

**语法**:  str.endswith(suffix[, start[, end]])
- suffix -- 该参数可以是一个字符串或者是一个元素。
- start -- 字符串中的开始位置。
- end -- 字符中结束位置。

**示例**
```python
s = 'I Love Python!!!'
suffix ='!!'
print (s.endswith(suffix)) # 返回 True
print (s.endswith(suffix,14)) # 返回 True
suffix='C'
print (s.endswith(suffix)) # 返回 False
```

**20.startswith()** 

**描述**:用于检查字符串是否是以指定子字符串开头，如果是则返回 True，否则返回 False。如果参数 beg 和 end 指定值，则在指定范围内检查。

**语法**:  str.startswith(substr, beg=0,end=len(string));
- str -- 检测的字符串。
- substr -- 指定的子字符串。
- start -- 字符串中的开始位置。
- end -- 字符中结束位置。

**示例**
```python
s = 'I Love Python!!!'
suffix ='I'
print (s.startswith(suffix)) # 返回 True
print (s.startswith(suffix,0)) # 返回 True
suffix='C'
print (s.startswith(suffix)) # 返回 False
```
**21.isalnum()** 

**描述**:检测字符串是否由字母和数字组成。str中至少有一个字符且所有字符都是字母或数字则返回 True,否则返回 False

**语法**:  str.isalnum()

**示例**
```python
s1 = 'Seven-11'
print(s1.isalnum())  # 返回False

s2='Seven11'
print(s2.isalnum()) # 返回 True
```
**22.isalpha()** 

**描述**:检测字符串是否只由字母组成。字符串中至少有一个字符且所有字符都是字母则返回 True,否则返回 False。

**语法**:  str.isalpha() -> bool 返回值为布尔类型（True,False）

**示例**
```python
s1 = 'I Love Python'
print(s1.isalpha())  # 返回False
s2='ILovePython'
print(s2.isalpha()) # 返回 True
```

**23.isdecimal()** 

**描述**:检查字符串是否只包含十进制字符，如果是返回 true，否则返回 false。
**注意**: 定义一个十进制字符串，只需要在字符串前添加 'u' 前缀即可。

**语法**:  str.isdecimal()

**示例**
```python
s1 = 'python3.8'
print(s1.isdecimal())  # 返回False
s2='23443434'
print(s2.isdecimal()) # 返回 True
```

**24.isdigit()** 

**描述**:检测字符串是否只由数字组成.字符串中至少有一个字符且所有字符都是数字则返回 True,否则返回 False。

**语法**:  str.isdigit() -> bool 返回值为布尔类型（True,False）

**示例**
```python
s1 = 'python3.8'
print(s1.isdigit())  # 返回False
s2='31415926'
print(s2.isdigit()) # 返回 True
```

**25.isidentifier()** 

**描述**:判断str是否是有效的标识符。str为符合命名规则的变量，保留标识符则返回True,否者返回False。

**语法**:   str.isidentifier() -> bool 返回值为布尔类型（True,False）

**示例**
```python
s1 = 'python3.8'
print(s1.isidentifier())  # 返回False
s2='_python'
print(s2.isidentifier()) # 返回 True
```

**26.islower()** 

**描述**:如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是小写，则返回 True，否则返回 False

**语法**:   str.islower() 

**示例**
```python
s1 = 'Python3.8'
print(s1.islower())  # 返回False
s2='python3.8'
print(s2.islower()) # 返回 True
```


**27.isupper()** 

**描述**:如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是大写，则返回 True，否则返回 False

**语法**:   str.isupper()

**示例**
```python
s1 = 'Python3.8'
print(s1.isupper())  # 返回False
s2='PYTHON3.8'
print(s2.isupper()) # 返回 True
```

**28.isnumeric()** 

**描述**:测字符串是否只由数字组成，数字可以是： Unicode 数字，全角数字（双字节），罗马数字，汉字数字。

指数类似 ² 与分数类似 ½ 也属于数字。

**语法**:   str.isnumeric()

**示例**
```python
s1 = 'Python3.8'
print(s1.isnumeric())  # 返回False
s2='222222'
print(s2.isnumeric()) # 返回 True
```

**29.isprintable()** 

**描述**:判断字符串中是否有打印后不可见的内容。如：\n \t 等字符。若字符串中不存在\n \t 等不可见的内容，则返回True,否者返回False。

**语法**: str.isprintable() -> bool 返回值为布尔类型（True,False）

**示例**
```python
s1 = 'Python3.8'
print(s1.isnumeric())  # 返回False
s2='222222'
print(s2.isnumeric()) # 返回 True
```
**30.isspace()** 

**描述**:检测字符串是否只由空格组成。若字符串中只包含空格，则返回 True，否则返回 False。

**语法**: str.isspace() -> bool 返回值为布尔类型（True,False）

**示例**
```python
s1 = ' '
print(s1.isspace())  # 返回 True
s2='I Love Python'
print(s2.isspace()) # 返回 False
```

**31.istitle()** 

**描述**:检测判断字符串中所有单词的首字母是否为大写，且其它字母是否为小写，字符串中可以存在其它非字母的字符。若字符串中所有单词的首字母为大写，且其它字母为小写，则返回 True，否则返回 False。

**语法**: str.istitle() -> bool 返回值为布尔类型（True,False）

**示例**
```python
s1 = ' I love Python '
print(s1.istitle())  # 返回 False
s2='I Love Python'
print(s2.istitle()) # 返回 True
```
#### 字符串修剪
**32.strip()** 

**描述**:用于移除字符串头尾指定的字符（默认为空格）或字符序列。

**语法**: str.strip([chars]);
- chars – 要去除的字符 默认为空格或换行符。

**示例**
```python
s2=' I Love Python '
print(s2.strip()) # 返回 'I Love Python'
```

**33.lstrip()** 

**描述**:用于截掉字符串左边的空格或指定字符

**语法**: str.lstrip([chars]);
- chars – 要去除的字符 默认为空格或换行符。

**示例**
```python
s2=' I Love Python '
print(s2.lstrip()) # 返回 'I Love Python '
```

**34.rstrip()** 

**描述**:删除 str 字符串末尾的指定字符（默认为空格）

**语法**: str.rstrip([chars]);
- chars – 要去除的字符 默认为空格或换行符。

**示例**
```python
s2=' I Love Python '
print(s2.rstrip()) # 返回 ' I Love Python'
```
#### 字符串加密解密
**35.maketrans()** 

**描述**:用于创建字符映射的转换表，对于接受两个参数的最简单的调用方式，第一个参数是字符串，表示需要转换的字符，第二个参数也是字符串表示转换的目标。

两个字符串的长度必须相同，为一一对应的关系。

**语法**: str.maketrans(intab, outtab，delchars)

- ntab -- 字符串中要替代的字符组成的字符串。
- outtab -- 相应的映射字符的字符串。
- delchars – 可选参数，表示要删除的字符组成的字符串。

**示例**
```python
intab = "aeiou"
outtab = "12345"
trantab = str.maketrans(intab, outtab)
str = "this is string example....wow!!!"
print (str.translate(trantab))
# 输出 th3s 3s str3ng 2x1mpl2....w4w!!!

```

**36.translate()** 

**描述**:过滤(删除)，翻译字符串。即根据maketrans()函数给出的字符映射转换表来转换字符串中的字符。

translate()函数是先过滤(删除)，再根据maketrans()函数返回的转换表来翻译。

**语法**: 

str.translate(table)

bytes.translate(table[, delete])    

bytearray.translate(table[, delete]) 

- table -- 翻译表，翻译表是通过 maketrans() 方法转换而来。
- deletechars -- 字符串中要过滤的字符列表。

示例

```python
intab = "aeiou"
outtab = "12345"
trantab = str.maketrans(intab, outtab)
str = "this is string example....wow!!!"
print (str.translate(trantab))
# 输出 th3s 3s str3ng 2x1mpl2....w4w!!!

```

#### 分割字符串

**37.partition()** 

**描述**:根据指定的分隔符(sep)将字符串进行分割。从字符串左边开始索引分隔符sep,索引到则停止索引。

**语法**: str.partition(sep)

-  sep —— 指定的分隔符

**返回值**：
 (head, sep, tail) 返回一个三元元组，head:分隔符sep前的字符串，sep:分隔符本身，tail:分隔符sep后的字符串。如果字符串包含指定的分隔符sep，则返回一个三元元组，第一个为分隔符sep左边的子字符串，第二个为分隔符sep本身，第三个为分隔符sep右边的子字符串。如果字符串不包含指定的分隔符sep,仍然返回一个三元元组，第一个元素为字符串本身，第二第三个元素为空字符串

**示例**

```python
s = 'https://www.xrloft.com'
print(s.partition('://')) # 返回 ('https', '://', 'www.xrloft.com')
print(s.partition(',')) # 返回 ('https://www.xrloft.com', '', '') 字符串s中不存在sep',',返回了两个空字符串

```

**38.rpartition()** 

**描述**:根据指定的分隔符(sep)将字符串进行分割。从字符串右边(末尾)开始索引分隔符sep,索引到则停止索引。

**语法**: str.rpartition(sep)

-  sep —— 指定的分隔符

**返回值**：
  (head, sep, tail) 返回一个三元元组，head:分隔符sep前的字符串，sep:分隔符本身，tail:分隔符sep后的字符串。如果字符串包含指定的分隔符sep，则返回一个三元元组，第一个为分隔符sep左边的子字符串，第二个为分隔符sep本身，第三个为分隔符sep右边的子字符串。如果字符串不包含指定的分隔符sep,仍然返回一个三元元组，第一个元素为字符串本身，第二第三个元素为空字符串。

**示例**
```python
s = 'https://www.xrloft.com'
print(s.rpartition('://')) # 返回 ('https', '://', 'www.xrloft.com')
print(s.rpartition(',')) # 返回 ('', '', 'https://www.xrloft.com')  字符串s中不存在sep',',返回了两个空字符串

```

**39.split()** 

**描述**:拆分字符串。通过指定分隔符sep对字符串进行分割，并返回分割后的字符串列表。

**语法**: str.split(str="", num=string.count(str))

- str -- 分隔符，默认为所有的空字符，包括空格、换行(\n)、制表符(\t)等。
- num -- 分割次数。默认为 -1, 即分隔所有。

**返回值**：
  返回分割后的字符串列表。

**示例**
```python
s = 'I Love Python'
print (s.split())       # 以空格为分隔符 返回 ['I', 'Love', 'Python']
print(s.split('o'))  #以o为分隔符，返回  ['I L', 've Pyth', 'n']

```
**40.rsplit()** 

**描述**:分字符串。通过指定分隔符sep对字符串进行分割，并返回分割后的字符串列表,类似于split()函数，只不过 rsplit()函数是从字符串右边(末尾)开始分割。

**语法**:  S.rsplit([sep=None][,count=S.count(sep)])

- sep -- 可选参数，指定的分隔符，默认为所有的空字符，包括空格、换行(\n)、制表符(\t)等。
- count -- 可选参数，分割次数，默认为分隔符在字符串中出现的总次数。

**示例**
```python
S = "this is string example....wow!!!"
print (S.rsplit( ))
print (S.rsplit('i',1))
print (S.rsplit('w'))

#输出以下结果
['this', 'is', 'string', 'example....wow!!!']
['this is str', 'ng example....wow!!!']
['this is string example....', 'o', '!!!']

```

**41.splitlines()** 

**描述**:按照行('\r', '\r\n', \n')分隔，返回一个包含各行作为元素的列表，如果参数 keepends 为 False，不包含换行符，如果为 True，则保留换行符。

**语法**:  str.splitlines([keepends])

- keepends -- 在输出结果里是否去掉换行符('\r', '\r\n', \n')，默认为 False，不包含换行符，如果为 True，则保留换行符。

**示例**
```python
>>> 'ab c\n\nde fg\rkl\r\n'.splitlines()
['ab c', '', 'de fg', 'kl']
>>> 'ab c\n\nde fg\rkl\r\n'.splitlines(True)
['ab c\n', '\n', 'de fg\r', 'kl\r\n']
```

**41.join()** 

**描述**:用于将序列中的元素以指定的字符连接生成一个新的字符串

**语法**:  str.join(sequence)

- sequence -- 要连接的元素序列。

**示例**
```python
s1 = "-"
s2 = ""
seq = ("r", "u", "n", "o", "o", "b") # 字符串序列
print (s1.join( seq ))
print (s2.join( seq ))
# 返回以下结果
'r-u-n-o-o-b'
'runoob'
```
#### 字符串替换

**43.replace()** 

**描述**:把字符串中的 old（旧字符串） 替换成 new(新字符串)，如果指定第三个参数max，则替换不超过 max 次。

**语法**: str.replace(old, new[, max])

- old -- 将被替换的子字符串。
- new -- 新字符串，用于替换old子字符串。
- max -- 可选字符串, 替换不超过 max 次

**示例**
```python
s = 'I Love Python'
print(s.replace('Python','C#')) # 返回 I Love C#
```

**44.expandtabs()** 

**描述**:把字符串中的 tab 符号 \t 转为空格，tab 符号 \t 默认的空格数是 8，在第 0、8、16...等处给出制表符位置，如果当前位置到开始位置或上一个制表符位置的字符数不足 8 的倍数则以空格代替。

**语法**: str.expandtabs(tabsize=8)

- tabsize -- 指定转换字符串中的 tab 符号 \t 转为空格的字符数。

**示例**
```python
str = "runoob\t12345\tabc"  
print('原始字符串:', str)
 
# 默认 8 个空格
# runnob 有 6 个字符，后面的 \t 填充 2 个空格
# 12345 有 5 个字符，后面的 \t 填充 3 个空格
print('替换 \\t 符号:', str.expandtabs())
 
# 2 个空格
# runnob 有 6 个字符，刚好是 2 的 3 倍，后面的 \t 填充 2 个空格
# 12345 有 5 个字符，不是 2 的倍数，后面的 \t 填充 1 个空格
print('使用 2 个空格替换 \\t 符号:', str.expandtabs(2))
 
# 3 个空格
print('使用 3 个空格:', str.expandtabs(3))
 
# 4 个空格
print('使用 4 个空格:', str.expandtabs(4))
 
# 5 个空格
print('使用 5 个空格:', str.expandtabs(5))
 
# 6 个空格
print('使用 6 个空格:', str.expandtabs(6))

# 以上实例输出结果为
原始字符串: runoob      12345   abc
替换 \t 符号: runoob  12345   abc
使用 2 个空格替换 \t 符号: runoob  12345 abc
使用 3 个空格: runoob   12345 abc
使用 4 个空格: runoob  12345   abc
使用 5 个空格: runoob    12345     abc
使用 6 个空格: runoob      12345 abc
```

#### 统计字符次数
**45.count()** 

**描述**:用于统计字符串里某个字符出现的次数。可选参数为在字符串搜索的开始与结束位置。

**语法**: str.count(sub, start= 0,end=len(string))

- sub -- 搜索的子字符串
- start -- 字符串开始搜索的位置。默认为第一个字符,第一个字符索引值为0。
- end -- 字符串中结束搜索的位置。字符中第一个字符的索引为 0。默认为字符串的最后一个位置。

**示例**
```python
s = 'www.xrloft.com'
print(s.count('o'))  # 返回2
print(s.count('o',0,9)) # 返回1
```

