---
title: Hexo自定义生成永久短链接
copyright_author: 林中的猫
abbrlink: 10aa1d61
date: 2023-03-03 15:58:40
updated:
tags:
categories: Hexo
keywords: 'hexo'
description: 对于Hexo的一些使用使用技巧
top_img: https://obsidian-1306832247.cos.ap-nanjing.myqcloud.com/hexo/Home06.jpg
comments:
cover: https://obsidian-1306832247.cos.ap-nanjing.myqcloud.com/hexo/Home06.jpg
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
permalink: posts/:abbrlink.html  # 此处可以自己设置,也可以直接使用 :/abbrlink;posts是自定义前缀。
abbrlink:
    alg: crc32   #算法： crc16(default) and crc32
    rep: hex     #进制： dec(default) and hex
```

###### 配置完成后生成（官方样例）

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

生成完后，原md文件的Front-matter 内会增加abbrlink 字段，值为生成的ID 。这个字段确保了在我们修改了Front-matter 内的博客标题title或创建日期date字段之后而不会改变链接地址。

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
