---
title: "用 Notion Calendar 打造高效 daily quest 系统"
author: 椒盐豆豉
type: post
date: 2024-03-09T22:33:00-08:00
url: /notion-calendar-daily-quest/
categories:
  - 重启电脑
tags:
  - productivity
  - tutorial
  - patreon
booktoc: true
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/112/069/271/020/228/708/original/d21683dbf7e74fc9.png
imageDes: "Midjourney prompt: notion calendar time management --ar 16:9"
---

今年 1 月 Notion 推出了一个可以关联 Notion database 的独立 Calendar app，我从一开始的“为什么要反复造轮子用一个新 calendar app”的不解到用上之后立刻觉得很顺手也就花了一天。之前本就是 Google calendar 重度用户，之前一直不想用 Google calendar 做 time blocking 。刚好 notion calendar 推出之前在 notion 里重整了一下自己的 daily quest 系统，现在 notion calendar 直接连上用来做 time blocking 刚好。用了一个月也已比较顺手，这里分享一下我用 notion calendar 做时间管理的 daily quest 系统。

<!--more-->

本文是我 [2024 年 3 月 Patreon 的月度选题](https://www.patreon.com/posts/2024-nian-3-yue-97913966)。所有人均可在第一时间免费阅读我的 patreon 文章，每月我会提前发起投票提供二至四个下个月可能会写的博客题材，因为兴趣比较杂内容可能会涵盖职业、科技、消费、理财、健康、效率等不同的话题，[加入 patreon 可以跟其它赞助者一起选出下个月你想看的博客文章](https://www.patreon.com/posts/100083093)，并且支持本博客的持续创作。下期选题：
- 租房还是买房，公寓还是 house
- 又丑又不舒服的雨鞋已成历史——vessi 安利
- 我的看书习惯演化史

## 什么是 time blocking
Time blocking 是一种常见的时间管理方法，即在 calendar 上把什么时间想做什么事用创建 calendar event 的形式标记出来。在团队合作场景中，这样可以有效张工自己的时间，避免被其它合作者塞入非必要的会议而打断专注时间。在个人工作环境中，它也能作为一个提醒和 guideline，能把大块时间聚合起来帮助自己进入专注状态，避免自己无所事事浪费时间在刷社交网络、看邮件、回消息等低生产力行为。

Time blocking 不像真正的会议和 appointment 一样有钉死的时间和地点，可以根据实际情况临时灵活调整。网上有很多相关技巧，这里不再赘述。

## 什么是 daily quest
算是一个我缝合了一些时间管理技巧总结出来的适合自己的每日任务列表。把想做的事情叫做”quest“这种游戏中常见的任务形式而不是加到 todo 里，也算是把生活游戏化的一种，根之前写过 [`Feel Good Productivity`]({{< relref "/posts/2024-01/12-book-feel-good-productivity" >}}) 中所提倡的“What would this look like if it were fun? ”算是一个思路，心理上把任务变成成就会更想做一些。

- 它跟 todo 的区别是，todo 算是更 time sensitive，也更细节，是要在某个时间点前完成某个具体的项目。一些在 todo 里的例子：周五交房租；周三去图书馆还书；这次去买菜要买的东西，等等。
- 但 daily quest 的单项任务内容又小于长期要做的 long term goal/bucket list 事项。长期 goal 的例子：能做十个标准引体向上；机车环台湾岛；做个独立游戏，等等。
- 一些我常见的 daily quest：写博客；打游戏；画像素画；电影之夜；社交；读书；练腿，等等。很重要的一点是，这里不只有痛苦的“任务”，更要有能让自己快乐的活动，这才是 quest 而不是 todo。

这些没有具体内容（比如“今天写 notion calendar 博客“就是更具体的 todo 内容），如果不 block 时间，往往会被生活中其它琐事挤没。所以结合 time blocking 来给它们预先安排时间是一个有效保证这些对个人成长和身心健康有益的事情能被完成的方法。

Daily quest 系统在上班的同时想做点自己的事情，或是不上班的时候要避免自己无所事事一天结尾充满浪费时间的悔恨的时候都特别有用。之前还在上班的时候我有用类似的 daily focus 来列出来每天主要想完成的几条任务，后来厌班就断掉了。[被裁了]({{< relref "/posts/2024-02/3-layoff" >}})之后没有强制起床上班的束缚更容易一天无所事事就过去了，遂警醒重建升级了 daily quest 系统。（其实还整合了 life quest 把之前想做的一些 long term goal 整合进去了）

## 什么是 Notion Calendar
Notion Calendar 是 notion 推出的一个独立 calendar app。它有如下特点让它成为了做 daily quest & time blocking 非常好的选择：
- 能连接多个 notion database，不再像旧的 notion database calendar view 一样一次只能看到一个 database 的事件。因此能把个人的多个项目和专门用来 time blocking 的 daily quest database 完全整合到 calendar view，时间可以分配得明明白白。各个 database 之间又互不干扰，可以使用不同的结构分别管理。
- 能与 Google calendar 同步。这点也至关重要，有了能与现有 appointment & meeting 系统兼容，与外界无缝沟通的桥梁，无需迁移，也有方便的工具能显示/hide 不同的 calendar。
- 有 Availability 分享功能，跟别人协作约时间变得非常容易。像自己创建 calendar event 一样直接鼠标拖拽就能多选出自己有空的时间，还能自动生成可转换时区的 email 文字，甚至可以生成一个能直接 schedule 的 link，不管是管理面试还是朋友之间约时间都很好用。对个人用户而言 calendarly 这个产品就没用了。
- 可以连接 Notion page 到 Google calendar event，做 meeting notes 和 time blocking 都能用得到，对 Google event 也是个很好的补充。
- Mac 的状态栏会显示当前 event 还有多久结束，或者下一个 event 还有多久开始，对 time blocking 非常方便（下图左上角的“写博客”就是一个 event）
![](https://media.douchi.space/douchi/media_attachments/files/112/069/587/018/850/936/original/d3fe853ec735039c.png)

此外，一些现阶段的团队合作功能也很不错：
- 可以叠加组员的 calendar，对用 notion 管理项目的 startup 很有用。
- 自己 block 的时间可以像 Google calendar、outlook 等企业用法一样设置隐私，控制组员是否可以看到 meeting 的细节还是只能看到时间

目前最大的缺憾是手机版又双叒叕暂时没有安卓版本。可以理解 MVP 先 launch iOS 的思路，不过作为一个生产力软件跨平台性至关重要，期待后续更新。

## 我的 notion calendar integrated daily quest 系统
Notion calendar 的基础是 notion database，在我的 daily quest database 里我有 today、future 和 all 三个 view。Today 最为常用，计划和调整的时候默认打开。Future 是前一天晚上如果有空计划第二天想做的事情可以提前写进去。这三个 view 当然是按时间 filter 和排序的。

每个 quest 除了标题之外，还有类型，mountain of value 和是否完成这三个值。
- 类型分为主线和支线：主线是一天中比较重要想完成的任务，支线则是锦上添花。为了控制自己不制定太多主线而导致完成不了带来的挫败感，会硬性规定一天的主线任务最多只有两个，都完成了就是非常有成就感的一天了。
- Mountain of value 则是这些任务给我带来的价值。大概扫一一眼如果一天或者近期的 quest 所带来的 value 不平衡，某些注重的价值持续缺失的话，可以主动添加一些相关价值的 quest 平衡。

![今天为例的 daily quest](https://media.douchi.space/douchi/media_attachments/files/112/069/884/335/466/788/original/2f380c56f5bf492a.png)

把这个 daily quest database 在 notion calendar 中关联之后，当天的 quest 就会出现在 calendar 上。我的做法是生成 quest 时只生成日期，因此在 calendar 里它们会出现在一天的最顶上（相当于 Google calendar 的 all day event 位置）。在 Calendar 里可以随时拖拽到自己想执行的时间来进行 time blocking。

Notion calendar 的 event 拖拽手感做得非常不错，能很容易地调整时间而不用手动输入。像前面说的，time blocking 的时间大多只是提供参考，并非严格规定，所以一件事因为种种原因没在原定时间进行我也会毫无心理负担地随时进行调整，核心思想是“不要因为浪费了 10 分钟而决定干脆浪费两小时”。

而真正有严格时间要求的 event 本就在 Google calendar 里，在 notion calendar 里能方便地通过不同颜色区分。

![某一周的 notion calendar，黄色为 Google calendar 事件，绿色为 notion daily quest database](https://media.douchi.space/douchi/media_attachments/files/112/069/809/249/353/212/original/152cce41cc782225.png)

当然，时间管理只是工具，不坐在电脑前的时候我也不会把所有事情都在 calendar 上标记。这个系统更多地是提供指导和规划，而非增加严格记录的 overhead。这也只是我摸索出的适合自己的方法，不一定适合所有人。希望大家都能找到适合自己的方法，也欢迎大家分享自己的相关技巧。