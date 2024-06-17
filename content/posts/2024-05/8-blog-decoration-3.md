---
title: 静态博客一年啦！Hugo 装修小记之三
author: 椒盐豆豉
type: post
date: 2024-05-31T05:46:00-07:00
url: /static-blog-one-year-in-hugo-decoration-3/
categories:
  - 重启电脑
tags:
  - tutorial
  - hugo
  - code
  - blog
booktoc: true
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/112/535/717/562/600/600/original/82852a6b1b3817f1.png
imageDes: "MidJourney prompt: pixel art style person decorating their home --ar 16:9"
---

不知不觉[从 Wordpress 迁到 Hugo]({{< relref "/posts/2023-archive/2023-05-31-blog-migrate-wordpress-hugo" >}}) 竟然已经一年了，本非建站博主竟然装修笔记也已经写了第三篇（[[一]]({{< relref "/posts/2023-archive/2023-06-21-blog-decoration" >}}), [[二]]({{< relref "/posts/2024-01/11-blog-decoration-2" >}})）了，果然静态博客前端代码好改就会忍不住开始折腾，想要的功能发现没有就会随时加上去，又积攒了写各种小修改，趁着静态博客一周年一起发了。会首先像[半年]({{< relref "/posts/2023-12/1-static-blog-half-year" >}})时候一样总结下半年来的新内容，想看装修笔记的可以直接前往[装修环节]({{< relref "/posts/2024-05/8-blog-decoration-3" >}}#装修)。

<!--more-->
## 内容
### 最受欢迎的博文
排名第一二的都是半年前就第一位的 [2023 年了你为什么需要写博客]({{< relref "/posts/2023-08/5-2023-why-you-need-a-blog">}})和从第五来到第二的[美国码农前半段职业发展道路（career ladder）]({{< relref "/posts/2023-archive/2022-08-15-software-engineer-career-ladder" >}})（旧文，都是搜索来的有机流量（换了静态博客之后[占我博客流量的 20%]({{< relref "/posts/2024-05/6-google-yourself" >}})，比用 wordpress 时候多了不少，不知道是不是偶然现象。这篇还是用 wordpress 时候写的呢！），再往后翻也有许多前半年的访问量排在新文前面。看来我新发的博文要加油了！新文章里：
1. [「被裁记」]({{< relref "/posts/2024-02/3-layoff" >}}) - 不出意料，毕竟这半年的最大生活状态变化就是被裁，写个啥都要隔三差五自己引用一下，又跟现在大市场环境比较相关。浪了小半年，对晚点旅行回来就要开始进行的找工作有种又本能厌恶又有点陌生刺激的感觉…… 
2. [「一些低门槛的实用上网小技巧」]({{< relref "/posts/2024-01/13-tech-tips" >}}) - 完全没想到这篇会受欢迎，写之前犹豫了好久因为觉得可能大家都已经知道了写出来没什么用，没想到还有挺多反馈说有学到新东西的！
3. [「静态博客半年记」]({{< relref "/posts/2023-12/1-static-blog-half-year" >}}) - 套娃了哈哈哈！
4. [「租房还是买房，公寓还是 house」]({{< relref "/posts/2024-04/1-rent-or-own-apartment-or-house" >}}) - 从租公寓到买 house 再到现在又租了两年公寓又变回了挺坚挺的不买党，这篇充满私货的万字长文终于被我给写了！觉得自己有理有据，能拦住一个不适合的是一个。
5. [「2024 新年理财和羊毛待办清单」]({{< relref "/posts/2024-01/7-new-year-investment-checklist-deals" >}}) - 随着理财理念成熟没啥新发现，就好久不写啥纯理财文了。年初薅羊毛写了这篇。

### 我最喜欢的新博文
[旧的在这里]({{< relref "/posts/2023-12/1-static-blog-half-year" >}}#我最喜欢的博文)内容就不重复了，这半年新写的里最喜欢的五篇：
- [「也说我的几个小坚持」]({{< relref "/posts/2024-04/6-little-things" >}}) - 喜欢的原因是，拉长了时间线，真的能看到自己成长了。以及，这篇虽然还是不短，但极力克服了写到又臭又长的欲望，精简了很多，竟然都能写成 bullet points 了！
- [「告别小白」]({{< relref "/posts/2024-01/14-bye-s3" >}}) - 这半年除了被裁之外另一个最大的生活变化是换掉了开了快 6 年的爱车，这篇有点 sentimental，总结了下小白和我一起走过的旅程。
- [「割以永治 part 3：切除子宫一周年 FAQ」]({{< relref "/posts/2023-12/8-hysterectomy-fighting-period-part-3" >}}) - 割以永治也过去一年多啦！为了改变我又臭又长的写作习惯，这回来了个自问自答 FAQ。但最喜欢的部分我问总是引用的 childfree 漫画画手要了授权，翻译成了中文放便扩散，也算是做公益了！
- [「这么深入浅出的免疫学为什么不在课本里——读《Immune》」]({{< relref "/posts/2024-04/7-book-immune" >}}) - 中译版的才 16 万字，我写了 1.6 万字的笔记，这书深入浅出太有意思了。
- [「美西大环线 Road Trip - Part 2: 我看过了许多美景」]({{< relref "/posts/2024-03/7-us-west-loop-road-trip-2" >}}) - 纯粹是因为我上次病假和再上次裸辞期间就想开的大环线 road trip 终于给我开了！以及碰到太多意外美景了。

### 特定读者群
本来想像上期一样找找有机流量博文访问量，翻了好几页发现都是之前写的旧博文，最高的[被裁]({{< relref "/posts/2024-02/3-layoff" >}})那篇都排到第 21 了，遂作罢。想到逐渐加了些博客聚合站，如[积薪]、[川流]，还写[教程]({{< relref "/posts/2024-01/3-hugo-blog-heatmap" >}})有了一些引用，读者人群又跟我之前的非常不同，就挑几家说吧：
- 聚合站读者们最喜欢：[「一些低门槛的实用上网小技巧」]({{< relref "/posts/2024-01/13-tech-tips" >}})、[「被裁记」]({{< relref "/posts/2024-02/3-layoff" >}})、[「年度购物之最」]({{< relref "/posts/2023-11/8-shopping-2023" >}})
- 被引用的流量：流传颇广在不同渠道看到好几次的[如何给 Hugo 博客添加热力图]({{< relref "/posts/2024-01/3-hugo-blog-heatmap" >}})，以及意外被引用了一篇科普[「什么是链接追踪，如何简单规避 UTM」]({{< relref "/posts/2023-09/5-url-sanitizer" >}})。虽然不想成为技术博客但这种对普通人也有用的科普或许以后可以多写点。
- 长毛象读者喜欢：[「也说我的几个小坚持」]({{< relref "/posts/2024-04/6-little-things" >}})、[「人到中年做一次全面健康回顾」]({{< relref "/posts/2023-12/3-health-review" >}})、[「2023 这盘角色扮演我玩得如何」]({{< relref "/posts/2023-12/12-2023-in-review" >}})
- Telegram 读者喜欢：[「静态博客半年记」]({{< relref "/posts/2023-12/1-static-blog-half-year" >}})、[「租房还是买房，公寓还是 house」]({{< relref "/posts/2024-04/1-rent-or-own-apartment-or-house" >}})、[「也说我的几个小坚持」]({{< relref "/posts/2024-04/6-little-things" >}})
- RSS 读者喜欢：[「被裁记」]({{< relref "/posts/2024-02/3-layoff" >}})、[「高效、async 的信息流才是好的信息流：我的 RSS setup」]({{< relref "/posts/2023-archive/2022-08-28-my-rss-setup" >}})、[「一些低门槛的实用上网小技巧」]({{< relref "/posts/2024-01/13-tech-tips" >}})
- 最后还有，之前装修添加了一些导航按钮（相关、随机、前后文），用的人还不少，最初发现渠道是这些的博文：[「健身有余，智能不足的 Garmin Venu 3S 一个月使用感受」]({{< relref "/posts/2023-10/3-garmin-venu-3s" >}})、[「All of Us Strangers 结尾点题无关浪漫才是最大的升华点」]({{< relref "/posts/2024-01/9-all-of-us-strangers" >}})、[「高效、async 的信息流才是好的信息流：我的 RSS setup」]({{< relref "/posts/2023-archive/2022-08-28-my-rss-setup" >}})

## 装修
### 首页显示最新文章/静态彩色 tag
之前我的[首页]({{< relref "/" >}})没有显示博客，需要点进[博客]({{< relref "/posts/" >}})才能查看博客，而且是阅读视图不便快速浏览。又觉得专门加个 archive page 有些冗余，于是自己看了下 Hugo doc 提取了前 25 篇文章做成个 list 放在首页。

又觉得光放文章列表有点单调，想提取前三个 tag 给定固定的随机颜色放在文章名后。Hugo 模版里提供了 md5 函数，hash 了之后取前 6 位作为颜色的 hex code，再调整一下透明度，就大功告成了。

```Go-HTML-Template
<ul>
  {{ range (first 25 (where .Site.RegularPages "Type" "post")) }}
    <li>
      <a href="{{ .RelPermalink}}">{{ .Title }}</a> 
      {{range (first 3 (.Params.tags))}}
        {{ $tagColor := substr (md5 .) 0 6}}
        <!-- hex code attach opacity to end of code, 1A is 10% opacity  -->
        <!-- to add link here, you'd need to search Taxonomies for url, but it doesn't have chinese tag -->
        <div class="tag" style="--tag-color: #{{$tagColor}}1A" >{{ . }}</div>
      {{end }}
      <div class="archive">- {{.Date.Format "2006-01-02"}}</div>
    </li>
  {{ end }}
</ul>
```

```css
/* css */
.archive {
  display: inline;
  color: var(--gray-500);
  font-size: 0.75em;
}

.tag {
  display: inline;
  padding: 0 $padding-4;
  border-radius: 2px;
  font-size: 0.75em;
  background:var(--tag-color);
  color: var(--gray-500);
}
```

效果如下：
{{< archive >}}

### 博客统计
重整首页之后把热力图从[近况]({{< relref "/now" >}})挪到了首页，就顺手又加了个博客统计 shortcode：

```Go-HTML-Template
{{$scratch := newScratch}}
{{ range (where .Site.Pages "Kind" "page" )}}
    {{$scratch.Add "total" .WordCount}}
{{ end }}

博文数量： {{ len (where .Site.RegularPages "Section" "posts") }} 篇 | 累计字数： {{div ($scratch.Get "total") 10000.0 | lang.FormatNumber 1 }} 万字
```

### 相关文章
Hugo 自带了通过分类和 tag 选取相关文章的功能，直接引用 `.Site.RegularPages.Related`，取前 5 篇，放到一个 list 里。缺点是这个计算方式只会给出引用当篇文章之前发布的文章，之后发布的即便更相关也不会向前更新了。先凑合着用吧。

```Go-HTML-Template
{{ $related := .Site.RegularPages.Related . | first 5 }}
{{ with $related }}
<h2>相关阅读</h2>
<ul>
 {{ range . }}
 <li><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></li>
 {{ end }}
</ul>
{{ end }}
```

### 剧透/Content Warning 模糊
{{< empty >}}
加了一个鼠标 hover/手机点击消除模糊的 shortcode，效果如下：{{< spoiler "我是剧透" >}}。

```html
<div class="spoiler">{{ index .Params 0 }}</div>
```
```Css
/* css */
.spoiler {
  filter: blur(4px);
  display: inline;
  &:hover {
    filter: blur(0);
  }
}
```
此处有个 tricky 的地方不知道是我的模版问题还是 Hugo，即如果使用这个短代码前的文字块没有别的定制模块的`<div>`，就会自动给短代码生成一个`<p>` tag，导致模糊部分即便 `display:inline` 也会另起一行。简单的 hacky solution 是我又加了一个只有一个 inline `<div>` empty shortcode 插在需要使用的剧透之前:

```html
<div class="empty" />
```
```css
/* css */
.empty {
  display: inline;
}

```
{{< wrap "https://media.douchi.space/douchi/media_attachments/files/112/535/256/042/897/078/original/284f4f7ef46eb222.jpg" "今天在 Massai Mara 碰到的猎豹" >}}
# 文字包裹图片和图片脚注
我的模版本来在 markdown 图片 render 的语法中就有脚注功能`![脚注](图片 URL)`，但文字样式跟正文一样。修改了一下 `render-image` 变成了居中、斜体、文字更小的文字脚注。这个样式还用在了题图和下面要提到的 wrap 图片中。

之前还只有全屏图片和等距 column 镶嵌图片两种图片格式，很多时候不想让图片占全屏或者没有文字来凑等距，不方便排版。于是添加了一个让文字包裹在图片周围的 shortcode。

```Go-HTML-Template
<div class="wrap {{if .Get 2}}wrap-left{{end}}">
  <img src="{{.Get 0}}">
  {{ if and (.Get 1) (gt (len (.Get 1)) 0) }}
    <i class="image-desc">{{ .Get 1}}</i>
  {{ end }}
</div>
```
```css
/* css */
.wrap {
  float: right;
  max-width: calc(min(100%, 400px)) !important;
  padding-left:  $padding-8;
  padding-top: $padding-8;
  text-align: center;
}

.wrap-left {
  float: left;
  padding-right:  $padding-16; 
  padding-left: 0px;
}
.image-desc {
  font-size:small;
  margin-top: 2px; 
  color: gray; 
  text-align: center;
}
```

### NeoDB 卡片手动修改个人评分
之前按照博友[教程](https://www.sleepymoon.cyou/2023/hugo-shortcodes/#%E5%BC%95%E7%94%A8neodb%E6%9D%A1%E7%9B%AE)添加了 neodb 卡片，但有个问题是 neodb 使用人数较少，很多条目的评分完全不能反应作品的水平或个人偏好，有时候作品简介也会缺失。因此在短代码里加了两个 field 来手动 override 评分和简介（没有选择直接从 neodb API 获取因为懒得看 API）：

```Go-HTML-Template
<div class="db-card-title">
  <a href="{{ $dbUrl }}" class="cute" target="_blank" rel="noreferrer">「{{ $dbFetch.title }}」</a>  
</div>
{{ if .Get 1}}
  {{ $itemRating :=  .Get 1 }}
  <div class="rating"> 个人评分：<span class="allstardark"><span class="allstarlight" style="width:{{mul 10 $itemRating }}%"></span></div>
{{ end }}
<div class="db-card-abstract">
  {{ if .Get 2 }}
    个人短评：{{ .Get 2 }}
  {{ else }}
    {{ $dbFetch.brief }}
  {{ end }}
</div>
```
效果如下：
{{< neodb "https://neodb.social/movie/5BP6Kl3tgQc9KI5RcL5VOR" 8 "" "是挺好看的，但没了《Fury Road》那种摇滚震天血火汽油交织让人头皮发麻那种爽和震撼了，其实动作场面也不少，量大管饱的给了三座不同城镇戏码，但没了音乐和节奏总感觉像一部“正常”好莱坞大制作而不是能狂与燃到这么疯癫都能走上主流的邪典了（为啥呀，难道音乐是 immortan Joe 的主题）。但算是完整地把在前者中当作背景故事的 Furiosa 和遥远的家乡补全了，也让这个角色和社群更为动人。小 Furiosa 的演员好有灵气啊甚至跟 Anya 有点像但又透出更多狠劲，超帅。锤哥这个角色乏善可陈不能怪他，角色本身跟 Jo 和 war boy 们比起来就没啥亮点，但莫名觉得在学 Tom Hardy 这两年愈演愈烈的夹子音就有点难忍。看完总觉得不够过瘾，前作太珠玉在前了。">}}

### 热力图字数上限
之前流传挺广的[博客热力图]({{< relref "/posts/2024-01/3-hugo-blog-heatmap" >}})中我用字数作为热力图单个数据点的数值，如 1 万字分成四等份。如果有文章超过了一万字则不会显示，因此每次写出超过上限的文章我都会调整分的等份（如 1.5 万字分四等份）。这样的缺点是绝大多数文章的区分不明显，极少数文章白占了几整个颜色。于是修改了一下代码，把超过字数上限的数据 round down 到上限，这样就无需一直修改字数上限且使图的区分不均匀了：

```javascript
// sum 是当天所有文章的总字数，push 进 data 的是千字
data.push([key, Math.min(10, (sum / 1000).toFixed(1))]);
```