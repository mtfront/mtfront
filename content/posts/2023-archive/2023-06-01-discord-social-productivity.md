---
title: 从社交到生产力，一篇文上手 Discord
author: 椒盐豆豉
type: post
date: 2023-06-01T05:15:40+00:00
url: /discord-social-productivity/
image: https://media.douchi.space/douchi/media_attachments/files/110/470/438/068/647/694/original/b97367e8a2b96a19.png
categories:
  - 重启电脑
tags:
  - tutorial
  - discord
  - tech
  - productivity
---

Discord，一个虽然疫情期间扩展了很多新用户，但似乎仍然在青少年及 PC 游戏玩家之外的主流群体中是个神秘的”小众平台“。很多不关注互联网动态也不打 PC 游戏的我的同龄人甚至没听过这个名字。

这点上我有点想吐槽 Discord 的宣发和新手引导。因为虽然是游戏语言起家，但其实通过这 8 年的发展，Discord 的文字聊天也已具有强大的丰富强大的功能（自定义 reaction、markdown 富文本、回复和 thread，forum channel、AI 助手等），外加比 slack 更强大的 server 管理工具（自由度很高的 permission 和 role 管理、AutoMod、Onboarding 模版、可定制邀请链接、server subscription 喝 boosting 等众筹手段等），以及强大的开放 API 所带来的众多插件和无限可能，其实从社群运营还是个人生产力管理角度，都是一个很强大的工具。但市场拓展宣发和上手难度造成了在很多人心目中它还只是一个 PC 游戏玩家的小众平台，实在很可惜。

前阵子刚好听了一个 discord for productivity session 教大家如何把 discord 当个人生产力工具用，外加刚好看到 wirecutter 一篇很有趣的 [Discord Improved My Marriage](https://www.nytimes.com/wirecutter/blog/discord-improved-my-marriage/) 的文章，索性也写一篇上手指南给大家按头安利一下。

本文是我 [2023 年 4 月博客投票的选题结果](https://www.patreon.com/posts/2023-nian-4-yue-81345509)，被我拖延到现在 [6 月投票都已经放出了，欢迎点进链接进行投票](https://www.patreon.com/posts/83914635)：

- 2023 年入坑游戏选什么平台
- 个人博客如何选择工具和平台
- 十年没去过理发店自己理发经验总结

<!--more-->
![](https://media.douchi.space/douchi/media_attachments/files/110/470/430/064/348/841/original/995e2db7fd005cf9.png)

## 基本概念

### Server

Discord 与传统以聊天为主的软件最大的不同是主要组织形式不是私信或群聊，而是“server“。如果说一对一的私信是一维的文字交流，多人群聊是二维的话，那 server 就是一个三维的交流空间了。一个 server 里能有多个 channel，同一个 channel 中又可以有无数个 thread。channel 又分为文字 channel 和语音 channel 两大类。

与 slack 的 workspace 对标不同的是，slack 主要面向职业用户，绝大多数人可能只有一个 workspace，你虽然可以添加和 sign in 不同的 workspace，但切换起来较为麻烦。而 discord 的 server 则更像是现实生活中不同的社交圈，可以同时存在无缝切换（上图中左边那一列就是我加入的不同 server）。你甚至还可以为每个 server 定制不同的昵称和头像来完成 identity 的区分。

### Voice Call

Discord 有两种 voice call - channel VC 和私信/群聊（DM/GDM）VC。私信里的 VC 比较好理解，就像你用微信、WhatsApp、Telegram、FaceTime 等软件拨打语音电话类似。这个 call 一旦发起会一直占据这个私信的主要空间，一直提醒对方选择接或忽略。与其它软件不同的是它没有“挂断”，只有忽略，是对方发起的一个状态，不会因为接收方的行为而中断。

channel VC 则是一个更“固定”的空间，可以想象成现实生活中的会议室——不管有没有人在里面开会，会议室都在原地。人们可以随时进入和离开会议室。当然，可以通过定义不同的 role 和 permission 控制哪些 server 成员能进入特定的 VC 和发言。

此外，近年 discord 还给 channel VC 添加了 text in voice，即附属文字频道。你可以把它想象成 Zoom 的 chat。

无论是哪种 VC，参与者都能打开视频和分享桌面开始直播。

### App
![](https://media.douchi.space/douchi/media_attachments/files/110/470/430/738/432/851/original/fb322b9060eb7094.png)

Discord 给开发者提供了[较为完备的 API](https://discord.com/developers/docs/intro)，与 telegram 类似，开发者可以利用这些 API 制作各种各样的 bot 来实现各种功能。server admin 可以从网上搜索或者在 Discord 官方提供的 app directory （上图） 里寻找适合自己的 app 添加到 server。因为有完善的开发者平台，这大大拓展了用户可以不离开 discord 平台用简单的 command 就能做到的事：生成 AI art、听歌、翻译、玩文字游戏、接收其他平台的 notification 等等。

### Nitro

使用 Discord 是免费的，Discord 也不像其它很多 web 2.0 时期流行的社交平台一样靠广告赚钱。它的收入来源之一是会员 Nitro，是一种程度上的 freemium 模型。Nitro 的模式是，基础功能所有人都能免费使用，Nitro 面向 power user 有一些功能升级。列举一些常用的如：

| 功能 | 免费用户 | Nitro 用户 |
| --- | --- | --- |
| 上传文件大小（图片，视频等） | < 25Mb | < 500Mb |
| 直播 stream 画质 | 720p 30fps | 4k 60fps |
| Emoji | 可使用 unicode emoji 和本 server 静态 emoji | 可使用动态 emoji 和跨 server emoji（因此衍生了作为“表情包”被使用的 emoji server） |
| Soundboard（直播中的“声音”形式的 reaction） | 可使用 discord default 和本 server 上传的 custom sound | 可使用跨 server sound |
| 各种装饰性 perks | 深/浅色主题 | 各种彩色皮肤、profile 和头像装饰等 |

最近还新增了 Nitro basic tier，针对 casual 聊天用户，便宜很多但只有 emoji perk。

总之免费用户完全能正常使用 discord，但付费用户会得到一些 quality of life improvements。采取类似盈利模式的大家熟知的产品还有 Notion 和 Telegram（但 telegram 才刚开始做付费用户，目前功能非常鸡肋）。

## 社交

Discord 的 slogan 是“imagine a place“，想象一个地方。因为其“三维”的社交功能，我觉得在某种意义上它比现在还不成熟的 VR 更接近所谓的“metaverse“——它就是一个跟朋友进行各种互动的虚拟空间。下面提供一些我创建或者参加过的 use case 作为参考。

### 本地活动 server

传统群聊的单线程话题平时朋友闲聊还好说，在组织活动、约行程时会非常混乱。大家应该都经历过微信群里约个旅游甚至只是一顿人稍微多点意见不一的饭的时候的惨状——这个人哪个时间不行，这个人机票哪天，大家提议了什么餐厅，后来的人找不到之前商量好的消息要反复问等等。要是中间再插点与行程无关的话题就更混乱了。经历了几次 trip plan 和本地外地各种不同朋友排列组合生成的群聊混乱后我把经常一起活动的朋友拉了个 discord server：

- 分了几个不同 channel - 吃饭，电影，活动，访客，交易等等，要约人直接在 channel 里喊话，有人应就当场开 thread，单个活动以 thread 为单位，如某月某日周几越饭。这样参与这个饭局的人在里面讨论 logistics，主线不参与的人在 channel 里也不会被 spam
- 只想熟人参加的活动可以直接开 private thread，除管理员外其它没有被 @ 进 thread 的成员看不到，可以随时添加人，避免了产生 N 个排列组合聊天群为了协调一个活动的情况
- 讨论到重要信息就把 message pin 起来，后来的人不用重复问
- 欢迎公开加入的活动直接创建 server event，没有加入 thread 的人也能 sign up event
- 按照兴趣和状态给大家分发了不同角色，如电影、爬墙，本地常住和外地访客等。召集人的时候可以 @ role 一键通知相关 role 的人。
- 交易频道是个 forum channel，以接近论坛帖子的形式方便浏览搜索以免被消息冲掉

### 论坛衍生群

她乡论坛的非官方衍生 discord 群是当年让我开始重度使用 discord 的源头，虽然时隔两年多已经不复当年全盛时期大家全球面姬的盛况，但依然是我现有的最紧密联结的活越大群体。

因为超过 300 人的社群大小，所以跟几人到十几人的熟人小群的互动模式也略有不同，社群里有更多的权限管理和 bot automation：

- Roles & permission
    - 管理员，有 admin 权限的一个管理小队，有相关的管理员 channel 商量群务，比如群规修改、冲突干预等等。
    - 身份验证，因为是女性社群，为了提升某些不自觉的男的混进来的门槛，入群需要语音验证之后才会发村民身份可见大多数频道，顺便欢迎新群友，介绍社群功能等等。早先只有管理员有权限，后来为了减小管理员验证压力，也征召了一些群友作为验证员。
    - 活跃的群成员会给一个有创建 event 权限的 role，这样自己组织和编辑活动无需管理员操作。
- Bot automation
    - 自助通过 reaction 分发各种 role 的 [Carl-bot](https://carl.gg/)
    - Gamify 聊天，记录群成员活跃登记，随机发送 prompt question 的 [mee6](https://mee6.xyz/) 等等
- 村民大会，一个 forum channel 用来申请拉人入群、给社群提意见等等，便于搜索组织。
- 交易闲置和组团发车的 forum channel
- 不同语音频道不同用途。早期社群成员会分享一些各自专业的相关内容，中期一度有群友在群里一起打游戏，中后期也有挂着语音频道一起自习、刷题的。

### 个人社区

我最初用 discord 其实是因为[当年做 patreon](../side-hustle-im-on-patreon/) 有 discord integration 可以作为一个福利和跟金主的联系方式所以建了一个金主 server。在 Patreon 上关联 bot 之后即可实现自动给不同 tier 的 patron assign Discord role 从而实现权限管理等，比 patreon 平台内本身能提供的交流渠道灵活很多。

后来我在运行长毛象和博客的时候发现需要一个渠道来给大家通报更新，不然长毛象或者博客挂了只有本身就有我联系方式的熟人能联系到我。因此把这个 patreon server 改成了一个[我的各个渠道集中更新的消息中心](https://discord.gg/cESS4JpsdG)。当然活跃度有限所以也没有放过于 fancy 的功能，绝大多数时间作为长毛象的 backup communication channel。

### 大型 community

我参与的不多不深入介绍了

- 应用，如 MidJourney 这个 genAI 应用和盈利完全是基于 discord 的，目前有一千六百万人，应该是 discord 上最大的社群。（看惯了熟练网公司的用户数量觉得这个没什么，但 discord 是一个有即时通讯功能的软件，可以对标一下一千六百万人的微信群是什么体量）
- Influencer，比如科技博主 MKBHD
- 各个游戏，因为本来就是给游戏玩家用的所以自然用 discord 做社群管理也很方便，也方便玩家们找队友等。比如我加的有 DiabloIV、Portion Craft，Sea of Stars 的等等。
- 各类组织，比如我加过 web design 的，Monterey 水族馆的等等。

## 生产力

### 内建功能

- Mark as todo - 可以把单条消息标记为代办
- 具体到每个对话和 channel 的 notification 都可以定制，这样不会信息过载。太多 notification 等于没有 notification。
- Markdown - 消息支持 markdown 格式便于排版组织

### 个人 server

因为工作内容很多在 discord 上，从 notion 或者其他笔记软件 copy 和链接也没有很方便，我的各个设备也都有 discord，索性开了个自己的 server 当短笔记。

- 中英文搜索都很好用，还能加各种 filter（有没有媒体，谁发的等）
- 消息关系管理。因为 discord 又有普通 reply 又有 thread 又有 channel，可以方便灵活的组织信息。比如 reply 可以做笔记之间的电梯（当然也可以直接 copy message 链接），thread 可以作为一个话题聚合多条消息，channel 则是固定、长期的不同消息分类。
- 文件传输。discord （即便免费用户）传文件限制也比 notion 小很多（25Mb），有 Nitro 更是可以上传 500MB 的文件，视频预览也比 notion 方便，图片甚至可以外链和预览。
- Notes & Brain dump。一些 text channel 随手写笔记。
- AI bot。Discord 官方支持的用 openAI 的 bot，可以直接 @ Clyde 聊天。
- Test。我的各种测试消息。

### 项目协调

虽然我业余没有跟别人合作项目，但是之前[跟其他人出点子的时候想到](https://douchi.space/@mtfront/110267785858352675)即便两个人的项目建个 discord server 组织起来也比单线 DM 方便很多。

- Mentor check in channel，需要跟不参与项目的第三方 check in 的时候用，平时不致于 spam 别人，也容易查找项目成员聊天的 context。
- 分项目进度 update status，这个工作中我也会用到
- 临时学到的 tips 啦
- 聊天讨论产品细节之类的
- 做的产品本身也可以跟 discord integrate

## 总结

因为又具备即时通讯软件的及时性，又有生产力软件的组织工具，还有开放平台的 API integration，熟用 Discord 可以一站式满足我的很多需求。当然，没有 community 生硬地学习一个软件总是很枯燥的，熟悉它最好的方法还是参与一些自己感兴趣的社群。如果不知道从哪开始，不妨加入一些我建立的还不那么活跃的小社群瞅瞅看吧！

{{< button href="https://discord.gg/cESS4JpsdG" target="_blank">}}椒盐豆豉客厅（也算是本站官方 Discord）{{< /button >}}

{{< button href="https://discord.gg/ncT4tDWmZP" target="_blank">}}游戏玩家联邦{{< /button >}}

