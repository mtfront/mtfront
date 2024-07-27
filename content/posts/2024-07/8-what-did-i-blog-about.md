---
title: 我的博客都写了些什么
author: 椒盐豆豉
type: post
date: 2024-07-26T23:22:00-07:00
url: /what-did-i-blog-about/
categories:
  - 不行就分
tags:
  - blog
  - 复盘
  - 问卷
booktoc: false
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/112/856/867/081/692/285/original/fe6d3b44d9ef71b7.png
imageDes: "当年像素画 100 天项目后期画的《Witcher 3》像素图"
---

前些天在[土木坛子](https://tumutanzi.com/archives/17322?utm_source=blog.douchi.space)看到把博客文章标题扔进 AI 做总结的点子感觉不错，想效仿一下。虽然说这个博客只有近几年写的内容，远不能代表我 20 年的博客史，不过遗失在 blogcn、网易、新浪、校内/人人、知乎、豆瓣的一些旧文从少年不知愁滋味的矫揉造作到半瓶子晃荡的大放厥词也不少，丢了真是一点都不惋惜反倒庆幸呢。现在这个博客建于 2020 年从豆瓣出逃之时，补档了一些近些年写过的文章，算是前额叶发育完全后比较有代表的思绪了。
<!--more-->

拿前阵子写的[博文列表]({{< relref "/posts/2024-05/8-blog-decoration-3" >}}#装修)中提到的短代码稍作修改，即可产生一个方便复制粘贴的标题列表：

```Go-HTML-Template
<ul>
  {{ range (where .Site.RegularPages "Type" "post") }}
      <li>{{ .Title }}</li>
  {{ end }}
</ul>
```

然后扔进 chatGPT 里，得到了下面的总结：
> 1. 旅行：记录公路旅行 ~~、海岸线游览~~和~~国家公园~~游记。
> 2. 博客搭建：分享使用Hugo创建和美化独立博客的经验。
> 3. 读书：介绍读书心得和书籍推荐。
> 4. 理财：讨论个人理财~~和订阅服务管理~~。
> 5. 健康与健身：记录健身、断食和健康检查。
> 6. 游戏：评测和推荐~~独立~~游戏。
> 7. 职业：记录码农生活和职业发展。
> 8. 评测：评测科技产品和~~户外~~装备。
> 9. ~~反思~~：分享日常生活~~的反思和自我提升~~。
> 10. ~~创意与DIY~~：探索~~简笔画、~~ 像素画~~和DIY项目~~。

基本大差不差，但感觉和人工分析还是有一定差距，为了避免太误导人划掉了些离谱的。让它按频率排序似乎也不怎么靠谱，明显偏重较近期的文章。再比如游戏不仅仅是独立游戏，“反思”那一条也大可不必，我这么不喜欢 grow 的人自我提升什么呀（但不排除是 clickbait 标题误导了 AI 🤣），改成“生活”更恰当一些。最后一条就更离谱了，像素画就算了（题图就源自出圈了的那篇 [100 天像素画]({{< relref "/posts/2023-archive/2020-08-09-100-days-of-pixel-art" >}})），我这么手笨的人几时搞过简笔画和 DIY 项目了，博客全文搜索都找不出 DIY。即便是 GPT-4o 和 AI 擅长的总结项目，感觉还是离能代替人类很远呐。

偶尔会在不同博友那里看到对我的介绍是“生活丰富多彩”的博主，但其实看我写的东西感觉都挺俗的，没看出哪里多彩了。甚至看这个结果自从换了静态博客之后还不幸沦为 AI 眼中的装修博主了（没有贬低装修博主的意思只是我不想当装修博主而已）。反倒是 [telegram 剪报频道](https://t.me/mtfront)的内容稍微丰富些，但感兴趣的内容未必都有足够积淀能写博客。

最近半年失业写博时间增多，第一次出现了很多“想写博客但不知道写啥”的状态，backlog 里有一堆备选但感觉都是自己翻来覆去说的话题也没有那么大动力写，总想发掘点什么新奇有趣的话题。让 AI 一总结，确实验证了我翻来覆去就写那么点俗东西的自我印象。

说到这儿就有了两个问题：
- **读者中的博主们平时都写些什么呢？** 要是有兴趣总结欢迎当问卷传下去写成自己的总结或者留言，也当给博友们的写作提供点新思路了。
- **读者们想看我写点什么呢？** 当然每个月都还是有 [patreon 投票](https://www.patreon.com/posts/2024-nian-8-yue-108440104)，但受众显然小了很多，外加选项都是我自己出的也很难跳出思维定势。虽然有高级金主命题选项和有一次开卷让大家评论，但总共也就写过那么两三篇自由命题。读博客的人应该比看到 patreon 的人多多了，欢迎留言提供思路。