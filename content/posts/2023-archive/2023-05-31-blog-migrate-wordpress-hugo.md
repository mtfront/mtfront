---
title: 新的静态博客上线啦！aka Wordpress to Hugo 的又一篇倒腾
author: 椒盐豆豉
type: post
date: 2023-05-31T05:15:40+00:00
url: /blog-migrate-wordpress-hugo/
categories:
  - 重启电脑
tags:
  - tutorial
  - wordpress
  - project
  - PSA
  - digital nomad
  - blog
---
## TLDR

- 博客从自建 Wordpress 迁移到 Github Pages 啦
- RSS 换了！请用新链接订阅 [![](https://douchi.sfo3.cdn.digitaloceanspaces.com/random/logo/rss.png)](https://blog.douchi.space/index.xml)`https://blog.douchi.space/index.xml`
- 赘述一下为啥要迁移，两种方式优劣
- 勉强能算教程的迁移过程
<!--more-->

## 不是说不爱捣腾吗，咋也开始搞建站了

老朋友们可能会发现本博客变样子了，而且速度变快了。其实这不是改模版换外观而已，而是我[断断续续历时半个月](https://douchi.space/@mtfront/110387062276075527)把博客从自建的 Wordpress 站迁移到 Gigthub Pages 了。每次看我 social post 直接在博客访问的朋友们应该除了了外观和部分新功能（比如 Google 搜索）需要适应之外没啥影响。[跟我一样用 RSS](https://blog.douchi.space/my-rss-setup/) 的朋友们，烦请更新 RSS feed：

## 新 RSS

[![](https://douchi.sfo3.cdn.digitaloceanspaces.com/random/logo/rss.png)](https://blog.douchi.space/index.xml)`https://blog.douchi.space/index.xml`

## 为啥要迁移

我是 20 年的 Wordpress 老用户，从小学开始写博客在 blogcn 上入了坑，后来新建现在这个博客时候也就按习惯继续用了，其实建站时候未做太多横向对比。跟建完站就跑不写文流的博主相比，我也更注重内容本身不那么爱搞技术，所以就一直没捣腾。但是最近因为长毛象豆豉站升级版本之后可能小服务器带不动了需要升级服务器，[于是动了在博客服务器上抠点钱下来的念头](https://douchi.space/@mtfront/110337909488324896)。

其实这两年用自建的 Wordpress 也遇到不少问题，虽然都不大，但隔三差五就（趁我在外面玩的时候）坏了，要小修，甚是烦人。于是最近有点空余时间的时候索性一鼓作气执行了。

### Wordpress 自建站的缺点

- 隔三差五会坏掉。光看我 [discord server 里站点状态的更新](https://discord.gg/cESS4JpsdG)一大半都是博客故障通报就知道了，内容较为简单的博客比上千人用的社交网络还多围护就很离谱。绝大多时间修是好修的，[偶尔需要 debug](https://blog.douchi.space/wordpress-all-in-one-wp-security-aios-locking-cloudflare-out/)，但一个人运行的东西又不可能 24 小时维护，别人要看文章的时候用不了就很烦人。
- 要钱。因为要自己租服务器，就算可以多个应用 share，也是一笔开支。
- 访问速度慢。自己的小服务器优化不到哪去。
- 臃肿难定制。其实 Wordpress 功能很多，博客只是其中一小部分，于是有很多用不到的 bloated 服务和代码在占用宝贵的服务器资源，虽然提供了图形界面，但大多数定制被模版所限，模版和插件质量也良莠不齐需要自己鉴别。而直接改代码又得读它臃肿的代码很麻烦。

### Github Pages 静态博客/Hugo 的优点

- 稳定可靠。有问题本地 build time 就能发现。外加依托微软的 infra 肯定比自己的服务器可靠多了。
- 快。用户载入的就是最直接的 html 文件，没有什么 run time cost。外加微软的服务器肯定比我组的小破服务器快啊。以及我不爱捣腾建站，就在最流行的 Jeykll 和 Hugo 里稍微看了一下按自己需求挑了 build 更快的 Hugo。（据说 Jeykll 上百个页面就会很慢了）
- 不要钱。Github Pages 目前和可预见的未来基本功能是免费的。（域名我本身已经有豆豉站的域名了，附加金钱成本为 0。当然不想花这个 Github Pages 的默认域名又不是不能用）
- 用 Markdown，迁移和用其他工具写草稿什么的都很方便，写起来也顺手。Wordpress 虽然也兼容 markdown 但是导出经常会出一些莫名其妙的东西。
- 代码简洁，定制方便，本地测试容易。找好了模版随手改个 css 或者 html 之类的很容易。
- 版本管理。依托 Git 自然而然有了版本管理。

### 当然，也有一些痛点

- Wordpress to hugo 的导出插件其实不是很好用，我迁移的绝大多数时间花在手动改文章格式上。
- 不熟悉 git 和 terminal 操作的朋友可能需要一些额外上手时间以及碰到问题估计会头大，Wordpress 毕竟是图形界面还是受众更广的。
- 需要额外图片压缩/存储支持（文章写多了全原图存 GH 上不方便）

## 极简建站/迁移教程

记录一下我的过程和选择，可能不大适合小白上手。

### 确定框架

简而言之据说 jeykll 慢 hugo 快，我话比较多就用 hugo 了。不喜欢捣腾没有横向对比太多。

随便搜了一篇[教程](https://levelup.gitconnected.com/build-a-personal-website-with-github-pages-and-hugo-6c68592204c7)装了 hugo，按着走就行。注意它的建议是只 commit `/public` folder（这样 draft 可以自己保密）。但这样的缺点是必须上传本地 build 好的网站，不方便多设备在没有/没法装 hugo 的设备上写文章，所以我还是传了整个 repo。反正草稿在哪不能写不是。所以它在 `cd public` 这一步去掉直接 push 母文件夹即可。

### 找模版

简单 Google 随便找了个[模版库](https://themes.gohugo.io/)，其中这一款 [hugo book](https://hugo-book-demo.netlify.app/) 符合我的需求，顺着 demo 找到 [repo](https://github.com/alex-shpak/hugo-book) 按照其中说明安装即可。

它的教程建议把整个模版添加为一个 module，我觉得这样自己改东西被它限制了就没加，直接整个 repo clone 下来 commit 了。

### Wordpress 导出

到了前一步按模版的 readme 走的话本地的 hello world 应该已经能跑起来了，重头戏是从我的 wordpress 迁移。新建站无需迁移以前博客文章的同学可以跳过这几步。

Google wordpress to hugo 找到了官网上推荐的 [WordPress to Hugo Exporter](https://github.com/SchumacherFM/wordpress-to-hugo-exporter)，按说明下载，scp 到自己的 Wordpress 服务器上。它的 plugin 我用 Wordpress 的图形界面进不去，于是直接用了 [command line](https://github.com/SchumacherFM/wordpress-to-hugo-exporter)。

其中我不需要 wordless 服务器上传的图片（反正晚点服务器也要停掉），因此 comment 掉了 [convert_upload](https://github.com/SchumacherFM/wordpress-to-hugo-exporter/blob/master/hugo-export.php#L493)，否则的话导出和下载完导出的 zip 文件都会很慢。

### 导入 Hugo

直接把 zip 文件里的 posts 复制粘贴到你本地 hugo repo 的 posts 文件夹下即可。

### 手动修改格式

不知道是我 Wordpress 插件装太多还是导出工具没有更新，总之我的导出文件里有很多 Wordpress 的格式需要改掉。这一步我基本没用上导出的内容（导出的 metadata 比如 tags & category 之类的还是很有用的），纯复制原文到 notion 再展粘回去搞定的。

此外我 Wordpress 是用了一段时间才把媒体放到 S3 上，因此还有很多链接等服务器关了就会失效，我混合传了长毛象 + 手动传 S3 也都迁移了。

还有头大的点是我有些博客之前没有用定制链接，就直接用 Wordpress 生成的 ID，显然迁移之后文章之间互链也不能用了。手动挨个改掉。

其实这一步很多东西应该能 automate，但是我一时偷懒没写 script，导致花了最多时间。我[这个串](https://douchi.space/@mtfront/110387062276075527)的绝大多数时间都是在干这些枯燥工作。

### 修改模版

- 外观上 link 和 button 的样式
- 加 Disqus 评论
- 博客 post 页加 title 和日期、tag 等 metadata（这个模版主要不是用来做博客的所以博客功能有很多地方比较简陋）
- 加 Google 站内搜索（原生的搜索中文优化不好，而且是本地生成的 performance 有一定问题）。Google 提供了[一键添加](https://programmablesearchengine.google.com/)，还能自己定制一些东西。
- 改改 menu

### 发布到 Github Pages

照着前面教程来即可，注意 source 我建议选 Github Actions 而不是 branch，这样 build 的过程放到 github 上，修改东西不需要在装了 hugo 的机器上本地 build。

### 使用定制域名

如果没有自己的 custom domain 的话跳过这一步。我为了尽量无缝就沿用了过去的域名。去你的 github page repo → setting → pages → custom domain 按步骤来即可。即：

- 先在 GitHub 上修改，这样你的网站会跳转到域名指向的网站。
- 再在 DNS 提供商上添加一个 record，把这个域名指向你的 github page 域名。

## 总结

早迁移早超生！毕竟 GitHub 的生态还是比各种博客服务（notion、medium、writely 之类的）稳定。发现如此简单之后我感觉我不会再推荐确定能写下去的人博客用 wordpress 了，迁移成本比想象中大好多。我的时间主要花在 migrate 而不是建站。如果不确定要不要写我反而推荐先用 notion 写，到时候 markdown 迁移可能更方便。

以及，大家加我的新 RSS 哇！（声嘶力竭 [![](https://douchi.sfo3.cdn.digitaloceanspaces.com/random/logo/rss.png)](https://blog.douchi.space/index.xml)`https://blog.douchi.space/index.xml`

{{< support >}}