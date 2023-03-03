---
title: Hexo自定义生成永久短链接
copyright_author: 林中的猫
abbrlink: 10aa1d61
date: 2023-03-03 15:58:40
updated:
tags:
categories: Hexo
keywords:
description:
top_img:
comments:
cover:
toc:
toc_number:
toc_style_simple:
copyright:
copyright_author_href:
copyright_url:
copyright_info:
mathjax:
katex:
aplayer:
highlight_shrink:
aside:
---

在写博客的时候，一些文件，文件夹难免会写成中文。这就导致生成的最终链接带有中文，然后以复制，中文将会翻译成英文，一大串，令人窝心，昨天在逛Hexo官方插件的时候突然发现了这个插件`hexo-abbrlink`，该插件是根据帖子标题生成静态帖子链接.使用过后觉得不错，推荐给大家。

### 安装步骤

##### 安装插件

```
npm install hexo-abbrlink --save
```

##### 修改config.yml文件中的permalink

```
permalink: posts/:abbrlink/
```

###### 两种算法

```
alg -- Algorithm (currently support crc16 and crc32, which crc16 is default)
rep -- Represent (the generated link could be presented in hex or dec value)
```

###### 算法设置

```
# abbrlink config
abbrlink:  
  alg: crc32  #support crc16(default) and crc32
  rep: hex    #support dec(default) and hex
```

可选模式：

- crc16 & hex
- crc16 & dec
- crc32 & hex
- crc32 & dec

###### 配置完成后

```
permalink: posts/:abbrlink/
abbrlink:  
  alg: crc32  # 算法：crc16(default) and crc32
  rep: hex    # 进制：dec(default) and hex
```

## 样品

所生成的链接如下 ：

```
crc16 & hex
https://post.zz173.com/posts/66c8.html

crc16 & dec
https://post.zz173.com/posts/65535.html
crc32 & hex
https://post.zz173.com/posts/8ddf18fb.html

crc32 & dec
https://post.zz173.com/posts/1690090958.html
```

### 模板文件修改（自选）

在博客所在的文件夹里，搜索文件夹`scaffolds`，找到模板文件`post.md`
推荐修改成的格式：

```
title: {{ title }}
date: {{ date }}
comments: true
categories:
tags:
```
