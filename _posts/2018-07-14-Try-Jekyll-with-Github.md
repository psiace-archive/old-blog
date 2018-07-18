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
* 启用 GitHub Pages 的用户页面服务
* 使用优秀的 Jekyll Theme
* Jekyll Theme 的组织结构
* 一些第三方服务和个性化配置
* 将你的页面发布 :)

好吧，让我们现在就开始，玩的开心～

### 本地部署 Jekyll/GitHub Pages 环境

首先我们需要一台联网的计算机，当然，如果没有也不用担心，我会考虑在后面添加如何使用手机来完成这项工作。

首先，你需要安装 Ruby 语言环境，这里提供 Fedora 系统上的命令行安装方法

`sudo dnf install ruby ruby-devel`

如果你使用的是 Ubuntu 系统，只需要把命令换成 

`sudo apt-get install ruby ruby-dev`

至于 [Y/N] 我们当然是选择 Y :)

如果你在使用 Windows 或是其它操作系统，请参考[这里](https://www.ruby-lang.org)，链接指向了 Ruby 的官方网站，你可以很轻易得到安装办法。

接下来，我们需要依次执行下面图示的命令：

![Install & Test](https://psiace.me/src/FeiDianShare/carbon-install-test.png)

不使用 `gem install bundler jekyll` 的原因只是我们想要构建一个与 Github Pages 完全相同的环境。

在浏览器中输入它提供的地址（也许是 `http://localhost:4000` 或是 `http://127.0.0.1:4000/`），你就可以看到一个官方提供的模板。

类似下图：

![Test Page](https://psiace.me/src/FeiDianShare/test-page.png)

如果你喜欢它，可以直接在这个上开始工作，打开文件夹，在 `_post` 目录下以 `yyyy-mm-dd-title.md` 按示例新建文件，编辑内容，然后就可以在页面上看到更改了，稍后我会额外介绍这些内容。


### 启用 GitHub Pages 的用户页面服务

如果你还没有 [GitHub](https://github.com) 的账号，我强烈推荐你注册一个，因为这是世界上最为活跃的~~同性~~交友社区之一 :) 只要访问主页，你就可以找到入口。

我强烈建议你参考 GitHub 的官方文档，它非常详细地介绍了所有你可能想要了解的内容。当然，你需要一点阅读英文文档的能力，至少要能够使用翻译。

好了，现在你已经有了 GitHub 的账号，通常情况下，我会建议你创建一个名为 `yourusername.github.io` 的存储库（请容许它使用 README 文档对存储库进行初始化，特别是当你打算试验而没有准备好内容），这样你就可以获得一个由 GitHub 友情提供的子域名，所有在主分支（`master`）的符合要求的内容都将被重构并发布，通常情况下，你可以在浏览器访问 `https://yourusername.github.io`，然后看到 `README.md` 被转化后的内容。

如果它没有正常显示或者你想在其它存储库启用 GitHub Pages，请打开存储库的 `Settings` 然后根据提示操作。如果你觉得页面光秃秃，可以通过 `Choose a theme` 来选择一个官方主题，但这不是必要的，因为我们接下来会介绍一些关于使用优秀的 Jekyll 主题和进一步定制的内容。

### 使用优秀的 Jekyll Theme

造轮子是一件有意思的工作，但它往往需要花费大量的时间，而且一个好的想法可能需要经过大量的调试才能正常工作，如果你不满足于 Jekyll 的几个默认主题，那么我建议你试着使用一些优秀的 Jekyll 主题，它们往往实现了以下功能：

* 响应式布局
* 良好的文件结构
* 标签云/文章分类
* 优化的 SEO 设置
* 第三方评论/统计插件支持

从优秀的 Jekyll 主题开始可以让你更专注于文章本身，而不是看上去数目众多的 CSS 代码 :)

这里我特别推荐三个主题：

* **[Huxblog-Boilerplate](https://github.com/Huxpro/huxblog-boilerplate)**，by [@Huxpro](https://github.com/Huxpro/)，Apache License v2.0

![Huxblog](https://psiace.me/src/FeiDianShare/Huxblog.png)

* **[Jekyll NexT](https://github.com/Simpleyyt/jekyll-theme-next)**，by [@Simpleyyt](https://github.com/Simpleyyt/)，Unknow

![NexT](https://psiace.me/src/FeiDianShare/NexT.png)

* **[Leonids](https://github.com/renyuanz/leonids)**，by [@renyuanz](https://github.com/renyuanz/)，MIT License

![Leonids](https://psiace.me/src/FeiDianShare/leonids.png)

点击主题名，你将跳转到它们的存储库，请选择你所喜欢的主题下载

相信我，我们可以完全避开 Git 以及它的命令行工具，如果你不想跳过这些，那么你可能需要另外查看其它文章，我暂时没有介绍这些的计划。

如果你想查找更多主题，我强烈建议你查看 [Jekyll Themes](http://jekyllthemes.org)，请从中挑选你喜欢的那个。

### Jekyll Theme 的组织结构

我注意到我此前并没有提示如何使用这些 Jekyll 主题，其实很简单：`cd your-jekyll-theme` & `bundler install` & `jekyll serve`，同样你可以在浏览器得到一个本地预览的版本。即便你使用的命令没有包含 `--watch` 选项，内容的构建仍然会是实时的。

我知道你已经受够了空荡荡的主题或是为了演示而填充的没意义的内容以及我的啰嗦，但请再稍稍忍耐一下，这里会谈到 Jekyll Theme 的组织结构和一些简单的内容组织方式，这将有助于你下一步修改/配置主题。

来吧，让我们用文件管理器或是你喜欢的文本编辑器打开你选定的主题所在的文件夹，看看里面有什么宝贝：

通常情况下，Jekyll Theme 会是下面所示的结构：


```
.
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.md
|   └── sample-and-test.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2015-10-29-How-to-begin.textile
|   └── 2013-04-26-Hello-World.md
├── _data
|   └── members.yml
├── _site
└── index.html
```

* _config.yml

  保存配置数据。很多配置选项都会直接从命令行中进行设置，但是如果你把那些配置写在这儿，你就不用非要去记住那些命令了。

* _drafts

  drafts 是未发布的文章。这些文件的格式中都没有 `title.MARKUP` 数据。

* _includes

  你可以加载这些包含部分到你的布局或者文章中以方便重用。可以用这个标签  `{% raw %}{% include file.ext %}{% endraw %}` 来把文件 `_includes/file.ext` 包含进来。

* _layouts

  layouts 是包裹在文章外部的模板。布局可以在 YAML 头信息中根据不同文章进行选择。 这将在下一个部分进行介绍。标签 `{% raw %}{{ content }}{% endraw %}` 可以将content插入页面中。

* _posts

  这里放的就是你的文章了。文件格式很重要，必须要符合: `YEAR-MONTH-DAY-title.MARKUP`。The permalinks 可以在文章中自己定制，但是数据和标记语言都是根据文件名来确定的。

* _data

  格式良好的网站数据应该放在这里。jekyll 引擎将自动加载此目录中的所有 yaml 文件（以 .yml 或.yaml 结尾的文件）。如目录下有 member.yml 文件，则可以通过 `site.data.members` 访问该文件的内容。

* _site

  一旦 Jekyll 完成转换，就会将生成的页面放在这里（默认）。最好将这个目录放进你的 .gitignore 文件中。

* index.html 和其它 HTML, Markdown, Textile 文件

  如果这些文件中包含 YAML 头信息 部分，Jekyll 就会自动将它们进行转换。当然，其他的如 .html，.markdown，.md，或者 .textile 等在你的站点根目录下或者不是以上提到的目录中的文件也会被转换。

* 其它 文件/文件夹

  其他一些未被提及的目录和文件如 css 还有 images 文件夹，favicon.ico 等文件都将被完全拷贝到生成的 site 中。

是的，这里搬运了 Jekyll 官方网站的内容，因为它们已经被介绍的很详尽。我不愿意做一些重复的工作。

我会在下一部分结合实例来讲一下各个部分的使用。

### 一些第三方服务和个性化配置

#### 常规

用你最喜爱的文本编辑器打开你的 Jekyll Theme，首先我们需要编辑 `_config.yml` 文件，通常情况下，它会包含一些网站所必须的 SEO 信息，以及你一些个人信息，按照你的情况把它填好，如果里面没有你所需要的内容请留空。社交链接和默认的第三方服务通常是在这里进行配置。

哦，我想我们不需要那些为了展示而配备的文章，如果你恰恰和我一样使用 `Fedora with Gnome` （我只是不确定其它系统的情况）我建议你将它们移动到 `模板` 文件夹中，这样你就可以按它的格式新建文章。

让我们来看一下用于文章的 `.markdown(.md)` 文件与平时有什么不同，这里给出一个示例：

    ---
    title: Elements
    description: Markdown-How-To
    date: 2013-12-24 23:29:08
    categories:
      - Foo
    tags:
    ---

    The purpose of this post is to help you make sure all of HTML elements can display properly. If you use CSS reset, don't forget to redefine the style by yourself.

    ---

    # Heading 1

    ## Heading 2

    ### Heading 3

    #### Heading 4

    ##### Heading 5

    ###### Heading 6

    ---

    ## Paragraph

    Lorem ipsum dolor sit amet, [test link]() consectetur adipiscing elit. **Strong text** pellentesque ligula commodo viverra vehicula. *Italic text* at ullamcorper enim. Morbi a euismod nibh. <u>Underline text</u> non elit nisl. ~~Deleted text~~ tristique, sem id condimentum tempus, metus lectus venenatis mauris, sit amet semper lorem felis a eros. Fusce egestas nibh at sagittis auctor. Sed ultricies ac arcu quis molestie. Donec dapibus nunc in nibh egestas, vitae volutpat sem iaculis. Curabitur sem tellus, elementum nec quam id, fermentum laoreet mi. Ut mollis ullamcorper turpis, vitae facilisis velit ultricies sit amet. Etiam laoreet dui odio, id tempus justo tincidunt id. Phasellus scelerisque nunc sed nunc ultricies accumsan.

    Interdum et malesuada fames ac ante ipsum primis in faucibus. `Sed erat diam`, blandit eget felis aliquam, rhoncus varius urna. Donec tellus sapien, sodales eget ante vitae, feugiat ullamcorper urna. Praesent auctor dui vitae dapibus eleifend. Proin viverra mollis neque, ut ullamcorper elit posuere eget.

    > Praesent diam elit, interdum ut pulvinar placerat, imperdiet at magna.

    Maecenas ornare arcu at mi suscipit, non molestie tortor ultrices. Aenean convallis, diam et congue ultricies, erat magna tincidunt orci, pulvinar posuere mi sapien ac magna. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Praesent vitae placerat mauris. Nullam laoreet ante posuere tortor blandit auctor. Sed id ligula volutpat leo consequat placerat. Mauris fermentum dolor sed augue malesuada sollicitudin. Vivamus ultrices nunc felis, quis viverra orci eleifend ut. Donec et quam id urna cursus posuere. Donec elementum scelerisque laoreet.

    ## List Types

    ### Definition List (dl)

    <dl><dt>Definition List Title</dt><dd>This is a definition list division.</dd></dl>

    ### Ordered List (ol)

    1. List Item 1
    2. List Item 2
    3. List Item 3

    ### Unordered List (ul)

    - List Item 1
    - List Item 2
    - List Item 3

    ## Table

    | Table Header 1 | Table Header 2 | Table Header 3 |
    | --- | --- | --- |
    | Division 1 | Division 2 | Division 3 |
    | Division 1 | Division 2 | Division 3 |
    | Division 1 | Division 2 | Division 3 |

    ## Misc Stuff - abbr, acronym, sub, sup, etc.

    Lorem <sup>superscript</sup> dolor <sub>subscript</sub> amet, consectetuer adipiscing elit. Nullam dignissim convallis est. Quisque aliquam. <cite>cite</cite>. Nunc iaculis suscipit dui. Nam sit amet sem. Aliquam libero nisi, imperdiet at, tincidunt nec, gravida vehicula, nisl. Praesent mattis, massa quis luctus fermentum, turpis mi volutpat justo, eu volutpat enim diam eget metus. Maecenas ornare tortor. Donec sed tellus eget sapien fringilla nonummy. <acronym title="National Basketball Association">NBA</acronym> Mauris a ante. Suspendisse quam sem, consequat at, commodo vitae, feugiat in, nunc. Morbi imperdiet augue quis tellus.  <abbr title="Avenue">AVE</abbr>


此文章来自 NexT 主题，介绍了基本的 Markdown 用法，你可以对照页面来看，最前面被一组 `---` 包围的内容属于 YML，包含了文档的信息：标题，描述，分类，标签，日期；我建议你为每篇文章添加这些内容来记录。

你可能还需要修改关于介绍博主的内容，一部分主题会在 `_config.yml` 中进行集成，还有一部分主题会包含一个名为 `about/resume` 的文档，请把里面的内容换成你自己的。还有一种会使用 `_data` 文件夹内的数据或是引入 `_include` 文件夹中的内容，也同样请你修改它们，语法很简单，不做赘述。

这样你就可以把信息完全替换成你自己的，但我建议你保留页脚的部分信息，该内容通常会申明你使用的是什么主题。

#### 第三方服务

啊哦，其实我有点担心是不是描述的足够清楚，如果有什么疑问的话请直接联系我。这一部分会介绍到如何加入第三方服务。

来看看我们需要哪些第三方服务：

1. 评论
    - 多说
    - Disqus
    - 来必力
2. 统计/SEO
    - 百度
    - 谷歌

这里以 来必力 和 谷歌分析 为例，选用这两个的原因只是因为方便，你可以自由选择适合你情况的服务。






（未完待续...)
 

