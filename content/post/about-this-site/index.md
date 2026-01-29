---
title: 关于本网站的建立
description: 对个人博客网站构建和部署的一些简要记录
date: 2026-01-26T23:04:21+08:00
lastmod: 2026-01-28T23:13:18+08:00
image: hugo.png
draft: false
links:
  - title: orzephyrous.github.io (GtiHub Repository)
    description: Where this site is hosted.
    website: https://github.com/orzephyrous/orzephyrous.github.io
    image: https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png
tags:
  - tech
  - software
  - memo
---

# 关于本博客网站的建立

## 起因

其实很久以前我就在各种视频网站上看到过建立个人博客的教程，也早就知道Github Pages可以白嫖一个github.io的个人网站，不过一直未能付诸实践（完全的拖延症晚期）。

作为一个拖延症晚期患者，想让我有执行力显然不止需要一个理由：

- 其一：最近在[bangumi](https://bgm.tv)上看到了关于建立个人博客的小组话题[^1]<sup>,</sup>[^2]，一时兴起，觉得“是时候建一个自己的博客网站了”。

[^1]: [新搭建的个人博客只活了3小时](https://bgm.tv/group/topic/449311)
[^2]: [宣传一下我的博客](https://bgm.tv/group/topic/445792)

- 其二：之前搭了NAS，之前把一些配置什么的都记录在一个Markdown文件中存在OneDrive里，当作自己的备忘录。近期，新增了一些docker容器，把新番订阅、下载、刮削、观看的一套流程基本定型了，我觉得总体来说做得还是比较满意的，想写个博客记录下来，放到网络上供人参考。

- 其三：2026年1月新番[异国日记](https://bgm.tv/subject/493016)勾起了一些内心深处写日记的愿望。转念一想，“日记”还是频率太高了，我的生活也没有到能每天都有活的程度。总的来说，大概就是把博客当日记+备忘录用吧。

综合起以上全部，我终于开始付诸实践。

## Why Hugo?

尽管之前学过一点点编程，但本人并非科班程序员，更不懂什么前端后端，只能写写Markdown这样的，静态网站应该就是我的极限了。

静态网站方面，久闻Hugo“最快”的大名。然而观摩众多bangumi用户的博客，疑似都是Astro。再看教程，似乎还是Hugo更容易搭起来一些，而且我本身也不排斥命令行操作，遂选择了Hugo（当然不是因为Astro一点进Theme页面全是付费主题）。

## Hugo How?

基本步骤全部都是跟着教程走的，没有碰到报错或问题。教程主要看Hugo官网的[Quick Start](https://gohugo.io/getting-started/quick-start/).

### 安装Hugo

最初的尝试都是在我安装了Arch Linux的笔记本上进行的，环境配置全靠包管理。

```bash
sudo pacman -S hugo
```

### 初始化网站和主题

```bash
hugo new site orz # 用hugo初始化网站文件夹
cd orz # 进入初始化后的文件夹
git init # git初始化
git submodule add https://github.com/CaiJimmy/hugo-theme-stack/ themes/stack # 用git submodule把主题文件配置到git中并拉取下来
echo "theme = 'stack'" >> hugo.toml # 设置主题
```

（后续把hugo.toml挪到`/config`文件夹中了）

当然，添加github仓库信息也是配置的一环

```
git remote add origin git@github.com:orzephyrous/orzephyrous.github.io.git
```

### 网站配置和部署

主要参考Hugo官方的[部署教程](https://gohugo.io/host-and-deploy/host-on-github-pages/)以及Stack主题的[Starter仓库](https://github.com/CaiJimmy/hugo-theme-stack-starter)。Github账户这边的配置主要参考前者（Github还配置了一下ssh），而大多数参数和github workflow配置都是直接复制了后者。

尽管是抄百家之长，不过我还是更喜欢自下而上（Bottom-Up）的构建方式，那样能更清楚我每一个配置都具体做了什么。因此，在这个博客建立之初，整个页面其实只有博客大标题，后续才加入了侧边栏的头像和说明。

文章TOC的配置甚至是在写这篇博文的同时才引入的，侧边栏的tag、搜索、主页面配置都还没有做。

## 未来

目前Stack主题的config我也还仍在一项一项研究当中。不过总之网站是跑起来了。能跑就行~

等配置研究明白之后，基本就只有写Markdown的工作了。我目前没有这网站引入别的功能的想法，后续的维护应该会轻松很多。

## 鸣谢

- [Hugo](https://gohugo.io/)：全世界最快的静态网站框架
- [Hugo Theme Stack](https://stack.jimmycai.com/)：好看的网站主题，提供了详细的主题文档、部署教程
- [Hugo Theme Starter Template](https://github.com/CaiJimmy/hugo-theme-stack-starter)：详细全面的网站template，从零开始理解hugo就从这份模板开始。
