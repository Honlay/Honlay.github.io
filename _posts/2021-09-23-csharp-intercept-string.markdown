---
layout: post
title: C#常用截取字符串方法
date: 2021-9-23 19:20:23 +0900
category: Unity
---
```c#
string str ="123abc456";
int i=3;
```
1.取字符串的前i个字符
```c#
str = str.Substring(0,i);
```
或
```c#
str=str.Remove(i,str.Length-i);
```
2.去掉字符串的前i个字符
```c#
str=str.Remove(0,i);
```
或
```c#
 str=str.Substring(i);
```
3.从右边开始取i个字符：
```c#
str=str.Substring(str.Length-i);
```
或
```c#
 str=str.Remove(0,str.Length-i);
```
4.从右边开始去掉i个字符
```c#
str=str.Substring(0,str.Length-i); // or str=str.Remove(str.Length-i,i);
```
5. 判断字符串中是否有“abc” 有则去掉之
```c#
using System.Text.RegularExpressions;
   string str = "123abc456";
   string a="abc";
   Regex r = new  Regex(a);
   Match m = r.Match(str);
   if (m.Success)
   {
    //下面两个取一种即可。
      str=str.Replace(a,"");
      Response.Write(str);  
      string str1,str2;
      str1=str.Substring(0,m.Index);
      str2=str.Substring(m.Index+a.Length,str.Length-a.Length-m.Index);
      Response.Write(str1+str2);
   }
```
6. 如果字符串中有“abc”则替换成“ABC”
```c#
str=str.Replace("abc","ABC");
string str="adcdef"; int indexStart = str.IndexOf("d");
int endIndex =str.IndexOf("e");
string toStr = str.SubString(indexStart,endIndex-indexStart);
```
7.截取字符串最后一个字符的问题!
```c#
str1.Substring(str1.LastIndexOf(",")+1);
```
8.截取字符串最后一个字符
```c#
k = k.Substring(k.Length-1, 1);
```
