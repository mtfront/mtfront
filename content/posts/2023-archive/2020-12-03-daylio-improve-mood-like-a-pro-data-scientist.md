---
title: 改善心情 like a pro data scientist
author: 椒盐豆豉
type: post
date: 2020-12-04T02:28:06+00:00
url: /daylio-improve-mood-like-a-pro-data-scientist/
categories:
  - 喜欢就买
  - 多喝热水
  - 重启电脑
tags:
  - LPT
  - productivity
  - tech
  - tutorial
  - wellness

---
很明显，标题是一个 click bait。很明显 I’m not even a data scientist 我怎么 like a pro 哈哈哈。起这个 click bait 的原因是这篇文章的原型叫“[生活数字化 – Daylio 和 Habitica 体验](https://www.douban.com/note/709478242/)”，但那篇文跟我其他文章相比点击率低得惊人，以至于我在为了错过好工具的读者们惋惜（并没有），于是赶紧安上大热词汇 DS 来优化一下。

诚然，要我我也不想看什么“buzzword A 和 buzzword b“体验啊？就好像同样是改善生活质量的测评，iPad、MBP、Dyson 这种广为人知的品牌真的比我写的 Oura ring, Oynx Boox 之类的小众玩意儿阅读率高太多了，哪怕后者适用性更广，但谁看到一个不认识没听过的单词想要看呢？

离题了，here’s the thing：大概两年前，我因为工作不顺心情非常差执行力奇低，于是开始想用 app track 一下自己的情绪。另外，记录情绪变化也是抑郁症自检的经典方式之一。哦不，其实真实原因是我不知道在哪看到别人的 Year in Pixel 感到羡慕，去搜了一下发现 Year in Pixel 这个 app 功能又少又难用，就转投了有类似功能的 Daylio，然后自然而然被推送了同个门类的 Habitica。这两个一个是极简日记+统计 app，一个是生活游戏化任务管理，表面上看没什么可比性，其实都有点数据化、gamify 生活目标的意思。

2020-12-11 补充：app 果然跟游戏界完全相反，游戏是早买早享受，晚买享折扣，不买会白送。app 则是早买早享受，晚买必涨价。引发这个感叹是我别人看了我这篇之后写回馈提到了买了 $12.99/yr 的 daylio subscription，我大惊，我一年多前是以 $1.99 终身买断的，这也涨价太多了吧。

## A/B test your mood（premium feature）

这是我最晚发现也觉得最有用的 Daylio 的功能，所以放在前面讲。简单来说，你可以选定一个情绪或者活动，然后查看做没做这个活动对你当天和下一天心情的影响。

{{< columns >}}
![](https://media.douchi.space/douchi/media_attachments/files/105/318/314/766/728/444/original/f9d525197ed009cc.png)
<--->
![](https://media.douchi.space/douchi/media_attachments/files/105/318/316/091/974/777/original/10d4f8cdcaa1a5a7.png)
{{< / columns >}}

比如上图中，我今天发现过去 30 天里上了 16 天班 ，14 天厌班，厌班对情绪有统计意义上的强烈负面影响。感觉干 day job 续命上班这条路线快要走不下去了。我第一次 burnout 到一行班都干不下去的工作时间是接近三年，第二次是一年半，两次都以裸辞告终。第三次快要或者已经来了一段时间了，这回间隙是八九个月，或许是时候要下定决心辞职来个 mini retirement 了。

{{< columns >}}
![](https://media.douchi.space/douchi/media_attachments/files/110/455/142/424/295/779/original/440f4edc0bedea28.png)
<--->
![](https://media.douchi.space/douchi/media_attachments/files/110/455/142/771/406/541/original/73be5b3e9f4eec0e.png)
<--->
![](https://media.douchi.space/douchi/media_attachments/files/110/455/143/110/169/233/original/237b1e33a670a8b3.png)
{{< / columns >}}

再比如上图中一些显而易见的活动。即便社恐如我）跟朋友交流跟好心情大幅正相关，其他正相关的还有打游戏、吃好的、旅行、看电影等；最负相关的是生病/感觉不舒服，生病的天情绪比不生病的差 10% 非常准了，其他负相关还有学习（记录里应该主要是刷题），工作（of course）等。

{{< columns >}}
![](https://media.douchi.space/douchi/media_attachments/files/110/455/143/717/863/485/original/4c39e3171a349f14.png)
<--->
![](https://media.douchi.space/douchi/media_attachments/files/110/455/144/652/396/885/original/85bdc24173756f1b.png)
<--->
![](https://media.douchi.space/douchi/media_attachments/files/110/455/145/156/761/640/original/3aa16fb36f439948.png)
{{< / columns >}}

不过最令我惊讶的是，睡眠时间长（我的标准是 fitbit 统计睡 7h15m 以上）跟情绪并无相关性（左图1）。发现这点之后，我就把我的“good sleep“和”long sleep“分开了，然后分别 track 睡眠时间和睡眠质量。过去的一个月中，果然发现“long sleep”并不一定跟情绪相关，反倒是“good sleep“倒是有轻微地加成。这下我可以更放心的调整睡眠计划，而不是一味地追求“早睡”了。（当然，睡太少往往也睡不太好，但不必像以前一样追求七八小时的睡眠了）

## 一分投入一分收获的记录形式

看到这里很多朋友有疑问，心情数据是怎么产生的？显然现代民用方便的技术并还没有什么无需脑后插管的高科技来自动检测，这完全是一个“一分耕耘一分收获，投入多少就会收获多少”的手动记录形式，你自己不坚持记录的话数据不完整是没有参考意义的，也没有人会像贴心管家/你妈一样帮你盯着哪里过得不好。

但好消息是，它形式足够简单，每天 notification 提醒 log 当日心情我至今已经用了两年不间断了。最简单的用法是只输入一个情绪，想要更有帮助的话可以选择和自定义一些当天发生的活动（下图 2、3）。

当然还可以附加一些简短笔记作为自己 reference，比如将来看到特别高兴或者不高兴的一天就可以回去自己看到底发生了什么。

![](https://media.douchi.space/douchi/media_attachments/files/110/455/145/964/456/220/original/67d09d9849b15a14.png)

每日可以定时推送通知提醒记录（安卓版）通知是悬窗形式，可以在通知栏里直接选情绪（一般是五种，从好带坏）快速记录。当然也可以点进 app 详细记录今天的 activity 和 notes。我一般是晚上 11 点 59 分推送，随手花五秒记完。偶尔忘掉了它会提醒你 streak lost，第二天再补上就好。

另外，有每周/月/年总结报告可以看。详细的生活数据组合起来可能会有平时不易察觉的发现（见上图 5、6）。比如很明显，我工作日比周末的情绪明显低落。再比如每个情绪都有常见同时出现的活动。

{{< columns >}}
当然了，还有最初吸引我来的 Year in Pixels。一年过完看看自己的情绪走向，对于记录狂来说还是很有吸引力的。

此外虽然截屏能做到，但是各个模块的导出功能也是挺方便的，可以自己生成图/pdf 方便分享。缺点是按模块分享的，不方便整个报告分享。另外报告的内容也有很多可以完善的地方，比如我就想要个各 activity 的饼状或者折线图。

还有个功能我最近才开始用，就是目标系统。可以自定义或者从建议里选取一些项目，比如早睡觉、每天锻炼、读书等，然后自定义提醒频率。结合记录的功能如果有固定目标的话应该也不错。我最近加了个锻炼的目标，有时候看到自己成功“连击”了锻炼还是有点激励作用的。
<--->
![](https://media.douchi.space/douchi/media_attachments/files/110/455/146/271/861/371/original/5db142e5a96aee63.png)
{{< / columns >}}

缺点是没有网页版/桌面版，所以喜欢长篇的朋友可能不太方便。不过 app 的本身就是一个极简、轻量级记录，单个数据意义不大，连续起来效果最佳。手机端轻便的特性也能最大程度使每日记录更便利。

## Why Habitica is not for me

Habitica 把生活中的任务/habit/todo 游戏化来激励自己，完成任务会有经验值奖励，可以购买装备，捏人，组团完成任务等的 gamify 思想我本来是吃的，但是没用多久就停用的理由如下：

1. 我不管是打游戏还是学习从不组团。自己一个人用的话就跟 todo list 没多大区别了（还会比专业的 todo list 少很多功能，要高投入（比如给自己设置任务，奖励等），简简单单用的话激励性就不大了。
2. 我没有明确短期之内比较固定的目标，所以激励机制对我而言也可有可无。

但整个 app 也还是蛮可爱的，大家可以试试，画风如下：

![](https://media.douchi.space/douchi/media_attachments/files/110/455/146/975/999/849/original/eca97dac618dbb11.png)



{{< details "Migrated Comments" open >}}

### Comment by crossairplane on 2021-02-18 00:16:30 -0800
已经被种草Daylio，速速试用，完全戳中本人记录狂魔懒得分析的点，现在价格订阅制是有点「离谱」，不过倒是想看看情绪稳态情况，向内看看哪些才是内驱并且狂喜的，重在点滴记录，真实反馈。😉

### Comment by 椒盐豆豉 on 2021-02-18 00:22:15 -0800
我感觉近一两年来 App 界价格尤其膨胀的离谱，最近刚好在试用几个新领域的 App，都功能不咋样还 subscription 贵的要死，同为开发者也觉得 justify 不起来 🤦🏻‍♀️现在回头看 Daylio 当年甚至现在的价格简直都是良心了。

### Comment by 茶茶 on 2021-09-23 00:41:43 -0700
通过豆瓣上的健康习惯博文摸到这篇文章，尝试了Daylio，感觉非常适合自己，感谢豆豉的推荐~唯一的问题也还是订阅制价格太贵了。

往年我使用纸质手帐Hobo Weeks的时候，会把年计划那一页用来涂色，每天一个小格子，涂上当天的心情色，最后跟year in pixels效果还蛮像的。

### Comment by 椒盐鸵鸟 on 2021-09-23 00:43:43 -0700
嗯我也很惊讶他们涨价涨那么多，我当年是 $1.99 一次性买断的，这个涨幅真的是…

{{< / details >}}>