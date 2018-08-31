---
title: "网站历史修改"
date: 2018-08-23T16:01:23+08:00
lastmod: 2018-08-23T16:01:23+08:00
draft: false
tags: ["关于", "网站历史"]
categories: ["about"]
author: "den"

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
# comment: false
# toc: false

# You can also define another contentCopyright. e.g. contentCopyright: "This is another copyright."
contentCopyright: '<a href="https://github.com/gohugoio/hugoBasicExample" rel="noopener" target="_blank">See origin</a>'
# reward: false
mathjax: true
---



# 网站历史

**20180820** 使用HUGO (静态程序)+ GITHUB(存储空间) + NETLIFY(网站建立) + GODADDY(域名)

# 网站修改简要过程

## 0x00 要增加的内容

功能特性

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

## 1x00

下载网站主要内容https://github.com/rbind/yihui ，使用DOWNLOAD ZIP，然后解压到C:\HUGO下,命名为dneg。

下载皮肤https://github.com/yihui/hugo-ivy ,使用DOWNLOAD ZIP，皮肤放入dneg文件夹的THEMES文件夹下

dneg下右键CMD，命令

```
hugo server
```

此时很慢，并且一会会出线一些报错，因为有些文件连接到TWITTER，国内连不上，所以先把这些报错中的相关文件删除。删除了/EN/和/CN/下的相关报错文件后，再重新运行hugo server，速度就快了。

## 2x00 针对config.yaml的修改

```
baseurl: "https://www.dneg.org/"

googleAnalytics: "UA-121180306-1"

```

menu main下增加

[]: 

```
name"Categories"
      url: "/categories/"
      weight: 5

name: "Tags"
    url: "/tags/"
    weight: 6    
```



## 3x00

\static\ 增加favicon.ico（收藏夹图标）和google44a15adabb438656.html（谷歌站点认证）两个文件

\static\images  寻找新的logo.png替换

复制\themes\hugo-ivy\layouts\_default\的single.html到\layouts\_default下（不然categories和tags点击后显示的空页面）

## 9x00 技巧

1. 对于不发表的文章，台头那里填入draft: yes
2. d
3. d
4. 





