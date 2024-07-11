---
title: 'Solitude: 为你的网站添加 51.la 统计'
categories:
  - 网站搭建
tags:
  - Hexo
  - Solitude
  - 51.la
cover: 'https://s3.qjqq.cn/47/661bb928f1af9.webp!color'
abbrlink: a1b5f4a6
date: 2024-03-28 08:00:00
recommend: true
update: 2024-03-28 08:00:00
---

## 介绍

统计访问这信息可以更好的对网站的细节做出调整。

因为大部分人都不知道如何添加统计信息，做教程给大家参考。

## 教程

1. 注册 51.la 账号
    ![](https://s3.qjqq.cn/47/661bb25aa2065.webp!color)
2. 点击应用管理，在 我的应用 > 添加应用统计
    ![](https://s3.qjqq.cn/47/661bb2a224533.webp!color)
3. 点击查看报表，点击配置
    ![](https://s3.qjqq.cn/47/661bb3629680d.webp!color)
4. 选择参数配置，填写基本信息，应用名称随便，统计域名添加需要使用的。
    ![](https://s3.qjqq.cn/47/661bb3bf80bf4.webp!color)
5. 点击统计代码，选择手动安装点击获取 SDK 追踪代码
    ![](https://s3.qjqq.cn/47/661bb40a8f963.webp!color)
    ![](https://s3.qjqq.cn/47/661bb42402d6d.webp!color)
6. 复制同步安装的代码到配置文件extend 处，建议放在body里（下面是演示，请不要直接复制，将链接替换成你自己的）
    ```yaml
    extends:
        head: # 在head中插入 / Insert in head
        body: # 在body中插入 / Insert in body
            - <script charset="UTF-8" id="LA_COLLECT" src="//sdk.51.la/js-sdk-pro.min.js"></script>
            - <script>LA.init({id:"3F15j2vtdTo7PPcN",ck:"3F15j2vtdTo7PPcN"})</script> 
    ```
7. 关于页面展示代码获取
    ![](https://s3.qjqq.cn/47/661bb539ebfc0.webp!color)
8. 将其中的类似 `https://v6-widget.51.la/v6/3F15j2vtdTo7PPcN/quote.js` 的代码复制到 about.yaml 中
```yaml
tj: # 统计
  url: https://v6-widget.51.la/v6/3F15j2vtdTo7PPcN/quote.js # 需要到51la官网注册自行获取
  img: https://s3.qjqq.cn/47/661baa7669e8f.webp!color # 背景 
```

## 效果

![](https://s3.qjqq.cn/47/661bb5c398a33.webp!color)
![](https://s3.qjqq.cn/47/661bb60b6c379.webp!color)