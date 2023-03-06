---
title: Hexo图片加载动画
copyright_author: 林中的猫
categories: Hexo
abbrlink: a16629f9
date: 2023-03-03 21:31:16
updated:
tags:
keywords:
description:
top_img: 
comments:
cover: https://obsidian-1306832247.cos.ap-nanjing.myqcloud.com/life/Home03.jpg
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
图片懒加载
1.新增hexo-lazyload-image模块

npm install hexo-lazyload-image --save

2.在主目录配置文件_config.yml增加配置

```yaml
lazyload:
  enable: true
  loadingImg: /img/loading.gif
```

这个就是图片没加载出来的时候，出现一个动图转转转的文章页样式