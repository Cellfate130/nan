---
title: "HUGO相关"
date: 2018-09-01T16:01:23+08:00
lastmod: 2018-09-01T16:01:23+08:00
draft: false
tags: ["hugo"]
categories: ["hugo"]
author: "den"

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
# comment: false
# toc: false

# You can also define another contentCopyright. e.g. contentCopyright: "This is another copyright."
contentCopyright: '<a href="https://github.com/gohugoio/hugoBasicExample" rel="noopener" target="_blank">See origin</a>'
# reward: false
mathjax: true
menu:
  main:
    parent: "专题"
    weight: 7
---

本文很长！！！

# 1x00 HUGO搭建

VIA https://gdzhu8023.github.io/post/buildblog/

## 在Github使用Hugo搭建个人博客

### 基础安装

1. Git (需要安装)

2. 到 [Hugo Releases](https://github.com/spf13/hugo/releases) 下载对应的操作系统版本的Hugo二进制文件（hugo或者hugo.exe）

   Hugo Releases：<https://github.com/gohugoio/hugo/releases>

   本文以Windows为例，所以下载：**hugo_0.24.1_Windows-64bit.zip**

   下载之后解压得到“hugo.exe”文件。

   windows环境变量 path 添加 `hugo.exe` 所在路径(将hugo.exe所在的目录添加到系统环境变量PATH下面)，打开cmd，输入“hugo version”。

   ![img](https://images2015.cnblogs.com/blog/311516/201707/311516-20170703141434737-679968384.png)

   安装配置完命令行输入 `hugo --help` 会有输出

### 生成博客

1. 新建一个文件夹用于保存hugo要生成的文件

2. 目录下右击 选择 `Git Bash Here` ,进入Git命令行工具，在命令行中输入

   ```
   $ hugo new site mysite
   ```

3. 然后hugo会自动生成这样一个目录结构：

   ```
   ▸ archetypes/
   ▸ content/
   ▸ layouts/
   ▸ static/
   config.toml
   ```

   config.toml目录是hugo博客的配置文件,所有的全局配置都要放在这个文件中。接下来创建内容,

   ```
   $ cd mysite
   $ hugo new about.md
   ```

   执行完后在content目录下会出现about.md文件。打开about.md文件,在文件上面可以看到这么几行:

   ```
   ---
   title: "About"
   date: 2017-07-28T20:54:37+08:00
   draft: true
   ---
   ```

   单篇博客的配置在+++内配置。
   title就是博客的标题,**draft=true**表示这是一篇草稿,Hugo默认是不会渲染草稿状态的博客的,完成博客后使用

   ```
   $ hugo undraft content/about.md
   ```

   命令可以改变博客的draft状态,或者手动到文件中修改。

   正文的内容写在+++区域的下面,使用markdown的语法。比如:

   ```
   ## 我是一个标题
   
   放一些内容
   ```

   一般为了便于管理,不会直接将posts放在content文件下,可以在content目录内新建一个post目录:

   ```
   hugo new post/first.md
   ```

   可以看到在content/post/下产生了一个first.md文件。

### 安装主题

接下来安装主题,我们直接使用Hugo推荐的一些主题。比如说我使用的是blackburn这个主题:

```
git clone https://github.com/yoshiharuyamashita/blackburn.git themes/blackburn
```

将主题git clone到themes/blackburn目录下,在config.toml中配置:

```
theme = "blackburn"
```

这样主题就安装好了。

### 启动Hugo

终于到了看实际效果的时候了,在博客的项目根目录下运行:

```
hugo server --buildDrafts --theme=blackburn
```

如果在配置文件中已经配置了theme的话就不需要再指定 **- -theme** 参数了, **- -buildDrafts** 参数的意思是渲染所有的post包括 **draft=true**状态的。

打开浏览器,在地址栏中输入: [http://localhost:1313](http://localhost:1313/), 就可以看到我们的博客了。

### 更改配置

> 主题地址，可参考 <https://themes.gohugo.io/blackburn/>

- 一般来说使用默认的配置就可以了,但是要注意配置baseurl参数:

  ```
  baseurl = "http://这里是你的域名/"
  ```

- 当我们把博客部署到服务器上的时候注意要把配置中的baseurl改成自己的域名。

主题的配置参数也是在config.toml中配置,各个主题的配置不尽相同,需要参考主题的文档,这里给一个我使用的主题的配置:

```
baseURL = "gdzhu8023.github.io"
languageCode = "en-us"
title = "浮世尘烟"
author = "Zhu Guodong"

# Shown in the side menu
copyright = "&copy; 2017. All rights reserved."
canonifyurls = true
paginate = 10
theme = "blackburn"

[indexes]
  tag = "tags"
  topic = "topics"

[params]
  # Shown in the home page
  subtitle = "Move on"
  brand = "Menu"
  googleAnalytics = "UA-103593285-1"
  # CSS name for highlight.js
  highlightjs = "monokai"
  dateFormat = "02 Jan 2006, 15:04"
  #disqusShortname
  disqus = "gdzhu8023"

[menu]
  # Shown in the side menu.
  [[menu.main]]
    name = "Home"
    pre = "<i class='fa fa-home fa-fw'></i>"
    weight = 1
    identifier = "home"
    url = "/"
  [[menu.main]]
    name = "Posts"
    pre = "<i class='fa fa-list fa-fw'></i>"
    weight = 2
    identifier = "post"
    url = "/post/"
  [[menu.main]]
    name = "About"
    pre = "<i class='fa fa-user fa-fw'></i>"
    weight = 3
    identifier = "about"
    url = "/about/"
  [[menu.main]]
    name = "Contact"
    pre = "<i class='fa fa-phone fa-fw'></i>"
    weight = 4
    url = "/contact/"
  [[menu.main]]
    name = "Topics"
    pre = "<i class='fa fa-folder fa-fw'></i>"
    weight = 5
    url = "/topics/"
  [[menu.main]]
    name = "Tags"
    pre = "<i class='fa fa-tags fa-fw'></i>"
    weight = 6
    url = "/tags/"

[social]
  # Link your social networking accouns to the side menu
  # by entering your username or ID.

  # SNS microblogging
  twitter = "MaTure_Zhu_GD"
  facebook = "de.found.5"
  #googleplus = "/u/0/110451572416739183954"
  weibo = "2760705767"

  # SNS career oriented

  # SNS news
  #reddit = "*"
  #hackernews = "*"

  # Techie
  github = "gdzhu8023"
```

### 关于部署

假设你需要部署在`GitHub Pages`上，首先在GitHub上创建一个Repository，命名为：**gdzhu8023.github.io**（gdzhu8023替换为你的github用户名）。
并且要在该Repository的setting里面，**GitHub Pages**部分设置一下

在站点根目录执行 Hugo 命令生成最终页面：

```
$ hugo --theme=blackburn --buildDrafts --baseUrl="https://gdzhu8023.github.io/"
```

如果一切顺利，所有静态页面都会生成到 **public** 目录，将pubilc目录里所有文件 push 到刚创建的Repository的 master 分支。

```
$ cd public
$ git init
$ git remote add origin git@github.com:gdzhu8023/gdzhu8023.github.io.git
$ git add -A
$ git commit -m "first commit"
$ git push -u origin master
```

浏览器里访问：<https://gdzhu8023.github.io/> 就可以访问你的博客了

### 域名解析

如果你有自己的域名，那么可以将自己的域名解析到xxx.github.io，这里推荐使用CNAME记录类型。

在Github的xxx.github.io下增加一个CNAME文件，文件内容是你自己拥有的域名。

之后，通过域名服务商添加CNAME记录类型就可以了。

### 使用总结

日常操作总结

```
--新建博客markdown文件，并编辑博客内容(文件名为 **.md )
hugo new post/useGit.md
--生成静态页面
hugo --theme=blackburn --buildDrafts --baseUrl="https://gdzhu8023.github.io/"
---发布
cd public 
git add .
git commit -m "new blog added"
git push origin master
```

### 日常填坑

1. 添加Topics 和 Tags
   - 首先config.toml中的menu部分要添加配置,weight按顺序填写

```
  [[menu.main]]
    name = "Topics"
    pre = "<i class='fa fa-folder fa-fw'></i>" //这行是文字前面的那些图形的东西
    weight = 5
    url = "/topics/"
  [[menu.main]]
    name = "Tags"
    pre = "<i class='fa fa-tags fa-fw'></i>"
    weight = 6
    url = "/tags/"
```

- 在博客的**.md文件中的头部添加你要的Topics 和 Tags（例如本篇博客的配置）

```
  ---
  title: "在Github使用Hugo搭建个人博客"
  date: 2017-07-29T21:33:13+08:00
  draft: true
  tags: [2017-07]
  topics: [Install or Config]
  ---
```

- 大功告成，标记和话题就出来了

1. home中预览文字和图片

   这个问题困扰了我一天，给主题作者发了发了好几封邮件，终于解决了这个问题，非常感谢主题作者

    

   Yoshiharu Yamashita

    

   的帮助

   话不多说，首先确保主题是GitHub上最新的(蜜汁尴尬，我是几天前clone的，少了一个html文件，导致渲染就是不成功，好吧，我的锅)，主要是要在 **.markdown （你的博客本地文件）中添加预览说明，如果添加图片需要加入标签，for example：

    



   - FAQ
     - Q： 为什么不把此部分贴称文本？
     - A： 因为贴进文本中就被hugo渲染了，导致home的图片和预览就失效了，具体为什么？我怎么知道，不要在意这些细节！几行代码而已啦！

### 添加Discus评论系统

1. 注册Discus（需要科学上网）
   \> <https://disqus.com/>
2. 首页点击 **GET START** ， 选择第二个 **I want to install Disqus on my site**
3. 在**Website Name**中输入一个名称，点击创建
4. Continue 正常配置
5. 配置页面有一个 `Shortname Your website shortname is gdzhu8023.`
6. 将你的shotname配置到config.toml 

```
  disqus = "gdzhu8023"
```

1. 大功告成，部署到GitHub上即可加载评论系统了
2. 友情提示：访问你博客的人需要科学上网才能加载评论，万恶的GFW

### 

### 

# 2x00 Go Hugo SEO

via [mtchavez](https://blog.el-chavez.me/2015/11/26/go-hugo-seo/)

## Page Keywords

Whether you have blog posts or your main site generated with Hugo you will want to set `keywords` per page. This will allow you to set your dynamic `meta` keyword tags for content. An example in markdown would be to add keywords to your page metadata:

```yaml
---
keywords:
- mysite
- mysite keyword
- Another useful keyword
title: My Homepage
---
```

With this added per page we can now add the `meta` tag for our keywords so that we have dynamic keywords per content page. In order to do that we will use a templating function to achieve this. In a `header` partial template or your default tamplate add the meta tag to your `<head>`

```go
<meta content="{{ delimit .Keywords ", " }}" name="keywords">
```

## Page Title

Applying the page title by page is relatively easy and is in most themes and examples. You may want to include your site name with the page title or the theme you are using or have created may not have this set up yet. To do this you can do a relatively simple check for the homepage and title to correctly display. Again add this to wherever youd `<head>` tag gets generated

```go
<title>{{ $isHomePage := eq .Title .Site.Title }}{{ .Title }}{{ if eq $isHomePage false }} - {{ .Site.Title }}{{ end }}</title>
```

In addition to the page title you will want to add a `meta` tag for the title as well

```go
<meta content="{{ $isHomePage := eq .Title .Site.Title }}{{ .Title }}{{ if eq $isHomePage false }} - {{ .Site.Title }}{{ end }}" property="og:title">
```

## Page Description

One other useful dynamic page setting we can utilize is to add a per page description as well as using your site description. To set the site description you do this in your hugo `config.toml`, or `config.yaml`. Set this in the `params` section to be able to use in your templates.

```toml
[params]
description = "Site stuff for being a good site with internet tubez."
```

In addition to a site description we can use a per page description by adding a `description` field

```yaml
---
keywords:
  - mysite
  - mysite keyword
  - Another useful keyword
title: My Homepage
description: Where you should come to find my homepage updates and stuff
---
```

Now we can follow the same pattern as before with our page title and set the page description, if available, with our site description. Again in the `head` section we will add another meta tag

```go
<meta content="{{ $isHomePage := eq .Title .Site.Title }}{{ .Site.Params.description }}{{ if eq $isHomePage false }} - {{ .Description }}{{ end }}" property="og:description">
```

------

With a few custom settings and meta fields per page we can easily utilize them to build more dynamic page content. Whether you are building a blog or doing your whole site with Hugo you can still keep your SEO in mind.

本文章记录使用HUGO过程中的某些问题。

### hugo 怎么插入本地 image

在site 的目录下的 static 下就是存储的静态文件，创建 media 目录存放图片等媒体文件，引用的话，直接「/media/xxx.png」 。

**_注意：_** 不要使用 xxx.PNG 这样的大写后缀，生成的静态页面为小写后缀，然后出现找不到该 Image。

### hugo content 顶部添加 preview、next

vi `themes/hyde-y/layouts/post/single.hat.html`

在`</header>`前添加：

```
<br/>
{{ partial "bloc/content/navigation" . }}
```

### google，baidu 完全搜索不到博文

因为google，baidu 还没有收录我们的URL，所以在google 里输入：site:网址URL 如果能搜索出来则说明，google 已经添加我们的网址。不能则需要提交网址到 google。百度同理。
https://www.google.com/webmasters/tools/home

### Hugo 还不支持生成目录树

### 四、进阶

#### 1、index.html、single.html和list.html

站点的首页模板在themes/hyde/layouts/index.html中。除首页外，其他Post或叫Page，都被Hugo抽象为两类：单体页面和列表页面，对应这两种页面的默认模板都在themes/hyde/layouts/_default中，分别对应着single.html和list.html。

我们之前通过hugo new welcome.md创建的Post使用的是single.html模板，而查看tags或categories的页面默认采用的是list.html，比如查看tonybai.com/categories/golang，你会在浏览器中看到分类在golang这一类的所有Post列表。

#### 2、type和section

我们执行如下两个命令：

```
$hugo new post/firstpost.md
tonybai.com/content/post/firstpost.md created
$hugo new post/secondpost.md
tonybai.com/content/post/secondpost.md created
```

创建后我们可以看到站点的源文件结构变成了：

```
... ...
├── archetypes
├── config.toml
├── content
│   ├── post
│   │   ├── firstpost.md
│   │   └── secondpost.md
│   └── welcome.md
... ...
```

hugo中源码文件的布局影响着最终生成的html文件的结构布局。有些时候我们的站点可能会分成若干个部分，每部分通过目录隔离开，比如这里content下的post目录，这样hugo转换后，firstpost.html和secondpost.html也会在public的post目录下。这里的“post”被称为一个section。

hugo会为每个section自动生成index.html页，采用的是index.html模板。

至于是否采用的是hyde/layouts/_default下的list.html，这要看host的匹配order，官方给出的是：

```
/layouts/section/SECTION.html
/layouts/_default/section.html
/layouts/_default/list.html
/themes/THEME/layouts/section/SECTION.html
/themes/THEME/layouts/_default/section.html
/themes/THEME/layouts/_default/list.html

这个例子中THEME=hyde, SECTION=post
```

在本例子中，/layouts/下是空的，不予考虑。/themes/hyde/layouts下没有建立section/post.html模板，/themes/hyde/layouts/_default/section.html也不存在，因此用的是_default/list.html。

hugo官方建议静态站点源码文件按section组织，每个section使用相应(同名）的type，这样section下面的.md就会自动使用响应type的meta data。

当我们hugo new post/firstpost.md时，hugo会到archetypes下找是否有post.md文件，如果有则使用post.md文件的categories和tags来初始化content/post/firstpost.md的元数据，如果没有post.md，则使用archetypes/default.md的。

#### 3、模板语言

Hugo使用Golang的模板语法，表达能力很强大；配合Hugo predefined的变量或自定义变量，你可以玩转模板。关于模板内容较多，这里不赘述，需要时查看[官方详细的manual](http://gohugo.io/templates/go-templates/)。



### 需要完善的地方：

1. 点开作者可以看到他发表的哪些文章列表

2. 顶部导航栏固定通过CSS header {position: fixed;

3. 搜索功能

4. 

   目标 极简 是否有必要增加与减少

   - [ ] 自适应
   - [ ] 多语言
   - [ ] 增加作者
   - [ ] 增加投稿
   - [ ] 最近发表的文章支持，显示最近的10篇
   - [ ] 分类支持，并且可以显示分类内的文章数量
   - [ ] 标签云支持
   - [ ] 一键回到页面顶部
   - [ ] RSS支持，并且可以自动发现RSS
   - [ ] 自定义菜单支持，不限个数，自定义排序
   - [ ] 自定义友情链接支持
   - [ ] 支持文章按年份日期进行归档
   - [ ] 支持GA分析统计
   - [ ] sitemap站点地图
   - [ ] 404错误页
   - [ ] 支持关键字SEO优化
   - [ ] Google站内搜索
   - [ ] See Also 支持
   - [ ] Disqus评论支持
   - [ ] 文章阅读数统计
   - [ ] 百度分析
   - [ ] 固定文件的处理GITHUB上怎么传文件 是本地全HUGO好 上传所有文件 还是在GITHUB上直接增加一个MD文件 
   - [ ] robots（放网站跟目录）.txt



### 功能特性

1. 最近发表的文章支持，显示最近的10篇

2. 分类支持，并且可以显示分类内的文章数量

3. 标签云支持

4. 一键回到页面顶部

5. RSS支持，并且可以自动发现RSS

6. 自定义菜单支持，不限个数，自定义排序

7. 自定义友情链接支持

8. 支持文章按年份日期进行归档

9. 支持GA分析统计

10. sitemap站点地图

11. 代码高亮

12. 404错误页

13. 支持关键字SEO优化

14. Google站内搜索

15. See Also 支持

16. Disqus评论支持

17. 不蒜子页面计数器支持

    # 9x00 技巧

    1. 对于不发表的文章，台头那里填入draft: yes
    2. d
    3. d
    4. 


