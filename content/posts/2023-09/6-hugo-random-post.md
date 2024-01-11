---
title: 给 Hugo 博客添加随机文章入口
author: 椒盐豆豉
type: post
date: 2023-09-20T01:06:00+00:00
url: /hugo-random-post/
categories:
  - 重启电脑
tags:
  - code
  - project
  - tutorial
  - hugo 
  - blog
bookToc: false

---

我想给自己的博客加一个随机文章入口，作为页面右边的分类和 tag 之外的另一个发掘文章入口，移动端也更容易。在网上一搜，Google 第一页没有看到太显眼的简单适合我博客的答案：要么是最简单的 [build time randomize](https://geekthis.net/post/hugo-random-numbers/)，不能每次点击/刷新都出新文章；要么要生成 json 索引，对 hugo 语言和 config 不是很熟悉的我折腾了一下没搞出来，遂放弃。

想说这么简单个功能不至于不能纯拿 JS + html 写吧，博客少则几十多则几千的随机数性能应该也不成问题，随自己折腾出来个方案供大家参考。

<!--more-->

我的需求：
1. 动态随机，每次点击随机一篇不同的文章，非 build time 随机。
2. 使用灵活，至少在我的模版里目录和文章里都能用。

在模版本身的 partial 和 shortcode 里突击了一下凑合出来下列代码。

```
// themes/{我的主题}/layouts/partials/docs/random.html
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
<a class="random" onclick='goToRandomPost()'>随便看看</a>
```
这里偷懒直接改了窗口地址所以直接跳转，如果需要返回地址渲染更多信息的话将`window.location`那一行按需改掉即可。都是标准 js 不废话了。

Shortcode 版 script 完全一样，显示部分加了两个参数方便在文章里 customize，第一个参数控制要现实什么文字，第二个参数控制是链接形式还是按钮形式。

```
// themes/{我的主题}/layouts/shortcodes/random.html
{{- if eq (index .Params 1) "button"}}
  <a onclick='goToRandomPost()' class="book-btn">{{ index .Params 0}}</a>
{{- else -}}
  <a onclick='goToRandomPost()' style="cursor: pointer;">{{ index .Params 0}}</a>
{{- end -}}
```

个人认为相较 Google 搜出来排名靠前的 json 生成 index 版本（[[1]](https://discourse.gohugo.io/t/how-to-get-a-random-post-link/28957)[[2]](https://kevinquinn.fun/blog/add-a-random-page-button-to-hugo-site/))对我而言有如下优点：
1. 设置更灵活简单。无需 debug 不同模版的 config，复制粘贴两个文件就能直接用。
2. 修改逻辑简单且保存就能看，无需重新生成 index。
3. 将来要扩展功能（比如增加文章数、在同 tag 里推荐相关文章等也更方便。

[既然英文也没见到类似做法也翻了篇本文的英文版。]({{< relref "/posts/2023-09/7-hugo-random-post-en" >}})

写到这儿了就直接用上吧：
