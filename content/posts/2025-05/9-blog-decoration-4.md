---
title: 静态博客两周年 & Hugo 装修小记之四
author: 椒盐豆豉
type: post
date: 2025-05-30T20:41:00-07:00
url: /static-blog-2-year-in-hugo-decoration-4/
categories:
  - 重启电脑
tags:
  - tutorial
  - hugo
  - code
  - blog
  - 复盘
booktoc: true
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/114/438/341/418/991/623/original/5ebac6b9bb4ea394.png
imageDes: "摄于 2025-4 九份·台湾"
---

现在这个博客的[“建站”日]({{< relref "/posts/2023-archive/2020-10-29-hello-world-its-me-again" >}})其实应该是 2020 年 10 月 29 日，时隔多年之后终于趁着建长毛象的时候域名买都买了克服了拖延症重回独立博客界。虽然用 Wordpress 的时候也挺高产，但远不如[迁移到 hugo]({{< relref "/posts/2023-archive/2023-05-31-blog-migrate-wordpress-hugo" >}}) 之后来得上心，遂用静态博客启用的时间（2023 年 5 月 31 日）开始作为现在这个博客的建站纪念日。这一晃竟然就是第二个周年的博客总结了，号称不折腾如我装修小记也写到第四篇了（[1]({{< relref "/posts/2023-archive/2023-06-21-blog-decoration" >}})｜[2]({{< relref "/posts/2024-01/11-blog-decoration-2" >}})｜[3]({{< relref "/posts/2024-05/8-blog-decoration-3" >}})）。时光飞逝岁月如梭啊。

<!--more-->
## 内容
### 最受欢迎的博文
发的时候就没怎火热过的旧文[「美国码农前半段职业发展道路（career ladder）」]({{< relref "/posts/2023-archive/2022-08-15-software-engineer-career-ladder" >}})纯靠着有机流量（搜索引擎、别处的引用？）来到了浏览量第一且远超后面的文章。另一篇靠有机流量（应该是被放在某校非官方新生手册里了）旧文[「什么是链接追踪，如何简单规避 UTM」]({{< relref "/posts/2023-09/5-url-sanitizer.md" >}})也排在前 5。 It's a marathon not a sprint 放在 content creation 上真是真理呀。新的文章里：
- [「居家健身入门指南」]({{< relref "/posts/2024-09/3-workout-from-home" >}}) - 长毛象上当时就被转了很多，或许也是我近年来无意中从职场/消费主义博主转型养生博主的一个侧面证明？ {{< emoji "https://emojis.slackmojis.com/emojis/images/1643515632/16550/meow_googlytrash.png?1643515632" >}}
- [「2024 浪潮退去平台期的找工总结」]({{< relref "/posts/2024-09/5-job-hunting-2024" >}}) - 无需多说，职场文总是流量很多。
- [「失业十个月中的财务状况」]({{< relref "/posts/2024-11/3-finance-after-layoff" >}}) - 理财 + 职场双 buff 了。
- [「2024 年度购物之最」]({{< relref "/posts/2024-11/8-shopping-2024" >}}) - ~~消费主义博组最后的余晖~~
- [「工作十年了」]({{< relref "/posts/2024-10/5-career-10-years" >}}) - not my average 职场文，难得偏向感受了一些。

### 我最喜欢的新博文
这一年新写的里最喜欢的五篇：
- [「懒人如何保持健康饮食——敷衍食堂每日饮食结构」]({{< relref "/posts/2025-03/4-food-composition" >}}) - 文本身没什么好说的，但做标题那张图做得非常快乐，而且算是 design driven (?) 先想做那张图才有了博客，这般复盘了一下之后又惊喜地发现自己吃得还蛮健康的这种成就感。
- [「用《君幸食》中扶霞总结的中餐烹饪方法术语一秒钟把敷衍食堂变高大上」]({{< relref "/posts/2024-12/3-fancy-food-name-from-invitation-to-a-banquet" >}}) - 这篇比较奇特，大半的主要内容其实是读书笔记原封不动摘抄，但有这个 idea 本身挺有趣的，把本来可能只有非常喜欢中国饮食的人才会看和关心的内容变成了一个还蛮好玩的小活动。怎么连着两篇都是关于吃的……~~难道本厨渣要变成美食博主了~~
- [「工作十年了」]({{< relref "/posts/2024-10/5-career-10-years" >}}) - 不喜欢写职场文但还是当了这么多年职场博主，难得用 sentimental 的角度来写职场这个我并不喜欢的东西。
- [「Short index of my past 10 years」]({{< relref "/posts/2024-09/1-short-index-of-my-past-10-years" >}}) - 我喜欢写总结，我喜欢做“问卷”形式的博客，这篇两者占全了。而且检阅自己过去喜欢的东西的编年史真的让人有种到了中年之后难得的怀旧感觉。
- [「2024 年终总结」]({{< relref "/posts/2025-01/1-2024-in-reivew" >}}) - 虽然这篇还是不短，但是难得尝试了把以前要拖成好几篇的总结合并在了一起，且每个 section 都尽量精简了，也算有进步吧。

### 内容分析
把过去一年的博客文章标题和 tag 扔给 chatGPT 让帮忙总结都写了什么内容，精简一下 cha 老师的结论（有趣的是发现这么简单的文字数据分析 cha 老师也有 hallucination 加了一些我没写过的东西进去，interesting）：
- 生活与自我观察
  - 「关我辟事」（Vol.18–40，共23篇）
  - 复盘与总结：如[「2024 年终总结」]({{< relref "/posts/2025-01/1-2024-in-reivew" >}})、[「失业十个月中的财务状况」]({{< relref "/posts/2024-11/3-finance-after-layoff" >}})、[「博客印象收集」]({{< relref "/posts/2025-01/3-blog-impression-survey" >}})
- 健康与养生：13 篇
- 职业与工作：[「出厂设置」播客]({{< relref "/posts/2024-11/2-podcast-other-than-default" >}})的几篇文章，以及一些 debug log 之类跟工作无关但算是技术相关的博客也被算进来了。
- 金钱与消费：包括了各种理财文和测评。I wouldn't categorize as that but fine...
- 旅行与摄影：大的两篇游记竟然都是 Oregon…… 上班之后出去玩频率是大幅降低了。
- 博客写作与技术
- 阅读与内容导读：去年是有意多写了几篇读书笔记 which 我很满意。

每月平均 5～7 篇文章。今年产量有点堪忧，有一些「关我辟事」在充数，我有在考虑再改回月刊了。不过本月博客产量又 bounce back 了，这竟然是第 9 篇了，赶上去年高产期了。

cha 老师还总结了过去一年的高频标签：
| 标签名                 | 篇数 |
| ------------------- | -- |
| `关我辟事`              | 23 |
| `wellness`          | 13 |
| `tech`              | 9  |
| `blog`              | 8  |
| `patreon`           | 6  |
| `reading`           | 5  |
| `money`             | 4  |
| `travel`            | 4  |
| `software engineer` | 6  |
| `career`            | 6  |
| `复盘`                | 5  |
| `问卷`                | 5  |
| `消费主义陷阱`            | 9  |
| `random`            | 5  |


## 装修
### 站外项目
今年博客本身的装修跟去年比波澜不惊，倒是这个博客之外整了两个项目：
- 日记站：虽然说我对这个博客本身也没多高要求，日常碎碎念也有长毛象之类的渠道，但有了介于碎碎念和提笔写文之间的日记站之后好像真的思路更活跃了，甚至主博有好几篇文章都是日记站写着写着发散出来的。journaling 真是个好东西。因为追求简单随意所以本身也没怎么折腾装修，基本是拿来了 [paper](https://themes.gohugo.io/themes/hugo-paper/?utm_source=blog.douchi.space) 主题稍微改了改就直接用了，也特意没加 analytics。
- [跬步]({{< relref "/posts/2025-04/4-steps-page" >}})：逛博客逛到的开源项目 running_page 本热力图爱好者一见钟情了，像写博客做播客一样，健身也能输出倒逼输入。自从有了跬步页面好像跑步 hiking 都更 motivated 了。

本站的装修则都是一些小的 refinement 了。这个主题用了两年，声称不折腾博主如我断断续续也加了很多小 customization，如果将来真的看腻了要换主题可能还有一些不舍（和麻烦）呢。

### 高亮笔
网上冲浪逛到一篇[「为什么小白更该使用静态博客」](https://blog.hahaha.net/posts/life/27/?utm_source=blog.douchi.space)看到的样式。当时博主还用的是另一个颜色，所以搬运到我博客上时基本就是**微调渐变、圆角的样式以及改成我博客的主题色**，效果即所见。写读书笔记的时候还蛮好用的。我是直接把 markdown 的加粗换成了这个样式，如果要保留加粗的话当然也可以自开一个 shortcode。

```css
  b,
  strong {
    font-weight: bolder;
    margin: 0 -0.3em;
    padding: 0 0.3em;
    border-radius: 0.6em 0.3em;
    background: 0 0;
    background-image: linear-gradient(to right, var(--color-link-light),  var(--color-link-superlight));
    -webkit-box-decoration-break: clone;
  }
```

### 单篇文章精简目录
写[「优秀简笔画火箭教程——读《System Design Interview: An Insider's Guide》」]({{< relref "/posts/2024-07/3-book-system-design-interview-1" >}})时因为用了多级标题，本博客默认的目录是 `h2` 和 `h3` 都在目录里，导致目录变得超长。

发现 Hugo 本身的目录级数参数 `markup.tableOfContents.endLevel` 只能[全站调整](https://discourse.gohugo.io/t/can-i-override-toc-setting-for-only-one-file-in-front-matter/36085?utm_source=blog.douchi.space)不能单页 override，于是自己加了个 `compactToc` param，作为可以单篇文章设置为只显示一级目录的 hacky solution。

首先在本模版的 `baseof.html` 里加上条件：
```Go-HTML-Template
<div class="book-toc-content {{ if .Params.compactToc}}compact-toc{{end}}">
```

然后在 css 里添加样式：
```scss
.compact-toc {
  nav > ul > li > ul {
    display: None;
  }
}
```

### emoji 
看到博友的[Twikoo評論系統的個性化設置](https://www.gigigatgat.ca/posts/twikoo-tutorial/?utm_source=blog.douchi.space)就顺手抄了作业给品论区加了 emoji。

评论区加都加了，emoji config file 也都自己选过来了，干脆也顺手给文章里加了个 emoji shortcode。Nothing fancy，其实就是把图片的样式调整到适合插入文字的大小，每次选表情的时候直接 copy twikoo config 里的表情 URL。 {{< emoji "https://emojis.slackmojis.com/emojis/images/1643515259/12808/meow_dj.png?1643515259" >}}{{< emoji "https://emojis.slackmojis.com/emojis/images/1666375634/61879/partyblob.gif?1666375634" >}} {{< emoji "https://emojis.slackmojis.com/emojis/images/1643515240/12583/meow_glowsticks.png?1643515240" >}}

```Go-HTML-Template
<!-- emoji's can be found https://slackmojis.com/ -->
<img src="{{ .Get 0}}" width="22px" height="22px" style="margin-left: 2px; margin-right: 2px;"/>
```

### Podcast card
[发布「出厂设置」]({{< relref "/posts/2024-11/2-podcast-other-than-default" >}})的时候顺手加的 shortcode，支持了 Apple 和 Spotify 自己的 podcast embed。效果如下：

{{< podcast "https://open.spotify.com/embed/episode/5suvGcz9zuaL1nDQXuslGr?utm_source=blog" >}}
{{< podcast "https://embed.podcasts.apple.com/us/podcast/4-%E7%A8%8B%E5%BA%8F%E5%91%98%E7%BB%8F%E7%90%86-em-%E7%8E%B0%E8%BA%AB%E8%AF%B4%E6%B3%95-%E8%80%81%E6%9D%BF%E4%BB%AC%E5%88%B0%E5%BA%95%E5%9C%A8%E5%BF%99%E5%95%A5/id1777737220?i=1000699446616?utm_source=blog" >}}

```Go-HTML-Template
{{ $url := index .Params 0 }}
{{ if in $url "apple" }}
    <iframe 
        style="border-radius:12px" 
        src="{{ $url }}" 
        width="100%" 
        height="152" 
        frameBorder="0" 
        allowfullscreen="" 
        allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" 
        loading="lazy">
    </iframe>
{{ else if in $url "spotify" }}
    <iframe 
        allow="autoplay *; encrypted-media *; fullscreen *; clipboard-write" 
        frameborder="0" 
        height="175" 
        style="width:100%;overflow:hidden;border-radius:10px;" 
        sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-storage-access-by-user-activation allow-top-navigation-by-user-activation" 
        src="{{ $url }}">
    </iframe>
{{ end }}
```
（顺便立个 flag 有空赶紧自己重新画一张封面）

### 彩色 hashtag
[装修小记 3]({{< relref "/posts/2024-05/8-blog-decoration-3" >}}) 里提到我做了文章列表放在首页作为博客快速入口，其中写了个小彩色 static hash tag，即用 tag 的内容文字做一个 hash 作为颜色代码，这样只要内容一样颜色就是一样的，方便辨别。做都做了，把样式也提出来做单独做了个 `tag` 短代码偶尔在文章里能用到，如 {{< tag "职业" >}} {{< tag "理财" >}} {{< tag "健康" >}} 等等。

```Go-HTML-Template
{{ $content := .Get 0}}
{{ $tagColor := substr (md5 $content) 0 6}}
<!-- hex code attach opacity to end of code, 33 is 20% opacity  -->
<!-- to add link here, you'd need to search Taxonomies for url, but it doesn't have chinese tag -->
<div class="tag" style="--tag-color: #{{$tagColor}}33" >{{ $content }}</div>
```

### Reaction
也是博友那看到一篇 [`<open-heart>❤️</open-heart>`](https://zhuzi.dev/posts/2025-01-12-open-heart/?utm_source=blog.douchi.space) 的装修笔记，对 twikoo 的一大遗憾就是没有 reaction，所以顺手就装上了。

值得一提的是，原版代码应该没有针对稍微有些流量的网站进行优化，因此用了比较昂贵的 list operation，很容易用超失效。博友[第三夏尔](https://thirdshire.com/hugo-stack-renovation-part-three/?utm_source=blog.douchi.space)那里有使用 hardcoded emoji list 而不是 list operation 的方式避开了这个限制。（cloudflare worker 每天的免费 `list` 流量只有 1000，而 `get` 则有 100,000）

其实工程上来说不用 `list` 反而是更好的选择，因为 hardcoded list 在 worker 端相当于一个 server side validation，whereas 用 `list` 的话其实只要前端修改 html 或者直接 send request 就能给文章 react 一些自定义内容，是个巨大的 security risk。（是前司的面试题里的一个部分 🤣）

代码都在链接的教程里，这里就不赘述了，只贴一下本站的自用样式。

```css
open-heart {
  border: 0.5px solid var(--color-link);
  border-radius: .4em;
  padding: 2px 8px;
}
open-heart:not([disabled]):hover,
open-heart:not([disabled]):focus {
  border-color: var(--color-link-light);
  cursor: pointer;
}
open-heart[disabled] {
  cursor: not-allowed;
  background-color: var(--color-link-light);
  color: #fff;
}
open-heart[count]:not([count="0"])::after {
  padding-left: 4px;
  content: attr(count);
  color: var(--color-link)
}

.reaction-container {
  margin-top: 16px;
  gap: 8px;
}
```

### Update hugo 版本
手~~贱~~更新了一下 hugo 版本，push 上去发现 build 又 break 了。仔细看 error message，发现模版里用的某些 function 又 deprecate 了……挨个全修复了一遍。比较复杂的是本来的 neodb 卡片用了 `data.getJSON` 在新版 hugo 里被 deprecate 了，建议是用 `resources.GetRemote` 和 `transform.Unmarshal`，但用法不是特别一样，让 chatGPT 给写了一段。新的 API 跟旧的用法不一样，GPT 写得代码也不对。我自己定睛看了一眼才把代码修复。

不一样的部分：

```Go-HTML-Template
{{ with try (resources.GetRemote $request ) }}
  {{ with .Err }}
    {{ errorf "%s" . }}
  {{ else with .Value }}
    {{ $dbFetch = . | transform.Unmarshal }}
  {{ else }}
    {{ errorf "Unable to get remote resource %q" $request }}
  {{ end }}
{{ end }}
```