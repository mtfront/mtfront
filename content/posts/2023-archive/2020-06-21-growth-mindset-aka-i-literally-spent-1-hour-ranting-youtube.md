---
title: Growth mindset (aka I literally spent 1 hour ranting youtube)
author: 椒盐豆豉
type: post
date: 2020-06-22T00:04:00+00:00
url: /growth-mindset-aka-i-literally-spent-1-hour-ranting-youtube/
categories:
  - 重启电脑
tags:
  - career
  - software engineer

---
{{< hint warning>}}
(Heavily 中夹英 please X out before we disgust each other.)(又一个本来想写短广播结果废话太多索性变日志稍微正式一点的结果）（但是全是 engineer 半瓶子醋感想非学术探讨，旨在给业外友邻拓宽思路，没读过 MBA 也没读过 marketing，请勿以我为准）
{{< / hint >}}

虽然因为 manager 糟糕也对本身职业发展毫无正面作用浪费我一年时间，对 FB 第一个组[印象极为恶劣也日常吐槽](https://www.douban.com/people/mfcndw/status/2461468157/)，也因此对做 growth 为一个职业没啥好印象，自己赶紧转方向不说还逢人就劝退。但不得不说那一年很多边角料软知识，尤其是多少培养了一点的 growth mindset，所以之后对使用、学习其他互联网产品乃至分析现实问题都感到受益。

## 小变化，大 impact

比如经常听人说“XX 这么小的因素不会有什么影响，因为买得起还是买得起买不起本来就买不起”就会多想一步，毕竟做 growth 时候一个 button 蓝色变绿色或者一行字变大俩号这么细微的变化，都可能带来百分之十几甚至几十的流量/转化率，基数一大影响相当可观。自己设计产品、做 feature 甚至从别的产品上学、评测时候也会变得非常 aware 这方面影响。

比较 subtle 的例子又比如我们之前 VR 广告想说机身图片对 VR 没啥表现力，花了半天功夫做了一套 video feed promotion 等着收 impact，结果 CTR 反而大幅下降，最后分析了半天觉得应该是视频广告本身消耗时间比图片长且 interuptive（跟 feed 里看到图片比），感兴趣又没有感兴趣到立即下单的一部分观众点进去看完之后就当 consume 了一个内容，出来就 move on 了。

## 能简勿繁

另一个很容易被没有 growth mindset 的人忽略的重要概念是 conversion funnel。其实这东西早在还没 growth 这个概念的时候就已经是营销学一个经典概念了。讲人话：

![网上随便找的图](https://media.douchi.space/douchi/media_attachments/files/110/456/431/702/495/533/original/645b615fd541b298.png)

广义上来说，达到产品提供者实际想要的目的，每多一步都流失一部分用户。没流失的用户占上一步用户总量就是 conversion rate。很多时候发现码农搞出来一大堆精密严谨功能多的系统然后洋洋自得，其实 steps 太多，每个 step 重点太不集中实际效率并不高（我写文废话太多其实也有这个毛病）。

拿到传统实物消费领域，为什么 Amazon 要弄一键下单，为什么第三方点上网站光是加了 Amazon 的 logo/商品链接就能提百分之十几的销量（Trust me this was the first task I got as a growth engineer），为什么苹果敢在 in app purchase 收 30% 的重税但服务提供商还是不情不愿的花大量人力物力财力 intergrate (Trust me this was one of my biggest projects)？就是因为多一步填信用卡数据的 friction 增加转化率就会大幅下降，更不用说大家都不愿意自己的信息被到处存在不熟悉的第三方网站上了。

在互联网领域，对广告卖家而言 funnel 可能到用户看了广告下单才结束，对平台可能是用户从看到这个东西到看了/点了广告就算成功。你在网上每多进一个网页/对话框，都是一个又可能造成流失的 step。再细看到具体组目标也不尽相同，自然有不同 funnel steps。 playback growth 可能是你点进去看了这个视频超过 30 秒就是 funnel 尽头，survey growth 可能是回答完所有问题点了提交并且提交信息“有效”是成功。

How you present it matters

然后根据每一步的呈现形式和内容不同，每一步的转化率又有很大优化空间。比如这两年网络条件允许了，只要能放视频的平台都开始在 feed 上 autoplay 了。为什么？比原来的要“点进视频”少了一个步骤啊？本来因为 thumbnail 制作不佳、标题起的不好，甚至是单纯懒得点而错过的视频，现在因为 autoplay 转化率可能都会提升了。

不同形式比如常见的 non-interruptive 广告/通知形式如 megaphone/banner （在界面顶端一小条那种，通常没有图或者有很小的图，可以点 X 去掉），乃至贴片广告，好处是不干扰用户继续使用主体功能，另外因为不干扰所以被 dismiss 的几率低一些，所以增加了实际 impression。坏处是不吸引注意力，impression 可能是无效的，转化率可能比较低。如下图（”Pinned poll“那个部分是一个 megaphone）
![](https://media.douchi.space/douchi/media_attachments/files/110/456/432/657/814/652/original/2942aebf8eeb07ac.png)

{{< columns >}}
对应的常见 interruptive 广告如 popup diaglog, interstitial 等一整页不点不让继续的（YouTube 推广自己的 premium 非常，非常爱用这一套，我从来没见过有 service 敢如此滥用 interstitial。我们之前都是非常重要的通知才敢用，一般也不会轻易批这个 budget）。好处当然是用户不点不能继续，所以转化率可能会高一些。坏处是破坏了服务本身的主体用途，非常影响用户体验。可能 premium 转化率高一点点，但牺牲的是 playback time, ads impression, etc，很多时候愤怒的用户干脆直接退出了。 如右图。
<--->
![网上随便找的图](https://media.douchi.space/douchi/media_attachments/files/110/456/432/860/679/745/original/591d49037269fd3b.png)
{{< / columns >}}

其他的 interruptive 形式还有视频里的广告。这个是平台/创作者本身赚钱的方式，只好忍了。（但是 YouTube 最近广告越来越 aggressive 了，以前一般四五秒跳过，现在多变成十几秒跳过就算了，不能跳过的还越来越多了，还甚至有几分钟乃至几十分钟的广告欺负你懒得点，甚至如果有两个广告第一个跳过你错过了点的话第二个跳过又要十几秒）（用户的主流平台不在桌面端，手机 app、电视等等多得是，so please don’t mention ad blocker like you think all people only use one device again. Also not all people like to take advantage of content creator）

就拿我刚才吐槽的这个 [YouTube survey](https://www.douban.com/people/mfcndw/status/3000361636/) 来说，真是一个教科书级的差 UX + growth 101 what you shouldn’t do 教学：
![](https://media.douchi.space/douchi/media_attachments/files/110/456/433/499/710/758/original/bb4523d2e3dce10a.png)

1. 最直观的，对用户、内容制作者甚至广告商而言，“不点 survey 不给看视频”，甚至不给看视频前面的广告，这都是直接的利益损失。周围全是能 Autopay，点一下就能去看全部的视频/广告，这个把 thumbnail 变小，挤占标题空间导致折叠更多（英文本来就非常不适合行宽过小），还要多点好多下才能看。
2. Survey 本身 UX 非常差：视频本身 indicator 都只有“like/dislike“两个纬度，加上被动 context 顶多再有“忽略”和“屏蔽“这一个 survey of recomendation 居然初始就有 6 个选项？别急还没完，选了”not sure“的话之后还有 follow up question 给 5 个选项问你为啥 not sure。行吧行吧我不看了还不行吗？讲真我还是第一次看到敢在 feed 里插 inline survey 给这么多选项的。
3. 一般这种 survey dismiss 也是衡量效果的重要数据。但是图里这个 UX 做的（整个视频套在一个 survey module 里这个形式），就怎么说呢，我确实很难想象 dismiss 的对象是 survey only（but the video itself is included inside of it!) 还是整个 module.

类比一下，你打客服、结束视频通话等偶尔会在结尾收到一个 survey。虽然转化率低了点很多人不做 survey，但好歹用户的主要目标已经达成了。How about customer service force you to do a survey on waiting time or menu experience before they help you out??? 比如 messenger 现在视频结尾给你个 dialogue survey 都嫌烦开始转通话完之后发个 message 一样的 survey 了，你管还真是反其道而行之。

我对这个 survey bad UX 甚至 bad for itself 投入产出比奇低过于愤怒，以至于我怀疑是不是 survey 组 KPI 不够快要被开了去跪着求别的组给加的。没有这个东西就不会有我今天这篇 rant。

---

当然，大多数人还是没必要通过当 growth engineer 这个大坑来 gain such mindset. 有空可以自己报个公司免费那种 growth 101 之类的培训课去上上，对改变看世界的角度还蛮有帮助的。感觉很多 backend engineer 乃至业外普通用户还是太瞧不上或者 over simplify 这些犄角旮旯的苍蝇肉了。



{{< details "Migrated Comments" open >}}

### Comment by 山月 on 2021-03-27 21:03:18 -0700
中夹英读起来太带感了XD

{{< / details >}}