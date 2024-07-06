---
title: Solitude：实用技巧
description: 收集一些使用 Solitude 的实用技巧。
recommend: true
sticky: 1
tags:
  - 网站搭建
categories:
  - Solitude
abbrlink: 2135ef16
date: 2024-07-04 00:00:00
cover: https://s3.qjqq.cn/47/668696d14d29c.gif!color
---

## 文章置顶

在新建文章的`Front-matter`添加`sticky: 1`，其中数字越大，置顶优先级越高。

```markdown
---
title: Solitude：实用技巧
date: 2024-07-04 00:00:00
description: 收集一些使用 Solitude 的实用技巧。
recommend: true
tags:
  - 网站搭建
categories:
  - Solitude
sticky: 1
---
```

## 文章封面尺寸大小

根据 Heo 的设计，使用 `508x225` 的尺寸作为文章封面的大小。

## 使用青秸的卜算子

```yaml
busuanzi: true
busuanzi_use: 1 # 0: 原版 / 1: 青秸(other: 其它自定義的busuanzi平台)
CDN:
  option:
    busuanzi_qj_js: https://pv.lemonso.com/js
```