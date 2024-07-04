---
title: 'Solitude: 渲染器 markdown-it'
categories:
  - 网站搭建
tags:
  - Hexo
  - Solitude
cover: 'https://s3.qjqq.cn/47/661e6a863673e.webp!color'
abbrlink: 941787ac
date: 2024-03-28 08:00:00
update: 2024-03-28 08:00:00
---

## 安装

1. 安装插件
    ```bash
    npm un hexo-renderer-marked --save # 卸载默认渲染器
    npm i hexo-renderer-markdown-it # 安装高阶渲染器
    ```
2. 添加配置信息
    ```yaml
    markdown:
        preset: 'default' # 使用的 MD 语法，默认使用的 GFM
        render:
            html: true # 渲染 html
            xhtmlOut: false
            langPrefix: 'language-' # 在代码块的类名中添加前缀（指定语言时）。
            breaks: true
            linkify: true # 如果你写了一个链接而不是 [name](link) 方式，会自动识别为链接并渲染。
            typographer: true # 将替换常见的印刷元素。
            quotes: '“”‘’' # 替换文章张的 "" '' 号
        enable_rules:
        disable_rules:
        plugins: # 使用插件
        anchors:
            level: 2 # 渲染标题的级别（h1,h2,h3）
            collisionSuffix: ''
            permalink: true
            permalinkClass: 'headerlink'
            permalinkSide: 'left'
            permalinkSymbol: ''
            case: 0
            separator: '-'
        images: # 图片的一些编译
            lazyload: true # 是否需要渲染 lazyload
            prepend_root: false
            post_asset: false
        inline: false
    ```

## 使用 Katex

1. 安装插件
    ```bash
    npm i @renbaoshuo/markdown-it-katex --save
    ```
2. 修改Hexo配置文件
    ```yaml
    markdown:
        preset: 'default'
        render:
            html: true
            xhtmlOut: false
            langPrefix: 'language-'
            breaks: true
            linkify: true
            typographer: true
            quotes: '“”‘’'
        enable_rules:
        disable_rules:
        plugins:
        +    - '@renbaoshuo/markdown-it-katex'
        anchors:
            level: 2
            collisionSuffix: ''
            permalink: true
            permalinkClass: 'headerlink'
            permalinkSide: 'left'
            permalinkSymbol: ''
            case: 0
            separator: '-'
        images:
            lazyload: true
            prepend_root: false
            post_asset: false
        inline: false
    ```
3. 修改主题配置文件
    ```yaml
    katex:
        enable: true
        per_page: true # 是否在每页都加载 / Whether to load on each page
        copytex: true # 是否开启复制公式 / Whether to enable copy formula
    ```