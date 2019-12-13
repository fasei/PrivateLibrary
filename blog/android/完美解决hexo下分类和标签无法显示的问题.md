---
title: 完美解决hexo下分类和标签无法显示的问题
tags: [hexo,tools]
date: 2019-02-22
categories: hexo
---

# 概述

今天更换了一个新的主题，之后发现无法正常添加 分类页 和 标签页，经过一下午的研究，终于找到了最完美的解决方案。

<!--more-->

## 步骤一
你需要在 hexo 根目录的 source 文件夹下新建一个 tags 文件夹，然后在 tags 文件夹里面新建一个 index.md 文件。快捷命令为：

```
 hexo new page "tags"

```

## 步骤二
编辑 index.md 文件，内容如下：

```
---
title: "tags"
type: tags
layout: "tags"
---
```

重点来了:

**注意！这里面最重要的就是 layout 选项，后面的参数对应的是你 主题文件夹下 layout 文件夹下第一级的布局文件。比如，我的主题是用 ejs 写的，那么对应的就是 layout/tags.ejs，如果没有，那么就会出现空白的现象！如果你的 tags 文件的命名时 a.ejs，那么你就应该写成 layout: "a"。
**

## 步骤三

编辑主题配置文件:
```
nav:
  home: /
  about: /about
  tags: /tags

```
## 步骤四
编辑 hexo 配置文件 Directory 选项。

检查一下名称是否对应

```
# Directory
tag_dir: tags


```
至此，完美解决。

最重要的就是看一下你的主题文件里有没有标签页或者分类页的布局文件，一般来说都是有的，只是命名和存放的位置可能不同，所以大家要根据实际情况来修改。



















