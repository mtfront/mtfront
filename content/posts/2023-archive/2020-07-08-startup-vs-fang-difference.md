---
title: 在 startup 干了半年，与我过去几年大厂 FANG 工作体验有何不同？
author: 椒盐豆豉
type: post
date: 2020-07-09T01:54:00+00:00
url: /startup-vs-fang-difference/
categories:
  - 喜欢就买
tags:
  - career
  - software engineer

---
在早上 promise 了大家今天要摸鱼的鞭策下提前完成了今天的 minimum 活儿，可以顺利写写我在大小厂当普通码农的不同工作体验供大家参考了。以前在大厂各自的体验写过很多篇了就不赘述，本文仅关注大小厂横向对比。对以前大厂经历感兴趣的话可以参考文末附录里我以前写的日志。

{{< hint warning >}}
(Heavily 中夹英 please X out before we disgust each other. 另外我在一亩三分地和知乎都有号，之前有人盗帖已经被 Warald 亲自打脸抄送我然后把盗文者删贴扣分了，所以请某些人洁身自好，沦为跟营销号一样没节操。人都在美国了就别玩天朝贴吧那套了。)
{{< / hint >}}

一点我的背景便于理解：本身对写码没什么热爱，半码农专业完全是高考志愿报的不咋地调剂的专业，直到大四上学期申学校的时候还不想去码农专业，申了一半码农项目一开始的动机纯粹是为了“本专业保底”，后来在论坛上耳濡目染多了给自己洗脑“反正不爱上班哪行不是不高兴，不如选个钱多/身份容易的职业不高兴”，就乐呵乐呵的去技校读码农专业了。后来的工作经历期间也不乏转 management track 机会，但我一向我这么讨厌跟人打交道和没野心，还是老老实实当 engineer 吧。

毕业阴差阳错懒得刷题顺理成章地进了 FANG 里垫底的血汗工厂就没再面试了。混了几年[忘了初心又嫌钱少路远](https://www.douban.com/people/mfcndw/status/3020776285/)，换了 FANG 里另一家血汗，一来就碰上坑爹 manager 导致一直觉得跟整个公司气场不合。呆了俩组混了一年半载觉得再不换换环境就要被 depression 逼疯了，遂在几家小到中型（100～1000 人）startup 里纠结一番选了个钱最少人最少单口碑和产品皆不错的 startup，现在干了快到半年。赶上疫情，其实就去了公司一个月，剩下时间全在家办工。

如上文所说，工作对我来说唯一的目的就是糊口，一点爬梯欲望都没有。世界上可能没有几个丁克比我更铁（regardless of sex orientation）不需要为养娃筹钱，没有奢侈品爱好顶多买买平价电子产品和游戏，也毫无职业上的野心。因此，以下工作体验也均以此中职业目标/工作风格为前提。我只干过三家公司五六个组，经验难免有局限，为了简洁提到“大厂”与“Startup”也是个人经验，不一定适用于所有大厂与 startup。

## 工作内容

### 大厂：

无论是刚毕业 entry level 还是后来 lead 项目和小团队，或是去新组 ramp up，我呆过的两家大厂都给我感觉有很多 overhead，实际写码时间远不如现在的小公司多。这些 overhead 包括但不限于：

- 项目前期撕逼扯皮 scope、resource、design、planing——由于大厂“水份”多，划水的时间也多，经常出现前期厌班拖拖拉拉没写，deadline 前一两天赶工到吐血的情况。
- 中期跟其他组或职能 cross function 合作。同样，好的 manager/PM/TPM 和组织架构可以有效提升这个部分的效率，但同样可遇不可求。像我在 Why I quit 你脸那篇里提到过不止一个例子：你自己读代码要三周还不一定对合作组三天就能解决的问题全靠对方愿意帮你的意愿、合作组没有人知道代码内容、前期 manager/PM 没协商好项目做到一半才发现 assumption 是错的等等。
- 开发过程中由于庞大代码库、services、规范和框架所造成的不可避免的 slowdown，如 environment setup、configuration、dependency migration 出现的问题等等。不同公司和组用的工具不同、文档质量不同可能有所影响，但我呆过的两家都各有各的好与坏。
- 真正的 operation load，毕竟用户多代码量大，光 debug/monitor 工具就一堆够令人迷惑的了。在[此点名批评 FB](https://www.douban.com/people/mfcndw/status/2559100614/)，跟亚麻的 oncall 效率完全不是一个数量级。
- 整体划水时间较多，很多时候这种“明明有事做甚至明确知道怎么做且没有被 blocked 的情况下就是不想开始，宁愿花水浪费时间，想说再划一下就去工作结果从早划到晚划也没划好活儿也没干还搞到很晚没有 work life balance“的情况[其实并不快乐](https://www.douban.com/people/mfcndw/status/2989119810/)。好的 manager/PM/TPM 可以有效缓解这种情况，但能不能碰到全看运气，且随着工作经验和能力范围所涉及的 scope 增多，难免会要自己解决这些问题。

因此实际上写代码，或者说个人觉得真正在“干活儿”的时间可能只占全部工作内容的一小部分。Design doc 虽然也是产出，但跟写码完全是两种效率感。更何况根据公司风格不同很可能 design doc 也没什么好写或者写出来没什么提升。

### Startup：

明显感受到[大半时间在写码](https://www.douban.com/people/mfcndw/status/3011417851/)。原因可能有以下几条：

- 产品小迭代快，虽然不一定有大厂完善的 continuous deployment framework，但代码基本简单直接达成目标，不懂的问题在组里一问也能很快得到答复。
- 人少，各人在干嘛 standup 和 sprint board 一目了然，有需要出活儿 peer pressure，也不像大厂一样大家对互相内容没那么了解能假装复杂。当然，划水也不如大厂容易。
- 少去了中间层的 planing 和 resource 扯皮，一个东西做不做经常来个大客户、一个 PM 跟 EM 拍板就能决定做不做或 priority。Tech 方面全公司就那么几个元老码农、每个职能就那么一个组，决定会很快被做出。
- 没有 setup overhead，开发与测试简单，直接原生语言测试工具+直接改数据库。记忆犹新我第一个要写一个新 test class 心中一惊心想以前在大公司这直接是能从 small 变成 medium 的活儿，谁知道上手一些根本没有多少东西需要 setup/mock，几十分钟搞定。setup 新的 repo 基本上也是随手 clone 下来照 readme run 几行命令就能跑了，如果 readme outdated 发相关组/support，work hours 一小时内得到回复，就算要修复也很少超过一天的。
- 没有组间扯皮，有也是俩 manager/engineer 开个半小时会解决。engineer 之间的问题要么手把手解决，要么立刻甩来应该从哪开始看的链接。

另外，小厂虽然总用户量比大厂小许多，但代码对产品的影响直接了许多。成就感比在大厂明显太多了。

## 待遇福利

跟翘楚很多湾区大厂如 FB 自然是没法比（[专门写 FB 那篇](..//why-i-quit-facebook-part-i-personal-experience/)聊的比较多）。base 在一个数量级，但少了 RSU。佛系稳扎稳打小公司 senior level 跟去 FANG 比不算纸钱应该有 30%～50% 的 pay cut，我面的独角兽/pre-ipo 的规模稍微大一些的算上纸钱（因为变现可能性更大）也可能有 0%～20% pay cut 。食堂只有一个且质量一般，零食也不多。医保跟 401K 都比大厂差很多。发财的潜力而言我们也是一个细分市场，我不认为会也不是为了暴富来的。总体而言，并不适合拖家带口或想早日靠工资财务自由的人。当然 remote options 是另一个考虑方向。Hot startup 可能福利更好一些，但我没有具体了解。

为了积累经验刷简历 leadership，就看个人奋斗方向和努力了。比如我是冲着比大厂“有意思”的工作内容和好一点的工作体验来的，组里都是老司机，也没什么升职压力，毕竟全公司就俩 staff engineer 元老，就没什么好刷的了。但比较有职业规划想要奋斗的我觉得也肉眼可见机会多一些，毕竟呆个一两年就成了组里元老，向管理方向发展，主动提出 initiative 等 impact 都比较大。当然我才刚来，还不知道将来这段经历放在简历上会有什么影响吃不吃香，目前日常来搭讪的 recruiter 也依然是熟脸大厂和 startup 都有，给开的 title 跟过去也暂时没什么变化。

另外我司平时就不 sponsor H1b（可 transfer）和绿卡，这就排除掉很大一部分人了。很多湾区 startup 虽然也 sponsor h1b+绿卡，但终究还是变数比较多。为求最快最稳妥拿身份肯定还是大厂好。（当然，今年这情况也实在是没什么好选的了）

（注，这篇文章是几年前还在上一份工作的时候写的，现在在的 pre-ipo 中厂是 sponsor 的，欢迎来找我 refer）

## Work life balance

### 正面影响，前面提到过了就不展开讲了

- 迭代快，合作效率高，实际出活儿率高
- 支持 Remote
- 少 overhead
- Deadline 较为灵活

### 负面影响

- 人少活儿清楚，划水不方便
- 因为效率高带来的实际工作量增加

今年情况特殊，大多数时间居家办公，具体工作量也不好跟以前比较。目前的状况是因为居家办公所以工时变长了（但大厂的友邻似乎也是这样），目前为止虽然也有厌班，但世界出活儿率高带来的成就感正反馈也多。整体感觉前面提到的“无效划水”变少，没有升职压力和 peer pressure 等等，但对工作时间自控力要求较高。

## 公司文化

大厂毕竟一下几万号人，虽然风格不同，但多多少少会有不少 bureaucy 和 transparency 问题。文化活动也因为人多而少了份参与感。我在大厂 5 年基本除了 pride parade 和必须去的 happy hour 和全手之外没参加过什么没 swag 的活动。

小厂人少就自带优势了，公司组织活动一样是发在 channel/calendar 上，但少了在汪洋大海里筛选的步骤，you can’t miss anything，感兴趣的直接去参加。volunteer 之类的公益活动当然不比大厂更多，但因为人少 visibility 高感觉很容易参与。各种 channel 也因为整体人少而多了很多亲切感，比如[之前发现](https://www.douban.com/people/mfcndw/status/2999186057/)有人开了个 slack channel 举办居家 vlog 活动员工自己拍展示 wfh 生活。

每周公司全手直接公布销售额，大订单，客户 feedback 等，今年情况特殊还公布了财务状况（预算等），公司动向也基本上是一有确定消息就告诉大家。 engineer demo visibility 也高，我在大厂 5 年也没 demo 过几次，startup 来了几个月当着全公司 demo 过两次了，而且都是特小的 feature。Hackthon 参加了一次也拿了奖。

公司有 channel 日常 share user success story、有趣的 use case、customer feedback、消息等。比如有一次我就[偶然看到我们公司还有南极客户](https://www.douban.com/people/mfcndw/status/2999143808/)，用我们的软件扫了南极冰川。干了这么些年码农第一次有 making the world a better place 的感觉。

另外不知道是我现在这个公司本来就有远程文化还是小公司特有，直接 zoom/slack call sync/pair coding 解决问题，虽然社恐有电话压力，但很多时候确实效率高了很多。（我刚来第一个项目卡住了就跟 VP of engineering pair coding 结果他秒解决搞得我又觉得快被 fire 了半天）比起来之前在 FB 跟别的组踢皮球给我留下心理阴影真是太大了。

不算今年情况特殊，我们公司之前就非常 remote friendly，大概有一半员工是 remote，除了在美国各地外还有诸如波兰、南非等地。有这种 option 不禁有了又自由一些了的幻觉。

Verdict

整体而言我个人纯工作幸福感还是提高了的，不后悔当初从大厂辞职。当然也会偶尔怀念一下这次没签的大厂和其他规模大一些的 pre-ipo 的钱，但想想其实好像多要那么些钱除了心理安慰好像其实也没什么用。当然，这种事情没法 A/B test，个人侧重点也不同，没有绝对高下。像我这样不是为了暴富或者热爱的事业的情怀，而是为了有自由选择的 peace of mind 幻觉以及纯想换环境而降薪去小厂的应该也不是特别有代表性。Just saying，单单能开阔一下思路发现自己有能接受的选择这一点就已经很幸运了，更何况我还开拓了新的长期目标思路（pursue indie game dev），虽然不确定跟来了小厂有没有直接联系。

在大厂决定辞职之前最后有段时间特别痛苦的时候被人一语道破：好的开端不应该让人的路越走越窄[（更详细的讨论）](../why-i-quit-facebook-part-2-whats-next/)。我这次的职业选择应该就是在践行这一点吧。如果能给哪怕千分之一的读者相似的启发，那这篇文也算没白写了。

