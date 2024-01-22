---
title: '我的信息摄入 & 读书 tracking workflow'
author: 椒盐豆豉
type: post
date: 2021-01-23T03:02:53+00:00
url: /information-consumption-reading-tracking-workflow/
categories:
  - 喜欢就买
  - 重启电脑
tags:
  - patreon
  - productivity
  - tutorial

---
本篇为[本月 patreon 金主们选出来的题目](https://www.patreon.com/posts/45913724)。

其实我算是信息 consumption 比较没有条理的人，绝大多数时间都是想到哪看到哪，这些年也没怎么深挖过各种 GTD workflow。去年底[把个人项目管理迁移到 notion 上的时候](../2020-side-project-recap/) 想说再给 notion 一个机会试用一下，经过几周的整理觉得效果不错，所以渐渐也开始轻度整理一下自己的 information consumption workflow。

毕竟，过去太多的东西看过就忘了，没有一个系统性内化沉淀的过程看了也受益程度有限。更何况信息 overflow 的年代没有良好的信息 consumption workflow 的话有很多好东西容易错过，比如永远“收藏了不看”的内容平台内收藏夹。

## **平台原生解决方案的弊端**

可能很多人都有的一个习惯是，“收藏过了等于看过”，于是收藏夹里那些“留着以后再看”的东西就真的就从来没有再看过，不知道错过了多少有趣有用的信息。我反思了一下可能有如下原因：

- 各平台收藏夹 surface 形式不同，查阅不方便。比如豆瓣的收藏夹就藏得很深，手机端至少要经过“我的 -> 我的豆列/收藏 -> 豆列 -> 选择合适豆列”才能开始浏览，而且豆列的排序也非常谜，打开基本上看不到想看的内容，就打消了一大半用它来吸收、反刍信息的欲望。
- 各平台收藏夹内容功能的欠缺。就不要求有 tag，reminder，分类这种高级功能了，就连简单的“已读/archive/favorite“这一个信息 consumption 流程绝大多数平台都没有。再拿豆瓣举例，我要到达上述目的至少需要”在收藏夹阅读->区分’以后有用的资料性’或’看过一次就好的消耗性’内容 ->把已读内容加到已读/favorite 收藏夹 ->从旧的收藏夹移除“这一系列麻烦的步骤。不整理的话，久而久之收藏夹就会被 overflow 而减低以后的阅读效率。
- 有太多平台信息零散不能一次看完，就像要 maintain 多个投资账户一样有很多 overhead，每个平台都单独看一遍收藏夹的话费时费力效率低。
- 各平台收藏夹 implementation 不一样，比如豆瓣收藏夹是乱序的，youtube 的 watch it later 居然是正序的且看完也不自动清除，大多数 social network 的收藏夹又是正序的等等，一起浏览起来非常混乱。

## **我现有整合方案**

### **网文/视频整合 – Pocket**

解决上述原生平台收藏系统弊端的方法自然是用第三方的、专门用来收藏整合信息的 app 了。我目前使用的 Pocket，没有做过横向对比不知道优缺点，但暂时觉得它还算好用。
{{< columns >}}
![](https://douchi.sfo3.digitaloceanspaces.com/blog-scw/2021/01/uri_mh1611363816220-473x1024.jpg)
<--->
![](https://douchi.sfo3.digitaloceanspaces.com/blog-scw/2021/01/Screenshot_20210122-170007-473x1024.png)
{{< / columns >}}
整个环节中最关键的一点是，加连接方便。在手机端，装了 pocket app 之后在系统层面的 share 选框就可以 add to pocket 了。开了剪切板权限的话，如果剪切板里复制了连接，打开 pocket app 还会询问是否将剪切板里连接也加入收藏。加入之后还可以简单编辑 tag 等。在电脑端我没有装 app，chrome 插件可以方便实现类似操作，点击将当前网页加入收藏，右键单击可选择打开 pocket 主页面进行浏览。

基本上所有文字平台和 YouTube 上的”晚点再看“我都会加到 pocket 里。（Youtube 自身的 watch later 实在是太难用）

在收藏夹内我使用最多的是 archive 和 favorite，tag 倒是没怎么用过。archive 就是读完文章之后 archive，保证主页面永远是没看到过的。favorite 自然就是读完觉得好和将来可能会用到的。

### **读书记录 – Read More + Notion + 豆瓣**

之前读书只有开始读和读完会在豆瓣上记录，久而久之尤其碰上比较难读的书会进度缓慢甚至偷懒就搁置了。

### **Read tracker – Read More**

在长毛象友见一下找了个 reading tracker 现在用了快两个月，读书效率大增。手机端类似的 app 很多，我随便搜的这个是 Android only 的，但 iOS 上应该也有类似。我用的这个叫 Read More，是个独立开发者的小项目，我的用法如下：

- 加书方便， Google books 的数据库，实体书直接扫码电子版搜名字，目前读的两本（一中一英一实体一电子）都是一下找到毫无压力。
- 每本书加到在读之后有 goal tracking、进度、highlight、quote 等。这样每天为了达成目标拒绝偷懒拿出来读一会儿目的就达到了。
- 内置 tracker 直接记录时间 + 进度、也可以读完自己手动加。我一般是开始读书就打开 timer。
- 我本来在用内置的 highlight 功能，后来发现导出不太方便（只能 pdf，跟作者写了邮件 feature request 导出 notion 作者回了说等 notion API 出了 beta 就加，所以不知道什么时候能加上），于是现在全面改成自己用 notion 做了一套模版做读书笔记。

{{< columns >}}
![](https://media.douchi.space/douchi/media_attachments/files/105/327/053/309/495/237/original/9b73fe528e0a43cc.png)
<--->
![](https://media.douchi.space/douchi/media_attachments/files/105/327/058/471/705/086/original/5e85d4d5b9cb8d37.png)
{{< / columns >}}
### **读书笔记整合 – Notion**

读书笔记散落在各平台的话其实跟没记一样，将来写读后感的时候也很难快速找到。在去年底启用 notion 整理个人项目比较成功之后又拿 notion 做了一个读书笔记 tracker。

![](https://douchi.sfo3.digitaloceanspaces.com/blog-scw/2021/01/Screen-Shot-2021-01-22-at-6.19.01-PM-1024x830.png)

{{< columns >}}


![](https://douchi.sfo3.digitaloceanspaces.com/blog-scw/2021/01/Screen-Shot-2021-01-22-at-6.22.14-PM-751x1024.png)
<--->
大体框架的结构放在一个 DB 里，以书为单位，大致按阅读状态（在读和读完分类）分类，并加了一个 calendar view。首页显示类型、我的评分、平台和我的阅读时间这些我认为比较重要的内容。

展开每本书页面之后有更详细的信息，诸如阅读的起始和终止时间（起始跟豆瓣记录有冗余，但方便我在 notion 里排序），作者，语言等。

页面的正文内容就是我的读书笔记了，这是一个 inline table。根据平台不同会有细微差别，但大体上有四列：
- 位置：页码、章节、Kindle 笔记的 location 等
- highlight：原文 quote，如果是实体书的话是我手动录入，微信读书和 Kindle 的话就是 app 里高亮部分，各有导出方法
- Note：我当时的笔记和感受
- Image：如果有重要的图会拍下来在手机里传上来
{{< / columns >}}


关于平台导出，微信读书自带导出可以复制笔记到剪切板 markdown 形式，我太懒的话不会一条条整到 notion table 里，整段粘贴进来能看就行。Kindle 则是在 https://read.amazon.com/notebook ，懒的时候全文复制，勤快的时候就整合到 notion table 里。

此外 Kindle 我还用过连接 readwise 导出到 notion 的功能，但没有继续用。原因一是这个 app subscription 比较贵，我 Kindle 撑死一月一两本主要阅读平台并不在 Kindle 上，所以单独为这个订阅不划算。二是它导出的格式也是 plain text，没比网页直接复制强太多。对于大量在 Kindle 上阅读的人来说或许订阅自动同步有用，但对我来说比较鸡肋。反正它有 free trail 大家可以试试。

### **宏观阅读记录 – 豆瓣**

虽然弃了豆瓣的社交功能，不过我个人的书影游记录还是在豆瓣上的。一来“想读”标记比较方便，二来有些轻快度过没有读书笔记的书不会在 notion 上有记录减少 maintainence overhead 所以用豆瓣作为宏观补充，三来也有文化产品的集中 consumption，四来写书评跟别人安利比较方便。不过豆瓣数据说没就没，所以读书笔记这种比较难备份迁移（插件时好时坏）的东西就不在上面放了。

### **其他形式的笔记**

### **知识性整合 – Notion**

因为 notion 的 toggle list 便于整理而不被细节 overwhelm，所以平时吸收知识的笔记我也逐渐迁移到 notion 上了。

笔记的分类用 nested page 来管理，各 page 内部全是 toggle list，方便快速定位不被信息 overflow 的同时，能快速 dive into details. 比如图片、具体 instruction、source 之类的我都会扔到 toggle 里平时折叠起来，需要时候再展开。

话说，toggle list 这么简单、好用、极度提高生产力的东西为啥还没有被所有笔记软件推广，费解。

![](https://douchi.sfo3.digitaloceanspaces.com/blog-scw/2021/01/Screen-Shot-2021-01-22-at-6.43.46-PM.png)

另外，其实刚才的读书笔记那一页除了读书笔记之外，我还有结构类似的“视频”笔记，觉得有价值的视频也会以相似的结构记录下来，当然单页的结构比较简单没有评分、阅读时间之类的栏目。善用 toggle list 不至于过目即忘当作消遣。

![](https://douchi.sfo3.digitaloceanspaces.com/blog-scw/2021/01/Screen-Shot-2021-01-22-at-7.01.57-PM-861x1024.png)

### **简单文字速记 – Simplenote**

Apple notes 虽然满足需求、功能够多也够轻量，但是致命缺点是不跨平台。作为速记我需要在任何平台都能查看，而我现在手头用的平台就有 Mac, Android, iOS, Windows 等。另外，需要离线 access，所以排除诸如 Google Keep（而且便签形式我真的用不惯）。最好的替代品目前用过的只有 Simplenote 了，同步够快，够轻量。唯一的缺点是不能插图片。

### **Todo List – TickTick**

被豆瓣友邻推荐的，简单轻量省心 get things done. 配合 Android notification widget 用也非常快速。

不过我用它仅限于快速轻量的 todo （比如”明天填这个表“），对于比较大的需要花时间的项目（比如”写这个文章“、“画这个画”、”做这个项目“、“研究这个东西”），我还是会放在 [notion backlog](../2020-side-project-recap/) 里，否则因为要花时间不能一下做完，放在线性的 todo list 里只会一直 snooze 根本没法 track，最后 todo list 也 overflow 了，事情也没做。至于 personal backlog is a topic for another day.

## **Reflect**

只记录不 reflect 的话信息还是不会内化到脑子里。我现在基本上觉得对自己有价值的东西都会尽量复盘。具体表现在：

- 书影游短评
- 感触比较深的书写读后感 – 这个时候之前 notion 里的读书笔记就派上用场了，轻松浏览一下快速 pickup 当时的感触无遗漏。[去年写了一篇](../book-story-of-art/)，还有几篇在 backlog 里。
- 项目复盘，小的基本零零散散在长毛象和 telegram channel 里，大的都会在博客发布。

## **附录 – Inputs**

2019 年反送中之后就不上微博了不然要友尽一堆人，2020 年豆瓣审查丧心病狂之后也背井离乡不怎么上豆瓣了，现在的主要信息摄取集中在如下几个平台：

### **Mastodon**

我的主要社交平台，由于屏蔽、静音、过滤功能完善而且毕竟是个比较小众的自选圈子，并且我自己自建实例的内容多少跟我偏好和本身的网络社交圈相关，所以刷起来体验比以前上豆瓣天天生气预约太多了，用象友潘潘的话来说有种精神领域移民的感觉。至于还不熟悉 mastodon 的朋友，可以参见云五老师这篇[为什么要使用长毛象？长毛象(Mastodon)怎么玩？](https://yukieyun.net/nonsense/mastodon-benefits-and-how-to/)

### **WomenOverseas**

之前豆瓣友邻建的女性论坛，由于友邻的热心经营和本身的受众群，论坛氛围非常好讨论质量很高，也经常搞一些交流信息、生产内容、社交互动的活动。

### **书**

现在主要集中在实体书、微信读书和 Kindle store 上，阅读平台主要是 [Onyx Boox Nova 2](../oynx-boox-nova-2-in-between-kindle-and-ipad/) 和 [iPad](..//ipad-pro-setup/)。

### **RSS**

各处（主要是长毛象和之前豆瓣上）搜寻来的独立博客。

### **YouTube**

我的首页基本充满了电子产品、车、游戏测评，偶尔会有一些人工智障算法乱入有意思的内容也会看看。

### **Netflix**

我是 Netflix 的脑残粉，被动 explore 相比“听了推荐再去主动找资源/订阅相应频道“的好处是很多以前不会被大规模传颂营销流行的优质节目能被动动遥控就看到，尤其是纪录片/剧这种根本不会传到中文营销圈的东西，没有订阅的话肯定错过 99%。本来想简单写一下，不过一写就已经能单独成篇了，请移步[我看过的 Netflix 上的错过可惜的“冷门”佳片](../netflix-hidden-gems/)。

### **Reddit**

经过几年的培养之后现在主要是刷首页推荐已经足够看到想看的趣味视频、糗事、萌宠之类的娱乐性内容了。

### **Twitter**

基本上是我关注的画手和游戏开发者，有关注少量朋友。

### **Instagram**

前两天发得很多，这两年非常少发了，顶多是 story 晒猫。随着人工智障算法愈演愈烈 feed 也很少看了，主要是看朋友们发的 story 了解一下大家最近在干嘛。应该也是我现在唯一在用的主要跟现实中朋友社交的平台了，基本是当朋友圈用。

### **Artstation**

[隔三差五上去看看原画发掘一下大触](../artstation-intro/)。比起来别的平台信噪比太低了。

### **Telegram Channel**

非常偶尔没得看了蹲厕所才会去看看。我个人不太喜欢 TG channel 这种既不适合分享长文、信噪比又低、又反馈互动较弱的“广播”形式。



{{< details "Migrated Comments" open >}}

### Comment by 山月 on 2021-01-23 10:43:13 -0800
两年前尝试过Instapaper与Pocket一起使用，以相比较，感觉Pocket和其他服务之间的集成、连携会做得更好。现在不晓得如何。

### Comment by 椒盐豆豉 on 2021-01-23 11:28:28 -0800
我前阵子也试过 instapaper，也感觉没 pocket 用得顺手

### Comment by bamboobone on 2021-01-23 14:07:19 -0800
立刻去下了个ios版本的 Bookly，准备试用看看这种tracking app是不是适合我。受椒老师的notion格式启发修改了一下现有的读书页面。

### Comment by 椒盐豆豉 on 2021-01-23 17:08:50 -0800
行动力拔群！话说博客建好了也可以经常分享读书安利呀如果都有现成笔记了的话，还蛮想看建筑师/设计师平时看的书的安利的。
{{< / details >}}