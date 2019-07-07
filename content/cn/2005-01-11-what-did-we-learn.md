---
title: 我们到底学到了什么？
date: '2005-01-11T19:07:00+08:00'
slug: what-did-we-learn
---

# Hugo网站托管至Netlify

Sat, May 6, 2017 

 [hugo](https://www.choyang.me/zh/tags/hugo), [netlify](https://www.choyang.me/zh/tags/netlify)

- 
- 
- 
- 
- 

在用 blogdown 建站之初是托管在Github Pages，具体过程[这篇日志](https://www.choyang.me/zh/post/hugo/)做了详细介绍。看到[Yihui的这篇博客](https://yihui.name/cn/2017/04/url-to-content/)才发现[Netlify](https://www.netlify.com/)部署托管静态网站更加方便，提供了 Jekyll、Hugo 等引擎自动编译静态网站，不需要像 Github Pages 那样用 Git 管理副产品[1](https://www.choyang.me/zh/post/hosting-hugo-on-netlify/#fn:Github-Pages-Net)。更为方便的是，Netlify 支持编译 Github 仓库的代码，这样我们可以把 Hugo 网站源代码上传至 Github 用 Git 管理，然后在 Netlify上发布网站：

1. 用 Github 账户登录 Netlify
2. 右上角选择`New site from Git`
3. 选择 Github ，然后关联包含网站源代码的仓库
4. 设置：
   - Branch：`master`
   - Build Command: 建议选择`hugo_0.19`
   - Publish Directory:`public`[2](https://www.choyang.me/zh/post/hosting-hugo-on-netlify/#fn:publishDir) 
5. `Deploying`，默默等待一两分钟，Netlify 随机分配一个子域名`*.netlify.com`，可以随意修改`*`的内容。

如果需要自定义自己域名为`www.<your_domain>`，[Netlify中有详细说明文档](https://www.netlify.com/docs/custom-domains/#dns-configuration)，，如下设置即可：

- `A`记录，类型为`@`，`104.198.14.52`
- `CNAME`记录，类型为`www`，设置为Netlify 中的域名`*.netlify.com`

待处理：去掉`www`前缀，启动`https`

------

1. Github Pages 中需要管理编译生成的网页文件，而结合 Netlify只需要上传生成网站的源代码至 Github，把 `public`文件夹添加至`.gitignore`，Hugo 默认把网站编译到 `public` 文件夹下， 文件夹，如果自定义修改了`config.toml`中的参数`publishDir`，用相应文件夹代替`public`即可 [↩](https://www.choyang.me/zh/post/hosting-hugo-on-netlify/#fnref:Github-Pages-Net)
2. 或者与`publishDir`一致 [↩](https://www.choyang.me/zh/post/hosting-hugo-on-netlify/#fnref:publishDir)