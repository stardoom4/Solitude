---
title: 'Solitude: 添加豆瓣页并自定义样式'
categories:
  - 网站搭建
tags:
  - Hexo
  - Solitude
cover: 'https://s3.qjqq.cn/47/66225241c85f6.webp!color'
abbrlink: a2fcd92c
date: 2024-03-28 08:00:00
update: 2024-03-28 08:00:00
---

{% note info simple %}
写在前面：主题将在 1.8.10 版本后不再内置豆瓣页样式，如需使用请自行添加。
{% endnote %}

## 介绍

通过豆瓣页展示你的豆瓣信息

## 教程

1. 使用命令安装插件
    ```bash
    npm i hexo-douban --save
    ```
2. 在站点配置文件 _config.yml 中添加豆瓣配置，具体可以参照项目文档
    ```yaml
    douban:
        id: 270559401
        builtin: true
        item_per_page: 10
        meta_max_line: 4
        customize_layout: page
        book:
            path: books/index.html
            title: '我的书单'
            quote: '读书之乐，无穷无尽。'
            option:
            cover: ''
            type: banner # 这里选择banner可以添加顶部banner，不填则不添加
            desc: '记录了我读过的书籍。'
            leftend: '与书为伴，与书为友。'
            rightbtn: '部署项目'
            rightbtnlink: ''
        timeout: 10000
    ```
3. 使用 hexo douban 命令生成豆瓣页
4. 运行 hexo server 查看效果
5. 使用自定义样式，添加到自定义样式文件中
```css
.hexo-douban-items {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    flex-direction: row;
}
.hexo-douban-items .hexo-douban-comment {
    display: none;
}
.hexo-douban-items .hexo-douban-item {
    position: relative;
    width: calc(100% / 4 - 9px);
    border-radius: 12px;
    border: var(--style-border);
    box-shadow: var(--efu-shadow-border);
    background: var(--efu-card-bg);
    transition: 0.3s;
    animation: slide-in 0.6s 0.3s backwards;
    border: var(--style-border);
    margin: 8px 0;
    height: 160px;
    min-height: 160px !important;
    overflow: hidden;
}
@media screen and (max-width: 1200px) {
    .hexo-douban-items .hexo-douban-item {
        width: calc(100% / 3 - 9px);
    }
}
@media screen and (max-width: 899px) {
    .hexo-douban-items .hexo-douban-item {
        width: calc(100% / 2 - 9px);
    }
}
@media screen and (max-width: 600px) {
    .hexo-douban-items .hexo-douban-item {
        width: 100%;
    }
}
.hexo-douban-items .hexo-douban-item:hover {
    border-color: var(--efu-main);
}
.hexo-douban-items .hexo-douban-item .hexo-douban-picture {
    width: 120px;
    height: 100%;
    top: 0;
    padding: 10px;
}
.hexo-douban-items .hexo-douban-item .hexo-douban-picture img {
    margin: 0;
    height: 100%;
    max-width: 100%;
    border-radius: 6px;
}
.hexo-douban-items .hexo-douban-item .hexo-douban-info {
    display: flex;
    flex-wrap: wrap;
    align-content: flex-start;
    height: 100%;
    position: relative;
}
.hexo-douban-items .hexo-douban-item .hexo-douban-info .hexo-douban-rating {
    position: absolute;
    bottom: 5px;
    line-height: 16px;
}
.hexo-douban-items .hexo-douban-item .hexo-douban-info .hexo-douban-meta {
    display: -webkit-box;
    overflow: hidden;
    -webkit-box-orient: vertical;
}
@media screen and (max-width: 1300px) {
    .hexo-douban-items .hexo-douban-item .hexo-douban-info .hexo-douban-meta {
        -webkit-line-clamp: 3 !important;
    }
}
@media screen and (max-width: 899px) {
    .hexo-douban-items .hexo-douban-item .hexo-douban-info .hexo-douban-meta {
        -webkit-line-clamp: 4 !important;
    }
}
.hexo-douban-items .hexo-douban-item .hexo-douban-info .hexo-douban-title {
    transition: all 0.2s ease 0s;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    width: 100%;
}
.hexo-douban-items .hexo-douban-item .hexo-douban-info .hexo-douban-title a {
    border-bottom: 0;
}
.hexo-douban-items .hexo-douban-item .hexo-douban-info .hexo-douban-title a:hover {
    background: none;
    color: var(--efu-main);
}
.hexo-douban-pagination {
    margin-top: 1.25rem;
    animation: slide-in 0.6s 0.3s backwards;
}
.hexo-douban-pagination .hexo-douban-button {
    background: var(--efu-card-bg);
    height: 2rem;
    line-height: calc(2rem - 2px);
    border-radius: 8px !important;
    margin: 0 0.3rem;
    padding: 6px 12px;
    box-shadow: var(--efu-shadow-border);
    border: var(--style-border);
    transition: 0.3s;
    display: inline-flex;
    align-items: center;
}
.hexo-douban-pagination .hexo-douban-button:hover {
    background: var(--efu-main);
}
.hexo-douban-tabs {
    white-space: nowrap;
    overflow: hidden;
    display: flex;
    padding: 0.4rem 1rem 0.4rem 1rem;
    background: var(--efu-card-bg);
    border-radius: 12px;
    border: var(--style-border);
    animation: slide-in 0.6s 0.3s backwards;
}
.hexo-douban-tabs:hover {
    border-color: var(--efu-main);
}
.hexo-douban-tabs a {
    padding: 0.1rem 0.5rem;
    margin-right: 6px;
    font-weight: 700;
    border-radius: 8px !important;
    border-bottom: 0;
}
.hexo-douban-tabs .hexo-douban-tab-active {
    background: var(--efu-main);
}
```
5. 添加到页面
    ```yaml
    extends:
        head: # 在head中插入 / Insert in head
            - <link rel="stylesheet" href="/css/custom.css">
    ```
## 寻找豆瓣ID
1. 注册并登录豆瓣
2. 拖拽这张照片到浏览器地址栏，可在地址后缀中看到你的豆瓣ID
    ![](https://s3.qjqq.cn/47/66224fe99d9be.webp!color)
3. 地址栏ID即为你的豆瓣ID
    ![](https://s3.qjqq.cn/47/662250284b8bd.webp!color)
## 预览
![](https://s3.qjqq.cn/47/66225082097ea.webp!color)