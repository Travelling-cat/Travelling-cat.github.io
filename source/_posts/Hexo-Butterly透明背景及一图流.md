---
title: Hexo-Butterly透明背景及一图流
copyright_author: 林中的猫
abbrlink: 3ef3bd48
date: 2023-03-06 19:38:44
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

# Hexo-Butterly透明背景及一图流

## 一图流效果

<img src="https://obsidian-1306832247.cos.ap-nanjing.myqcloud.com/hexo/Hexo%E4%B8%80%E5%9B%BE%E6%B5%81%E6%96%87%E7%AB%A0.jpg"/>

## **设置图片**

Butterfly自带主题修改功能，位于文件 `_config.butterfly.yml`。

设置网站背景，并将主页顶部图和页脚背景设为透明。

```
# Image (圖片設置)
# --------------------------------------

# The banner image of home page
index_img: transparent

# Beautify/Effect (美化/效果)
# --------------------------------------

# Website Background (設置網站背景)
# can set it to color or image (可設置圖片 或者 顔色)
# The formal of image: url(http://xxxxxx.com/xxx.jpg)
background: url(https://example.com/img/background.jpg)

# Footer Background
footer_bg: transparent
```

## 引入一图流相关样式

新建一个文件，位于 `source/css/modify.styl`，并增加一下内容（可自行修改）

```
@import 'nib'

// 顶部图
#page-header
  &, &:before
    background: transparent !important
  &.post-bg, &.not-home-page
    height: 280px !important
  #post-info
    bottom: 40px !important
  #page-site-info
    top: 140px !important

  @media screen and (max-width: 768px)
    &.not-home-page
      height: 200px !important
    #post-info
      bottom: 10px !important
    #page-site-info
      top: 100px !important

.top-img
  height: 250px
  margin: -50px -40px 50px
  border-top-left-radius: inherit
  border-top-right-radius: inherit
  background-position: center center
  background-size: cover
  transition: all 0.3s

  @media screen and (max-width: 768px)
    height: 230px
    margin: -36px -14px 36px

  [data-theme='dark'] &
    filter: brightness(0.8)

// 页脚
#footer:before
  background-color: alpha(#FFF, .5)

  [data-theme='dark'] &
    background-color: alpha(#000, .5)

#footer-wrap, #footer-wrap a
  color: #111
  transition: unset

  [data-theme='dark'] &
    color: var(--light-grey)
```

在主题配置文件 `_config.butterfly.yml` 的 `inject.head` 引入样式。

```
# other (其他)
# --------------------------------------

# Inject
# Insert the code to head (before '</head>' tag) and the bottom (before '</body>' tag)
# 插入代码到头部 </head> 之前 和 底部 </body> 之前
inject:
  head:
    - <link rel="stylesheet" href="/css/modify.css">
```

## 设置透明效果

新建一个文件，位于 `source/css/transpancy.css`，并增加一下内容

```css

/* 文章页背景 */
.layout_post>#post {
    /* 以下代表透明度为0.7 可以自行修改*/
    background: rgba(255,255,255,.7);
}
 
/* 所有页面背景 */
#aside_content .card-widget, #recent-posts>.recent-post-item, .layout_page>div:first-child:not(.recent-posts), .layout_post>#page, .layout_post>#post, .read-mode .layout_post>#post{
    /* 以下代表透明度为0.7 */
    background: rgba(255,255,255,.7);
}
/*侧边卡片的透明度 */
:root {
  --card-bg: rgba(255, 255, 255, .7);
}
/* 页脚透明 */
#footer {
	/* 以下代表透明度为0.7 */
	background: rgba(255,255,255, .0);
}
```

在主题配置文件 `_config.butterfly.yml` 的 `inject.head` 引入样式。

```
# other (其他)
# --------------------------------------

# Inject
# Insert the code to head (before '</head>' tag) and the bottom (before '</body>' tag)
# 插入代码到头部 </head> 之前 和 底部 </body> 之前
inject:
  head:
    - <link rel="stylesheet" href="/css/modify.css">
    - <link rel="stylesheet" href="/css/transpancy.css">
```

修改

本篇文章基于 [@Android](https://android99.com) 大佬写的[Butterfly主题 一图流背景与顶部图修改 ](https://android99.com/2021/08/10/butterfly-top-image-modify/)以及[@LYT](https://blog.lyt11.cn/)大佬写的[hexo butterfly主题设置背景透明度和字体](https://blog.lyt11.cn/posts/ffa37d2ba5f9/))

