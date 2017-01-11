---
title: 使用PIP管理Python模块（Use pip install package）
date: 2016-06-12 20:41:19
tags: python
---

## 简介
Pip是管理Python模块的工具，目前Python3中已经包含，但是Python2中没有。
使用Pip可以很好管理Python模块，例如安装某一模块。

## 安装pip
安装PIP最简单的方式是利用PIP源码安装：[获取pip](https://pypi.python.org/pypi/pip)
解压缩代码压缩包，进入路径，运行setup.py即可。具体如下所示。
```
python setup.py install
```

## 安装模块
PIP安装好之后，就可以很简单地利用其安装其他模块了。具体如下所示。

```
	 python -m pip install PackageName
```