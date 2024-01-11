---
title: 什么是链接追踪，如何简单规避 UTM
author: 椒盐豆豉
type: post
date: 2023-09-17T22:58:00+00:00
url: /url-sanitizer/
categories:
  - 重启电脑
tags:
  - code
  - project
  - tutorial
bookToc: false

---

在大众对上网隐私问题逐渐关注和各种公司变本加厉收集用户隐私、隐私泄露事件层出不穷的今天，互联网甚至传统行业（如汽车）的隐私收集无处不在，普通用户很难躲避厂商花招频出的追踪手法。不过，作为最常用一种追踪方法，UTM（Urchin Tracking Module）链接追踪的规避还是相对容易的。本文就来介绍一下什么是 UTM、如何规避这种链接追踪，以及提供一款逻辑简单的 Chrome 小插件来方便地在网页端去除链接中的追踪参数。

写这篇文章的起因是，昨天和女朋友一起在手机上看 B 站视频，期间想到个段子，我想让女朋友发视频链接给我好做 reference，女朋友犹豫了一下说 app 分享会有追踪隐私问题不大想用。B 站账号几百年前注册的中国手机早已停用所以大概连月活都算不上的我突然来了兴趣想看看墙内 app 的追踪有多凶，就让她把链接发来然后从头到尾解释了一遍如何去掉里面的追踪参数。今早起来遂产生了这么简单的逻辑顺手写个插件吧的想法。那插件写都写了，只能在桌面端用够不到追踪更严重的手机端，干脆顺便写个全套科普好了。

<!--more-->

## 什么是链接追踪 / UTM
拿我近期比较喜欢的一个 B 站视频举例：
- 这是最精简的视频地址：`https://www.bilibili.com/video/BV1KP411Y7df/`。`.com` 和前面的部分是 B 站的域名，`video` 是这个页面的类型（当然也可以是自定义的任何东西，不一定是视频页面就要叫 video），`BV1KP411Y7df` 是这个特定视频的 ID。
- 这是按分享按钮会生成的网址：`https://b23.tv/ABCDEF`，ABCDEF 是我隐去了个人信息替换的乱码。
- 在浏览器输入上面短链接之后，它会被解析成 `https://www.bilibili.com/video/BV1KP411Y7df/?buvid=blah&is_story_h5=false&mid=blah&plat_id=106&share_from=ugc&share_medium=android_i&share_plat=android&share_session_id=blah&share_source=COPY&share_tag=s_i&timestamp=1695019227&unique_k=blah&up_id=487640933` 的形式。`?`后面跟着的每个`&`隔开的东西都是一个 tracking 用的参数，此处我把个人信息省去换成了`blah`方便示例。

我们可以从参数名字里猜猜可能涉及到的个人信息。比如 `share_session_id`，这是你本次跟 B 站服务器链接 session 的唯一 ID，用它可以定位到你的账号，以及大概率当时登录的 IP（也就有了你的大体地理位置）和设备等。`buvid`和`unique_k`看起来也是跟你的账户直接相关的唯一 ID。

B 站大概是放在 URL 里的参数太多了链接很长，因此分享链接才需要生成一个短链接，否则发在消息里贴在社交网络上都很不好看。短链接的作用可以看成是一个索引——将长链接的全部信息存在数据库中，然后生成一个较短的编码来方便用户分享，同时也能隐藏一层长链接中所追踪的信息增加去掉参数的麻烦程度。短链接的实现方法是一道经典的码农系统设计面试题，感兴趣的可以去搜搜"shorten URL"。

YouTube 上的“分享”按钮会生成一个格式为`https://youtu.be/1ING-LVW7wM?si=ABCDEF`的链接，其实也是短链接的一种，后面的`si`这个参数也是在后台存储了所有的追踪信息，相当于短链接的一种。不同的是如果通过这种链接访问 YouTube，会自动跳转到干净的 `https://www.youtube.com/watch?v=1ING-LVW7wM` 格式。

## UTM 有什么用
这些追踪信息是跟着链接走的，也就是说这个链接不管被别人在什么平台转多少次，B 站有这个链接都能定位到你的账户。一般情况下这些数据有如下目的：
- 后台对用户行为进行分析以便优化产品，如用的什么设备，在什么平台看视频，用户来自哪里，用什么方式生成的分享链接等等
- 针对用户信息投放推送，如跟你本地相关的视频等
- 将用户信息售卖给第三方方便广告投送，我不熟悉 B 站的盈利模式不知道有没有这方面的业务，但平时大家说的广告业务是互联网巨头的绝大多数营收来源就是从这儿来了一部分
- 墙内国情定位分享链接的用户

当然，UTM 只是追踪的一个手段之一。如果你是直接登录一个网站，即便用干净的 URL 该网站也能获取你的很多信息（比如 IP 和设备等），VPN 能解决部分问题但不能解决全部问题，这里不在本文的讨论范围不想详细展开。

但对于非直接登录网站的追踪，UTM 就很有用了。比如邮件中的链接可以让发送邮件 campaign 的宣传方分析受众渠道，用户转发到其它平台上的链接可以帮助定位来源衡量 campaign 的有效性等。

## 如何规避 UTM 链接追踪
既然数据是从网址参数中来的，解决方法也很直接——在链接中直接去掉这些参数再转发即可，即手动去掉`?`后面的内容。

当然，有些网站也把不含有追踪信息只有访问资源的 ID 放在参数中，比如 YouTube 主页点进一个链接 `https://www.youtube.com/watch?v=1ING-LVW7wM`，这里的`v=`后面实际上是 video ID，去掉这个参数的话是找不到视频的。因此去掉参数时要依情况而定，基本上参数的名称都能比较直白地揭示其用途。也可以试着打开自己手动净化后的链接看看资源还能不能正常打开。

就这个简单操作我做了一个净化 URL 的 Chrome 小插件：
### [URL sanitizer Chrome 插件商店链接](https://chrome.google.com/webstore/detail/url-sanitizer/ajkpelpeineingjfmenbgkhophnlofgc)
![](https://lh3.googleusercontent.com/CC3g1LA5x-M7hcLmQhTUZ7mJGVGhHPqR48hXZpW3y3vUqq93q1LUVRaQHM-bczASA0oupmHr8KYZq02Q4t-kg8GV=w640-h400-e365-rj-sc0x00ffffff)

它只有两个简单功能：
- 打开一个带有追踪链接的网址，点击这个插件，净化过的链接会直接复制到你的剪贴板
- 手动在插件里修改要净化的链接，点击右边的复制按钮可以复制。适用于在网站上点“分享”按钮之后生成的带 tracking 的链接。（如果是短链接的话本插件没有带解析功能，需要在浏览器中打开生成的分享链接页面然后在那个页面上使用插件。YouTube 因为不是端链接可以直接使用）

目前只简单验证过 YouTube 和 B 站的链接，如果发现其它大站有用 parameter 做非 tracking 信息导致不可用的可以在 github 提交 issue 或者留言告知我方便增补。

如果你想[读代码](https://github.com/mtfront/url-sanitizer/blob/master/popup.js)，会发现它的基本逻辑非常简单：将所在页面的 URL 从`?`分开只取前面的。

如果读到这里你也想自己制作一款 Chrome 插件的话，[可以参考我这篇简单教程]({{< relref "/posts/2023-archive/2022-07-19-how-to-build-chrome-extension" >}})。

当然像前面说的，UTM 追踪也只是众多追踪手段其中的一种，即便完全规避 UTM 也无法保证个人隐私的绝对安全，scope 太大我也不是网络安全专家，在这里就不展开了。


