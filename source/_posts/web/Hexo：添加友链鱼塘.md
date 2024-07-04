---
title: Hexo：添加友链鱼塘
categories:
  - 网站搭建
tags:
  - Hexo
cover: 'https://s3.qjqq.cn/47/66224075412c5.webp!color'
abbrlink: d3883050
date: 2024-03-28 08:00:00
update: 2024-03-28 08:00:00
---

{% note success simple no-icon %}
写在前面：主题将在 1.8.10 版本后不再内置友链鱼塘，如需使用请自行添加。

本教程使用Heo的友链鱼塘样式
{% endnote %}

## 介绍

友链鱼塘是一种友链展示方式，可以展示友链的最新文章，让你的网站更加活跃。

## 教程

1. 使用命令创建页面
    ```bash
    hexo new page moments
    ```
2. 将以下内容复制到 source/moments/index.md 中
```markdown
---
title: 友链鱼塘
desc: 最新文章订阅
date: 2024-01-28 21:29:15
type: "banner"
cover: ''
leftend: 使用 友链朋友圈 订阅友链最新文章
---
## 🐟 鱼塘
<div id="hexo-circle-of-friends-root"></div>
<script>
    let UserConfig = {
        private_api_url: 'http://192.168.31.44:8000/', /* 填写你的api地址 */
        page_turning_number: 12, /* 点击加载更多时，一次最多加载几篇文章，默认10 */
        error_img: 'https://sdn.geekzu.org/avatar/57d8260dfb55501c37dde588e7c3852c', /* 头像加载失败时，默认头像地址 */
        sort_rule: 'created', /* 进入页面时第一次的排序规则 */
    };
</script>
   
<style>
    .cf-article-group{
        margin: 0 -8px;
    }   
</style>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/zhheo/JS-Heo@master/mainColor/heoMainColor.css">
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/zhheo/JS-Heo@master/moments5/app.min.js"></script>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/zhheo/JS-Heo@master/moments5/bundle.js"></script>
```

3. 修改 private_api_url 为你的api地址
4. 重新生成网站
    ```bash
    hexo clean && hexo g
    ```

## 添加钓鱼

1. 在 moments/index.md 顶部（front-matter以下）添加以下代码
```markdown
<div class="title-h2-a">
    <div class="title-h2-a-left">
        <h2 style="padding-top: 0;margin:0.6rem 0 0.6rem;">🎣 钓鱼</h2>
        <a href="javascript:fetchRandomPost();" id="random-post-start" style="transition-duration: 0.3s; transform: rotate(63000deg); opacity: 1;" data-pjax-state="">
            <i class="solitude st-restart-line"></i>
        </a>
    </div>
    <div class="title-h2-a-right">
        <a href="/links/" data-pjax-state="">全部友链</a>
    </div>
</div>
<div id="random-post"></div>

<script>
var fdata = {
    apiurl: "http://192.168.31.44:8000/", /* 填写你的api地址 */
    defaultFish: 100,
    hungryFish: 100,
}
</script>

<script type="text/javascript" src="https://cdn.cbd.int/solitude-source@1.0.5/js/moment/random_post.min.js"></script>
```

2. 在 moments/index.md 中的 style 标签里添加以下代码
```css
#random-post {
  min-height: 32px;
  background: var(--efu-card-bg);
  border: var(--style-border-always);
  box-shadow: var(--efu-shadow-border);
  padding: 20px 30px;
  border-radius: 12px;
  margin-top: 8px;
}
.random-friends-post {
  text-decoration: none;
  border-bottom: 2px solid var(--efu-lighttext);
  color: var(--efu-fontcolor);
  font-weight: 700;
  padding: 0 4px;
}
.random-friends-post:hover {
  text-decoration: none;
  border-bottom: 2px solid var(--efu-none);
  color: var(--efu-white);
  background: var(--efu-main);
  border-radius: 4px;
  box-shadow: var(--efu-shadow-main);
}
.random-post-start {
  transition-duration: 0.3s;
}
.random-post-start:hover {
  color: var(--efu-hovertext);
}
#page .title-h2-a {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 0.5rem;
}
#page .title-h2-a a {
  margin-left: 0.5rem;
  color: var(--efu-secondtext);
  font-weight: 700;
}
#page .title-h2-a a:hover {
  color: var(--efu-main);
}
#page .title-h2-a .title-h2-a-left {
  display: flex;
  align-items: center;
}
#page .title-h2-a .title-h2-a-right {
  font-size: 14px;
  color: var(--efu-secondtext);
}
```

## 完整代码

```markdown
---
title: 友链鱼塘
desc: 最新文章订阅
date: 2024-01-28 21:29:15
type: "banner"
cover: ''
leftend: 使用 友链朋友圈 订阅友链最新文章
---

<div class="title-h2-a">
    <div class="title-h2-a-left">
        <h2 style="padding-top: 0;margin:0.6rem 0 0.6rem;">🎣 钓鱼</h2>
        <a href="javascript:fetchRandomPost();" id="random-post-start" style="transition-duration: 0.3s; transform: rotate(63000deg); opacity: 1;" data-pjax-state="">
            <i class="solitude st-restart-line"></i>
        </a>
    </div>
    <div class="title-h2-a-right">
        <a href="/links/" data-pjax-state="">全部友链</a>
    </div>
</div>
<div id="random-post"></div>

<script>
var fdata = {
    apiurl: "http://192.168.31.44:8000/", /* 填写你的api地址 */
    defaultFish: 100,
    hungryFish: 100,
}
</script>

<script type="text/javascript" src="https://cdn.cbd.int/solitude-source@1.0.5/js/moment/random_post.min.js"></script>

## 🐟 鱼塘

<div id="hexo-circle-of-friends-root"></div>
<script>
    let UserConfig = {
        private_api_url: 'http://192.168.31.44:8000/', /* 填写你的api地址 */
        page_turning_number: 12, /* 点击加载更多时，一次最多加载几篇文章，默认10 */
        error_img: 'https://sdn.geekzu.org/avatar/57d8260dfb55501c37dde588e7c3852c', /* 头像加载失败时，默认头像地址 */
        sort_rule: 'created' /* 进入页面时第一次的排序规则 */
    }
</script>
<style>
.cf-article-group {
    margin: 0 -8px;
} 
#random-post {
  min-height: 32px;
  background: var(--efu-card-bg);
  border: var(--style-border-always);
  box-shadow: var(--efu-shadow-border);
  padding: 20px 30px;
  border-radius: 12px;
  margin-top: 8px;
}
.random-friends-post {
  text-decoration: none;
  border-bottom: 2px solid var(--efu-lighttext);
  color: var(--efu-fontcolor);
  font-weight: 700;
  padding: 0 4px;
}
.random-friends-post:hover {
  text-decoration: none;
  border-bottom: 2px solid var(--efu-none);
  color: var(--efu-white);
  background: var(--efu-main);
  border-radius: 4px;
  box-shadow: var(--efu-shadow-main);
}
.random-post-start {
  transition-duration: 0.3s;
}
.random-post-start:hover {
  color: var(--efu-hovertext);
}
#page .title-h2-a {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 0.5rem;
}
#page .title-h2-a a {
  margin-left: 0.5rem;
  color: var(--efu-secondtext);
  font-weight: 700;
}
#page .title-h2-a a:hover {
  color: var(--efu-main);
}
#page .title-h2-a .title-h2-a-left {
  display: flex;
  align-items: center;
}
#page .title-h2-a .title-h2-a-right {
  font-size: 14px;
  color: var(--efu-secondtext);
}
</style>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/zhheo/JS-Heo@master/mainColor/heoMainColor.css">
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/zhheo/JS-Heo@master/moments5/app.min.js"></script>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/zhheo/JS-Heo@master/moments5/bundle.js"></script>
```

## 效果

![](https://s3.qjqq.cn/47/66223d41d13b2.webp!color)