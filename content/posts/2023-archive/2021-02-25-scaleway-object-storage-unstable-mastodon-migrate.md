---
title: Scaleway Object Storage 不稳定和 Mastodon 迁移备份笔记
author: 椒盐豆豉
type: post
date: 2021-02-25T23:38:35+00:00
url: /scaleway-object-storage-unstable-mastodon-migrate/
categories:
  - 重启电脑
tags:
  - debug
  - mastodon
  - software engineer

---
我的长毛象实例 douchi.space 一直采用 Scaleway 的 Object Storage，因为它们前 75G 免费，对于这种小服务很划算。但是最近一个月连续发生两次故障，因为是免费 tier 所以客服修复的时间也没有保证。本文记述了故障可能的产生原因、debug 过程、修复方法和以后可能采取的 precaution messures。

## Incident

先叙述一下事件经过，想要直接看解决方案的可以[点此链接跳转](#solution)。

首先造成本站用户两天发图看图全部碰运气这个事的锅在我。第一次出现故障的时候我就做了备份，但是因为客服在一天之内解决了问题所以我就没有启用那个备份。[toot](https://douchi.space/web/@mtfront/105652403331715601)

短短不到一个月，第二次故障又出现了：[toot](https://douchi.space/web/@mtfront/105779854532841128)

这次客服回的慢很多，我又听说荷兰区服务没有巴黎稳定，于是参考这篇 [object storage 跨区迁移教程](https://www.scaleway.com/en/docs/how-to-migrate-object-storage-buckets-with-rclone/)装了个 rclone 开始把本站在荷兰区的媒体迁移到巴黎区的 bucket 上。(aws s3 cli 看了半天文档也没找到如何快速在两个 endpoint 间迁移，怀疑要写 ACL，犯懒弃坑）

怪我高估了这个迁移 script 的性能，想说服务器好说有 20Mbs 的 IO 吧，应该用不了几个小时。结果实际上奇慢无比，跑了几小时基本是 1G/h 的速度，我就有点慌了，才开始用 mastodon cli 清理了一下媒体文件，从本来的 80G 降到只保留一周缓存的 30G 左右。

但为时已晚，rclone sciprt 还在无休止地跑，本站用户发图看图极为不便。于是我今天痛下杀手把 mastodon 挂在新的巴黎 bucket 上了。反正能发新图看新图有些老图看不了总比不能发新的看新的强。截止 2/25 2:40pm PST，这次 incident 总计 impact 两天半，要是上班发生这种事我不被 fire 也得写 COE 了

!https://s.w.org/images/core/emoji/14.0.0/svg/1f926-1f3fb-200d-2640-fe0f.svg

（咦这篇不就是 COE ）感谢长毛象友的包容。

2/26 11AM 更新：时隔 3 天半客服终于回邮件声称解决了，root cause 是“bucket was desynchronized”，以后可以直接拿来当关键词找客服。

## Potential Root Cause

虽然曾在亚麻工作，但我对 object storage 底层原理并不了解，平时也只是拿来就用。因此以下仅为本人推测：

Object storage 管理媒体文件的服务运行不畅（index or cache slow, need fix or restart），因此即使媒体文件即使已经传输到存储空间上，但对外界来说”找不到“这个媒体文件。

作为 object storage 的用户（我），无法直接接触存储服务器上运行的底层服务，因此只能等 Scaleway 方面客服踢给 engineer team 解决。但由于客服对底层服务也不熟悉，一个问题可能有多种成因，因此在踢皮球期间我的媒体服务继续不稳定。

## Impact

我到现在也不是特别确定这次和月初那次是同一个 root cause。具体表现：

期间本站图片可以上传，但上传之后无法显示（图裂）。外站图片也是图裂，但可以点击发布时间到对方的服务器上直接查看（因为裂的只是本站的缓存），但如果对方锁嘟的话便无法用此方法查看（因为去外站相当于匿名用户查看）。

我在后台 debug 则发现在 Scaleway console 里，有时候这个 object 会存在，有时候则不存在。此外 Mastodon sidekiq 里也没有 S3 相关错误，证明图片本身确实被正确上传到了媒体存储上，因此断定是 Saleway 那边的锅，于是发 ticket 给客服。

## Solution

1. 在 object storage 给客服开 ticket，描述问题、问题发生时间，以及提供一两个受此问题影响的 object public link。
2. 清理 mastodon 媒体文件，减少需要迁移的文件数。（我一开始没有做这一步，追悔莫及）
3. 在备份目标放创建一个新 bucket，用[这篇教程](https://www.scaleway.com/en/docs/how-to-migrate-object-storage-buckets-with-rclone/)在自己的任意 instance 上安装 rclone 并备份媒体。
    - 任何 server 都行，但我图方便直接在我运行 mastodon 的服务器上跑了。如果你有 dedicated server 应该可以改改 param 让 rclone 跑得更快。我没有这么做是因为我懒了，并且很后悔……
    - 由于近一个月发生了两次类似事件，我把备份媒体从本来在用的荷兰区换到了据说比较稳定的巴黎区。
    - 记得 access 一定要设成 public-read 不要用默认的 private，[不然会发生悲剧](../migrate-object-storage/)
4. 备份完成（在我这里是接近完成）后，参考[这篇云存储 setup 教程](https://pullopen.github.io/%E7%AB%99%E7%82%B9%E7%BB%B4%E6%8A%A4/2020/07/22/Move-mastodon-media-to-Scaleway.html)把现在在使用的媒体存储迁移到新的 bucket 上。需要改的地方有：
    1. nginx （如果你有设置的话），如果你之前是按上面提到 pullopen 那篇教程设置的话，应该在 `/etc/nginx/sites-available/media` 下
        1. `location /SOURCE_BUCKET_NAME/`> `location /DEST_BUCKET_NAME/` 这步不改的话旧的媒体可以显示，但新传图会 503.
        2. `proxy_pass` 改成新的 endpoint
    2. `.env.production` 下面几项分别改成新的 bucket 名和地区
        1. `S3_BUCKET=SOURCE_BUCKET_NAME`
        2. `S3_ENDPOINT=SOURCE_BUCKET_ENDPOINT`
        3. `S3_REGION`
        4. 如果换了新的服务商的话下面两个也要改：
            1. `AWS_ACCESS_KEY_ID`
            2. `AWS_SECRET_ACCESS_KEY`
5. 重启 Nginx 和 Mastodon
    1. `sudo nginx -s reload` && `systemctl reload nginx`
    2. `sudo systemctl restart mastodon-web && sudo systemctl restart mastodon-streaming && sudo systemctl restart mastodon-sidekiq` （不一定三个全部重启，但我一般怕出幺蛾子都一起重启）
6. 这时你的 Mastodon 就已经在使用新的 bucket 了，为了保险起见我会时不时再 run `rclone sync --progress old_bucket new_bucket` 确保期间漏掉的媒体同步（这个命令默认不会删除 old_bucket 里没有的媒体，所以可以放心）

## Precaution Messures

为了杜绝上述问题在未来发生，几个 precaution measures 可以采取：

1. 定期清理 mastodon 缓存，不要觉得反正不到 75G 就懒得清理。偷懒一时爽，备份火葬场。（毕竟清理缓存也经常要跑好几个小时）
    1. `RAILS_ENV=production ./bin/tootctl media remove --days 7 --verbose`
    2. `RAILS_ENV=production ./bin/tootctl media remove-orphans`
    3. `RAILS_ENV=production ./bin/tootctl preview_cards remove --days 7 --verbose`
2. 留一个备份 bucket，定期 run `rclone sync` 来备份，这样主 bucket 有问题时候可以快速 sync 然后切换到新 bucket 上。当然大家也可以做个 cron job 来定期自动备份，但是懒如我怎么会做这种事情呢……定期备份就已经很给面子了。记得跑备份的时候要开 `screen`

这篇算是我写了这么久博客第一次写 COE 吗……果然自己捣鼓比上班用心多了。

---
{{< hint info >}}
如果您觉得本文对您有帮助，想支持我的博客创作，或者有特定的内容想要看到，或者想约 coffee chat，欢迎点击下面按钮成为我的金主：
{{< /hint >}}
{{< button href="https://www.patreon.com/bePatron?u=46962965" target="_blank">}}成为 Patreon 金主{{< /button >}}
{{< button href="https://ko-fi.com/S6S130C16" >}}在 Kofi 上给我买杯奶茶{{< /button >}}