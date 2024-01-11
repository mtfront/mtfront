---
title: 我的豆瓣书影游替代又一次尝试：Notion 精神仓库
author: 椒盐豆豉
type: post
date: 2022-04-28T04:29:15+00:00
url: /douban-notion-backup/
ig_es_is_post_notified:
  - 1
categories:
  - 喜欢就买
  - 重启电脑
tags:
  - project
  - tutorial
  - 复盘
bookToc: false
---

## [先放链接：椒盐驼鸟的精神仓库](https://www.notion.so/2485c762efe040b988531aaa3e45ad25)

内容由我手动更新 + 豆瓣同步（感谢[竹子的这篇教程](https://zhuzi.dev/2021/06/05/douban-backup-sync-notion/)），豆瓣同步的部分[有做过轻微修改](https://github.com/mtfront/douban-backup)适应我自己的需求。暂时有如下功能：

- 除了书、影、游之外还暂时加入了 hiking trail review
- 自动同步我豆瓣标记读过、看过、玩过的条目评分、短评、标签和封面等信息
- 手动维护的 hiking trail review
- 每个条目有如下一些 tab
    - 按时间顺序排列的 gallery（最近读/看/玩/走过）
    - 推荐条目（按评分和打分时间排序）
    - 不同分类（如影视有 Netflix、纪录片、华裔、单口等主题，游戏有主视角、俯视角、像素风等，方便查看分类推荐）
- 不同分类折叠，方便跳转


大体长这个样子：
<!--more-->
{{< columns >}}
![](https://s3.nl-ams.scw.cloud/mtfront-blog/2022/04/Screen-Shot-2022-04-27-at-9.12.19-PM.png)
![](https://s3.nl-ams.scw.cloud/mtfront-blog/2022/04/Screen-Shot-2022-04-27-at-9.20.38-PM.png)
<--->
![](https://s3.nl-ams.scw.cloud/mtfront-blog/2022/04/Screen-Shot-2022-04-27-at-9.20.17-PM.png)
![](https://s3.nl-ams.scw.cloud/mtfront-blog/2022/04/Screen-Shot-2022-04-27-at-9.21.12-PM.png)
{{< / columns >}}

在之前无数次的豆瓣逐步收紧审查之中已经无数次考虑过备选方案，但最后都没有实施。其中包括但不限于如下选项：

- 使用 IMDB、Goodreads 等替代平台——没有很好的中文条目支持，而且没找到比较普遍的书影游能集中记录的平台
- [NeoDB](https://about.neodb.social/doc/howto/) ——由之前不开放注册的 NiceDB 而来，可以方便地导入导出，几乎满足所有需求。我没有继续用下去的两点原因是：
    - 需要登录才能查看条目，不方便跟不适用长毛象等 fediverse 的朋友分享
    - 是像我们一样靠着热情为爱发电的网友支持运作的中心化平台，虽然能方便地导入导出数据但毕竟控制权不在自己手上，也不像大公司一样稳定，我对其 longevity 略有 concern
- 使用 Notion 搭建自己的书影游数据库

其中各种导入 notion 的工具早在 2020 年就出现了不少，相比其他两种方式有如下优点：

- 可以随意 customize，自己控制权更大，内容不限于书影游，各条目里也可以添加短评之外的内容（如链接、图片等），甚至可以用动态 gif 做封面
- 可以设置多种排序、filter 功能
- 方便没有账户的用户无需登录查看
- 数据库可以导出，也有开放 API
- 产品较为成熟，longevity

我没有更早开始用这个方法的原因是：

- Notion 的 performance 一直被诟病，数据库一大就卡得没法用
- 虽然有各种导入工具，但是手工整理工作量还是较大
- 手动添加条目较为麻烦

这两天豆瓣开始停止支持海外手机验证，离实名验证估计也不远了，造成了新一波迁移热。不过这并不是促使我迁移的原因（我也忘了为什么我现在决定迁移），只是刚好赶上了这个档口，其实拖了很久早想做了，外加 notion 这两年也确实改进了 performance 大数据库没有那么卡了。

按照[竹子的这篇教程](https://zhuzi.dev/2021/06/05/douban-backup-sync-notion/)拖延了一阵之后才按照我的数据库结构 debug 好了 workflow，做了相应修改，后来又拖拖延延几天才手动添加了 trails 和给评分较高的条目加了标签，手动调整了封面等等。

结果刚修好 workflow 豆瓣就整这一出。以后豆瓣要是完全不能用的话修改一下代码从 NeoDB 自动同步应该也不会太难，暂时就先用豆瓣吧。（不过自己做 side project debug 的时候真是比上班快乐多了



{{< details "Migrated Comments" open >}}

### Comment by Elizen on 2022-05-03 08:07:47 -0700
抄了一份，还差之前读过的书和电影的海报没弄进去。非常感谢。

### Comment by Elizen on 2022-05-04 04:56:30 -0700
又来了，咨询个问题。新的内容，我通过你的 Github Action 都搞进去了，但是之前的所有电影和书的资料，参考竹子的脚本，无法下载下来海报，有什么办法能把之前的海报搞下来么？

### Comment by 椒盐鸵鸟 on 2022-05-04 11:13:45 -0700
我没有计划 backfill 我之前的数据所以就没改这块。可以去她的原文里找到 GitHub repo 给她提 feature request。

### Comment by Elizen on 2022-05-04 23:05:02 -0700
好的，感谢。

### Comment by bo on 2022-07-05 07:05:39 -0700
請問是每一條都自己加封面嗎？

### Comment by 椒盐鸵鸟 on 2022-07-18 19:40:02 -0700
是 workflow 自动从豆瓣拉取的，代码在这里 <a href="https://github.com/mtfront/douban-backup/blob/main/sync-rss.js#L441" rel="nofollow ugc">https://github.com/mtfront/douban-backup/blob/main/sync-rss.js#L441</a>

### Comment by jules on 2023-04-30 04:40:21 -0700
来考古了（鞠躬）想请问一下椒老师在使用rss更新之前的数据的海报是手动加进去的吗？（上面回复的workflow是在更新数据的时候加的海报）

### Comment by 椒盐豆豉 on 2023-05-07 21:26:49 -0700
是文中提到的教程里的脚本里拉的 <a href="https://zhuzi.dev/2021/06/05/douban-backup-sync-notion/" rel="nofollow ugc">https://zhuzi.dev/2021/06/05/douban-backup-sync-notion/</a> 但是那个脚本是放封面图而不是 content cover 不大符合我的偏好，所以它一次性拉完之后我又手动挪了一部分
{{< / details >}}