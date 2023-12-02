---
title: 静态博客半年记
author: 椒盐豆豉
type: post
date: 2023-12-01T18:08:00-08:00
url: /static-blog-half-year/
categories:
  - 重启电脑
  - 关我屁事
tags:
  - blog
  - hugo
booktoc: true
image: https://media.douchi.space/douchi/media_attachments/files/111/509/945/675/233/390/original/e0afeee188dea4cf.png
---

半年前，我把从快 20 年前开始用的 Wordpress blog [迁移到了 github pages 上开始用 hugo 做静态博客]({{< relref "/posts/2023-archive/2023-05-31-blog-migrate-wordpress-hugo" >}})。从小学开始写博客在 blogcn 上入了坑，后来[三年前新建现在这个博客时候]({{< relref "/posts/2023-archive/2020-10-29-hello-world-its-me-again" >}})也就按习惯继续用了，其实建站时候未做太多横向对比。三年用下来发现 20 年前用托管站时候不曾想过，现在自建站要处理的问题良多，遂动了迁移静态博客的念头。外加本来就是程序员，技术门槛几乎不存在，也用不到除了博客和评论外的其它 CMS 或电商功能，用 Wordpress + VPS 花钱找罪受，遂在[日本出行]({{< relref "/posts/2023-11/7-japan-2023" >}})最后几天体验 digital nomad 生活的时候一鼓作气把博客给迁移了。

现在刚好半年，回头看可是说这大概是我写博客史上最庆幸和后悔没早做的决定，所以迫不及待没等到一年就来写这个总结。本文就来回顾一下这半年中平台变化给我的博客本身和写博客习惯带来的改变，以及半年来我的博客都写了些什么。

<!--more-->

## 变化
迁移博客之后，我发现给我带来的变化远大于迁移前的预期。迁移前我可能想的是能省下租服务器的钱以及不需要维护这种“硬件”变化。没想到给我更大的改变反而是软性的。

### 更新更频繁写作动力更足了
我万万没想到迁移一个静态博客能让我的博客产量暴增。拿 2023 年举例。1 到 5 月还没迁移博客的这五个月时间里，我总计发布了 10 篇博文，其中 3 篇还是播客刚开始做早起更新复制粘贴文案（现在已经不在博客上单独发文宣传播客[只留一个入口]({{< relref "/posts/2023-archive/2023-01-18-podcast-bgm" >}})了），真正的博文只有 7 篇 。迁移静态博客之后的 5 月底到 11 月的 6 个月里，我总计发布了 52 篇博文（数完我自己都震惊了），月均产量是原来的 6 倍多。光迁移之后的这半年的产量已经超过以前高产年份的全年总量了（2021 年写了 46 篇）。而且个人认为也没有在水博客，对这半年的产文质量还是挺满意的。

我作为一个写了 20 年博客的人，换形式的新鲜劲当然也有，但应该不只是这个原因，而且这几个月毫无消退的迹象产量不降反增，我觉得有如下几个原因：

#### 编辑本地化
不存在网络状态的影响，随时随地都能写。以前虽然也能在笔记软件里打草稿，但还要复制到编辑器里重新排版就没有太大动力不在编辑器里写，也不存在遇到点什么网络或者服务器小问题担心草稿丢失的情况。

#### 使用 markdown
markdown + 用平时写码用的编辑器，本来就比 Wordpress 的 GUI 顺手很多。可能已经是我先入为主，一直不大认同“markdown 不适合非技术纯文字输出者“这种说法。它语法如此简单，且写博客基本只需要记住 heading、超链接和图片三个快捷键就能很快排版，需要用到其它语法随时查 cheat sheet 几秒钟的事，远比 GUI 里点找按钮点按钮从键盘切换到鼠标高效且简单得多，也就跟大众熟知的复制粘贴 ctrl + C & ctrl + V 一个记忆难度。

更何况 notion 和很多论坛的输入也是 markdown 语法，复制粘贴方便不说，这些 consumer facing product 也在用根本不是一个技术性的东西，个人认为更利于写作者回归文字本身。

#### 有 GitHub history
这点算是程序员更 comfortable，没有上手和迁移成本就能让所有编辑历史都保存了下来，因为知道能保留更久而更愿意花精力写更多。作为对比不管是第三方托管还是自建站，上面的内容要额外花精力甚至金钱备份。过去虽然写得羞耻东西更多不见微妙，但少数想保留下来的东西因为长年累月更换平台、设备、平台倒闭等原因也散落在各处，这件事本身就很 discouraging。而 GitHub 只要我的饭碗还在，可预见的未来应该 not going anywhere.

### 更愿意个性化了
Wordpress 当然也提供了很多个性化的选择和有很多现成的插件可选。但其一它那个 php gui 编辑器用起来就很别扭，不是想去写模版或者大改的话懒得去设置本地编程环境用真的编辑器；其二我也对 php 没那么熟悉只有某份工作用过一年的 hacklang，改起来更为头大；其三也没有功能完整的版本管理，很多修改都是 throw away work；其四可能也是框架和用途更广泛的原因，很多模版代码真的很臃肿。种种因素让我一个（并不是特别爱倒腾的）程序员都不是很愿意个性化我的网站，普通用户绝大多数更只能看模版和插件面子了。

静态博客这边，虽然对 go 更不熟，但是模版、样式和功能绝大多数时候改 JS + HTML 就行，外加本地部署测试环境所见即所得，debug 起来容易太多了。我算是不爱倒腾模版的人，但是随手改一些 quality of life 的小地方更简单顺手，外加有 github 做版本管理，就更愿意去个性化自己的站点了。

### 重新整理了分类
之前自己 Wordpress 博客的分类和 tag 组织我一直不是很满意。借着迁移之机重新把自己的分类放到站点 motto 喜欢就买 不行就分 多喝热水 重启电脑 这四句话里了，用了半年感觉概括性还挺强的挺满意的。

### last but not least, 维护成本和难度大幅降低
金钱自不用说，少了服务器的月租，钱虽少但一年也能多吃几顿我外卖了。最重要的是 GitHub 它的稳定性肯定比我用的野鸡 VPS 供应商强，以及静态博客部署好就不会自己崩掉，用来维护的时间成本消失了可以更多时间花在文字本身，也不至于出现别人想看文章但我博客却挂了这种情况。

看了一眼记录，静态博客之前至少一个月挂一回。挂的时候我在家能立刻修还好说，要是刚好我在外面它挂了，这动辄几小时甚至几天的 down time 带来的站点 availability 根本没眼看。变成静态博客托管在 github pages 上自然就稳定如鸡从来不挂了。

之前 Wordpress 挂掉时候的原因还需要 debug，这点我也觉得极为不“非程序员“友好。最常见的状况是自动清理数据库 log 的 process 不知道什么原因挂掉了或者没有及时清理，导致 database log 憋满了硬盘，数据库服务无法运行，博客自然就挂掉了。我还遇到过一些自己作出来的[疑难杂症]({{< relref "/posts/2023-archive/2022-11-10-wordpress-all-in-one-wp-security-aios-locking-cloudflare-out" >}})，网上完全搜不到现成答案只能自己 debug，难以想象非程序员如何在这种情况快速自救（说是自己作但也没有任何非 GUI 操作，就是在一个插件里把 cloudflare 不小心给 block 了）。

更何况完全托管在 github 这种需要极高稳定性的站点上，基本可以完全不用担心 DDOS 这种事。cloudflare 没挡掉的部分 GitHub 也会帮你挡掉。亲眼见过别的长毛象小站点被人 DDOS 掉几千块，和我自己的长毛象站点被 DDOS 幸亏 cloudflare 上能进行一些手动处理能挡掉。没有网络安全相关经验的个人托管的博客遇到这类事件应该也会很头大。

## 内容
说完了给我自己带来的变化（真没想到能写这么多，我可真是个话唠），来盘点一下读者们能看到的内容吧。

### 最受欢迎的博文
1. [2023 年了你为什么需要写博客]({{< relref "/posts/2023-08/5-2023-why-you-need-a-blog">}}) - 毫不意外是我访问量最高的一篇博客。但最令我惊喜的是，后来发现真的安利动了好几位博友开始写博客了，光上次在我自己发起的[#中文独立博客分享](https://douchi.space/@mtfront/111336888563955403)里就看到几个因为这篇开始写的，成就感爆棚。喜欢看博客想要看到更多的网友开始写博客，这篇没想到真的一定程度上达成了这个愿景。
2. [如何建立写博客的习惯]({{< relref "/posts/2023-08/6-keep-blogging" >}}) - 应该也是乘了上一篇的热度。
3. [年度购物之最]({{< relref "/posts/2023-11/8-shopping-2023">}}) - 没想到这么近期发的一篇消费主义购物总结短文会短短时间就称为我博客第三受欢迎的文章，可能刚好趁着黑五天时地利吧。顺带提一句今天刚看过 11 月的带货收入是平时的 4、5 倍，果然到了购物的季节。![](https://media.douchi.space/douchi/media_attachments/files/111/506/617/989/600/179/original/2755a38e28208606.png)
4. [从社交到生产力，一篇文上手 Discord]({{< relref "/posts/2023-archive/2023-06-01-discord-social-productivity" >}}) - 这篇我也不知道为什么会火，安利来说是比较 niche 的一篇文章。可能因为是静态博客发布之后第一盘博文？
5. [美国码农前半段职业发展道路（career ladder）]({{< relref "/posts/2023-archive/2022-08-15-software-engineer-career-ladder">}}) - 看到排这么靠前有点惊讶，因为这是一篇旧文，根本不是近半年写的。当然我的读者从豆瓣上开始本来就很大一部分来源于[职业]({{< relref "/tags/career">}})相关的文章，功能性比较强嘛。

### 最受欢迎的话题
1. [消费主义陷阱]({{< relref "/tags/消费主义陷阱">}}) - 测评/安利/体验类文章应该是我近几年写博客的最大主题，我也时常自居消费主义博主。这个博客甚至附带了一个[剁手安利数据库](https://mtfront.notion.site/mtfront-shopping-reviews-e568ee6ebaa44b5da146cbe4ac4663eb)（虽然开始写[玩物志]({{< relref "/tags/monthly">}})之后好久没更新了吧）。虽然测评博主这个市场早已过饱和所以靠这个做大以我愿意付出的精力应该没什么可能，但是专业测评之余，看看本来就认识的普通人写的体验也算是一个补充吧。另外本来都在免费写了，近两年开始用 affiliate，收入甚至可以稳定 cover 豆豉站的所有运营成本了，也算是意外收获吧。
2. [blog]({{< relref "/tags/blog">}}) - 我不怎么捣鼓建站，前面说的意外写了几篇流传稍微广一些的博客，导致写博客本身的博文也排名比较靠前。估计放长远点会被其它我常写的话题盖过吧。
3. [productivity]({{< relref "/tags/productivity">}}) - 没想到我已经写过这么多生产力相关了！
4. 各种生活相关 - 没有一个单一的 tag，大体就是[游记]({{< relref "/tags/travel" >}})、爱好、[健康]({{< relref "/tags/wellness">}})这类。虽然单篇没有特别受欢迎的，但是零零散散也有不少浏览量。
5. [职业]({{< relref "/tags/career">}}) - 感觉近半年写的少了，但像前面说的旧文被翻出来的浏览量竟然也挺高。

### 我都在写什么
这半年写的博文里（一篇文章可能属于多个分类）：
- [喜欢就买]({{< relref "/categories/喜欢就买/">}})：测评、体验、书影游、兴趣类文章。23 篇占据了几乎半壁江山，当仁不让地位居第一。
- [不行就分]({{< relref "/categories/不行就分/">}})：一些关于生活的随机感悟，本非情感博主半年只写了 3 篇勉强到这个分类的。
- [多喝热水]({{< relref "/categories/多喝热水/">}})：健康相关和游记，写了 13 篇。
- [重启电脑]({{< relref "/categories/重启电脑/">}})：教程和职业相关，做的 side project 基本也在这里。16 篇。
- [关我屁事]({{< relref "/categories/关我屁事">}})：我个人站点相关的 PSA。

### 我最喜欢的博文
数据往往不跟我个人便好相符，这里留个角落也插点私货（等等，整个博客不就是我的私货）。这半年来我最喜欢的博文有：
- [玩物志第 7 期：未来近在咫尺]({{< relref "/posts/2023-11/11-spark-joy-monthly-vol-7-2023-11">}}) - 因为是月报而不是更通用、有用的文章，所以通常都不会太多人读。但每次我都写得非常开心，可能我就是喜欢卖安利吧。这一期格外喜欢，因为硬件上并没有玩太多东西去太多地方，也并不是第一期把消费月报 repurpose 成一个全面的月度小结，但这个月我的心态确实发生了很多变化，不再擅长表达情绪的我也通过玩物志这个形式一定程度上表现出了我对生活重燃的热情，自己很喜欢。
- [2023 年了你为什么需要写博客]({{< relref "/posts/2023-08/5-2023-why-you-need-a-blog">}}) - 能带动哪怕一个人坚持写博客也值了。本来写之前会怕辞不达意，没想到写出来之后比预期的满意。
- [从潜水员戴夫聊起，说说这些年我喜欢的独立游戏]({{< relref "/posts/2023-09/9-favorite-indie-games">}}) - 也是本来只想浅浅安利一下 Dave the Diver 顺便复制粘贴一下近年来喜欢的独立游戏短评，没想到越写越激动洋洋洒洒快写成万字长文了。我的博客读者中喜欢游戏的不那么多似乎很难卖出安利，但这里面每个游戏都很喜欢，希望能透过文字传递出一点热爱。
- [黄石和大提顿秋游]({{< relref "/posts/2023-10/2-yellowstone-2023">}}) - 我很少写游记，绝大多数时间都用照片 + 嘟的形式记录。这篇本来只是想把发过嘟的图 photo dump 到博客来给只看博客的读者分享一下我看到过很震撼的美景，没想到写着写着就变成一篇 legit 的游记了。
- [Urban 遇上 Travel, 全方位提升出行体验的 Aer 背包全家桶]({{< relref "/posts/2023-09/4-aer-bag-collection">}}) - 本来就是一个 niche 的爱好，外加是中文圈不怎么有名的牌子（可能 peak design, bellroy 在中文世界名气更大也动不动就上少数派），所以写出来通常没啥流量。但自从入坑 one bag travel 界以来真是打开了新世界大门，不是不买包，只是没遇到对的包，一入 aer 深似海，出行方式完全改变开始坚定 [one bag travel]({{< relref "/posts/2023-archive/2023-06-02-one-bag-travel-2-years-in">}}) 了。

## 流量分析
### 流量来源
- 直连链接：67% 的流量来自这里，大多数应该是我自己在长毛象、[Telegram 剪报频道](https://t.me/mtfront)和 [Discord 社群](https://discord.gg/cESS4JpsdG)上发布的更新。
- Google 搜索：16% 的流量，我没想到占比这么高。
- 友链、其它博客中的引用、博客聚合站等：8.9%，没想到会占这么高比例……
- womenoverseas：2.1%，偶尔觉得比较实用或者适合论坛的文章会搬运到她乡上，或者在相关回复中提到对应博文。
- 豆瓣：1.3%，还没有完全脱离豆瓣的时候会在豆瓣上同步更新一些文章，链接到博客。
- RSS：0.9%，没想到只有这么少，但也有可能是大家使用不同的 RSS 阅读器，以及有些阅读器未附送 referral 信息所以算在直链里了。

### 有机流量
没有关注我其它社交渠道，通过搜索而来到我博客的人们。在这之中访问量最高的几篇是：
1. [湾区 vs 西雅图——搬家一年小记]({{< relref "/posts/2023-archive/2022-11-25-bay-area-vs-seattle">}}) - 可想而知，估计是搜索了湾区和西雅图的对比。
2. [在美国（湾区）送外卖是怎样一种体验]({{< relref "/posts/2023-archive/2020-10-09-food-delivery-doordash-bay-area-experience">}}) - 这篇我完全没想到在很长一段时间里贡献了我最大的 organic 流量，现在也跟湾区西雅图那篇不相伯仲。
3. [搞姬是世界上最幸福的事——这些年我看过的姬片]({{< relref "/posts/2023-archive/2021-04-22-lesbian-movies-i-watched">}}) - 虽然内容确实就是如题，也确实是我亲手写的，但总感觉被搜索引擎搜到跑来我博客有点……奇怪。
4. [美国码农前半段职业发展道路（career ladder）]({{< relref "/posts/2023-archive/2022-08-15-software-engineer-career-ladder">}})
5. [中年码农在 pandemic 的尾巴（？）再就业报告]({{< relref "/posts/2023-archive/2021-08-01-senior-software-engineer-pandemic-job-hunting">}}) - 这两篇都是实用性的职业文，意料之中。

其中搜索关键词按点击量排序：
1. 椒盐豆豉 - 意料之中，估计是已经在别的平台关注我或者看到过相关提及，或者是知道博客想来直接访问的人。这个分类的 CTR 高达 82.3%.
2. 姬片 - 前面说过了，不是很 comfortable 被这个关键词搜到。CTR 也有 10% _ :(´ཀ`」 ∠): _
3. Oura ring 测评 - 没想到多年前写的[一篇测评]({{< relref "/posts/2023-archive/2020-11-28-oura-ring-review-only-a-sleep-coach" >}})现在还有高达 20% 的 CTR 和一直有持续流量进来。
4. 三星z flip 3测评 - 也是[早年写的测评]({{< relref "/posts/2023-archive/2021-09-18-galaxy-z-flip-3-review" >}})，没想到这么多年了都出到 5 了 3 还会有 14% 的 CTR 点进来……
5. notion 豆瓣 - [完全不是教程只是 PSA]({{< relref "/posts/2023-archive/2022-04-27-douban-notion-backup">}})，点进来的人可能要失望了（也有 10% 的 CTR）。不过倒是给了教程链接。

### 访客分布
我的访客来自世界上 111 个国家这我也是没想到的，不过很大一部分原因可能是我的博客被豆豉站拖下了水，在薛定谔的墙里，所以应该有很多 VPN 流量。最多访客来自美国，占到 46%。中国大陆 + 香港紧随其后占比 20%（其中香港占到 8.5% 可能是 VPN？），日本 8%，加拿大 6%，新加坡 5%。美国内部，湾区、LA 和西雅图遥遥领先。

Google 给的访客兴趣中（一人可以有多个兴趣），科技爱好者 57%，阅读爱好者 54%，轻度电视和重度电影爱好者都占 44%，社交网络爱好者 37%。

45% 的人使用 iOS 访问我的博客，Mac 也占到 26%，接下来才是 Windows 21%，安卓 10%，Linux 4%（其实说明用 GA 统计真人较多，之前 Wordpress 自带的统计大多数都是 Linux 估计都是服务器跑的爬虫 network request 直接算进来了），Chrome OS 3%。这么看来 55% 是手机访问，45% 来自桌面端，比我想象的桌面端多！

## So...
换了静态博客之后疯狂输出了半年，现在热情丝毫不减，刚过去的 11 月是我写博客最多的一个月。博客是我生活的很大一部分缩影，所以不只是博客产量多，而是我的生活体验也丰富了（比如去做 rover，写的 side project，出去游玩，看的书影游等）并且有力气记录表达分享出来了。我不怎么写情绪，博客可能看不出来，前阵子经历了一段时间的存在主义危机，最近刚爬出来。

希望新年也能保持这半年的博客和生活热情，同时能带动更多人写博客就更好啦～也欢迎大家在评论里写下你最喜欢看哪篇或者哪方面的内容。

（或许我应该开点博客辅导课什么的……暂时没这个精力开课，感兴趣当小白鼠的同学倒是可以点下面链接在 Patreon 约谈，反正 1:1 什么都能聊，手把手做博客也不是不行🤔）

{{< support >}}