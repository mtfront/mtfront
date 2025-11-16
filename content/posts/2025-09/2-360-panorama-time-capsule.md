---
title: 做了一个展示 360 全景图的时空胶囊页面
author: 椒盐豆豉
type: post
date: 2025-09-07T19:49:00-07:00
url: /360-panorama-time-capsule/
categories:
  - 关我屁事
  - 重启电脑
tags:
  - Blog
  - Hugo
  - Code
  - Tutorial
  - Project
  - PSA
booktoc: false
bookComments: true
image: "https://media.douchi.space/douchi/media_attachments/files/115/166/083/407/635/237/original/45eeb3864c8d6e5e.jpg"
imageDes: "摄于 2025-08 Lake Union"
---

某日我在闲逛访客来源，逛着逛着就来到了[Joe 的天空之眼](https://houjoe.me/sky-eye/?utm_source=blog.douchi.space)这个页面，博主每到一个地方就会用无人机拍一张鸟瞰视角的 360 全景图留念，顿感新鲜立马想要借鉴一个。

<!--more-->

早年我轮番买过若干款无人机，甚至还在无人机相关公司工作过。Insta360 也算是 early adopter，一代就买了。除此之外前前后后各类传统运动相机也买了不少，无一例外都吃灰了。这些设备卖的卖丢的丢炸的炸，去年底把 [Insta360 Go 3](https://amzn.to/3S3P3in) 卖掉之后第 N 次赌咒发誓再也不买视频产品了，但总会被各类公司卖 life style 的消费主义陷阱吸引蠢蠢欲动，一直想要再找个 use case 当借口买点新东西。

这个天空之眼的静态停时之术倒是给了我新的思路——不玩社媒短视频也没耐心剪视频，这些设备不要当视频产品用就好了呀，静态图还是有长毛象和博客诸多可用空间的。外加明年要去南极浮潜，过两天要去班夫划船，横竖还是得搞点运动相机。又恰好可能半年都去不了一次 Costco 的我前两天去了一次就刚好碰到打折，于是就又入手了 [Insta360 X5](https://amzn.to/4mTnNje)。买完周末出去两次拍了点图，万事俱备，只欠装修博客了。

首先是寻找 panorama viewer 库。在网上搜到 [Pannellum](https://pannellum.org/documentation/overview/tutorial/?utm_source=blog.douchi.space)，打开感觉界面熟悉，然后意识到我之前某一份工作的时候公司产品用过它，人生是个圈儿。作者还提供了免费 CDN js 打包只有 21kb，轻量网站的话 0 代码无需部属即取即用，有 URL 就可以即时生成。官方 document 里可以找到可调参数，直接用 URL params 传入即可。如果需要更复杂的设置官网也给出了各种 configurable params。我需要的样式只需 panorama 原图和一张平面图当预览即可，嵌入格式如下：
```html
<iframe 
  width="100%" 
  height="400" 
  allowfullscreen 
  style="border-style:none;"
  src="https://cdn.pannellum.org/2.5/pannellum.htm#panorama=${原图URL}&preview=${预览图 URL}">
</iframe>
```

此处原图需要 equirectangular image。如果用的是 Insta360 系的相机的话，标准模式照片照出来就是这个格式，视频可以通过 Insta360 Studio -> Media（注意不是 Project 那个页面！只需要简单编辑的话 media 就够了不需要去 project，我一开始绕了半天…… ） -> 选取视频里想要的任意时间点 -> 360 view -> Take a snapshot，就会得到一张 equirectangular jpg.
![](https://media.douchi.space/douchi/media_attachments/files/115/166/252/877/595/992/original/e8653ba5f4f1bc21.png)

把这张图传到自己的 object storage 之后发现 viewer 提示有 CORS error。在自己的 object storage 设置页面 CORS Configuration。我用的 [digitalocean space](https://www.digitalocean.com/?refcode=708fdc9af879&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge) 可以按照 Origin 设定允许的 methods 和 allowed headers 等等。这里把 `https://cdn.pannellum.org/`的 `GET` 钩上即可。然后就可以得到一个网上可以嵌入或者直接点链接的全景图 viewer 啦：

<iframe 
  width="100%" 
  height="500" 
  allowfullscreen 
  style="border-style:none;"
  src="https://cdn.pannellum.org/2.5/pannellum.htm#panorama=https://douchi.sfo3.digitaloceanspaces.com/blog/360/icecave_2025.jpg&preview=https://media.douchi.space/douchi/media_attachments/files/115/082/688/677/831/228/original/2104d9629e8f6778.png" ></iframe>

之后就是在博客上手写一个集中展示 360 图的页面。好久没手搓 HTML/CSS 了。发现 AI 时代自己懂的简单的东西我还是不大有耐心叫 AI 给我写，有描述和改代码的功夫自己差不多都搓好了, maybe I'm just old……更花时间的当然是后面自己的样式微调。

我是用的是 hugo，平时的博客都在 `posts` 目录下，每一个 markdown 文件就是一个新的条目。这里我想把时空胶囊贴文和博文分开，于是与 `posts` 平级新开了个文件夹 `time-capsule`，在这个文件夹里放 `.md` 文件访问 `博客地址/time-capsule` 就会得到和博客列表一样的文章列表，可以从各处链接。

Hugo 目录下 `/layouts/posts/` 下会有 `list.html` 和 `single.html` 两个文件，用来定制各个目录下单篇文章的样式。把这个目录复制到 `/layouts/posts/time-capsule` 就可以自定义 `time-capsule` 下的博文样式。此外，我之前对模版的修改没有完全模块化，因此在 `baseof.html` 等处也有一些 hardcode 要改掉。为了不干扰正常博文的样式，我把这些单篇的 `type: post` 改为了 `type: time-capsule`，方便按 type 在共有区域区分对待。

[Joe 的天空之眼](https://houjoe.me/sky-eye/?utm_source=blog.douchi.space)是每个地方一张图，毕竟无人机能尽览无余。但我在地面上，一个地方通常会有多张图，因此也没有限制在一个页面一张图。因此没有把所有格式固定死，每个单篇其实就像一个正常博文一样，里面想放什么放什么。以后懒得写游记的 photo dump 可以直接往这里堆啦。

最终时空胶囊页面效果如下，目前只有两个胶囊，在[这里访问]({{< relref "/time-capsule" >}})：

![](https://media.douchi.space/douchi/media_attachments/files/115/166/363/878/866/806/original/4cda62fe0bd19f9a.png)

感觉时空胶囊因为是“凝固时空瞬间“所以做成卡片风格（拍立得？）比较搭，但我主页却是扁平化风格，稍微有点不 consistent。不过反正我也不是设计师，先这么着吧，以后看不顺眼再改 乁། ˵ ◕ – ◕ ˵ །ㄏ

根据我时常[输出倒逼输入]({{< relref "/posts/2023-08/5-2023-why-you-need-a-blog" >}})的风格，现在有了展示页，不知道 360 相机的利用率会不会高一点摆脱吃灰循环呢 (ง •̀_•́)ง