---
title: 建站三年了我可终于把长毛象服务器给迁移了
author: 椒盐豆豉
type: post
date: 2023-12-22T19:37:00-08:00
url: /mastodon-migration/
categories:
  - 重启电脑
tags:
  - mastodon
booktoc: false
image: https://blog.joinmastodon.org/2018/08/mastodon-quick-start-guide/vlcsnap-2018-08-27-16h43m11s127.png
imageDes:  "image from Mastodon quick start guide https://blog.joinmastodon.org/2018/08/mastodon-quick-start-guide/"
---

转眼间我的长毛象实例豆豉站已经建站三年多了。期间在云服务商内部一键升级过几次服务器，也原地涨价了不少次，但性能还是捉襟见肘。看到站友们安利的便宜大碗的服务器眼馋了好几次，都因为懒一直在拖延。除了性能瓶颈之外，之前服务器系统也逐渐跟新版长毛象的很多 dependency 开始冲突，每次升级都要手动修复，甚是麻烦。前阵子终于 pull the trigger 一鼓作气迁移了服务器。现在稳定运行了十来天来写个小记吧（不是教程）。

<!--more-->

## 建站
当年因为[豆瓣背井离乡事件]({{< relref "/posts/2023-archive/2020-12-23-douban-exodus-14-pixel-avatar" >}})与一大波友邻一起退瓣迁移到了草莓县，随后又因为部分县民排外一怒之下自己建了实例。

当年在气头上外加完全没有 fediverse/mastodon 使用经验，所以也没有做过多调研，就按手头站友写的[小白建站指南](https://pullopen.github.io/%E5%9F%BA%E7%A1%80%E6%90%AD%E5%BB%BA/2020/07/19/How-to-build-a-mastodon-instance.html?utm_source=blog.douchi.space)照猫画虎全盘照搬，直接在 DigitalOcean 上建了站。

## Object Storage 的折腾史
第一次大的迁移应该是挪 object storage。因为一开始抱着先试试看的心态没挂 object storage 就直接用的服务器 SSD 存储媒体，不停清除缓存还是很快耗尽，于是建站不久就按站友的推荐迁到了 Scaleway。它的前 75G 免费，对于我这种小站来说还蛮划算的。

不过便宜没好货，用了没几个月就发现 Scaleway 的服务不大稳定，尤其是荷兰区毛病很多，于是没几个月我就[从荷兰区迁移到了巴黎区]({{< relref "/posts/2023-archive/2021-02-25-scaleway-object-storage-unstable-mastodon-migrate" >}})。

好景不长，用了不到一年老毛病又来了，我一怒之下就把 object storage [从 scaleway 迁移]({{< relref "/posts/2023-archive/2022-01-23-migrate-object-storage" >}})到了跟服务器同供应商的 Digital Ocean。外加之前服务器在美国 object storage 在欧洲本来就速度有影响，现在到了同个区，媒体载入快乐不少。于是就这么快乐稳定地使用了两年，直到现在博客和豆豉站还都用的是 Digital Ocean 的 object storage。虽然 DO 的 object storage 要 5 刀一个月，但稳定使用至今从未出过问题，不禁让人感叹这钱还是花得很值的。

## 迁移动力
DO 是提供了预装 mastodon 虽然少了些 setup，但价格并不算优惠，这几年来涨了几次价之后逐渐离谱，服务商内原地升级了几次之后愿意承担的服务器性能也在日常使用面前捉襟见肘。

这次迁移前价格已经来到了 $18/month，而这只是小小的一个 2vCPUs 2G RAM 60G SSD 的服务器而已。2G 的 RAM 跑月活几百人的长毛象小站还是有点吃力，虽然加了 4G swap，但 timeline building & database 读取速度都很慢。要是再碰上点大用户迁移之类的 incident，服务器卡到 2G 网络年代，十分不爽。运行一段时间（一两周）基本就要重启一次服务，不然就会越来越卡。

除此之外，因为本地硬盘只有 60G，虽然媒体挂在 object storage 上，但本地数据库、swap、dependency、系统等所占空间还是长年累月增加，硬盘利用率已经在 90% 往上了，有时候升级下 dependency 都会空间不足。再继续使用不迁移的话，估计扩容也不远了，下一档月费 $24 又是一年多了几顿饭的开销。

此外 DO 当年预装 mastodon 的服务器还系统版本还在 Ubuntu 18.4。这些年随着 mastodon dependency 版本的更新，越来越多 dependency 跟 18.4 不兼容，需要手动调整绕开，升级体验不如以前顺滑了。上次 从 3.x.x 升级到 4.x.x 大版本更新的时候就折腾了老半天，导致现在 minor version 更新得也没以前勤快了。

## 选购服务器
中间也有不少次看其它站长安利便宜大碗的服务器动心好几次，一直因为懒在拖延。前阵子看到[博友安利供应商促销](https://t.me/FindBlog/352)发现价格真的差好多，外加我现在不在 revenue org 了年底工作量非常不饱和摸鱼划水了好久了，索性一鼓作气准备迁移。

一开始先考察了博友推荐的 CloudCone。确实便宜大碗，跟我现在一样配置（还大 40G SSD）的 VPS 只要 $26 一年，是我现在的 $216 的 1/8 不足。因为之前就性能不足，迁移的话象顺便加点配置，加到 4核 4G 也还是不足现在成本的 1/4，非常诱人。但之前被便宜没好货的 scaleway 折腾怕了，就去多看了看服务器测评，发现他们之前升级系统的时候似乎不大稳定，因此评分没有很高。大概也是小供应商，也很难在各大最佳 VPS 榜上见到，就多了一些顾虑。毕竟长毛象是大家的电子吊瓶，一会儿不刷就心慌，availability 要求还是比博客等私人用使用场景高一些。

搜测评的时候看到了之前被很多长毛象站长推荐过的 contabo，倒是评分高了很多。价钱也挺便宜，最便宜的 VPS 4v 8G 一年也就 $80 不到（它价格页面上写的是欧洲服务器的价格，美国区会加一点），CloudCone 没有完全一样的配置但这个配置介于 4v4G 和 6v8G 价格之间，也贵不了太多。无论如何都比我现在的便宜多了，CPU 和 RAM 都 double 了价钱只是 1/3 多一点。象上用得人多也稍微放心点，也在各大横评网站会得一些前几。遂激情购入一年。

买完登入服务器管理页面我突然能理解一点为啥这么便宜了。DigitalOcean 就是那种正常的现代的 GUI，而且能在网页上直接看服务器的性能 metrics 非常方便，之前还用过 AWS 和 Google Cloud 虽然没那么好看但也算是 2010s 的设计风格吧。Contabo 价格和宣传页面倒是挺现代，一进去服务器管理页面里立刻回到了上世纪九十年代。metrics 我也是至今没去找。不过反正服务器比以前大得多，性能 metrics 倒也不不用太过关注。

## 迁移
迁移本身过程比我想象中的容易多了，甚至感觉比升级还容易（毕竟自己的站有一些改动，每次升级还要处理 merge conflict）。顺着教程没碰到什么太大的问题一天（大多数时间在备份和转移数据库）解决。导入完数据库之后 DNS 改之前我还将信将疑这能好吗，没想到更新了 DNS record 之后丝滑上线了，甚至连之前升级常出的小岔子都没有。

新上线的豆豉站丝般顺滑，我仿佛从学生时代卡卡的笔记本打游戏瞬间升级到了工作之后买的高配 PC。之前看有站友说可能平均每个月会抽那么半小时风，在目前的十天运营中暂时也还没遇到过。另外现在性能有 head room 了，或许晚点有心情了能整点别的小服务。

花 1/3 的钱买了更好的服务，现在感觉就是一个值字。虽然日常工作是程序员，但我对技术本身没兴趣，不会以折腾为目的而折腾，一切实用优先。今年建站方面两个大折腾，一[从 Wordpress 迁到静态站]({{< relref "/posts/2023-12/1-static-blog-half-year" >}})，二是长毛象迁移服务器，都大获成功，非常实用，真不错。


