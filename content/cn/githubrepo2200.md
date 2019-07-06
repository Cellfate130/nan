---
title: "github 账号被停之后"
date: 2018-03-06T16:01:23+08:00
lastmod: 2018-03-07T16:01:23+08:00
draft: false
tags: ["预览", "主题"]
categories: ["短码", "index"]
author: "Typora"

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
    weight: 1
---

# 丢失 2 万 2 的 github star repo 是一种什么样的心情? -- 一个程序员,写于 github 账号被停之后

# 0x00. 发现被封  

2018/7/13 下午 15 点左右 ，我群里有朋友跟我说,我用 github pages 建设的网站访问不了了. 
然后 我一打开对应的仓库，404. 
嗯，是不是仓库被 block 了， 继续看账号. WTF ? 账号主页也访问不了了. 
登录试一下？无法登录,显示账号被停. 
由于网站的内容是 hugo 生成的，本地有备份，马上 scp 一份到 jp 服务器。 
并修改 域名的 DNS 指向。现在，网站基本上不影响访问了，但是我 github code 啊，我的 github star 的项目啊。。。 全丢失了.

# 0x01. 试图挽回  

13 号当天发邮件过去, 第二天 github 就回复了.只有寥寥数语. 而且,并没有指出具体导致被封的 repo. 
于是我又回复了邮件(下图中的上面部分),表示希望得到解封的机会, 比如哪个 repo 有问题, 可以帮助删除之类的. 
因为我现在账号完全被封(连登录都不可以),也没有办法删除仓库了. 
![2018.07.17_00h41m51s_001_.png](https://i.loli.net/2018/07/17/5b4ccbdb88119.png)差不多两天过去了, 不再有收到任何回复了.于是后面仔细看了下那句话: 

> Unfortunately, this means we'll have to keep your account suspended.

这句话,注意到那个词, keep, 差不多就是永久封的意思. 没得商量了.

# 0x02. 自行查找原因

搜索邮箱, github 并没有发邮件通知我,而是放在了一个叫 dmca 的仓库. 我是利用 google 搜索才找到这个的:

```
https://github.com/github/dmca/blob/master/2017/2017-11-14-Atlassian-2.md
https://github.com/github/dmca/blob/master/2018/2018-07-05-Jetbrains.md
```

第一个 gist 是 Atlassian 的一个算法,当然,这也只是一个算法,没有私钥,也是绝对不会工作的. 
第二个是 jetbrains-license-server-emulator 这个仓库其实也并没有侵犯 jetbrains 的权利。 
因为缺少一样关键的东西 ：钥匙。这是个没有私钥的代码，因此，不能用来真正破解任何东西 。 
因为这只是一个学习性质的项目。因此,作者才将它分享在了 github. 
我那天也只是觉得可以有学习的用途，或者启发。因此就 fork 了吧。 
fork 之前我也是看了介绍的, 作者特别说明,这个是不能正常使用的,只是学习目的。如果有问题，我肯定不会 fork. 

至于为什么不是封了仓库,而是直接把整个账号给永久封了, 
我猜测,应该是这里有两条的原因吧. 只有一条就封仓库,两条就封账号. 
没时间读他那些什么条文规则, 太多,浪费生命. 

# 0x03. 教训  

提醒一下，如果你此前像我这般信任 github 是一个好网站，那你错了。 
有部分童鞋，在了解到我的事情后，果断的把自己的仓库同步到了 bitbucket, gitlab 和 coding 等。 
github 的操作：没有任何通知，直接封你账号。封完之后，你账户下所有的 repo 全部 404， 你也不能再登录。 
此时，你在 github 的所有数据，已经不属于你了。 
你永远无法再访问到。你没有任何机会再备份你在 github 上面的数据（ issue, star 等）。 

对于一个免费的用户,github 的问题是一刀切. 直接封. 也不通知,不给解释的机会. 这样一个代码托管服务商, 虽然是免费的,但我以后可能也不放心它了. 使用人家的服务, 理应感谢它. 因此,这里没有要怼它的意思. 只是以自身的经历, 来提醒一下大家. 当然，我也有问题，1 是没有备份这些数据，2 是过分相信 github, 3 是没有注意版权问题. 这是我的问题。 

网络时代，任何云和服务的东西，都不要过于信任。 
本地一定要有自己的备份。有备无患。 
一旦被封，你的数据，将不再是你的数据。 
比如 github star 的 repo , repo url 等，要另外用个东西存起来。 
自己的代码，不要单一的 depend on gitbub. 
应该多同步到几个地方，比如 bitbucket, gitlab, [coding.net](http://coding.net/) , oschina git 等. 
比如像我这样，被 github 杀了个 措手不及。 
你的代码，你 star 的 repo, 你所有的心血，github 不分青红皂白，没有任何提示， 
直接就可以把你的账号永久停掉。 

另一个需要注意的是,使用国外的服务, 千万注意规避相关的版权问题. 
不管这个东西是不是真正的违反了 DMCA.这样可以避免一些不必要的麻烦. 

现在留下的，唯有几天前的一张截图留念：

![TIM 图片 20180717005918.png](https://i.loli.net/2018/07/17/5b4ccf03e541b.png)

现在这个页面已经是 404 了。

有部分

# 0x04. 接下来要做的  

开通 bitbucket, gitlab, [coding.net](http://coding.net/) , oschina git 等其它仓库及镜像 
在自己服务器架设 git 服务器，并设置为主仓库，所有其它仓库都是从主仓库同步。 

另外就是, star 收藏这种数据,不能再像之前那样,直接存在账户本身了, 
而是要自己架设一个类似 bookmark 之类的服务. 
服务器不是问题, 手里有好几个,再不行用之前撸的腾讯云也是可以的.

简单搜索了下, 找到以下两个项目貌似适合使用(如果有其它合适的,也欢迎各位推荐,谢谢):

Simple bookmark manager built with Go <https://github.com/RadhiFadlillah/shiori>

API-Driven, Geeky Bookmarking Service <https://github.com/dimonomid/geekmarks>

为什么要做这些? 我直接用这些 repo 托管网站的 star 功能挺好用的. 
嗯, 回到标题了, 你可能不理解我现在的心情. 
丢失 github 2 万 2 的 star repo 是一种什么样的心情? 
算起来,这些 star 都是相当一个一个点击收藏进来的. 
算年份的话, 差不多积累了有七八年吧. github 是 08 年成立的. 





PS: 请不要在这里跟我讨论什么版权问题，我不是来跟各位版权专家讨论版本问题的。 

既然因为这两个版权问题上有些模糊的repo, github把我的账号封了，我想我已经清楚了他们的 *规则* 和 *行径* 了。 
请不要再来*提醒*我关于github的规则云云。 

我觉得封整个账号并且不给机会解封是不合理的。 
如果你觉得合理的话，请继续你的想法。也不要回复了。

所以，如果你想表达你是多么的了解他们的版权规则和来说教我这个人是如何如何不懂老外的版权， 
谢谢，你不用回复了。

第 5 条附言  ·  49 天前



感谢@phithon 提供的api 接口，利用此接口可以查询到所有star的repo. (见https://[www.v2ex.com/t/471437#r_5908994](http://www.v2ex.com/t/471437#r_5908994)和 <https://www.v2ex.com/t/471437#r_5909309> )

抽时间做了个starred repo 导出到mongodb 的小工具：

<https://gitlab.com/hacklog/githubStarredRepoBackup>

<https://coding.net/u/c0ding/p/githubStarredRepoBackup>

这个小工具只是第一步。为什么导出到mongodb, 只是方便而已。 
后面再弄个html页面查询之类的比较方便，或者， 
再弄个添加或者bookmark接口之类的应该都会比较简单。 

运行效果： ![运行效果](https://coding.net/u/c0ding/p/githubStarredRepoBackup/git/raw/master/screenshot/run_result.png)

mongo db: ![mongo db](https://coding.net/u/c0ding/p/githubStarredRepoBackup/git/raw/master/screenshot/mongodb.png)

```
db.getCollection("starred").count()
2155
```

2155 条star repo全部找回

第 6 条附言  ·  49 天前



感谢大家的回复。 
其中有些回复提供了很有用的信息。对我的帮助很大。 
但是也不缺少一些在这里落井下石的人，我觉得这很正常。 
毕竟总有一些人区分不了自己是个什么样子，评判别人的时候，从来没想过自己的。 
你遇到这样的事情，看到如你评论我一般的评论的时候，你不一定能这么淡定。 
有句话叫，站着说话不腰疼。话糙理不糙

第 7 条附言  ·  48 天前



追加了一下最终的邮件，今天晚上收到githbub的最终回复了。 Screenshot from 2018-07-17 22-28-29.png

所以，最终的结果是，永久性封禁， 不予解封。跟我之前预料的结果差不多。

![Screenshot from 2018-07-17 22-28-29.png](https://i.loli.net/2018/07/17/5b4dfd498d32e.png)

第 8 条附言  ·  48 天前



谢谢大家的回复（所有人）。

**第 4 条附言** 仅针对喷子的。如果有让你感到不舒服。 这里表示抱赚。

--EOF

第 9 条附言  ·  48 天前



谢谢大家的回复（所有人）。

**第 4 条附言** 仅针对喷子的。如果有让你感到不舒服。 这里表示抱歉。

第 10 条附言  ·  47 天前



总有些人喜欢异想天开地来黑我。黑个人都不会，所以，你被我深深的鄙视了。 
为了防止评论被那些喷子或黑子给带歪了，这里我说明一下。 
\------------------------------------------------------------------------------ 
我的 github repo 没有任何关于 kms 的内容。 
此事和微软无关，请不要扯上微软。 
\------------------------------------------------------------------------------ 
至于和 jetbrains 的 ls server 相关的代码仓库的 fork, 这个确实存在。我 fork 了。 
不过，fork 了也只是当个备份之类的，并不代表我要利用这个代码什么的。 
喷子可能会说了，你 fork 了还狡辩什么，你就是要利用？ 
我没狡辩啊，fork 了就是 fork 了，这个没有什么值得掩饰的吧？ 
如果换个地方，换个时间，我可能还会 fork. 不过，不是在 github. 
大部分人，拿工具把 jar 包反编译一下，随便再 google 参考一下，就能写出一个 ls server. 用任何你喜欢的语言。 
当然，这种能力我也是有的。所以，fork 了，还真不是想要去利用它。因为代码我其实早写了。 
但这也仅限于研究，我基本上是提倡大家（有能力的）购买授权的。 
不得不承认，jetbrains 的产品一直是很优秀的。价格也算厚道。 
即使可能是因为与它相关的 repo fork 问题，我的 github 账号被封，但这毕竟与 jetbrains 无关。 
这是 github 的问题。在 DMCA 问题上，选择了更为简单和有效的方案，对于用户的数据则是选择无视的态度。 
\---------------------------------------------------------------------------------- 
关于事后的解决方案， 
有很多朋友给我提供了建议。这里我也说一下我的想法。 
\1. 仓库可以尽量使用私有的仓库，比如 bitbucket 之类的，提供免费无限私有仓库。 
私有仓库不会存在 DMCA 问题。 
\2. 有朋友提议，可以提交 counter DMCA notice, 这个的话，我没这个打算。来回邮件折腾的时间，可能并不会比我重新上传代码到另一个平台花费的时间少。而且，其结果也没有什么保证。 
\3. 可以新建一个小号，把之前通过 api 找回的 star, 写个小工具，重新调用 star 接口，把 star repo 瞬间转移到新的小号上。技术上来说，这样做也是可行的。完全可行。 
\4. 经历了这个事情之后，你还会用 github 账号吗？ 
账号肯定是会开通的。因为有一些软件的安装和部署，需要用到 github token. 
至于还会不会用它来存自己的 repo 了，我觉得这很难说。 
经历这次的事件，我也重新认识了 github 或者说国外的一些公司。 
短期内是不可能再用 github 的 repo 来存代码了。 
公有仓库方面，我体验了一下国内的 gitee，没有觉得不舒服的地方。 
私有仓库的话 bitbucket 和 coding 都可以。 
到于 gitlab 的话，反正我也开通了一个。 
\5. 我现在就在用 github, 要是不是要马上停止使用，并且转移到其它平台？ 
这个吧，看你的使用习惯吧。如果像我一样看到喜欢的 repo 就喜欢 fork 的话，建议马上停止使用。 
因为你可能并不知道你 fork 的几百上千个 repo 中有哪个是违反了 DMCA。 
毫无疑问，github 在对待 DMCA 的问题上面是很强硬的， 
反过来说，对于用户的数据，则从来不是他们需要考虑的事情。 
当然，如果你能花时间仔细阅读他们那些规则，并且，在任何时候，你都不会犯错，不会违反那些规则的话。 
你使用 github 还是很安全的。正如你手握一把利剑，但是你能掌控自如，确保不会误伤别人或者自己， 
那这个剑就能为你所用。 
-- 20180719 更新