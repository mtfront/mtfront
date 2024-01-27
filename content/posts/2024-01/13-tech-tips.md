---
title: 一些低门槛的实用上网小技巧
author: 椒盐豆豉
type: post
date: 2024-01-27T00:04:00-08:00
url: /tech-tips/
categories:
  - 重启电脑
tags:
  - tech
  - tutorial
  - productivity
booktoc: true
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/111/826/639/640/007/687/original/d2cd82313a084ec4.png
imageDes: "MidJourney prompt: a laptop and bunch of tools, game isometric 2D style --v 5.2 --ar 16:9"
---

该说互联网消除了信息壁垒呢还是用信息过载来实质意义上造成了更多信息壁垒呢？在互联网时代什么知识都在大多数普通人触手可及的范围内，这在几十年前还是难以想象的事。同时，互联网乃至社会的技术演变和细分的越来越复杂，也注定导致人不可能有时间精力和能力全知全能地知道所有最高效、省钱、优质的工具和方法。

想写这篇博客很久了，因为总会在日常生活中发现一些我已经习以为常所以以为大家都知道的 random 技巧其实别人不一定知道（当然也有很多我忘了写或者别人知道我不知道的欢迎在评论分享），想不出什么概括性的主题，索性一箩筐随机都写出来吧。

<!--more-->

## 浏览器定制多个搜索引擎
绝大多数浏览器在地址框直接输入文字都会用默认的搜索引擎搜索，但如果想要在特定站内搜索内容，需要从默认搜索引擎的搜索结果页面里点击，还要忍受可能误点广告、内容过信搜索引擎没有 index 的可能。去对应的网站在站内搜索又多了一个步骤。其实很多浏览器都提供了定制搜索引擎的功能，可以在地址框快速切换搜索引擎。以 chrome 为例，在 `settings -> search engine -> Manage search engines and site search` 里可以添加自定义的搜索引擎，在地址栏打对应 shortcake + 空格 + 关键字就能直接站内搜索。我比较常用的有：
- `maps`: `https://www.google.com/maps/search/%s?hl=en&source=opensearch` 
- `amzn`: `http://www.amazon.com/exec/obidos/external-search/?field-keywords=%s&mode=blended&tag=mtfront0f-20` 这里加入了我的 affiliate link，当然你可以自己定制
- `ytb`: `https://www.youtube.com/results?search_query=%s`

你也可以在自己常用的网站用它们的站内搜索，然后把跳转到的链接里你搜的关键词替换成`%s`就可以自己定制搜索引擎。

## 免费的 photoshop 网页版平替
Adobe 换成现在这个收费模式前大家还能用用盗版 photoshop，换了 subscription base 之后干脆就彻底抛弃 photoshop 了。非专业图像处理人员用网页版平替完全能应付日常偶尔改个图的小需求，不允许还有人不知道 https://www.photopea.com/ 这个网站。此外 photoshop 水很深不假，但熟练掌握曲线、魔棒、液化、印章等常用工具对普通人日常生活应个急还是很有用的。虽然现在各家都开始流行手机 AI 修图，但总有一些小细节还是得手动修的。

## 使用 RSS 订阅博客和新闻网站
作为一个从第一波博客兴起把 RSS 当作默认订阅方式的人看到博客没落后 RSS 逐渐成为一个 niche，最差情况网站干脆不提供 RSS 只允许用邮件这种低效方式订阅，最好也得新读者去“学习“痛心疾首。而最遗憾的是，其实 RSS 根本不是 geek 才能玩的什么高端技能，是个人随便进个 app store 搜个 RSS 阅读器出来甭管好坏都能用，根本没有使用门槛。但因为它变成了 niche，网上充斥着自建 RSS 服务等“高端玩法”，甚至很多 app 测评都抛出一大堆对新人无用的名词让人望而却步，也劝退了一大波稍感兴趣的人。

其实哪有那么复杂？简单暴力点来说，RSS 是独立博客的唯一正确订阅方式就对了，不接受反驳。如果你有看博客的习惯，随便搜个 RSS 阅读器开始用就行了（我现在用的是 Inoreader），用熟了之后自然会知道什么功能对自己重要。先前写过一篇 [RSS 的介绍文和一些我当时订阅的源]({{< relref "/posts/2023-archive/2022-08-28-my-rss-setup" >}})，希望能对起步有帮助。

## 使用 discord 替代 slack
之前 Slack 没改成免费版只有 90 天消息记录的时候或许还有非企业用户使用的动力（各类 productivity 向应用 integration 比较成熟），改了收费模式之后完全无法理解为什么还要有很多非企业社群容忍 slack。相比之下，Discord 没有被更多的社群作为沟通工具纯粹就是 toxic gamer 的品牌形象和管理层一直找不对着力方向的问题了。但产品本身无论是个人生产力、小群体交流还是大社群构建，真的都秒杀 slack。

先前写过一篇[个人生产力向的 Discord 介绍]({{< relref "/posts/2023-archive/2023-06-01-discord-social-productivity" >}})，有机会或许可以写一篇和 slack 的对比（我总计只呆过个位数使用 slack 的公司和社群所以 blocker 是不够全面了解怕写得不全面误导人，如果大家想看的话我也可以去努力 research 一下）。

## Object storage
经常看到有人询问稳定、有外链的图床，或者传大文件寻找平台苦手。各种网络服务自然也不少，但质量参差不齐，隐私也不一定能保证，有时候还会遇到内容审核的情况。专门的云盘服务如 iCloud、Dropbox、Google Drive 等的文件类型和分享、外链也有不同的限制。其实这种云存储文件的使用场景在各种网络服务中有非常廉价和标准的解决方案就是 object storage，可以看作是一个不套云存储服务壳的网盘服务。因为多为面向企业用户，因此私用基本不存在审核（除非高流量公用违法内容内容被投诉到供应商）。比较适合个人的使用场景：当图床、共享文件、给个人博客和长毛象等网络应用站点作为媒体存储等。

Object storage 有很多服务商，价钱也不一定恒定，这里随便贴一篇搜到的[横评](https://www.cloudzero.com/blog/cloud-storage-pricing/?utm_source=blog.douchi.space)作为参考。建议选用 S3 compatible 的，以防将来需要迁移保证兼容性。我个人用过的 Scaleway 有免费的 75G 额度，超出的计价也很便宜一个月几毛美金，不确定的话可以先开一个试试，个人博客用没什么问题，之前[长毛象用不大稳定]({{< relref "/posts/2023-archive/2021-02-25-scaleway-object-storage-unstable-mastodon-migrate" >}})，后来[迁移]({{< relref "/posts/2023-archive/2022-01-23-migrate-object-storage" >}})到了 [DigitalOcean](https://m.do.co/c/708fdc9af879) 固定月费 $5 每月 250G，应该不是最便宜的，但无论是长毛象还是博客用都很稳定，UI 也比较 intuitive，感兴趣的可以使用我的 referral link：

[![注册会得到 $200 分两个月分发的免费额度](https://web-platforms.sfo2.cdn.digitaloceanspaces.com/WWW/Badge%203.svg)](https://www.digitalocean.com/?refcode=708fdc9af879&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge)

## 开启浏览器上帝模式（dev tools）
程序员熟知且常用，但非程序员知道也很有帮助且其实门槛没那么高的工具，因为可能看起来更“吓人”一些所以放在最后。现代浏览器一般都有对应的 dev console，里面可以直接修改和运行前端代码来达到修改网站的目的。各个平台和浏览器有不同的打开方式，搜浏览器名 + shortcut/快捷键很快就能找到。如 chrome 我一般用快捷键 cmd + option + i，或者鼠标右键 inspect 打开。这里这说几个我比较常用的（以 chrome 为例）：

### Elements
这个分栏就是你当前所在网页的所有前端代码。直接在其中修改就能改变网页的前端代码来实现一些目的。比如前两天我在豆瓣写短评的时候被那个很窄的输入框给烦到了，前后编辑看不全很麻烦，于是就右击编辑框 -> inspect 打开了 elements 栏，找到这个文字输入框的 `style` 然后直接把 `height` 变大。不想每次要用到的时候修改，于是顺手写了个 [chrome 插件大瓣]({{< relref "/posts/2023-12/11-daban" >}})一键完成这个操作。

![](https://media.douchi.space/douchi/media_attachments/files/111/659/317/497/235/308/original/cbce4a3b9d2677ae.jpg)

再比如你看到一个网站字体或者颜色很好看，也可以在 elements 中搜索 font 或 color 来找到该网站所使用的字体和颜色。

还有一些写的比较烂的网站比如到点抢购的 button 是前端 disable 的可以手动去掉直接提前买，不过这两年应该比较少见了。

### Network
你的浏览器跟所开网页的服务器之间进行的通信。这里最有用的是拦截前端不让下载但你想下载的文件，比如图片、某些聊天软件的表情包等。因为它再怎么防下载，总得把文件从服务器传到浏览器上才能正常显示，那必定会出现在 network request 里。开着 network tab 然后刷新当前页面再按文件类型和名字搜索一下一般很容易找到你想要的文件。

此外，也可以从 request 里获得一些你想要的参数，如 user id 之类的。比如前两天我找餐厅预订签票 script 搜到了这个 the French Laundry（湾区附近一家很有名很难订的米其林三星餐厅）[tock script](https://github.com/chinhtle/reserve-tfl)，作者应该主要是自用所以没有设定用变量控制的改成其它餐厅的功能。但是读代码很容易能发现把打开的 URL 换成 tock 搜索对应餐厅的 URL 即可。而我想订的餐厅用的是 tock 的 widget，没有直接暴露其在 tock 的 URL。此时就可以打开 network tab，点预订，在 request 里搜索 tock，就能找到该餐厅在 tock 上的 identifier，从而修改 script 来订我想要的餐厅。

### Application
这里可以看作是一个网站存在你本地的小型“数据库”，`local storage` 和 `session storage` 里经常会有一些有用的数据，修改和删除它们可以在本地实现一些网页应用的修改，如移除、重设本地冷却期等。也是平时写码时候的常用功能。

### Console
这里是浏览器的输出平台，可以直接运行 js 代码。如果想写点前端小代码快速测试一下的话很方便。因为跟代码比较相关这里就不展开了。

## 一些 Mac 必备
我不大喜欢安装过多第三方应用（比如 launcher），以下是一些非常基础简单的 quality of life improvement，每换一台新 Mac 我都会设置。应用安装之后可以在 `Settings -> Login Items` 里加入登录自动开启项目。

### M1\2\3 magsafe 的 Macbook 也可以用 USB-C 充电
本来以为是常识结果发现好多人不知道（甚至是我 tech savy 的码农同事们），升级了 M 系的 mackbook 之后就被迫多带一根线了……之前在[清理桌面的时候吐槽过 magsafe]({{< relref "/posts/2023-08/4-tech-has-evolved" >}})，希望这篇文章能减少一些苹果声称自己环保但是反复造轮子浪费的受害者。此外，虽然标配充电头是 100W 的，但其实出游用[ 65W 旅行头](https://amzn.to/3Z6LwkB)手机电脑一起充绰绰有余，省很多空间。苹果标配的大充电头基本只放在家用了。

### 轻触点击
完全不能理解为啥不是默认开启。要按下去的触控板还能叫触控板吗，is this 2010？在设置 `Trackpad` 里打开 `Tap to click`。

### 三指拖拽
在某个版本之前一直是默认开启的，离了它都不会用触摸板了，不知道为啥后来的版本关闭了，而且设置藏得超级深，非常令人费解。在 `Accessibility -> Pointer Control -> Trackpad options` 里将 `Dragging style` 改成 `Three Finger Drag`。

### Spotlight 可做简易计算和单位换算
试用过一些第三方 launcher，最后发现我的需求也不过是打开应用、计算器和单位换算而已，杀鸡用牛刀，系统原生 spotlight 即可。

### 窗口管理
Mac 系统默认一直没有管理窗口的快捷键（可能被 windows 专利了），要进行分屏操作（如一边文档一边代码/博客）得用鼠标，很降低效率。网上有很多分屏管理的软件可以实现类似 windows 的快捷键分屏操作。比如我用的是 `Spectacle`，虽然已经停止维护但是功能简单易用没有花里胡哨的东西。

### 剪贴板管理
系统默认剪贴板像 iOS 一样只能复制一个东西，非常烦人。要实现安卓键盘一样的剪贴板功能也可以下载第三方应用实现。我用的是 `Flycut`，从控制栏就可以找到和搜索剪切板历史。