---
title: 网站搭建：通过Git部署到服务器
categories:
  - 网站搭建
tags:
  - Git
  - Web
cover: 'https://s3.qjqq.cn/47/662795895742a.webp!color'
abbrlink: 434e61db
date: 2024-03-28 08:00:00
update: 2024-03-28 08:00:00
recommend: true
---

## 安装 & 创建 Git用户

1. 安装 Git
    ```bash
    sudo apt-get install git
    ```
2. 创建 Git 群组并添加git用户
    ```bash
    # Ubuntu
    groupadd git
    useradd -g git git
    # Debian
    groupadd git
    usermod -a -g git git
    # CentOS
    groupadd git
    useradd -g git git
    ```
3. 设置密码
    ```bash
    passwd git
    ```
4. 屏蔽git用户登录
    ```bash
    vim /etc/passwd
    # 修改 git:x:1001:1001::/home/git:/bin/bash 为 git:x:1001:1001::/home/git:/usr/bin/git-shell
    ```
    {% note success simple %}
    把/bin/sh改为/usr/bin/git-shell，用户就只能用来克隆或者推送数据到远程 git 仓库，而不能用它登录到主机。
    {% endnote %}

## 配置Nginx

> 使用面板的话，可以直接在面板上配置
> 这里以1panel为例

1. 创建站点，选择静态站点
    ![](https://s3.qjqq.cn/47/6627936f5aace.webp!water)
2. `/opt/1panel/apps/openresty/openresty/www/sites/efu.me/index` 即为下一步中的`工作目录`
3. 设置目录所有者给git用户
    ```bash
    chown -R git:git /opt/1panel/apps/openresty/openresty/www/sites/efu.me
    chown -R 755 /opt/1panel/apps/openresty/openresty/www/sites/efu.me
    ```
## 创建裸仓库

1. 新建一个裸仓库
    ```bash
    mkdir -p /home/git/project/blog.git # -p 递归创建目录
    cd /home/git/project/blog.git
    git init --bare --initial-branch=master # --bare 创建裸仓库 --initial-branch=master 创建主分支
    ```
2. 设置权限
    ```bash
    chown -R git:git /home/git/project/blog.git
    ```
3. 配置 Hook
    ```bash
    vim hooks/post-receive
    ```
4. 添加以下内容 --work-tree 指定工作目录（你在Nginx上设置的网站根目录），--git-dir 指定仓库目录
    ```bash
    #!/bin/bash
    git --work-tree=/home/git/project/blog --git-dir=/home/git/project/blog.git checkout -f
    ```
5. 设置权限，让钩子可执行
    ```bash
    chmod +x hooks/post-receive
    ```
## 配置Hexo

1. 安装 hexo-deployer-git
    ```bash
    npm install hexo-deployer-git --save
    ```
2. 修改配置文件
    ```yaml
    deploy:
        type: git
        repo: ssh://git@你的服务器IP:/home/git/project/blog.git
        branch: master
    ```
3. 部署
    ```bash
    hexo clean && hexo g && hexo d
    ```
## 效果
![](https://s3.qjqq.cn/47/662792e65531a.webp!water)