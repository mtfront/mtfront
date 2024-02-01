---
title: Hugo 装修小记之二
author: 椒盐豆豉
type: post
date: 2024-01-17T15:07:00-08:00
url: /blog-decoration-2/
categories:
  - 重启电脑
tags:
  - tutorial
  - hugo
  - code
  - blog
booktoc: true
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/111/773/554/157/003/795/original/f2893d0676964f9d.png
imageDes: "MidJourney prompt: person decorating home, game isometric pixel art style --ar 16:9"
---

作为一个非建站博主，说好的不折腾换了[静态博客半年]({{< relref "/posts/2023-12/1-static-blog-half-year" >}})，继[初始装修]({{< relref "/posts/2023-archive/2023-06-21-blog-decoration" >}})之后这半年来还是零零散散多多少少给博客加了些小功能做了些小装修，反正现在闲就再写一篇好了。一些特别小的样式修改就不说了。写起来才发现不知不觉已经装修了这么多了……

<!--more-->

## 新功能
### 热力图
其实刚迁移就想给博客加热力图了，前阵子看到有热力图的博客和现成可取的教程就一鼓作气给自己博客改出来一个，[也写了一篇详细教程]({{< relref "/posts/2024-01/3-hugo-blog-heatmap" >}})，之后看到不少博友已经用上了（甚至大多数还保留了我的主题色和标题 🤣），甚至还有博友光速增加了功能和做了 Wordpress 插件版，还是挺有成就感的。
![](https://media.douchi.space/douchi/media_attachments/files/111/699/816/751/626/673/original/4e609362db2eb6ad.png)

### NeoDB 卡片
就是要添加这个功能才想起来写一篇这个博客。是在博友那里看到的[教程](https://www.sleepymoon.cyou/2023/hugo-shortcodes/#%E5%BC%95%E7%94%A8neodb%E6%9D%A1%E7%9B%AE)，本来也觉得我的[月报]({{< relref "/tags/关我辟事" >}})里的书影游部分光列文字有点干，一张张粘贴海报排版又有点麻烦，于是立刻也给自己博客加了卡片。稍微修改了一下 CSS match 我博客的主题色和去掉文字滚动条。
```css
.db-card-abstract {
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
}
.db-card-abstract::-webkit-scrollbar {
  display: none;
}
```
效果如下：
{{< neodb "https://neodb.social/game/20slbMvBANRjuFHdSjNjDW" >}}

### 随机博文入口
发现改成静态博客之后有机流量多了不少，经常有新读者出现。作为一个话唠，旧的文章光靠分类和 tag 也很难翻到。对 Hugo 和 Go 都不是很熟悉，所以网上现成的 build time randomizition 教程我不是很满意，于是自己动手写了一个动态的 JS based 随机文章。之前写过[完整教程]({{< relref "/posts/2023-09/6-hugo-random-post" >}})这里不赘述细节了。添加了之后发现访客们还挺喜欢点这个随机入口的，有不少文章的浏览量都是从这儿来的。
```javascript
<script>
  function goToRandomPost() {
    const pages = [
      {{ range ((where .Site.RegularPages "Type" "post")) }}
      "{{ .RelPermalink }}?utm_source=random",
      {{ end -}}
    ];
    const rand = Math.floor(Math.random() * pages.length);
    window.location.href = pages[rand];
  }
</script>
```

### 博客前后篇导航
我使用的模版 [Book]({https://themes.gohugo.io/themes/hugo-book/?utm_source=blog.douchi.space}) 虽然从审美到代码都简洁合意，但因为模版原本的主要用途是文档而非博客，因此有一些博客常用功能缺失，比如“前一篇、后一篇”的导航。查阅 Hugo 文档后修改了一下我博客的导航样式，把文章底部本来只有随机入口的按钮改成了个`<前一篇｜随机｜后一篇>`的导航条。
![](https://media.douchi.space/douchi/media_attachments/files/111/773/603/473/455/138/original/dcd2b56637fe4d9e.png)
```html
  <hr />
  <div class="post-nav">
    {{ with .Prev }}
      <a href="{{ .Permalink }}" ><< 前 | {{ .Title | truncate 15 "..."}}</a>
    {{ end }}
    <a onclick='goToRandomPost()' style="cursor: pointer">
      随便逛逛
    </a>
    {{ with .Next }}
      <a href="{{ .Permalink }}" >{{ .Title | truncate 15 "..."}} ｜ 后 >></a>
    {{ end }}
  </div>
  <hr />
```
还加了根据文章分类（我有个单独的英文 category）改变导航条语言的逻辑，虽然整个博客其它部分都是中文的吧好像也没啥用。
```go
{{ if (in .Params.categories "English" )}} ... {{ else }} ...{{end}}
```

### 添加嘟嘟 shortcode
也是个 iframe，经常嘟就照搬过来了稍微调整了下样式，做成了个短代码。不满的是不管站点的默认主题是啥（我站就是 light mode），站外 embed 似乎都是 dark mode……
```html
<div class="embed" style="margin-top: 16px; margin-bottom: 16px;">
  <iframe src="{{ index .Params 0 }}/embed" class="mastodon-embed" style="max-width: 100%; border: 0" width="800" allowfullscreen="allowfullscreen"></iframe>
  <script src="https://douchi.space/embed.js" async="async"></script>
</div>
```

### 添加 Video shortcode
我的模版似乎没有提供视频播放器代码，自己加了一个用 html video 的 shortcode。

```html
<video controls width="{{ if .Get 1}}{{ .Get 1}}{{ else }}100%{{ end }}" autoplay muted loop>
  <source src="{{ .Get 0 }}" type="video/mp4" />
</video>
```

## 样式和结构
### 评论迁移到 twikoo
我的博客被墙的不彻底，偶尔还是有墙内流量进来，然后误以为没有评论系统，体验不佳。外加 Disqus 总自作聪明把正常评论放到 spam 里导致我看不到真的很烦，界面也很臃肿，遂决定[迁移到很多中文博客在用的 twikoo]({{< relref "/posts/2024-01/1-comments-twikoo" >}})。迁移过程比我想象中容易很多，按官方教程 setup 之后现插现用了，能改的 configuration 也不少。不过没有了 reaction 有点遗憾，也有人提了 [feature request](https://github.com/twikoojs/twikoo/issues/577)，希望后续有机会看到吧。迁移了之后好像评论真的变多了……

### 添加了 Now 页面
受了 [rexarski.log](https://rexarski.com/now/?utm_source=blog.douchi.space) 和 [ouroboros](https://blog.pursuitus.com/now?utm_source=blog.douchi.space) 启发也建了个 [now 页面]({{< relref "/docs/now" >}})。前两天忘了在哪看到一篇博文说“now”页面就像是一个你很久没见的朋友问你近况你给 ta 的 catch up，比社交媒体的细节琐碎更概括，又比 about 里静态的状态更有实效性。觉得这个概念很棒。还顺便精简了一下边栏目录。

### 添加足迹地图
受博友启发，也给自己博客的 about 页面添加了[足迹地图]({{< relref "/posts/2023-11/5-footprints" >}})。其实就是直接拿 Google My Maps 嵌在个 iframe 里。iframe 的短代码之前做[时区转换器]({{< relref "/posts/2023-archive/2023-07-26-digital-nomad-timezone-converter" >}})的时候就添加了。
```html
<div class="embed" style="margin-top: 16px; margin-bottom: 16px;">
  <iframe src="{{ index .Params 0 }}" width="{{ index .Params 1 }}" height="{{ index .Params 2 }}" class="mastodon-embed" style="max-width: 100%; border: 0"></iframe>
</div>
```
{{< iframe "https://www.google.com/maps/d/embed?mid=1v4chfysQdXJw9332M9TJOAc4nFeyaac&ehbc=2E312F" "100%" 400 >}}

### localhost 排除在 Google Analytics 之外
喜欢看 analytics 的我经常会被自己在 local 编辑的数据污染真实数据烦到，于是在我的模版里排除了本地的数据。我的模版里 Google analytics 在 `themes/hugo-book/layouts/partials/docs/html-head.html`，其它模版不一定在这里，但是 `_internal/google_analytics.html`看样子是 Hugo 自带的模版，搜一下应该很容易找到在自己模版的位置。
```go
{{ if eq (getenv "HUGO_ENV") "production" }}
  {{- template "_internal/google_analytics.html" . -}}
{{ end }}
```

### 博客题图说明
之前提到最近[用 AI 给博客生成题图]({{< relref "/posts/2024-01/10-spark-joy-digest-vol-9-2024-1a" >}})，除了要添加 prompt 之外有时候也会有自己的照片，需要提供一些 context。我的模版只提供了`image`参数添加题图，于是我自己加了个`imageDes`加行小字给自己自定义说明用。当然也可以用作是副标题。
```go
{{ if .Params.imageDes }}
  <p style="font-size:small">
    <i>{{ $.Params.imageDes }}</i>
  </p>
{{ end }}
```

### 友情链接样式
之前是文字的，现在改成 button base 的 tag 云形式了。

### 修改文字选择高亮颜色
也是某天在别的博客自己拿鼠标圈圈画画的时候意识到的。浏览器默认应该跟自己设置的主题色相关，我的主题色刚好是浅绿所以自己看博客的时候一直是浅绿，没意识到别人看到的可能是默认的蓝色。遂添加了 override 使风格更统一：
```css
::selection {
  background: var(--color-link-light);
}
```