---
title: 迁移 Object Storage 时候发生的一些愚蠢事件以及解决方案
author: 椒盐豆豉
type: post
date: 2022-01-23T08:39:28+00:00
url: /migrate-object-storage/
ig_es_is_post_notified:
  - 1
categories:
  - 重启电脑
tags:
  - debug
  - mastodon

---
# 迁移 Object Storage 时候发生的一些愚蠢事件以及解决方案
TL;DR: 我用 rclone 迁移 object storage 的时候脑一残就把目的 bucket access 设成了 private，导致迁移之后长毛象无法访问新的 bucket 所有媒体文件都无法显示，最后只好使用 s3cmd recursively set public acl 了一遍所有媒体文件。

对事情经过不感兴趣想直接看的请点此直接跳转到 [Debug 步骤](../migrate-object-storage/#debug)和[解决方案](../migrate-object-storage/#solution)部分。

## **事情是这样的**

我之前 Mastodon 实例用的 object storage 是 scaleway，每个月每个 bucket 头 75G 免费非常适合各种小站诸如 mastodon，博客之类的。但问题是这个免费服务似乎隔三差五就 desync（我不是特别了解 object storage 底层逻辑就不瞎解释了），新上传的媒体无法被稳定访问。之前我是能忍就忍，几个月找一次客服的频率凑合。后来听说巴黎区比我一开始所在的阿姆斯特丹区稳定一些，[就迁移了过去](https://blog.douchi.space/?p=1301)。几个月相安无事没管这事。

但是前阵子这个老毛病又来了， 去年底我去欧洲玩的时候就被坑过一阵，前两天它又回来了。一怒之下我决定换服务。

先前[云五老师已经把驴肉火烧的媒体服务迁到了 S3](https://yukieyun.net/tech/mastodon-media-from-scaleway-to-aws-s3/)，S3 自然是以 availability 和 reliability 闻名，但是后续听说价格较贵，外加我几年前没用已经忘掉了的 EC2 欠费了我上次想迁移的时候付清了欠费居然又再次被关账户了，懒得再来回折腾。在 Linode 和 Digitalocean 之间犹豫了一下，前者新用户 $100 credit 以为能用 20 个月，注册之后才发现两个月 expire，遂一怒之下还是在服务器同托管商 digitalocean 加开了 object storage。

本来按照我自己[上次的迁移笔记](https://blog.douchi.space/?p=1301)顺顺利利跑了好几天 rclone，今天想说洗澡看电影前顺手 switch 了吧免得得一直 sync。结果 sync 了之后各处 credential 检查了半天也还是无法显示图片。

## **Debugging**

1. 没过几分钟我发现新传的图可以正常显示，头像、emoji、旧的媒体文件全部无法显示 -> 这表示从 mastodon server 到新的 digital ocean spaces 的 config 没有问题
2. 在 browser 里 inspect element 找到不能显示的媒体的地址，复制粘贴这个地址（我长毛象的 proxy 地址）打开，发现是 access denied （不是 404）
3. 在新的 storage 里找到对应的文件，发现文件存在，代表同步是成功的
4. 直接复制 storage 里文件的绝对地址打开，发现也是 access denied
5. 查看该 object access，发现是 private
6. 查看该 object 旧 bucket access，发现是 public

到此，元凶找到了，是我在[用 rclone 迁移](https://www.scaleway.com/en/docs/tutorials/migrate-data-rclone/)的时候，第 9 步选择 ACL 用了默认的 private 而不是 public-read。

## **Solution**

这里有两个解决方案:

1. switch 回旧的 bucket，重新 rclone with right access，再 switch back
2. 想办法改 access

因为 1 同步起来要好几天， 还要来回改设置，实在是太懒了，于是开始 2：

1. Google s3 set folder public，发现 S3 没有原生的 bulk set permission
2. 按照[这篇 stackoverflow 回答](https://stackoverflow.com/questions/52697745/how-to-change-all-the-folder-files-permission-private-into-public-in-digital-oce)，参考[这一篇教程](https://docs.digitalocean.com/products/spaces/resources/s3cmd/)在本地安装 s3cmd
3. 使用 `s3cmd setacl s3://spacename/path/to/files/ --acl-public --recursive` 把所有文件设成 public-read

期间还遇到几次 `S3 error: 404 (NoSuchKey)` 导致中断的情况（明明 skip 就好了为什么要中断这什么鬼设计），于是先分 bucket 把最重要的本地头像、emoji 和媒体同步了，站外 cache 同步了一部分随缘吧，以后线上看到看不了的再手动设置。

## **Takeaways**

1. 仔细看文档，不要瞎设 access
2. 不要一时偷懒就把 script 装在笔记本上，当时放在 server 上啥事没有也不用在家里费电
3. S3 这么成熟的产品居然没有 native support bulk ACL setting!!!! 然后就出现了如下地狱情况：

![](https://media.douchi.space/douchi/media_attachments/files/107/670/384/957/879/105/original/4e655ce5b057b509.png)

谁能想到酒足饭饱挂着电话陪瓜片赛博睡觉（？）然后打算悠闲地看个电影的周六夜晚我实际上在 debug object storage & download s3cmd & 手贱图方便在笔记本上直接装了所以现在眼巴巴地等着 30 万个 object 被 set acl-public……

---
{{< hint danger >}}
如果您觉得本文对您有帮助，想支持我的博客创作，或者有特定的内容想要看到，或者干脆就想单独聊五毛钱，欢迎点击下面按钮成为我的金主：
{{< /hint >}}
{{< button href="https://www.patreon.com/bePatron?u=46962965" target="_blank">}}成为 Patreon 金主{{< /button >}}
{{< button href="https://ko-fi.com/S6S130C16" >}}在 Kofi 上给我买杯奶茶{{< /button >}}