---
title: 又双叒叕一篇小白个人博客选什么工具或平台
author: 椒盐豆豉
type: post
date: 2023-06-11T02:57:00+00:00
url: /choose-blog-tool/
featured_image: https://media.douchi.space/douchi/media_attachments/files/110/524/994/735/412/405/original/6c7e830c4e3c7f92.png
categories:
  - 重启电脑
tags:
  - tutorial
  - patreon
  - wordpress
  - hugo
---

之前忘记在哪看到一篇建站教程 ，给了类似这么一张图，实在找不到原文/图了，大意翻译一下：

![](https://media.douchi.space/douchi/media_attachments/files/110/524/994/194/177/667/original/9871a5b4aede6230.png)

其实就是自嘲了一下博客圈都喜欢捣腾建站啦 refactor 啦什么的，建站教程/折腾日志写得越欢的实际后续博客文章数量越少。

![](https://rakhim.org/images/honestly-undefined/blogging.jpg)
（后来[象友评论补充](https://thirdshire.com/post/blogging-journey/)了我想找的那张[原图在这里](https://rakhim.org/honestly-undefined/19/)）

本写了二十年博客的话痨今天就来打破一下 stereotype，建完站之后的因为新鲜劲和 performance improvement 倒是已经井喷了三篇文章了。

趁着[前两天刚捣腾过一次建站](../blog-migrate-wordpress-hugo)还记忆犹新，也来老生常谈又双叒叕写一篇面向小白的“个人博客选什么工具或平台“的建站文。

本文其实是我 [6 月 Patreon 博客选题投票](https://www.patreon.com/posts/83914635) trending 胜出选项，没想到吧因为新博客表达欲过于旺盛已经学会抢答了（highly unlikely 但是万一最后另一个选项胜出大不了两篇都写），以前不拖到当月结束就不错了。[7 月博客投票提前释出敬请投票！](https://www.patreon.com/posts/84399357)

- 我就是不想 grow —— 一份码农生涯躺平挣扎记录
- 电驭游宅好伴侣，Aer 背包全家桶体验
- 纯远程工作讨厌做饭厨渣如何糊弄吃饭问题

## TLDR

本文受众是纯小白，有一定技术基础的相信可以根据自己需求选择。简化起见在此只讨论几种最常见的建博客方式：Github Pages，Wordpress 自建站，免费第三方托管（Medium, [wordpress.com](http://wordpress.com)，telegra.ph 等），Notion（其实也是第三方托管的一种），付费第三方托管（wordpress.com, squarespace 等）。

![](https://media.douchi.space/douchi/media_attachments/files/110/524/994/735/412/405/original/6c7e830c4e3c7f92.png)

私以为纯博客的话只有如下两种选择 make sense：

- 刚开始/还没开始写博客，想培养写作习惯，不会/不想花时间在学习 git 和一些 command line 基本操作：Notion
- 有写作习惯，或熟悉 git 和 command line 基本操作的人：无脑选静态生成（其中 github pages 是最流行且免费的托管平台）

<!--more-->

## 为什么排除了 Wordpress 自建站

原因我在前两天的[建站文](../blog-migrate-wordpress-hugo)中也稍有提到，在此复制粘贴：

- 隔三差五会坏掉。光看我 [discord server 里站点状态的更新](https://discord.gg/cESS4JpsdG)一大半都是博客故障通报就知道了，内容较为简单的博客比上千人用的社交网络还多维护就很离谱。绝大多时间修是好修的，[偶尔需要 debug](https://blog.douchi.space/wordpress-all-in-one-wp-security-aios-locking-cloudflare-out/)，但一个人运行的东西又不可能 24 小时维护，别人要看文章的时候用不了就很烦人。
- 要钱。因为要自己租服务器，就算可以多个应用 share，也是一笔开支。
- 访问速度慢。自己的小服务器优化不到哪去。
- 臃肿难定制。其实 Wordpress 功能很多，博客只是其中一小部分，于是有很多用不到的 bloated 服务和代码在占用宝贵的服务器资源，虽然提供了图形界面，但大多数定制被模版所限，模版和插件质量也良莠不齐需要自己鉴别。而直接改代码又得读它臃肿的代码很麻烦。

除此之外，其实对不熟悉 command line 和 git 的博主而言，即便很多服务器供应商提供 Wordpress 一键安装，但毕竟是自己运营一个带数据库的动态服务，后续要站能没问题地跑起来难免会接触到技术细节，其实对技术需求比抄 command 就能跑的静态生成站**技术要求高得多**。

此外兼容性其实也存疑，除非 Wordpress 架构内部迁移，否则很可能出现各种问题，[建站文](../blog-migrate-wordpress-hugo)也涉及了很多。

因此我在上图中把它放在了成本、定制性和难易程度都三不沾的中间。完全不推荐任何要建新站的人选择自建 Wordpress。

我上次建站选 Wordpress 纯粹是因为小学写博客时候流行沿用下来的习惯。用了快三年下来发现劳民伤财还不稳定，现在变成了一个坚定的 wordpress （博客用途）黑。

## 为何排除免费第三方托管(wordpress.com, medium, writely, [telegra.ph](http://telegra.ph) 等）

- 互不兼容，将来要搬家甚至自己保存内容只能看平台脸色，第三方工具的可用性不能保证
- 甚至有的站没有 RSS。关于为什么 RSS 对于任何认真写博客的人来说至关重要，见我之前写的 [notion RSS 教程](../rss-for-notion-zapier/)和[我的 RSS setup](../my-rss-setup/)
- 免费托管定制程度相当有限，没有模版还好说也不是所有人都需要定制化，但是个人简介、友情链接之类的 metadata 很多平台都没地方放就很令人不爽了
- 免费版有广告，毕竟平台 host 要赚钱嘛

## 为何排除付费第三方托管(wordpress.com, squarespace 等）

- 写博客是马拉松而不是短跑，只要有写作习惯，即便觉得现在成本可以接受，但多个几年积少成多，像我这种写了二十年博客的体验尤其深刻
- 这些平台多为多用途如电商、社区，需要很大灵活性，付费的很大一部分溢价是花在这些个人博客用不到的功能上的
- 迁移成本高（因为互不兼容）和平台掌控可以随意加钱导致的未来成本的不可预期性

## 什么情况推荐 Notion

像前面 TLDR 说的，主要是两类人。

- 刚开始/还没开始写博客，想培养写作习惯：这种时候花很多时间在建站研究上，迟迟不开始写文章，就落入了开头那张图里自嘲的只捣鼓建站不写文的陷阱。博客的本质是提供记录和传播自己想法的沉淀空间，考虑得再周全也不如先动手开始写。
- 不会/不想花时间在学习 git 和一些 command line 基本操作：Notion 虽然也有一定上手难度，但毕竟是一个面向普通用户的工具，且跨平台 & 有网页版，GUI 做的也还算简洁明了。

### Notion 博客的好处

- 易上手，跨平台，随时可以写
- 对个人用户免费，还自带图片存储空间
- （跟其它笔记软件相比）有较为好用且能公开分享的网页版，读者阅读方便
- 有一定定制性，通过数据库、各种排版技巧等可以做出漂亮的主页
- 数据库功能提供了灵活的 view，可以实现 category 和 tag 等功能
- 可以导出 markdown，将来迁移较为方便
- 通过一定手段可以实现 RSS

### Notion 博客的缺点

- 没有原生 RSS，[要生成 RSS 得折腾](../rss-for-notion-zapier/) 且免费与否看第三方工具脸色
- 定制程度有限，比如色调字体就改不了了
- 免费版留言和互动不便
- 无法统计访问量和访客信息
- Notion 有时候速度比较慢
- 不在搜索引擎中又是一个局域网
- 部分网友对其亲中的态度和数据安全性存疑

## 什么情况推荐 Github Pages

- 熟悉 git 和 command line 基本操作的人：装流行的静态站生成工具和跑起来看教程就是几分钟的事（至少我用的 hugo 是），详情参考[我的前两天的迁移文](../blog-migrate-wordpress-hugo)，考虑到其它所有的优点，已经会 git & command line 的可以无脑选这个选项无需再考虑 notion
- 有写作习惯：确定自己要长期写博客的话，考虑到下面即将提到的所有优点，如果你愿意花 30 分钟稍微学习一下 git（也就需要记住个位数的命令） & command line（用来装生成工具）操作，其实是一个一劳永逸的事情，可能不比 setup 好 notion 自己想要的排版和数据库的时间长

### 静态生成 Github Pages 博客的好处

- 免费，稳定（有微软/github 背书）
- 速度快，因为是静态页面
- 兼容性强易迁移，流行的基本都是 markdown 格式的文章
- 定制性高，网上到处都是免费模版能选，此外稍微会点 html & css & javscript 都能改出来很多功能，比在第三方的系统里倒腾方便和自由很多
- 有 git 背书的强大版本管理有迹可循
- 流行工具基本都支持 RSS
- 可以利用 Disqus 插件等方便实现留言区，很多模版也支持
- 可以留用 Google analytics 等统计访客信息，很多模版也支持
- 搜索引擎可以索引到，方便检索
- Github 对内容的审查不管有无与否肯定是比 Notion 的松的，至少墙外用户的数据肯定也不在中国（有象友在[评论里补充](https://douchi.space/@mtfront/110525031995790160) Github 应该是不能发 NSFW 的内容，我自己没有这个需求所以忽略了这一点，同样限制应该也适用于免费托管和 Notion。需要发 NSFW 的博客内容的话除了对应专用平台之外可能在本文里的选项只有自建站。）

### 静态生成 Github Pages 博客的缺点

- git 和生成工具的学习成本（也没有很高，有非码农零基础[象友补充](https://douchi.space/@mtfront/110525031995790160)道跟着教程两天就搭好了没出过问题）
- 需要另寻图床（当然也可以把原图直接存在 github repo 里啦但就有压缩的问题）
- 跨平台编辑（如没装 git 的电脑或手机）不便（可以在 github 网页版手写 markdown 但肯定没 notion 方便啦），像我其实就在 notion 里打草稿发的时候再复制，倒是 notion 复制直接是 markdown 很方便
- 如果没有定制域名把自己 github 用户名藏起来的话有人可以顺着你的 github repo 找到你的编辑历史、草稿等，所以不另建私人 repo 和不用自定义域名的情况下不如博客平台私密性好

## 总之

不管选用什么工具，希望大家都能找到自己私下也好公开也好的表达空间！Let’s make blog great again!（此处坑一篇想写很久的“为什么你需要一个个人博客”）

---
{{< hint info >}}
如果您觉得本文对您有帮助，想支持我的博客创作，或者有特定的内容想要看到，或者干脆就想单独聊五毛钱，欢迎点击下面按钮成为我的金主：
{{< /hint >}}
{{< button href="https://www.patreon.com/bePatron?u=46962965" target="_blank">}}成为 Patreon 金主{{< /button >}}
{{< button href="https://ko-fi.com/S6S130C16" >}}在 Kofi 上给我买杯奶茶{{< /button >}}