---
title: Mastodon SSL handshake failure debug
author: 椒盐豆豉
type: post
date: 2025-05-28T22:39:00-07:00
url: /mastodon-525/
categories:
  - 重启电脑
tags:
  - mastodon
  - Debug
booktoc: false
bookComments: true
image: https://douchi.space/oops.gif
---

我的长毛象实例从今年 4 月底开始总是出现 http error code `525` SSL handshake failure. 一开始以为是服务器运营商 contabo 超售，网上并未搜到同类问题，外加当时比较忙还在 travel 就没管，后来变成了个 recurring issue，每天都要坏掉被迫手动重启，定期自动重启也未能解决问题。前阵子终于闲下来了 debug 一下。现在稳定运行一周了看来是修复了，记录一下供其它站长参考。

<!--more-->

事件经过：
1. 一个多月前我站总是间歇性地出现 SSL handshake failure `525`，如果不管它的话过几个小时会自愈，重启服务器（不能只重启长毛象 service）的话会立刻解决，但大概过一天左右又会重现。
2. 因为当时比较忙没时间 debug，以为是 contabo 超售的问题，就重启先凑合着用。我先开始在容易出问题的时间之前设了个 cron job 每天重启服务器。但一两天后这个问题又只是顺势推移到了另一个时间点而已，也差不多是每天出现。
3. 终于有时间 debug 了，查了 nginx log 发现是 `worker_connection` 不够，默认的只有 800 多（可能我从哪里 copy 来的？）。把服务器配置扔个 cha 老师让给了个推荐，把 nginx 的 `worker_connections` 和 `worker_rlimit_nofile` 提高了。
4. 几天没出问题之后服务器又挂了，但这次是 `500`，而且不用重启刷新一下就会自愈。这么来了几次之后我又查了下 nginx log 发现有 `Too many open files` 问题。cha 老师帮助下把 `/etc/security/limits.conf` 的 `soft nofile`/`hard nofile` 都 bump 到 65535 了。

现在已经过了一段时间没问题了，定期查一查 open connection 数量也稳定没有增长了，反而是稳定在了一开始的 `worker_connection` limit 之下。post-moterm 一下由此可见根本原因应该是随着流量自然增长超了系统/nginx 的 `nofile`/ `worker_rlimit_nofile`，然后 retry storm 导致的 connection 爆炸。其实 cha 老师在我问步骤 3 的时候就提到了修改 `nofile`，不过应该是有一些 config 漏了，导致了后面的问题，才第二次改对的。第 3 步治了标，第 4 步才治了本。

一些本次 incident 比较 handy 的常用 command/文件：
- `ss -s` ：socket statistics 
- `/var/log/nginx/error.log`：network issue 十有八九都能在 nginx error log 里找到问题，可以先从 nginx log 里找找不到再去看 system/service log. 

找 cha 老师 debug 关键还是问对问题最重要，有时候真的废话有点多。最早的时候 debug 我搜的是类似于“server recurringly having SSL handshake failure”，只得到了一些比较 general 的 debug tips，就以为是 contabo 超售没有继续查下去。还是后来去查 nginx log 开始写具体的 error message 才能解决问题，其实也没比以前 Google + stackoverflow + 技术博客文章有本质上的区别。