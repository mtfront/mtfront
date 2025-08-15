---
title: 给站点设置维护状态页和对长毛象的一些吐槽
author: 椒盐豆豉
type: post
date: 2025-08-14T23:59:00-07:00
url: /status-redirect-page/
categories:
  - 重启电脑
tags:
  - tutorial
  - mastodon
  - rant
  - Debug
  - blaugust
booktoc: true
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/115/031/635/557/720/011/original/95ffe814276ac819.png
imageDes: "image from https://joinmastodon.org/"
---

自从[参加了 Blaugust]({{< relref "/posts/2025-08/3-blaugust" >}}) 想说能多写点博客之后，反倒是忙得完全没空写博客，成年人的世界真的是很难都要。忙生活享受夏天的西雅图和忙工作赶 release deadline 之余，这两天还在忙自己的长毛象实例升级。既然参加了 Blaugust 多唠两句那就写一篇吧。与其说是教程，可能唠嗑和吐槽长毛象的成分更多一些。

<!--more-->

因为都是个体户单服务器运行没啥分布式，每次长毛象迁移和升级都会有一段时间的 downtime。尤其是迁移时，需要导出数据库、重新编译等，可能几个小时都不能访问。当然还有一些时候实例跑着跑着自己就挂了。

我长毛象上比较熟的网友遍布各平台，每次挂了时候都 [telegram](https://t.me/mtfront)、[Discord](https://discord.gg/cESS4JpsdG) 乃至微信全平台被找，毕竟站点无法访问就是突兀的 `502`，大家也不知道是维护还是意外挂了，需不需要人工干预。即便是预先安排好的维护，也总有换算时区、长时间未登录用户没看到通知、意外维护超时等情况。


长毛象虽然自带一个 `500` error page 可以自定状态页，但是建立在长毛象服务运行的前提下才能显示，迁移或者 VPS 本身挂掉时自然也没办法。之前维护时我才用过 discord 和 bluesky 等通知方法， 但要单用一个 app 总也有使用门槛不方便所有人查看。

于是这次趁着升级便顺手让 chatGPT 写了个静态页面，再在 cloudflare 上设置了 redirect rules，在维护时候把站点自动跳转到静态状态页。

{{< wrap "https://media.douchi.space/douchi/media_attachments/files/115/031/186/829/672/029/original/3c0f9dd7aea94ca2.png" >}}
## 1. 写静态页
当然也可以调教 chatGPT 直接写，不过我要写的内容非常简单，就“正在升级中”和一个 discord 社区的链接，直接先手写一个 html 扔给 chatGPT 调样式。调完再网上随便搜个 html playground 预览一下效果，微调一下 css 即可。

想要直接把实时更新嵌入到页面的话，也可以考虑 embed 一个可以随时更新的社媒在这个页面。

## 2. 部署到 Github Pages
网上能部署静态页面的服务非常多，我博客什么的都在 github pages 上流程很熟了就顺手继续用了。

因为只有一个静态页，不需要任何框架，步骤非常简单：
1. 新建 repo。比如我已经有了 `douchi.space` 这个域名，想要状态页叫 `status.douchi.space` 的话，就把 repo 取名为 `status`。
2. 给里面扔个 index.html
3. 在 Settings -> Pages 中设置 Deploy from a branch 即可。
4. [optional] 设置 custom domain 隐藏 github repo 地址。跟设置博客一样，在 DNS 提供商里想要的域名添加一条指向 `repo 名` 地址为 `用户名.github.io` 的 `CNAME`，再把这个贴回 github pages 的 setting 然后保存。
5. 检查新域名确认 DNS 生效。

## 3. 设置 redirect rules
这里以我用的 cloudflare 为例：
1. 进入你的 DNS 管理页面 -> Rules
2. Create Rule -> Redirect Rule
3. 忽略模版，直接在 `If incoming requests match...` 选择 `All incoming requests`， Type 选 `Static` URL 选你新设置的状态页地址，比如 `status.XXX`。
4. 我一开始犯了 status code 选了 `301` 的错误，后来才发现浏览器是会 cache 301 redirect 的，因此用户会被爱本地”永久“ redirect 到状态页而不是本来的页面，需要用户手动清 cache。这里选 temporary redirect 的 `307`。

这个 rule 保存之后可以随时 enable/disable，生效速度非常快，很适合维护时候随时调配。

## 以下是对长毛象吐槽的部分
这次升级的原因是，昨天发现跟 cmx 和 mastodon.social 失联了。考虑到这俩站点都在 `v4.4.3`，以为使又搞出了什么 breaking change 的缘故，外加我站也确实好久没更新了好多 dependency 都 deprecate 了，就想说要么更新了算了。

之前好久没更新的原因：
-  4.X 版本以来无比脑残的 mobile 版竖边栏的设计（当年刚出的时候被骂成狗 Eugene 还嘴硬说是我们重金请了 designer 做的你们都不懂 excuse me 这么没有 UX 常识的 design 真的好意思收钱？）。我站升了 4.2 之后就一直用 custom CSS 翻转成顶栏凑和用。看其它站点的经验更新了 4.3 之后这个 CSS 应该会失效，所以没更新。
- 我站的操作系统和诸多 dependency 都 outdated 了，要跟新起来不但要升级系统还要重装一堆 dependency。
- 最重要的原因是之前诸多 customization 在从 4.2 -> 4.4 之后出现了巨多 merge conflict，我上次 merge 到一半实在是烦了就拖了。

其它的 customization 用处没有那么大，最主要的是：
- 嘟文编辑（官方最新版应该也有了这个问题不大）
- 一万字的字数限制（原版 500 字）
- 投票可以设 30 个选项（默认的 4 个也太少了）
- 图片和视频大小上限
- 未登录用户仅可查看 5 条最近嘟文
- 快捷按钮（至少官方上一个版本的挺难用的）
- 关闭 Email notification（不然有用户不慎打开了之后迁移经常把全站免费额度用完导致注册和找回密码的邮件也发不了，但现在关闭注册了这个问题应该不大）

这回想说互联性事大，还是升级了吧。为了避免每次都一堆 merge conflict 和 dependency issue，决定从非 docker 换到直接用官方的 docker image，放弃 customization 图个方便。（果然上次刚写了拖了几次都没写的[非 docker 迁移笔记]({{< relref "/posts/2023-12/9-mastodon-migration" >}})想说下次给自己迁移看方便果然就用不上了。

想到这儿，不禁又悲观了起来所谓去中心最后不也是靠主流服务提供商的 breaking change 软逼迫人更新……你敢想象如果 SMTP/POP3/IMAP 一天到晚发布 breaking change 或者比如 gmail 开始用一些新的标准导致你不升级 email 客户端/用指定服务提供商就收不了邮件吗？

升级本身过程倒还行了。碰到了如下问题：
- 系统 outdated：升级系统。ubuntu 的升级真是比 mastodon 顺利多了……（废话不然这系统还发得下去吗）
- 新版长毛象 require 三个新的 secrets，官方给的生成 script 不 work：reddit 上找到 work 的。大家纷纷吐槽 this shouldn't be this hard...
- 数据库备份 `pg_dump` 版本过旧不兼容新版的导入：最后 dump 成 plain SQL 解决的
- 官方 image 跟之前的 `.env.production` 的一些环境变量名字变了：逐个 debug 改名字。
- Docker 的各种操作问题：chatGPT
- Elastisearch 太吃内存：加 heap size

但现在有了 AI vibe upgrading 都问题不大。就是数据库导入真的花了好久时间……

重新跑起来之后发现还是看不到 mastodon.social 和 cmx 的嘟，我又拿出了四个账号测试了一下。

![](https://media.douchi.space/douchi/media_attachments/files/115/025/855/028/783/759/original/a4fe2a7988ff2882.png)

然后确定了是 cmx 和 mastodon.social 自己的问题。前阵子 cmx 也出过变成只进不出能看到外站的嘟但所有信息都出不了站的情况，估计这次也是一样。这级白升了…… 

但这事没完。今天 cmx 估计是终于察觉到了异样重启了自己的服务，一下 notif 都涌出来了。不愧大站，直接把本站给 DDOS 了，图都发不出去一直 `503`（因为积压了一天的嘟的图过来都会在本站被 cache 所以请求过多）。下午又有人反映上图中本能看到本站的 o3o 和 alive.bar 等也看不到本站了，想必是也给 somehow DDOS 挂了，于是顺手重启。以往重启能解决大多数问题，也只需要几十秒时间，谁知这次 `mastodon_web` 和 `mastodon_streaming` 就直接卡在了 restarting loop。Debug 了半天是 elasticsearch 的问题，又试图 disable 无果，vibe debugging 了半天修好。cmx 和 mastodon.social 也都是 4.4.3+ 的不知道是不是因为新版才这么不稳定。破毛病一堆重个启都能给我整塌了，前前后后浪费我两晚上时间了火气蹭蹭往上冒。

服务是能跑了，但跑着官方版，字数上限和投票选项上限都是小事也好改，今天站友给我说又有关注请求邮件了我才想起来这档子事四年前提了 [issue](https://github.com/mastodon/mastodon/issues/15495) 也还没修，大站能买付费邮件 plan，小站用的免费版来个锁嘟 + 关注人数多点的人迁移一下就能把全天的邮件配额用完，导致全站新注册和找回密码的邮件都发不出去。先前本站老遇到这个问题我在后台把发邮件的代码 comment 掉了，现在用起官方 image 这个问题又回来了。本来就是鼓励大家建站小站越多越好的所谓 decentralized social network，默认通知竟然是邮件这种需要商业服务配额的东西且不给选项关闭就还是太不成熟了。商业平台用惯了 take for granted 的东西真是失去了才知道珍惜。

{{< wrap "https://media.douchi.space/douchi/media_attachments/files/115/030/806/680/351/168/original/d28992c330a2e7c0.png" >}}
更新频繁的开源软件不稳定定理再次应验，自己单机用的东西还好说不升级就完了，fediverse 这种看似去中心化，实则 80:20 rule 大多数人集中在个别实例上的互联网形态就注定了小站迟早被官方用兼容性倒逼升级，然后升出点不稳定，早知道昨天断联是 cmx 自己的问题我就不升了，这个故事告诉我们真的是要坚信定理：

当然也知道开源软件为爱发电逐渐 mainstream 问题多顾不上也是正常的。还能咋办呢乁། ˵ ◕ – ◕ ˵ །ㄏ如果有一天不再自建站或者彻底离开了 fediverse，一定是被麻烦死的。