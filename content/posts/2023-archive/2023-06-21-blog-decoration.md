---
title: Hugo 小装修记
author: 椒盐豆豉
type: post
date: 2023-06-21T01:15:00+00:00
url: /blog-decoration/
categories:
  - 重启电脑
tags:
  - tutorial
  - hugo
  - code
  - blog
bookToc: false
---

这……[说好的不折腾](../blog-migrate-wordpress-hugo)，但事实证明建站果然是个巨坑（指上瘾而不是难搞），开始了就难以放下折腾，理解了为啥有那么多建站文了哈哈哈。本次小装修记是受了象友白石京的[装修笔记](https://thirdshire.com/post/hugo-stack-renovation/)启发，外加厌班，就顺便小改了一些博客功能。做了如下修改：

<!--more-->

## 增加字数统计
基本上是[象友装修笔记](https://thirdshire.com/post/hugo-stack-renovation/)里的提到的代码，不过我没有增加全站字数而是只在单篇文章里添加了每篇文章的字数和阅读时间。

因为想要进行一些样式控制，所以没在`post-meta.html`而是在我的主题的基础 html 里添加如下代码。一些本站才有的样式就不提了。因为我加在基础 html 而不是 post-meta 里，因此需要只显示在 post 里而不是任意页面需要添加类型 check。阅读速度是随便搜的中文阅读速度。
```
{{ if eq .Type "post"}}
  本文总计 {{ div .WordCount 1000.0 | lang.FormatNumber 2}}k 字, 阅读约需要 {{ div .WordCount 400}} 分钟
{{ end }}
```
此外需要注意的是 hugo 默认不统计中文字数，要统计的话需要在 `config.toml` 里添加 `hasCJKLanguage = true`。

效果如下:
![](https://media.douchi.space/douchi/media_attachments/files/110/581/258/560/737/540/original/264e8b93d8ce6395.png)

## 外部链接样式调整
给外部链接添加小 icon 基本是按[象友装修笔记](https://thirdshire.com/post/hugo-stack-renovation/)里来，把代码稍微简化了一下。此外因为我不想让 about 页的 logo 和菜单栏的外链 icon 显示，因此加了几个 condition 只在 post 里进行这些修改。此外既然改 link 了，又把外链添加了 `target="_blank"`在新窗口打开，站内的就直接在原窗口打开了。

在 `render-link.html` 添加如下代码：

```Go
{{- $isRemote := or (in .Destination ":") (strings.HasPrefix .Destination "//") }}
{{- $isPost := eq .Page.Params.Type "post"}}
{{- if .Page.Site.Params.BookPortableLinks -}}  // 原有
  {{- template "portable-link" . -}}  // 原有
{{- else if and $isPost $isRemote -}}
  <a href="{{ .Destination | safeURL }}"{{ with .Title}} title="{{ . }}"{{ end }} target="_blank">{{ .Text | safeHTML }}{{- if $isRemote -}}<span style="white-space: nowrap;"><svg width=".7em" height=".7em" viewBox="0 0 21 21" xmlns="http://www.w3.org/2000/svg"><path d="m13 3l3.293 3.293l-7 7l1.414 1.414l7-7L21 11V3z" fill="currentColor"/><path d="M19 19H5V5h7l-2-2H5c-1.103 0-2 .897-2 2v14c0 1.103.897 2 2 2h14c1.103 0 2-.897 2-2v-5l-2-2v7z" fill="currentColor"></svg></span>{{- end }}</a>
{{- else -}}
  <a href="{{ .Destination | safeURL }}"{{ with .Title}} title="{{ . }}"{{ end }} {{- if $isRemote -}} target="_blank"{{- end}}>{{ .Text | safeHTML }}</a>
{{- end -}}
```

## 修改标签云样式
我之前的标签云是模版默认的列表形式，占地面积大不说，还因为有过多标签造成滑动条套滑动条的状况，觉得有点丑就趁这次顺便改掉了。hugo 取标签的变量是 `Site.Taxonomies`，因此直接搜这个关键词，在 code 里找到我的模版里 render 标签和 category 的 html。它本来用的是一个 `<ul>`显示全部 list，我不想改 list style 就直接把 list 去掉了，每个元素用了如下代码显示：
```html
<a class="tag-cloud" href="{{ .RelPermalink }}" target="_blank">{{ .Title }} [{{ len .Pages }}]</a>
```
其中用了本站通用的 button 样式在主题的 css 里稍作修改：
```css
.tag-cloud {
  display: inline-block;
  font-size: $font-size-12;
  color: var(--color-link);
  line-height: 20px;
  border: 0;
  border-radius: $border-radius;
  padding: 0 1px;
  margin: 2px;
  cursor: pointer;
  background-color: white;

  &:hover {
    text-decoration: none;
    // background-color: #E8F6EF;
    filter: drop-shadow(1px 1px 1px var(--color-link));
  }
}
```
效果如下：
{{< columns >}}
![模版默认效果](https://media.douchi.space/douchi/media_attachments/files/110/581/312/655/772/622/original/b0d93e72fe464e82.png)
<--->
![修改后](https://media.douchi.space/douchi/media_attachments/files/110/581/317/824/909/111/original/d5fe6dced9d29b61.png)
{{< / columns >}}
其实 category 还是想用原来的样式或者稍微明显一点，不过就这样吧懒得改了……

