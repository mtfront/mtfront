---
title: 高效、async 的信息流才是好的信息流：我的 RSS setup
author: 椒盐豆豉
type: post
date: 2022-08-28T08:09:01+00:00
url: /my-rss-setup/
ig_es_is_post_notified:
  - 1
categories:
  - 重启电脑
tags:
  - patreon
  - productivity
  - reading
  - tutorial

---
# 高效、async 的信息流才是好的信息流：我的 RSS setup
简单来说，RSS 是一个内容生产规范，使阅读者可以跨平台、无干扰地在自己选择的阅读器上阅读各个订阅源集成、统一的内容，而无需专门去发布平台（各个播客、新闻网站、社交媒体、email newsletter 等） 查看。

像我一样从 RSS 盛行年代的过来的网民可能会把很多 RSS 带来的好处 take for granted，而这个流量至上的年代很多内容生产者会以其他不提供原生 RSS 支持的方式创作内容（mail list, notion, telegram channel，social platform post 等等），造成对习惯了 RSS 的读者而言 aggregation 困难和信息摄入效率低下，以至于这个无利可图的形式在跟很多新朋友提起都有点难以安利出去。

我在之前的一篇[如何利用 Zapier 给 notion blog 生成 RSS feed 的教程](https://blog.douchi.space/rss-for-notion-zapier/)里提到过 RSS 在现在这个年代对阅读者和创作者都仍有许多优势：

- 没有平台插入的、伪装成用户内容的广告
- 无需担心平台自作聪明的算法干扰导致你不在第一时间阅读 post 就错过内容
- 因为是生成一个标准规范的静态 feed 阅读而非直接访问对方网站所以像广播一样不可追踪
- 可以自选阅读器来控制阅读体验（界面、分类等）
- 创作者的内容更有机会被读者看到，而非被第三方平台算法裹挟
- 创作者的服务器压力更小，因为阅读器通常会在本地缓存一个版本，而无需每个读者都单独访问

了解了 RSS 是什么和其优势之后，另一个阻碍新用户的门槛往往是无从下手。第三方社交平台可以给新用户推送 influencer 来平缓地 cold start，但 RSS 这种完全依赖订阅源的形式，即便很多阅读器能推荐 feeds to follow，但往往只有大媒体和非常有名的 post 才会被推送，少了许多 personal touch。本文旨在分享我自己的 RSS setup 来帮助没有接触过 RSS 的朋友快速入坑。

本文是 [8 月 patreon 金主们票选出来的内容](https://www.patreon.com/posts/aug-2022-bo-ke-70538184)（我竟然在月内完成了我好骄傲）。[欢迎大家点进 9 月的投票选择下个月的博客](https://www.patreon.com/posts/sep-2022-bo-ke-71140728)：

- 真·小白友好美国理财 101·2.0 ([1.0 在这里，很多朋友跟我说看不懂所以打算写个 2.0](https://blog.douchi.space/personal-finance-for-dummies-in-us/)）
- 我的时间管理系统
- 八年美国互联网公司摸鱼经验总结
- Desk setup 2022（[2021 desk setup 在这里](https://blog.douchi.space/desk-setup-2021/)）

<!--more-->

## **阅读器选择 – Inoreader**

市面上 RSS 阅读器层出不穷，我近年用过最主流的两家是 Feedly 和 Inoreader，前者免费版虽然也够用但是付费内容较为鸡肋，广告也非常碍眼，现在已经完全 migrate 到 Inoreader only。免费版比 Feedly 好用，付费版杀手级功能我现在完全离不开。

免费版特点：

- 有广告但不是 in feed 广告，不影响阅读。RSS 这种核心是自己选择订阅源的清爽方式 in feed 广告实在是太影响体验了。
- 可使用 Google 关键词订阅
- 可以方便地分享到 pocket, dropbox 等
- 最多 150 个 feed 基本够用，folder 分类、read later 之类的基本功能也齐全

付费版特点：

- 可以订阅 email newsletter！可以订阅 email newsletter！可以订阅 email newsletter！重要的话说三遍。虽然 email 也可以通过设置 filter 提升效率，但是要单独开一个 app consume 东西和有 email 清零压力的话就会非常难受。where as 在 阅读器里跟平时信息源一致阅读率提升很多
- 可以订阅 Twitter、Reddit、Telegram Channel、Facebook page 等社交媒体的 feed
- 可以使用 automation rule 自动分类，比如我的有某些关键词/源/folder 自动星标，大幅提升阅读效率，先从星标的开始读压力小很多
- 语音朗读，中英文的效果都不错，喜欢做事的时候听 podcast 的朋友应该会觉得这个功能很实用，单看信息摄取目的的话毕竟本身是文字的内容会比 podcast 简洁很多
- 有便宜的去广告和扩容到 500 条 feed 的 plan，如果用觉得自己不是 power user 的话可以选择这个版本

我目前用的是前阵子大促 3 个月的，用了几天就离不开了。据说他们每年黑五会有年费半价，感兴趣的朋友可以先用免费版到时候入坑。

## **我的阅读系统**

### **Email Newsletter（付费功能）**

Inoreader pro 版可以直接添加 email newsletter，每个 feed 可以生成一个 email， 然后在相应的 newsletter 上照常订阅即可。

### **Telegram Channel**

直接在 telegram 里 consume channel 信息没有任何控制效率极低，好在这里有[第三方工具可以把任意 telegram channel 生成 rss feed](https://blog.feeds.pub/telegram-rss.html)，然后直接在阅读器里订阅即可。例如[复制这个链接订阅我的书影音游剪报用这个工具生成的 feed](https://rsshub.app/telegram/channel/mtfront)。

### **Automation Rules（付费功能）**

我基本只设置了关键词针对一些信噪比比较低的源筛选出精华内容。例如少数派、Telegram 上的自留地这种，平时发的内容如果每条都跟有点太多，于是我设置了例如“周报”、“本周看什么”之类的关键词筛选，符合条件直接加星。

对于信噪比比较高的渠道，比如 [visualcapitalist](http://www.visualcapitalist.com/)、[our world in data](https://ourworldindata.org/)、[阮一峰的科技爱好者周刊](http://www.ruanyifeng.com/blog/)等，我有一个必读 folder，设置了规则这个 folder 的内容自动加星。

### **Folders**

我有如下分类：

- Must Read – 上面提到的信噪比较高的渠道，打开 app 凡是有新的就会看。
- Newsletter – 用付费版订阅功能订阅的 email newsletter，厕所读物，大概一两天看一次
- Social – 这是各个社交平台上认识的网友的独立博客等等，aka 不一定对内容本身感兴趣但只是当了解大家的兴趣和生活，发布频率较低基本有内容就会去看（感觉我自己应该是这个分类里发布最频繁的…… ）
- News – 诸如 SoliDot 这种发布量比较大的、新闻性质的媒体。这个 folder 我不会清零，偶尔点进去刷两下
- Entertainment – 发布量较大，但跟 news 类相比不 time sensitive 的，比如少数派、自留地、不求甚解这类的
- Engineering – 一些技术博客，感兴趣的话题才会点进去看

### **Backlog**

因为重要的 folder 有清零习惯，但是很多文章当时不一定有时间/心情看，因此我会配合使用 pocket mark ”以后看“。出于发布频率或者是在手机上不方便编辑等原因“以后发我 telegram 剪报”的文章也会存在 pocket 里 。此外 Inoreader 只能从 RSS 源星标而不能标记外部文章，因此 pocket 也算是一个补充。

如果说 Inoreader 是每天都会看的 inbox 的话，pocket 就是一个想起来再看的 backlog 了。

## **一些我订阅的 RSS 源**

标注了 [email] 的是只提供了 email 订阅渠道，我用 inoreader 付费 newsletter 功能接受的源。其他的源都直接提供了 RSS feed，链接粘贴进 RSS 阅读器就可用。

### **新闻**

- [Morning Brew](https://www.morningbrew.com/daily/r?kid=aa5ac021) [email]，一个科技、金融新闻的综合性早报
- [TLDR](https://tldr.tech/) [email]，科技、科学新闻，除此之外还会推送一些好玩的开源项目
- Robinhood Snacks [email]，其实跟 morning brew 有点重复，而且利益相关感觉有 bias（上次 Robinhood 裁员的是它就只字未提），我一般先看 morning brew 这个快速看过作为补充
- [Good News](https://goodnews.eu/en/feed/)，会集中推送一些振奋人心的新闻，有利于缓解正式/环境抑郁
- [Rest of World](https://restofworld.org/feed/latest)，聚焦欧美之外的世界各地科技新闻
- [Solidot](https://www.solidot.org/index.rss)，发布频率非常高的各类新闻，可以扔到 news folder 当 feed 看
- [TruthOrFiction](https://www.truthorfiction.com/feed/)，会 fact check 网上一些流行传言

### **科技/互联网**

- [阮一峰的科技爱好者周刊](https://feeds.feedburner.com/ruanyifeng)，虽然是科技爱好者周刊但不仅限于科技行业，有很多各式各样科技相关的趣味新闻和 quote，每周必读
- [独立开发者的灵感周刊](https://www.decohack.com/feed)，介绍很多好玩的软件、服务、app，细节比较糙快平口语化很多错别字，但是看看新产品内容蛮好玩的不仅限于“独立开发者”
- [Benedict’s newsletter](https://www.ben-evans.com/newsletter) [email], 也是科技相关和一些 random idea，我只订阅了免费版本
- [The Pragmatic Engineer](https://newsletter.pragmaticengineer.com/) [email]，顾名思义码农行业 newsletter，我也是免费版
- [A list apart](https://alistapart.com/main/feed/)，网站设计和开发主题的技术博客

### **各类深度阅读**

- [Visual Capitalist](https://www.visualcapitalist.com/feed/) – 每周若干推送的数据可视化报告，内容从经济文化到自然科学都有
- [Our World In Data](https://ourworldindata.org/atom.xml) – 信噪比很高地发布一些 data explorer，从社会人文到环保等等
- [The Pudding](https://feeds.feedburner.com/pudding/feed)，各种好玩的数据可视化报告，信噪比也比较高一月就发一两篇
- [Bartosz Ciechanowski](https://ciechanow.ski/atom.xml)，不发则已，一发就是超长图文解释各种复杂的机械、物理概念等
- [Wait But Why](http://waitbutwhy.com/feed)，也是解释性长文，画风没有上面的精致，发布频率非常低
- [Nicky’s new stuff](https://ncase.me/feed.xml)，非常好玩的独立开发者，会把概念解释做成互动化小游戏教程
- [即食历史](http://cuphistory.net/feed/)，图文并茂的各种历史故事

### **文娱**

- [Newlearner 自留地](https://rsshub.app/telegram/channel/NewlearnerChannel)，涵盖科技、游戏、金融等，我的很多其他 newsletter 和独立博客都是在这上面发掘的
- [The GameDiscoverCo](https://newsletter.gamediscover.co/feed)，面向独立游戏开发者的分析，免费版内容比较浅但是看一下了解个大概还是不错的
- [The Marginalian](https://feeds.feedburner.com/brainpickings/rss)，文化、艺术、科学相关周刊
- [少数派](https://sspai.com/feed)，无需多说简中消费主义大本营，科技、游戏、影视等，信噪比比较低但是配合前面的关键词过滤还是的有不少可读信息的

### **其它**

- [Bird of the day](https://moresci.sale/@birds.rss)，每天图文介绍一种鸟。我偷了个懒直接用了 mastodon 上的 bot 的 rss。
- [Shyrism.News](https://shyrz.me/rss/)，每周推荐两篇各种不同主题的文章
- [我的书影游剪报](https://rsshub.app/telegram/channel/mtfront)，此处插入一条硬广，之前发的书影游内容比较多，现在大多数我从包括但不限于以上阅读源读到的觉得重要/有意思的内容会总结出来。

以上是大概扫了一眼我的订阅列表选了最近有动静的还算推荐的源，很多最近没发的可能有遗漏只是我订阅源里比较小一部分。此外大家有其他源/newsletter/telegram channel 的话推荐的话欢迎留言！
---
{{< hint danger >}}
如果您觉得本文对您有帮助，想支持我的博客创作，或者有特定的内容想要看到，或者干脆就想单独聊五毛钱，欢迎点击下面按钮成为我的金主：
{{< /hint >}}
{{< button href="https://www.patreon.com/bePatron?u=46962965" target="_blank">}}成为 Patreon 金主{{< /button >}}
{{< button href="https://ko-fi.com/S6S130C16" >}}在 Kofi 上给我买杯奶茶{{< /button >}}

{{< details "Migrated Comments" open >}}
### Comment by Ovler on 2022-08-28 01:33:03 -0700
Email Newsletter 还可以通过免费的 <a href="https://kill-the-newsletter.com/" rel="nofollow ugc">https://kill-the-newsletter.com/</a> 转化成 RSS 再进行订阅，这个服务也是可以自建的。

### Comment by 椒盐豆豉 on 2022-08-29 20:45:55 -0700
感谢分享！我还要用 inoreader 其它付费功能所以应该会顺便继续用了，但是可以想象应该对很多人非常有用了！

### Comment by 沉舟侧畔 on 2022-10-25 21:09:29 -0700
rss的困难之处在于原文有更新时无法提醒，还得自己重新回去看

### Comment by  on 2023-03-12 19:17:46 -0700
github上有一个仓库RSSHub，可以将任意内容转为RSS订阅

{{< / details >}}