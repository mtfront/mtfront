---
title: 中年码农在 pandemic 的尾巴（？）再就业报告
author: 椒盐豆豉
type: post
date: 2021-08-01T09:44:33+00:00
url: /senior-software-engineer-pandemic-job-hunting/
categories:
  - 重启电脑
tags:
  - career
  - software engineer
  - 复盘

---
拖延着，拖延着，我找工作结束也差不多一个月了，我居然还没有把找工作总结写出来，愧对不上班在家闲着，于是奋发图强从新做人打算在 7 月结束前把这篇干掉。

首先放上一些 context ：我， 工作经验 6 年多的美国码农，70% 的时间在做 backend 但也不排斥 fullstack 的 role。过去的工作轨迹两家大厂到一家中型 startup，去年 pandemic burnout 于是今年初辞职家里蹲，歇了半年皮痒了觉得没正现金流还是心慌于是 5 月重新开始找工作。更多背景可以在我前两天写的这篇[我的第三次裸辞，这回没有 deadline](../i-quit-again-without-offer-or-deadline/)里找到。

本文大致分 productivity 向的前两节，码农 specific 面试准备的中间几节，和比较 general 适用的 takeaways 最后一段。重点不同废话较多，可以用上面的目录直接跳转各取所需

## Setting the goal

像裸辞那篇文中提到的一样，既然这回目标是向钱优化，我这回主要投的是大厂或者 pre-ipo 的公司，一改上次看情怀投中期 startup 的方向。

于是在四月底的找工作第一天，我建了我的第一版目标公司 shortlist，来源包括：

- 打开 [level.fyi](https://level.fyi/)，按地点和我的目标 level filter，大体扫眼一眼包裹在我预期值以上的公司都加入 list
- 在[长毛象上征求符合条件的公司推荐](https://douchi.space/web/statuses/106144145522205427)

这样我很快有了第一版 short list。初步筛选后清除了一个之前的误区，就是

{{< hint warning >}}
误区： Senior level 只有 FAANG 能给顶配包裹，小公司都得打对折
{{< / hint >}}

事实上，随着某些 FAANG 仗势欺人 low ball 压 offer（cough Google cough），以及近两年市场水涨船高和一大批独角兽上市，现在市面上给得起 senior level 大概 400K 这个数量级工资的公司大把。这其中既包括了去年火热上市的一波新公司，也包括一下 pre-ipo 但是风险比较小能给纸钱的公司。反倒是 FAANG 里基本上最开始都会被压到 below 350K。不过现在很多人也对 big name 祛魅了，我很怀疑某些不知变通一个劲 gaslight candidate 的大厂这种策略能持续多久。

当然，E 轮以前的比较小的公司因为只有 base 不算纸钱的话，pay gap 还是跟大公司有超过 50% 的差距。另外因为规模小和疫情期间大厂们拥抱 remote working，这些小公司在非 tech hub 的地区跟大厂的 pay gap 就更严重了。比如去年 relocation 政策很多大厂至少在美国境内给了 85%~100% 的 relocation 调薪政策，而去年我在小公司有次聊天无意得知 staff level 但是在 Denver 的本组 tech lead 收入远低于其他在 tech hub（东西海岸）的组员。

因为我对压宝赌博暴富/白干毫无兴趣，所以这次非 pre-ipo 的小公司一概忽略，初选了大概十余个 pre-ipo & 大厂。

## 工欲善其事必先利其器

[像是我上次找工作一样](../why-i-quit-facebook-part-2-whats-next/)，这次我也用 notion 来管理找工作进程。不同之处是除了对上次的 kanban board 做了小规模修改更符合这次的需求之外，我另加了一个 page 专门记录每天的找工 log，包含每天的文字总结、量化分类的这天干了什么等，方便复盘。

![](https://s3.nl-ams.scw.cloud/mtfront-blog/2021/07/Screen-Shot-2021-07-31-at-4.54.24-PM-1024x449.png)

这是我这次的找工作 kanban board，跟上次的区别不大，几个关键点：

- 基本盘是一个按 Status 分组的 kanban board，status 包括：
    - Interested – 这个就是第一天做的那个感兴趣的公司 short list，随着找工作过程新发现当然也在不断加新的进来
    - Reached out – 要么是我已经网申的，要么是对面 recruiter 近期 reached out 的，总之算是一个“已经联系上了”的 pool
    - Need Followup – 这里放着需要我自己有 action item 的公司，比如对方邮件让我约下一步面试时间还没约、发了 take home assignment 还没做等等。现在已经面完了当然这一行是空的，面试期间这一列算是最重要的 todo list，以免忙乱中信息丢失
    - Waiting for update – 这里 action items 在公司方的部分，比如“我回复了有空的时间但对方还没确认”，“面完试了在等结果”等。如果一个公司在 waiting for update 里沉得太久就可以催一下了
    - Scheduled – 已经约了下一步时间的公司。下一步不一定是面试也可能是 HR、manager 聊天、take home assignment due date 等等。在这一步的公司我会 attach 一个 due date，方便在 calendar view 里查看
    - Offered – 已经给了口头 offer 的公司
    - Rejected – 发了拒信的公司
    - Withdrawned – 面到一半我不想面了的公司
- 最顶层（aka 在 board 里就能看到，不用点击单个页面）的 property 只放我这次最关心的内容，比如说我这次的就有地点、钱、POC 是谁、目前的状态/stage，下一个 due date 等。
- 每一列按 due date 和最后修改日期排序，方便一眼看到哪些最紧要需要关心/准备
- 各公司加个 emoji icon 方便快速区分，比如显而易见苹果就是🍎
    

每个公司的页面点进去之后有几个部分：

- Properties – 除了在 board 页面就显示的之外，还会有一些其他 field，比如 timeline，感兴趣程度等等
- Comments：用来记录时间线和做简洁笔记，比如一条“HR asked for availability on monday”，”sent availability to hr” 之类的，因为 comment 自带日期所以 track 起来比较方便
- 页面细节，如下图，基本上是电话/面试中记的笔记，bullets point + toggle 折叠避免 information overflow。code 做完当然要顺手 copy 过去，日后也可以当面经用。后期发来的 interview prep & benefit brochure 我基本上也会扔到里面

![](https://s3.nl-ams.scw.cloud/mtfront-blog/2021/09/Screen-Shot-2021-09-22-at-4.57.59-PM-935x1024.png)

再就业日记找工作 log 基本上就是一个简单 table ，一天一个 entry，有一个 multi select field 作为 tag 表示今天做了什么。正文的部分就是文字总结 bullets point 今天干了什么，并且同步发到长毛象的 [#大龄人口再就业日记](https://douchi.space/web/timelines/tag/%E5%A4%A7%E9%BE%84%E4%BA%BA%E5%8F%A3%E5%86%8D%E5%B0%B1%E4%B8%9A%E6%97%A5%E8%AE%B0) tag 下。后来还有好几个朋友跟我说这个找工日记能看到别人的 struggle 和进步还挺有帮助的，欣慰

![](https://s3.nl-ams.scw.cloud/mtfront-blog/2021/07/Screen-Shot-2021-07-31-at-6.01.50-PM-1024x867.png)

## 面试过程

我的计划是速战速决，以往经验战线拖太长往往后期会疲惫和懈怠，也不会有太大提升。整个找工作过程大致可以分为三个阶段：

### 准备阶段 Day 1 – Day 19

这个阶段是我准备方法的细节，如果不是要找工作的码农朋友可能会觉得稍显无聊，可以直接跳过这个阶段看[面试阶段](#面试过程)。

### 刷题

远古时期 leetcode（后简称 LC） 还只有 150 题，想进 FAANG 基本上是得通刷至少两三遍。近年来 LC 通胀已经有上千道题了，除了少数做题家大神外应该没多少人会全刷了。因此这次我基本只刷了公司 tag 和面经。

关于那个陈年问题——Senior 以上码农还需要刷题吗？要刷到什么程度？答案是肯定的，绝大多数公司面试还是会考算法题，除非有 LC medium 以上第一次见当成能解出来的自信，否则还是需要刷题练一下手的。

不过，刷题的强度和程度确实比 new grad 时候低了很多。毕竟经验少的时候电面 + onsite 五六轮面试里至少四五轮都是题，data point 绝大多数来源于题，考的题多自然碰到 hard 的几率也大，所以必然主要看刷题水平。而 senior 以上 level 不少公司甚至只有一两轮 coding，其余由 system design、behavior question 和 culture fit 等部分组成，coding 轮的考察重点基本上是“有能力把想法 implement 出来”，因此考 tricky question 的几率小了很多。（我对用 tricky question 当压力测试那套 bullshit 丝毫不吃，谁考我觉得谁是傻逼。我自己当面试官都只会出 medium 及以下）

其实我一年半前上次跳槽就面的是 senior level，不过主要对象集中在小厂，标准有所不同，因此这次算是我第一次面大厂的 senior+ level，刷题比上次认真了一些。上一次只面小厂的时候我主要在刷 LC easy 混手熟和少部分超高频的 medium（比如 LRU 之类）总计 70 道，拿到了若干不错的 D~E 轮小厂 offer。这回我也不分类型了上来就直接按目标公司 tag 刷，总计刷了 170 多道。

工作/面试这么多年熟悉了讨论，我几乎不会从头写答案了。刷题的流程基本上是：

- 读题和 example 理解题意（如果之前没有见过的话）
- 快速构思一下解题思路，一般不会超过 30 秒
- 看答案（很少看 LC 本身给的答案，讨论区高赞一般质量更高），理解答案思路。如果实在理解不了就直接跳到下一步
- 开着分屏左边 LC 右边答案用自己的风格复写一到两个自己觉得合理的题解（aka 不用特别 fancy 的 data structure，解法简单易懂，不追求最短行数，甚至不一定追求最优复杂度）
- 提交、debug if any，move on

按照这个方法，我前期集中刷题的时候速度大概是每天 6~13 道，因为是 tag 题所以一般肥瘦相间从 easy 到 hard 都有。因为不追求自己从头写而是直接看答案，所以刷 hard 也没以前那么痛苦了。

比较感兴趣的公司 tag 题面试前一两天还会飞速把所有 tag 题看自己之前写过的解或者答案过一遍。看公司 tag 题多少，不过这个飞速是真的超快过一遍，一天能看三四十道。

初始计划是刷题/看 design 一个月然后开始联系面试。刷着刷着觉得这只刷 tag 和面经比想象中的速度快啊，刷了两周多就觉得没劲了。于是改成了看完手头的 design 书就开始联系。事实上证明这也是非常正确的决定因为各家安排面试速度参差不齐，战线拉得比我想象中长。

### System Design

其实实际工作里真的没那么规整的 design，毕竟没到 staff level 实际能接触到的系统最多也就是一小块，哪能做到诸如”design whatsapp“这么大的 cope。因此说白了还是准备常见题型 + 看书理解原理 + 大致了解流行的工具 + 稍微结合实际工作经验瞎扯。这回我的 system design 做了如下几项工作：

- 重看 [Designing Data-Intensive Applications](https://amzn.to/3xmbsKH)（后简称 DDIA）。这本经典其实我两份工作之前就买了，看了前几章一直没看完，这次想说刚好一鼓作气看完（花了两周）当准备了。果然也非常有收获（尤其前几章）。
- 在 YouTube 上看高频 design 题视频。此处发现过去这么多年了新出的那些形式 fancy 的博主讲的好多是错的要么就是太浅，还是老牌 Tushar Roy 最靠谱。
- 在 notion 里整理了一个高频 system design 题 talk points 和 system components diagram，虽然面试时候参考几率不高但手上过一遍感觉心里更有底，再下次用的时候可以提升下效率

### 更新简历和准备 past experience/behavior question

我算一个比较能扯的人所以 experience 关以前基本没怎么准备过，这次唯一的例外是某些公司想面到 staff level，所以要适当 refine 一下过去的 project 甚至夸大一下 scope（senior level 是 cross team impact, staff 是 org level impact），因此我也在 notion 里挑了几个 project 的 talk points，格式基本跟 system design 的差不多，自己画了一些 component diagram，说的时候照着说比较有底。

当然，这个阶段说是 Day 1 – Day 19 但更准确的来说是 kick start 阶段，或者 dedicated 准备阶段。刷题、看面经、复习 design、更新简历这些活动在后面阶段空闲时间自然也会见缝插针地做。

### 面试阶段 Day 20 – Day 59

### 投简历

在开始准备的第 20 天我开始联系公司。主要有三个渠道：

- 找认识的人内推。大司的面试基本都这么来的。有好几家 refer 可以跳过电面直接 onsite。
- 跟以往一样的是在 Linkedin 里过来跟我搭讪过的 recruiter 里挑出来感兴趣的公司回邮件问还招不招。
- 以上渠道都没有的，直接网申

这回我直接网申的公司比例比以高不少，基本上都收到了回复（虽然有些比较慢已经到后期我不考虑了就 decline 了）。senior level 比 entry – mid level 找工作的好处之一是池子小了很多，条件合适投到系统里基本上 recruiter 如饥似渴地就来了，不像 entry 甚至部分 mid level 直接网申很可能石沉大海得主要靠 networking 提高命中率。

### 面试

从 5 月底开始有面试。因为不上班所以可以面试最大化，面试的工作量比全职上班大多了。最猛的一周我有 onsite * 4 + recruiter/HM chat/feedback * 10，甚至还会给 Onsite 中间的 lunch break 插一个 chat：

![](https://s3.nl-ams.scw.cloud/mtfront-blog/2021/08/Screen-Shot-2021-08-01-at-12.43.16-AM-821x1024.png)

然后总共有五周 calendar 是这样的，看起来时间很紧，但因为 window shopping 的快乐和一直在干实事所以其实比上班开心多了。

![](https://s3.nl-ams.scw.cloud/mtfront-blog/2021/08/Screen-Shot-2021-08-01-at-12.48.27-AM-634x1024.png)

最后的决定跟我一开始想象的完全不同，有几个出乎意料的转折，去了完全没想到会去的公司，钱与情怀算是都到最优，非常满意。

## Takeaways

### Big name is no longer cool… or generous

我这次面的公司基本上分为如下几个 tier：

### pre-pio 独角兽

如 discord，plaid 之类。这些公司的特点是处在快速上升期，公司整体比较有活力，八成会近年 IPO 所以风险较小（equity 不会变纸相当于少一半的 pay），面试也不像大厂一样死板。

通常情况下跳槽选这部分的人都是想赶上最后一班车暴富，像前面所说的，我对压宝赌博暴富/白干毫无兴趣，因为我并不需要那么多钱，也不信 FIRE 那一套。因此只选了自己绝对感兴趣的公司。甚至中间没 offer 惊慌期病急乱投医冲着钱（它家经常会给别厂 L5 给到 L6 的纸钱包裹，因此“钱多”）但并不认同 business model 的 Instacart 后来有了别的 offer 我也把 onsite 直接 cancel 了。

### 刚上市的新独角兽

如 affirm, doordash, airbnb, lyft, square 等。这类公司跟 pre-ipo 相比好处当然是 equity 可以直接变现风险更小，但还没有僵化到 FAANG 或者更老牌的平台期公司的地步，还是可以感受到一些年轻公司的活力。

这里再提一下我之前说过的误区（~~Senior level 只有 FAANG 能给顶配包裹，小公司都得打对折~~），在这里最为适用。新独角兽们的 package 基本上跟 FAANG 持平或者 beat，差不多能给到 TC 400K 左右这个 level。不想牺牲钱也觉得大司工作太僵化无聊的话，可以考虑这个 tier 的公司。

### FAANG – 业界龙头还在快速上升的大厂

此处有个笑话：

某厂 recruiter：那你方便透露其他还在面的公司吗？比如 X，Y 之类的？

我：Yeah.

Recruiter：Which specific ones？

我：All of them.

因为冲着钱所以 FAANG 里所有家都来了一套，这次面完感觉对其之前的印象完全打破：

- 首先 top tier cool kids no longer cool.
    - Google 压 level 压如狗，面试体验因为个例而奇差（下面说），要加面还给人往 L4 压。而且坊间传闻今年明显看到工作压力暴增尤其是 GCP，好多人都祛魅了。
    - FB 本来 perm 的事就从鄙视链上掉下来了，我去 onsite 之前才跟我说 re-hire 只能按直接升职的钱走 non negotiable，升职的钱嘛大家都知道肯定比市场价差一截，不能 compete offer 就直接 cancel 了 onsite，白边浪费了电面时间。
- Apple 本来果黑如我就大概率不会去，面试体验极差被问的问题不怎么专业，对员工也远不如其他厂好（但是面试官 tenure 都奇长），优点是有钱，compete offer 可以走很高，另外各组单独招人，我就是投了一份简历同时面了两份 onsite，如果需要增加中标几率的话大概是不错的选择。
- Netflix 在这个 list 里的唯一原因是前两年股票涨得凶而且纯现金包裹大，但是这两年随着别家水涨船高和都开始把 vesting schedule 变细（大多数公司 vest quaterly, 甚至有 vest monthly 的），而且人到中年不炒房的话对 base 高没太大兴趣，吸引力也有所下降。另外 Netflix 也是单组招人的，经常会碰到面的不错但是被拖着等其他 offer 回复的情况，因此性价比也不高。
- 最令人意外的是 Amazon，前期 frugal 如狗反复问期望工资一副给不起的样子，后期给了 offer 追着你跪舔疯狂撒币，甚至其他公司都比较准的 level.fyi 在 Amazon 上也不适用了，一亩三分地上有单手数的过来的 outlier 是真实可以要到的数字。面试时候我碰到个 Google 过去的还在纳闷为什么会有 Google 的人跑去 Amazon，拿到最终数字的一瞬间我明白了。大概是这两年香蕉厂名声太差，福利差钱少 PIP hire to fire 组合拳，谁有别的选择会去，招不到人大概是急了只能拿钱砸晕了。想要 compete outlier 大包的同学们可以去试试。另外，Amazon 的 L6 基本对应其他厂 L5~L6，band 大权力大一些（我以前在 Amazon 当 SDE I~II 时候的观察），如果在其他厂 struggle 拿不到 staff 的话 Amazon 或许可以绕开这个问题。

### 夕阳厂 – 也不一定在下降，但跳槽界不在 tier 1 的已上市老骨头

如 Salesforce, Snap, Twitter, Microsoft, Dropbox, Linkedin 等等。这些厂要么就是同 level 包可能会比 FAANG 还少一些（around 300k），下一个 level 又面不到（动不动是 15 yoe+ 的人），要么就是产品我真的毫无兴趣纯粹为了钱去的。这些厂在我这里面试体验最差，如果不是一开始不确定能拿到什么水平的 offer 的话我一定投都不会投。

比如我在 Dropbox 碰到了[面试生涯没面过 100 家也面过几十家公司的我碰到史上最奇葩的 recruiter](../the-most-unprofessional-recruiter-ive-ever-seen/)，在每次我都有 propose 解决方案的情况下鸽了我三次，永久拉黑。

再比如为了钱投的 Snap 但是下了 App 用了几分钟立刻被浮夸的内容和低劣的音质画质击退，不是目标受众用不下去的产品我是真的没办法，立刻试都不想面了。当然因为这是我早期的面试还没 offer 还是硬着头皮去了，结果体验奇差，好几个面试官心不在焉，director 讲话都特别 depressing，连滚带爬地吓走，连拒信都懒得要。

再比如 Microsoft，因为我有好友在所以在不同年代被内推过好几回，每次不是被 recruiter ghost 就是被简历/全部做对的 OA 拒（在其他家哪怕是老厂从来没有碰到过），不禁让我觉得他们的职位大概都是为了打 perm 并没有想要真的招人，永久拉黑此生都不会再投。

这里面体验最好的是 Twitter，从福利到面试官都还不错，当然最后因为钱和组都不是最好的选择所以也是我发出去的第一封拒信。

### 小公司整体上面试体验更好，更尊重 candidate

面试体验基本上是顺着我刚才列的那几个 tier 递减的。

比如 discord 和 plaid 的题都是模拟实际会碰到的问题在 local environment 解题和自己 debug、测试，面试更像是 pair coding。如果不是做题家而是对 coding 能力更有自信的话这种形式会更放松（另外其实面经也就那么几道题）。discord onsite 甚至还有个 cross function 纯聊天环节跟 3 个非 engineer 团队的人闲聊，literally 闲聊，不是 behavior question。比如我碰到的这个环节一位 40+ 的大姐姐先自我介绍完，来了位 MTF 上来就讲自己 pronoun，后面一个萌萌的金胡子明显顺男小哥顺滑添上自己 pronoun is him。瞎聊到 why this company 我跟 mtf 聊起了 pixel art, patreon 和打的游戏，一通 roguelike 互相安利之后大姐姐 is like 哇我一个字都听不懂，金胡子小哥道我虽然不打游戏但是我看剧，下周 gossip girl 就重启了星星眼。相谈甚欢。

刚上市的新独角兽们面试没这么灵活，但考刷题的同时至少能感受出来面试官对面试者还是上心的，recruiter 们反应也快而专业。

FAANG 面试就是八股文 + 势利眼，毕竟对方可以选择的 candidate 太多，明显可以感受到电面之前对 candidate 都是爱理不理，过了电面拿了 onsite recruiter 立刻上心了起来。面试官大多中规中矩，但因为刷题家进去的多，因此碰上奇葩的几率也高于小公司。

{{< columns >}}
比如我在 Google 第一轮碰到了史上碰到过最差的面试官（预设答案，疯狂打断，不接受讨论），差到第一轮没过 10 分钟我想直接 cancel 整个 onsite 不值得受这种侮辱。请看右边这封我面完试立刻发给 recruiter 的气到错别字都没改的讨伐信。

我是周五下午四点多发的，recruiter 周五晚上 8 点多回我邮件道歉说会 look into it。第二周拿到 feedback 之后 offer 加面，不过因为要加三轮外加要往 L4 压我就直接 cancel 了。通电话的时候感受到 recruiter 本身对这个事情也非常遗憾和懊恼，我们真情实感聊了半天，我还安慰她说不是她的错她已经做得很好了。

毕竟我算是个面试老油条了，碰到这种事情也就影响一天心情，又不是要在一棵树上吊死，骂完就 move on 了不会影响后面面试。但要是本来面试机会就不多的非大神 new grad 碰到这种傻逼面试官（对，我在一篇 suppose to be perfessional 的文里用了傻逼这个词，请体会一下我的愤怒）得有多 devasting。

当然，这种面试官八成也不会受到什么惩罚，最多就是偷偷被从以后的 loop 里拿掉而已。无奈
<--->
![](https://media.douchi.space/douchi/media_attachments/files/106/394/772/078/572/386/original/e5f9436c1f2cc3f9.jpeg)
{{< / columns >}}

FANG 的八股虽然无聊但好歹（除了个别奇葩以外）面试官大部分看起来 sharp & smart，夕阳厂则 not so much，一副 burnout/心不在焉脸的面试官比例大幅上升，虽说划水养老令人快乐，但连招人时候都装不出高兴的脸又能快乐到哪去呢？恕现阶段的我还无法理解。

最搞笑的是以 recruiting 出家的 LinkedIn，按理来说比其他所有公司都了解 candidate 的信息，recruiter call 都没有直接甩电面我还想说有够效率不废话反正我资料你们都有了，结果电面完安排 onsite 了跟我说 BTW this is a SWE level role。I was like what the fuck SWE level 一手打开 level.fyi，然后问是不是 entry level。对面还支支吾吾说不是跟 new grad 还是有区别的（实际上并没有）。见过其他厂 down level 一级的，这临 onsite 了告诉 candidate 面的是 down level 两级的操作我还是第一次见，更何况还是个 recruiting 产品的公司。礼貌地让他滚了之后永久地拉近黑名单，that’s not only insulting but incompetent.

### 面试是双选，有 leverage 有选择权一定要自信

没几年工作经验的时候，往往觉得自己是跪舔着要进公司，拿到机会对什么都 say yes 生怕错过，先薅着再说。这次跳槽明显体会到供需关系和 power dynamics 的变化，尤其是初期大厂 HR 的冷漠，到拿到 onsite 时候的态度突变，到拿到 offer 时候的百依百顺，主动权层层递进到面试者的手里。

整个面试过程的心境完全符合[云五老师](https://yukieyun.net/)做的这张图：

![](https://s3.nl-ams.scw.cloud/mtfront-blog/2021/08/Screen-Shot-2021-08-01-at-12.56.35-AM-1001x1024.png)

我一开始因为不知道能不能拿到 offer 所以 say yes 了几个组并不 match 的机会，后来拿了 offer 兴趣缺缺，现在想来，一开始就 push back 直接让 recruiter 换组的话或许不会这么浪费了几家公司。

另一家公司几年前我拿过 offer 体验很好最后差点就去了，这次面试体验比上次差远了，但鉴于给了 staff level 外加上次印象不错产品体验也好，还是在我优先级比较高的选择。也是一开始怕丢机会没有 push back 不 match 的组，所以多加了一轮别组 HM 聊天。本来这轮相谈甚欢以为拖了，结果过几天回来跟我说觉得适合别的组，再约一个。因为本来以为聊得来我期望比较高结果对方 didn’t feel the same 我已经有点伤心了，再约的那个还因为 coodinator 放假和公司国庆假放假等一拖再拖。过了一周回来我已经有 dream offer 了就直接跟他们说不用聊了。现在想来也是一开始太不自信，如果一开始就 push back 拿到比价合适的组可能就不会错过这个机会了。

还有一家公司，先前完全没想到会去，看了网上的包裹也觉得给不出能让人无法拒绝的工资，虽然面试体验出乎意料地好但还是抱着不去的心态，于是后期拖得慢也没管反正想说不会去。签了别家 offer 之后这家才聊到，结果跟 HM 一拍即合相谈甚欢，考虑到职业发展因素，甚至一开始坚定不去的信念都有点动摇。谁料最后拖了拖还是忍痛发了声情并茂地拒信之后 recruiter 光速打电话过来让我 shoot for the moon 然后给了一个没敢想的数字，居然一下把我给问住了第一次在 recruiting 电话里语塞。考虑了几小时之后决定撕了之前的 offer（挺喜欢的产品，但是没有喜欢到能拒绝多很多钱的地步）签这家。现在想来如果一开始不抱着“反正给同样或者多一点钱也不去”的心态，而是认真拖两家 deadline 认真 negotiate 的话，大概也不用撕 offer burn the bridge 了。（虽然被撕那家好像也表示理解没有特别不高兴）

双选过程特别明显的一家，聊完我觉得特别合适 background 完全 match 给钱也满意产品也满意，已经开始 YY 过完一生了（不）结果被对方拖了一周我催才催出来一句不合适。换位思考一下拖 offer 的时候 recruiter 和 HM 大概也是这个心情吧。

## New Start

说了那么多，差不多一个月前结束的找工季还是我职业生涯四次找工作里最刺激的一次。有连续被拒落入谷底，有发现新 dream 公司斗志满满，有被以为合适的拖延周转再失望，有签到合适的开始 YY 未来新生活，有突然被跑出 curve ball 几小时之内做出大改变。过了一个月还是仿若昨天的激动。

想到一个月后即将入职迎来的新生活还有点跃跃欲试，虽然似乎每次换工作都这样，但这次大概是改变最大的一次，也即将要尝试很多新的模式。虽然说不定一个月就 burnout 了发现自己还是厌班，但至少能做出努力和行动改变，还是在三十岁的尾巴上给自己交了个很满意的答卷的。希望这篇文能给还在工作上 struggle 的朋友们一些参考。

{{< support >}}

{{< details "Migrated Comments" open >}}

### Comment by tc on 2022-01-20 19:14:59 -0800
能否推荐几家西雅图地区的Tier1公司啊？

### Comment by 椒盐鸵鸟 on 2022-02-05 23:01:02 -0800
不能
{{< / details >}}