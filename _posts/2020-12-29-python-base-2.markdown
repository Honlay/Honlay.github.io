---
layout: post
title: 【Python基础2】安装并配置Anaconda环境
date: 2020-12-29 02:20:23 +0800
category: Python 
---



## 简介

官网:https://www.anaconda.com

Anaconda是一个用于科学计算的Python发行版，适用于数据分析的Python工具，也可以用在大数据和人工智能领域。

- 支持Linux、Mac、Windows系统
- 包含了Python和相关的配套工具，包括许多非常有用的第三方库;
- 利用Conda来管理包和运行环境，可以很方便地解决多版本python并存、切换以及各种第三方包安装问题;

### Conda

用来管理包、依赖与环境的工具（可执行命令）

- 包管理：与pip类似，conda将所有工具、第三方包都当做package来管理（包括python和conda自身），而且能够安装非python的包；
- 环境管理：可以方便地安装各种版本python、各种package、创建虚拟环境并快速切换；
- 文档：https://conda.io/docs/index.html
- Getting started：https://conda.io/docs/user-guide/getting-started.html
- Conda cheat sheet：https://conda.io/docs/_downloads/conda-cheatsheet.pdf

### Anaconda

Python的一种发行版，是一个打包的集合（预装好了conda、某个版本的python、众多packages、科学计算工具等），占用空间较大；

- 文档：http://docs.anaconda.com/anaconda/
- User guide：https://docs.anaconda.com/anaconda/user-guide/
- Getting started：http://docs.anaconda.com/anaconda/user-guide/getting-started/
- Anaconda cheat sheet：http://docs.anaconda.com/anaconda/user-guide/cheatsheet/

### Miniconda

- 只包含最基本的内容（python与conda，以及相关的必须依赖项）的命令行工具，适合对于空间要求严格的用户；

### Conda与Anaconda的联系与区别

Conda可以理解为一个工具，也是一个可执行命令，其核心功能是包管理与环境管理。包管理与pip的使用类似，环境管理则允许用户方便地安装不同版本的python并可以快速切换。
Anaconda则是一个打包的集合，里面预装好了conda、某个版本的python、众多packages、科学计算工具等等，所以也称为Python的一种发行版。

## 安装

官方下载：

- https://www.anaconda.com/download/
- https://repo.anaconda.com/
- https://repo.anaconda.com/archive/

清华大学anaconda镜像：

- https://mirrors.tuna.tsinghua.edu.cn/anaconda/
- archive：https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/
- miniconda：https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/
- pkgs： https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/

下载后根据提示进行安装，安装完成后内容如下：

- Anaconda Navigtor ：用于管理工具包和环境的图形用户界面，管理命令也可以在 Navigator 中手工实现。
- Anaconda Prompt ：Anaconda的命令行，通过conda命令可以控制和配置Python运行环境。
- Jupyter notebook ：基于web的交互式计算环境，可以编辑易于阅读的文档和展示数据分析的过程。
- Spyder：使用Python语言、跨平台的、科学运算集成开发环境。
- Reset Spyder Settings：恢复Spyder的默认设置。
  安装Anaconda完成后，Path环境变量将指向Anaconda自带的Python，其内置的第三方模块安装在自己的路径下，不影响系统已安装的Python目录；

## 使用conda进行环境管理和包管理

conda时anaconda中的环境管理器和包管理器
对于conda的操作都发生在命令行内，我们可以打开Anaconda Prompt进行操作。

### 检查conda

在使用conda前，我们先检查conda是否已经被安装，以及当前版本是否最新

```python
# 检查conda是否已经安装好，此命令会返回你安装的conda版本
conda --verson
>> conda 4.9.2
# 通过以下命令升级conda到最新版本
# 如果有新版可用，在提示proceed ([y]/n)? 中输入y进行升级
conda update conda
```

### 环境管理

环境管理是Python使用中的一大好习惯，如果你不想在一遍遍重装Python和系统中折腾循，那么环境管理是学习Python的过程中非常必要的一环。现在我们用conda进行环境管理。

#### 创建环境

```python
# 创建一个环境名为py34，指定Python版本是3.4
#（不用管是3.4.x，conda会为我们自动寻找3.4.x中的最新版本）
conda create --name py34 python=3.4
# 通过创建环境，我们可以使用不同版本的Python
conda create --name py27 python=2.7
```

#### 激活环境

```python
# 在windows环境下使用activate激活
activate py34

# 在Linux & Mac中使用source activate激活
source activate py34
```

激活后，会发现terminal输入的地方多了(py34)的字样，这表示我们已经进入了py34的环境中。

#### 退出环境

```python
# 在windows环境下使用deactivate
deactivate

# 在Linux & Mac中使用source deactivate
source deactivate
```

#### 删除环境

如果你不想要这个名为py34的环境，可以通过以下命令删除这个环境。

`conda remove -n py34 --all`

可以通过以下命令查看已有的环境列表，现在py34已经不在这个列表里，所以我们知道它已经被删除了。

`conda info -e`

### 包管理

我们使用conda进行第三方包的安装、卸载和更新。

对于包的下载，我们可以先设置国内镜像。这是因为Anaconda的服务器在国外，所以conda在下载包的时候速度往往很慢。所幸清华TUNA镜像有Anaconda仓库的镜像，我们将其加入conda的配置，即可解决这个问题。

```python
# 添加Anaconda的TUNA镜像
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
```

接下来我们进行包的安装，请进入指定的环境中（比如上节中的py34），这里我们以pandas（一个数据处理和分析的包）为例进行操作。

#### 查看已安装的包

```python
#使用这条命令来查看在当前环境中，已安装的包和对应版本
conda list
```

#### 查找可安装的包

```python
#我们可以通过search命令检查pandas这个包是否可以通过conda来安装
#命令返回了这个包的信息，所以是可以通过conda安装的
conda search pandas
```

#### 安装包

```python
#通过install安装pandas
#如果pandas已经存在于环境中，会提示已经安装，否则在提示proceed ([y]/n)? 中输入y进行安装
conda install pandas
```

#### 更新包

```python
#通过update更新pandas
conda update pandas
```

#### 卸载包

```python
#通过remove卸载pandas
conda remove pandas
```

以上就是conda对于包的安装、更新和卸载。值得一提的是，conda将conda、python等都视为包，因此，完全可以使用conda来管理conda和python的版本，例如

```python
# 更新conda到最新版本，这里conda被当作一个包处理 
conda update conda 

# 同样的，也可以更新anaconda到最新版本
conda update anaconda

# 更新python
# 例如我们所启用的环境是py34，使用的是python3.4,那么conda会将python升级为3.4.x系列中的最新版本
conda update python 
```

