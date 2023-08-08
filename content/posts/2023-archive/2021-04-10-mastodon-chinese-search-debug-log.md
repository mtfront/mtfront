---
title: Mastodon 中文全文搜索失效 debug 日记及修复方法
author: 椒盐豆豉
type: post
date: 2021-04-10T07:58:13+00:00
url: /mastodon-chinese-search-debug-log/
categories:
  - 重启电脑
tags:
  - debug
  - elasticsearch
  - mastodon
bookToc: false
---
我的长毛象实例最近全文搜索失效，debug 了一下失效原因。简而言之，elasticsearch 自动更新了，所以之前装的中文全文搜索 plugin 本来是给 6.8.12 built 的，现在 6.8.14 运行不了，elastisearch 就卡死了。

解决方法：

1. 在根目录下运行
```
/usr/share/elasticsearch/bin/elasticsearch-plugin remove analysis-ik
/usr/share/elasticsearch/bin/elasticsearch-plugin remove analysis-stconvert
```

来卸载旧版本 plugin。

2. 运行如下两个命令下载为新版本编译的两个中文 plugin。
```
/usr/share/elasticsearch/bin/elasticsearch-plugin install https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v6.8.14/elasticsearch-analysis-stconvert-6.8.14.zip/usr/share/elasticsearch/bin/elasticsearch-plugin install 
https://github.com/medcl/elasticsearch-analysis-stconvert/releases/download/v6.8.14/elasticsearch-analysis-stconvert-6.8.14.zip
```

3. restart elasticsearch，运行 `sudo systemctl restart elasticsearch`.

以下是 debug 过程，不想深入研究的可以不看。

1. 今天早上本站用户说搜索坏了，搜不到嘟文只能搜到用户名和 tag，我当时在手机上以为是之前搜索不全的老问题。
2. 今天晚上自己测试了一下，确实任何全文搜索都搜不到，打开 sidekiq 发现从四月初开始 failure 暴增，应该是有问题。
3. failed message `Faraday::ConnectionFailed: Failed to open TCP connection to localhost:9200 (Connection refused - connect(2) for "localhost" port 9200)` ，Google 此 message 可知是 elasticsearch （后简称 ES）的问题。
4. Google 如何查看 active ports（没错这玩意儿天天用但是永远记不住，but why bother though），用 `sudo netstat -tulpn | grep LISTEN` 发现 9200 not active.
5. Google 如何重启 ES，运行 `sudo systemctl restart elasticsearch` ，但发现 sidekiq 失败 message 并没有下降。Google 如何查看 ES 状态，运行 `sudo systemctl status elasticsearch`，发现重启失败，最后一行报错是 JAVA_HOME not set.
6. `export JAVA_HOME=/usr/bin/java` ,重启 ES，发现没有解决问题，Google 之后发现有人说可能这并不是错误所在。
7. Google 如何查看 ES log，运行 `less /var/log/elasticsearch/elasticsearch.log` ，发现报错 `uncaught exception in thread [main]org.elasticsearch.bootstrap.StartupException: java.lang.IllegalArgumentException: Plugin [analysis-ik] was built for Elasticsearch version 6.8.12 but version 6.8.14 is running` 。
8. 在 mastodon doc（https://docs.joinmastodon.org/admin/optional/elasticsearch/ ）里找到当初安装的俩中文 index plugin repo，进入 repo 找到安装方法，Google remove elasticsearch plugin 方法卸载旧 plugin，安装 6.8.14 相对应新版本的俩 plugin。
9. 重启 ES，查了几次 status 发现运行稳定，sidekiq 里 failed retry queue 稳定下降，在 Mastodon 里随便搜了几个中文出现了过去的嘟文，确认问题解决。

---
{{< hint info >}}
如果您觉得本文对您有帮助，想支持我的博客创作，或者有特定的内容想要看到，或者干脆就想单独聊五毛钱，欢迎点击下面按钮成为我的金主：
{{< /hint >}}
{{< button href="https://www.patreon.com/bePatron?u=46962965" target="_blank">}}成为 Patreon 金主{{< /button >}}
{{< button href="https://ko-fi.com/S6S130C16" >}}在 Kofi 上给我买杯奶茶{{< /button >}}