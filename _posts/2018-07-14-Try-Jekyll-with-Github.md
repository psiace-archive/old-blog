---
layout: post
title: 尝试使用 Jekyll 与 GitHub Pages
excerpt: 本文章介绍一些关于 Jekyll 与 GitHub Pages 的内容，为了简化流程仅仅介绍如何快速开始以及在已有主题之上进行个性化定制。
categories: [沸点分享记录]
tags: [Jekyll, GitHub Pages, 静态站点生成器]
creativecommons: true
comments: true
image:
  feature: https://psiace.me/src/FeiDianShare/Jekyll.png
  credit: Jekyll（Page Screenshots）
  creditlink: https://jekyllrb.com
---

*本文将帮助你快速入门，为了避免在介绍上花费过多时间，部分内容请感兴趣的同学自己查看官方网站和文档。*

[Jekyll](https://jekyllrb.com) 是一个优秀的静态站点生成器，[GitHub Pages](https://pages.github.com) 是 **GitHub** 提供的静态页面托管服务。使用这些，我们可以轻松地为项目/组织构建网站，也可以发布自己的博客和简历。

同时使用 Jekyll 和 Github Pages 的一个最大的好处是你可以只关注内容，这是由于有很多优秀的设计师和开发人员为 Jekyll 制作了大量的美观实用的主题，而 GitHUb 为我们节约了购置服务器的经费。唯一的限制可能仅仅是我们需要一些第三方服务来提供诸如评论和在线表单这样的功能。

本文会介绍以下几个方面的内容：
* 本地部署 Jekyll/GitHub Pages 环境
* 为你的储存库启用 GitHub Pages 服务
* 使用优秀的 Jekyll Theme
* Jekyll Theme 的组织结构
* 一些第三方服务和个性化配置

好吧，让我们现在就开始，玩的开心～

### 本地部署 Jekyll/GitHub Pages 环境

首先我们需要一台联网的计算机，当然，如果没有也不用担心，我会考虑在后面添加如何使用手机来完成这项工作。

首先，你需要安装 Ruby 语言环境，这里提供 Fedora 系统上的命令行安装方法

`sudo dnf install ruby ruby-devel`

如果你使用的是 Ubuntu 系统，只需要把命令换成 

`sudo apt-get install ruby ruby-dev`

至于 [Y/N] 我们当然是选择 Y :)

如果你在使用 Windows 或是其它操作系统，请参考[这里](https://www.ruby-lang.org)，链接指向了 Ruby 的官方网站，你可以很轻易得到安装办法。

接下来，按照


