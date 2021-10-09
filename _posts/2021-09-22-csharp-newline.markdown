---
layout: post
title: C#中的几种换行符
date: 2021-9-22 19:20:23 +0900
category: Unity
---
1.Windows 中的换行符“\r\n”

2.Unix/Linux 平台换行符是 “\n”

3.MessageBox.Show() 的换行符为 “\n”

4.Console 的换行符为 “\n”

换行符还因平台差异而不同。
为保持平台的通用性，可以用系统默认换行符
`System.Environment.NewLine`
