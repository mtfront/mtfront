---
title: BILT 2.0 解读
author: 椒盐豆豉
type: post
date: 2026-01-16T17:10:00-08:00
url: /BTIL-2.0/
categories:
  - 重启电脑
tags:
  - money
  - 导读
bookToc: true
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/115/816/139/057/157/897/original/4c4ecf92f30bb953.png
imageDes:  "摄于 Seattle Art Museum"
related_off: false
---

2026 年 1 月 14 日，以“房租也能免手续费赚信用卡积分”著称的 BILT 信用卡在烧完钱跟 Wells Fargo 掰了之后 hype 了数个月的重新包装 2.0 版本上线了。明显是钱烧完了必须开始 down to earth 盈利之后不可能提供之前的性价比，这场重新包装刻意引入了第二个点数系统 —— BILT cash 来掩盖“无手续费交房租房贷不可能是个能赚钱的业务“之后必须找地方赚钱的新系统。也因为刻意被设计得更复杂，初期也造成了诸多困惑。

本文是我根据现有信息和个人偏好得出的结论，希望对大家有参考价值。如有谬误/官方更新造成的结论不再使用，欢迎在评论区指出。

<!--more-->

## 2.0 transition 过程
- BILT 不再跟 Wells Fargo 合作，因此之前由 WF 发行的旧 BILT 卡将在 2 月 6 日失效。
- 现有持卡人**如果什么都不做**，Wells Fargo 会自动发给现有持卡人一张 `Wells Fargo Autograph` 信用卡。这张卡将在后面详述。
  - 这张卡会继承之前 BILT 卡的账户历史和余额，可以继续还款，也不会增加一条 credit line，不产生 credit impact。
  - 但卡号会有变化，因此在各类自动付款和 wallet 中需要当作一张新卡使用。
  - 没有 welcome bonus。
- BILT 与 cardless （第三方发卡商）合作发行了三张**新的 BILT 信用卡**，年费分别是 $0, $95，$495。后面会详述这三张卡。
  - 现有持卡人需要在 bilt 重新申请这些卡。完全是新卡，所以是否通过，credit limit 等跟旧卡没有关系。
  - 信用卡号一样，所以房租和各种 online wallet 可以无缝衔接。
  - 但是！这是一条新的信用卡，对信用的影响（account age, 5/24 等）除了没有 hard pull 之外完全相当于你申了一张新卡。
  - 如果申了新卡，BILT 会与 Wells Fargo 联系关掉旧的账户。所以对信用影响的综合是新卡 + 关旧卡。

## Bilt 2.0 内容
### 付房租房贷 
房租和房贷将有两种付款方式：
- 刷 BILT 信用卡，收 **3% 手续费**，跟其它任何信用卡（如果支持的话）一样。还款日期是信用卡还款期，最多可赚 2 个月晚还款的机会成本利息。
- 直接从链接银行 **ACH transfer**，无手续费（跟你连自己 checking account 直接交是一样的），钱一两天内被扣，跟 BILT 本身没有任何关系。不同是这个房租能积攒“up to 1X rewards"，但需要花费新的点数系统 BILT cash 来解锁。

### 三张卡
新用户都送差不多 1 个月房租解锁的 bilt cash，算是给 cover 2 月房租的见面礼🥜。
- Blue：免年费，1% cash back。
- Obsidian：$95 年费，在买菜和吃饭**二选一** 3% points back（up to $25k/year）。建于市面上有无数 3% dinning 免年费卡，大多数人可能会选买菜。hotel credits（限制很多牙缝里抠钱的人肯定有更好的卡可以忽略）
- Palladium：$495 年费，2% catch all cash back。有 priority pass。hotel credits（限制很多牙缝里抠钱的人肯定有更好的卡可以忽略）


### Bilt cash
- 新的 BILT 三张卡刷信用卡消费（注意，房租房贷不是信用卡消费）都能积攒 1x reward point + 4% Bilt Cash。这个 bilt cash 目前唯一的已知用途就是“解锁”刷房租积攒的 bilt rewards point。不要看有个“cash“在里面就当成是 cash back 了。
- 每 $30 Bilt cash 可以解锁 1000 房租房贷赚的 Bilt points。

用基础 points cashback 1x 的免年费蓝卡示例：

| 房租 / 房贷 | Bilt 信用卡消费 | 需要解锁的 Point | Bilt Cash | 可用 Point | 等效积分 |
|--------------|----------------|---------------|------------|-------------|-----------|
| $1000        | 0              | 1000          | 0          | 0           | 0%        |
| 0 (不走 BILT) | $750           | 0             |30           | 750        | 1%     |
| $1000        | $750           | 1000          |30         | 1750        | 2.33%     |

换句话说，房租的金额是你能赚取 2.33% cashback 的上限。其它信用卡消费 < 75% 房租的话，等效刷卡 cashback 介于 1%～2.33% 之间。如果是 2% 基础 cash back 的 $495 年费 Palladium 卡，则可再加 1% 来到 3.33%。

也就是说要理解 BILT 2.0 的关键是**不再把它当成一张能无手续费刷房贷房租的信用卡**。复杂 BILT cash 机制的完整目的就是要掩盖这个事实。either way，房租都是从你银行账户上直接扣的，只是影响你能拿 cash back 的上限。

真要 maximize 的话，假设房租 $3000，每个月要花 $2250 在 catch all （常见的吃饭、旅行、Amazon 和各种 5% cashback 都不算）上才能解锁这些点，想象不出到底是什么样的用户画像可以赚到这个钱…… 常年在 ebay 上倒卖二手的吗？绝大多数情况应该都是搞一张 2% 无限制的 catch all (比如 fidelity 或者 [Capital One Venture X](https://i.capitalone.com/G1o3wmYUk)) 更划算。更何况 bilt points 1:1 还是面向 travel，也就是说又要倒卖二手又喜欢 luxury travel 转点年均花掉等价 60K 以上的点数但又没有别家更划算的 travel 卡才能赚到，hmmm……

再次重申，现在这卡跟免手续费刷房租房贷已经没有任何关系了，房租是从银行账户直接扣的，**房租房贷只限制等效积分上限**，高 catch all 积分需要额外操作，且兑换积分规则由 Bilt 掌控（Bilt Cash 细节至今没有放出）。

### Another option
写完这篇博客发现 Bilt 的 founder Ankur Jain 今天在 [reddit 上发了一篇更新](https://www.reddit.com/r/biltrewards/comments/1qerq2n/a_note_from_me_ankur_jain_bilt_card_20_simple/)，基本上就是这两天被骂成狗了临时凑出来的 damage control，作为 bilt cash alternative（二选一）:


|Points on Housing|	Minimum everyday spend as a % of monthly rent / mortgage (Example of $2,000 rent)|
|-|-|
|0.5x points|	Spend at least 25% of monthly rent ($500)|
|0.75x points|	Spend at least 50% of monthly rent ($1,000)|
|1x points|	Spend at least 75% of monthly rent ($1,500)|
|1.25x points|	Spend the same or more as your monthly rent ($2,000)|

不花其它消费的话每个月房租赚 250 point（约等于没有，应该不会有人为了两块五开卡吧……）。也就是说基本上是一个 1.5% - 2.25% 的 catch all 卡。结论不变。

## 个人选择
本来如果像 1.0 一样没有额外的 benefits 但是房租房贷是刷在信用卡上的而不是银行转账，其实我有考虑留着这卡。把 due date 挪到月底的话可以钱在 HYSA 多赚两个月利息，按照 [Marcus + referal bonus](https://www.marcus.com/share/FAN-NS4-YMS9) 的 4.65% APY 的话每个月都能赚出一顿饭钱，无年费也不亏。只可惜 fine print 里发现现在变成了 ACH，那这卡对我没有任何意义。

进行上面一系列分析后我发现我个人而言竟然是直接转 Wells Fargo Autograph 更合适（懒得薅开户 bonus 就直接让它转了。搞笑的是刚收到它的信的时候还在想肯定不会留 Wells Fargo 的卡就随手把信息扔了，结果后来发现竟是不错的选择……）。前 [CSR 关掉之后本来就想要张吃饭卡]({{< relref "/posts/2025-07/4-csr-replacement" >}})来着，后来不想多申一张就没再开，现在勉强用着之前 chase 全家桶遗留的 freedom unlimited。这张返的范围比 CFU 多（streaming, 加油充电，travel 还能补 CSR 空位），还没 foreign transaction fee，BILT 直接转也不多一条 credit line/inquiry，points 能直接换现金适合我这种不玩点的，感觉挺合适的？换成这张之后 CFU 可以彻底弃掉了，chase 系里只用 freedom 的 5% 和 [prime](https://www.amazon.com/dp/BT00LN946S?externalReferenceId=34e34265-d58d-4b4a-9e5f-606dbea19d50) 那张就够了。

It was a good run though，烧钱阶段给大家送的点数支撑着我大半年上 Barry's 都没花钱还送 smoothie lol 新卡也不能说是特别垃圾吧，但为了用“交房租卡”骗更多人入坑而发明出来这个复杂的 bilt cash 系统再加上并不是很优秀的 benefits 既没有给 maxmizer 们提供发挥空间，又不适合消费结构简单的小白。如果只想一卡流或许可以考虑，但这个复杂的系统可能一卡流没看完就已经劝退了。我先退坑了，看看这公司还能蹦跶多久。另外这次的 marketing push 真是 financial influencer 的照妖镜，无脑吹这个卡的基本可以全拉黑了。

---
## 2026/2/7 更新
BILT 这个公司真的 scammy 体现之，我们楼不幸也用它的系统付房租，所以即便不用它的卡了也得去它系统里连银行账户。今天我去连银行账户，本来直接用 plaid 登录 verify，结果登完跟我说 error occurred，BILT 那边要重新登录。作为码农非常能理解这种问题咋写出来的，也就内心吐槽了一下草台就继续登录了。结果登录进去直接把我放到了申请它们那个新卡的页面？？？？？？不是介绍打广告的页面哦就是直接在申请过程中页面，要是不仔细看一路点 continue 的人不得莫名其妙直接办了张新卡？真的无语。更不用提前几天申卡 deadline 前每天发消息跟用户说“action required”让用户去申卡否则账户会被关，要不仔细看可能就稀里糊涂申了。不知道 3/1 下一波交房租的时候有多少人会稀里糊涂被 charge 3% 手续费或者干脆银行账户里没准备房租导致付款失败的……

rage quit 页面之后回到付房租的页面怒用传统的 routing/account number 方法加银行账户，现在还得等两天那小额 deposit 来 verify 账户。大众现在滥用 enshitification 这个词真的是有一定道理，互联网上包装精美的屎真的太多了…… 