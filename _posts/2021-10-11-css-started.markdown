---
layout: post
title: CSS快速入门
date: 2021-10-11 10:35:23 +0800
category: web
---



## 1.CSS简介

### 1.1 CSS是什么？CSS作用是什么？

> CSS（Cascading Style Sheet，可以译为“层叠样式表”或“级联样式表”），是一组格式设置 规则，用于控制web页面的外观。

### 1.2 如何让一个标签具有样式

1. 必须保证引入方式正确
2. 必须让css和html元素产生关联，也就是说得先找到这个元素
3. 用相应的css属性去修改html元素的样式

### 1.3 CSS的三种引入形式

#### 1.3.1 将css内嵌到html文件中，这种方式写的css又叫内联样式表，例如

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				/* css代码 */
				color: red;
			}
		</style>
	</head>
	<body>
		<!-- 通过自定义名字来产生关联 -->
		<div id="box">
			这是一个盒子
		</div>
	</body>
</html>
```

#### 1.3.2 将一个外部样式链接到html文件中，这种方式写的css又叫链接样式表，例如：

html文件

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<!-- css链接地址,好处：让html代码和css代码分离，方便维护 -->
		<link rel="stylesheet" type="text/css" href="style/index.css"/>
	</head>
	<body>
		<!-- 通过自定义名字来产生关联 -->
		<div id="box">
			这是一个盒子
		</div>
	</body>
</html>
```

index.css

```css
#box{
	color: aqua; 
}
```

#### 1.3.3 将样式表加入到html文件中，这种方式写入的css样式又叫行内样式表

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<!-- 行内样式表 -->
		<div style="color: green;">
			这是一个盒子
		</div>
	</body>
</html>

```



## 2.基础选择器

**CSS的书写规则**

```css
选择器{
    属性名称1：属性值1;
    属性名称2：属性值2;
    ...
}
```

选择器：查找html标签的方法

#### 2.1 id选择器

> ID选择器与类选择器的定义与引用方式类似，只是定义的符号不一样。ID通常表示唯一 值，因此，ID选择器在CSS 中通常只出现一次。如果出现多次也能解析，但是不建议这样使用

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 100%;
				height: 100px;
				background: blue;
			}
		</style>
	</head>
	<body>
		<div id="box">
			这是一个盒子
		</div>
	</body>
</html>
```

#### 2.2 类选择器

> 类（class）选择器就是将相同类型的元素进行分类定义，分类定义的好处就是能够复用。
>
> 在类名前面加符号”.”，表示定义一个类选择器，引用的时候在标签后面加class 引 用 ；例如：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			.box{
				width: 100%;
				height: 100px;
				background: yellow;
			}
		</style>
	</head>
	<body>
		<div class="box">
			这是一个盒子
		</div>
	</body>
</html>

```

#### 2.3 标签选择器

> 标签选择器就是直接使用HTML标签名称作为CSS选择器的名称，这种方式会影响 HTML中所有此标签的样式；例如：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			div{
				width: 100%;
				height: 100px;
				background: yellow;
			}
		</style>
	</head>
	<body>
		<div>床前明月光</div>
		<div>疑是地上霜</div>
	</body>
</html>
```



### 三种基础选择器的应用场景和区别

- id：名称不会出现多次，表示唯一，如果网页中有一个唯一的元素需要修饰，用id
- 类：名称可以出现多次，修饰同一类型元素，有多个元素具有同一样式时，可以用类选择器
- 标签：通过标签名称，可以选中所有同名的标签

## 3.基本属性

### 3.1 颜色表示方式

#### 3.1.1 RGB模式

> RGB模式，红(R)、绿(G)、蓝(B)每个的取值范围0~255

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<div style = color:rgb(255,0,0)>
			我是红色的
		</div>
	</body>
</html>
```

#### 3.1.2 RGBA模式

> RGBA模式，RGBA是代表Red（红色） Green（绿色） Blue（蓝色）和 Alpha的(色彩 空间)透明度，color：rgba（255,255,255,0.5)；A 透明度的取值范围是0~­1

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<div style = color:rgb(255,0,0,0.5)>
			我是红色半透明的
		</div>
	</body>
</html>

```

#### 3.1.3 16进制

> 16进制，用16进制表示颜色值，如#FF0000,#00FF00，可以简写成#F00，#0F0

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<div style = color:#000>
			我是黑色的
		</div>
	</body>
</html>
```

#### 3.1.4 颜色名称

> 颜色名称,直接用颜色名称表示颜色，如：red、green、blue、yellow等等

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<div style = color:blue>
			我是蓝色的
		</div>
	</body>
</html>

```

### 3.2 边框的相关属性

#### 3.2.1 设置四边边框

边框风格样式的属性值

- none 无边框
- solid 直线边框
- dashed 虚线边框
- dotted 点状边框
- double 双线边框

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 100px;
				height: 100px;
				background-color: orangered;
				border: solid;
			}
		</style>
	</head>
	<body>
		<div id="box">
		</div>
	</body>
</html>
```

#### 3.2.2 设置四边框的宽度

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 100px;
				height: 100px;
				background-color: orangered;
				border: solid;
				border-width: 5px;
			}
		</style>
	</head>
	<body>
		<div id="box">
		</div>
	</body>
</html>
```

#### 3.2.3 设置边框颜色

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 100px;
				height: 100px;
				background-color: orangered;
				border: solid;
				border-width: 5px;
				border-color: aqua;
			}
		</style>
	</head>
	<body>
		<div id="box">
		</div>
	</body>
</html>

```

#### 3.2.4 boder属性简写

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 100px;
				height: 100px;
				background-color: orangered;
				border: 3px solid blue;
			}
		</style>
	</head>
	<body>
		<div id="box">
		</div>
	</body>
</html>
```



#### 3.2.5 单独设置某边框

边框分为 border-left,border-top,border-right,border-bottom

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 100px;
				height: 100px;
				background-color: orangered;
				border-left: 3px solid blue;
			}
		</style>
	</head>
	<body>
		<div id="box">
		</div>
	</body>
</html>
```

#### 3.2.6 圆角边框

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 100px;
				height: 100px;
				background-color: orangered;
				border: solid;
				border-width: 5px;
				border-color: aqua;
				/* 所有角都设置为圆角 */
				border-radius: 20px;
				/* 后面给两个值 */
				border-radius: 0px 20px;   /* 0px表示上左、下右两个角 20px 上右、下左两个角 */ 
				/* 后面给3个值 */
				border-radius: 10px 0px 20px; /*10上左  0px 上右、下左 20px 下右  */
				/* 后面给4个值 */
				border-radius: 5px 10px 15px 20px; /*上左  上右 下右 下左 */
				
			}
		</style>
	</head>
	<body>
		<div id="box">
		</div>
	</body>
</html>

```

#### 3.2.7 设置半圆

> 把高度设置成宽度的一半 并且只设置下左和下右两个角的值,设置的值为宽度的一半

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 100px;
				height: 50px;
				background-color: orangered;
				border: solid;
				border-width: 5px;
				border-color: aqua;
				border-radius: 0px 0px 50px 50px; /*上左  上右 下右 下左 */
			}
		</style>
	</head>
	<body>
		<div id="box">
		</div>
	</body>
</html>

```

#### 3.2.8 设置圆形

> 把高度和宽度设置成一样，并且把四个圆都设置成宽高的一半

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 100px;
				height: 100px;
				background-color: orangered;
				border: solid;
				border-width: 5px;
				border-color: aqua;
				border-radius: 50%; /* 注意：单位不仅可以用px，还可以用百分比% */
			}
		</style>
	</head>
	<body>
		<div id="box">
		</div>
	</body>
</html>

```

### 3.3 背景相关属性

#### 3.3.1 背景颜色

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 100px;
				height: 100px;
				background-color: blue; /*设置背景颜色*/
			}
		</style>
	</head>
	<body>
		<div id="box">
		</div>
	</body>
</html>
```

#### 3.3.2 背景图片

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 800px;
				height: 800px;
				background-image: url(../img/1.jpg) /*设置背景图片*/
			}
		</style>
	</head>
	<body>
		<div id="box">
		</div>
	</body>
</html>
```

#### 3.3.3 背景重复

> 重复平铺满 repeat;
>
> 向Y轴重复 repeat­y;
>
> 向X轴重复 repeat­x;
>
> 不重复 no-­repeat; 

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 500px;
				height: 500px;
				background-image: url(../img/1.jpg);
				background-repeat: repeat;
			}
		</style>
	</head>
	<body>
		<div id="box">
		</div>
	</body>
</html>

```

#### 3.3.4 背景位置

> 横向（left,center,right）; 
>
> 纵向（top,center,bottom ;

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				width: 500px;
				height: 500px;
				border: solid;
				background-image: url(../img/1.jpg);
				background-repeat: no-repeat;
				background-position: left top; 
			}
		</style>
	</head>
	<body>
		<div id="box">
		</div>
	</body>
</html>
```

### 3.4 字体相关属性

#### 3.4.1 定义字体 font-family

> 字体可以定义多个，使用","隔开，确保当字体不存在的时候直接使用下一个

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				font-family: 华文黑体,serif;
			}
		</style>
	</head>
	<body>
		<div id="box">
			字体可以定义多个，使用","隔开，确保当字体不存在的时候直接使用下一个。
		</div>
	</body>
</html>

```

#### 3.4.2 设置字体大小 font-size

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				font-family: 华文黑体,serif;
				font-size: 20px;
			}
		</style>
	</head>
	<body>
		<div id="box">
			字体可以定义多个，使用","隔开，确保当字体不存在的时候直接使用下一个。
		</div>
	</body>
</html>

```

#### 3.4.3 字体粗细

> font-weight;normal(默认值)、bold(粗)、bolder(更粗)、lighter(更细)

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				font-family: 华文黑体,serif;
				font-size: 20px;
				font-weight: bold;
			}
		</style>
	</head>
	<body>
		<div id="box">
			字体可以定义多个，使用","隔开，确保当字体不存在的时候直接使用下一个。
		</div>
	</body>
</html>

```

#### 3.4.4 字体颜色 color

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				font-family: 华文黑体,serif;
				font-size: 20px;
				font-weight: bold;
				color: red;
			}
		</style>
	</head>
	<body>
		<div id="box">
			字体可以定义多个，使用","隔开，确保当字体不存在的时候直接使用下一个。
		</div>
	</body>
</html>

```



### 3.5 文本相关属性

#### 3.5.1 横行排列 text-align

> text­-align,横行排列，值：center 居中，left靠左，right 靠右

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				font-family: 华文黑体,serif;
				font-size: 20px;
				font-weight: bold;
				color: red;
				text-align: left;
			}
		</style>
	</head>
	<body>
		<div id="box">
			字体可以定义多个，使用","隔开，确保当字体不存在的时候直接使用下一个。字体可以定义多个，使用","隔开，确保当字体不存在的时候直接使用下一个。
		</div>
	</body>
</html>
```

#### 3.5.2 文本行高

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				
				font-family: 华文黑体,serif;
				font-size: 20px;
				font-weight: bold;
				color: red;
				text-align: left;
				line-height: 50px;
			}
		</style>
	</head>
	<body>
		<div id="box">
			字体可以定义多个，使用","隔开，确保当字体不存在的时候直接使用下一个。字体可以定义多个，使用","隔开，确保当字体不存在的时候直接使用下一个。
		</div>
	</body>
</html>

```

#### 3.5.3 字符间距 letter-spaceing

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			#box{
				
				font-family: 华文黑体,serif;
				font-size: 20px;
				font-weight: bold;
				color: red;
				text-align: left;
				line-height: 50px;
				letter-spacing: 10px;
			}
		</style>
	</head>
	<body>
		<div id="box">
			字体可以定义多个，使用","隔开，确保当字体不存在的时候直接使用下一个。字体可以定义多个，使用","隔开，确保当字体不存在的时候直接使用下一个。
		</div>
	</body>
</html>

```



