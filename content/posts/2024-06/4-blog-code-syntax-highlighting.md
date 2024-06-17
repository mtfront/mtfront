---
title: 给 Hugo 博客的代码区块更换主题
author: 椒盐豆豉
type: post
date: 2024-06-17T14:46:00-07:00
url: /blog-code-syntax-highlighting/
categories:
  - 重启电脑
tags:
  - tutorial
  - hugo
  - code
  - blog
booktoc: true
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/112/633/976/859/126/167/original/17126f3386e04afa.png
imageDes: "MidJourney prompt: syntax highlighter --ar 16:9 "
---

前阵子写[「博客装修小记之三」]({{< relref "/posts/2024-05/8-blog-decoration-3" >}})）的时候突然意识到 Hugo 默认的代码高亮区块主题 `monokai` 在我博客的浅色主题里下显得很突兀，遂想换成个浅色的。对 syntax highlighting 一无所知的我本来以为在模版里改几行 css 就好了，没想到稍微看了一下发现因为 hugo 和所用 highlighter 文档不怎么样，埋得还挺深，颇找了一番才改好，顺手写一下给大家省省时间吧。

<!--more-->

## 何处切换主题
如果不是要自己从头写主题、微调配置的话，下面一行配置加到 `config.toml` 或者你模版对应的 config file 里即可。官方的 [configure markup](https://gohugo.io/getting-started/configuration-markup/#highlight) 文档里还提供了一些其它选项定制化和不同的 config 语言。如果你已经知道自己要什么主题，修改这个参数并保存即可立刻看到结果。

```toml
[markup]
  [markup.highlight]
    style = 'monokai'
```

问题来了，style 都有什么选项啊？

## 选择配色
代码写久了愈发讨厌各种 stereotypical 跟写代码/geek 联系起来的 dark mode，晚上看手机还行，白天阅读大量生产力文字黑暗模式看久了眼花，工作没几年就把编辑器和 terminal 全换成浅色模式的 `solarized-light` 了。要是不喜欢浅色版的话，它也有个深色版配色也比很多默认配色好看多了。

{{< columns >}}
这是一个挺有名的配色，文档也不错，各大编辑器、terminal 甚至 photoshop palette 都有[现成能下载](https://ethanschoonover.com/solarized/)的版本。我最早应该是在还是一个 SDE I 的时候看到组里 senior 在用就立刻抄过来了。
![](https://github.com/altercation/solarized/raw/master/img/solarized-palette.png)
<--->
![](https://github.com/altercation/solarized/raw/master/img/solarized-vim.png)
{{< /columns >}}

本来想把博客继续换成 `solarized-light`，但它是暖色系的，跟我博客的绿色主题有轻微地不搭，于是想看看有什么其它 style。帮助甚微的 hugo [Syntax highlighting](https://gohugo.io/content-management/syntax-highlighting/)文档里对不想要自己从头开始写配色只想选模版的人唯一的有用信息是提到 Hugo 用的是 [`Chroma`](https://github.com/alecthomas/chroma)做 syntax highligter。

搜 syntax highlighter styles 之类的关键词找到了 [`pygments` demo](https://pygments.org/demo/) 可以试不同的语言，也就有了支持的 style list。后来回到 `Chroma` 的文档发现官方也提供了 [Chroma Playground](https://swapoff.org/chroma/playground/) 可以用来测试。

我把这些在线工具里的浅色配色挨个试过去，最后选了 `paraiso-light`。回到自己博客的 `config.toml` 里，将 style 替换即可：

```toml
[markup]
  [markup.highlight]
    style = 'paraiso-light'
```

看看成果，比以前的默认深色主题是合适多了！

{{< columns >}}
![默认配色 monokai ](https://media.douchi.space/douchi/media_attachments/files/112/633/991/075/706/395/original/8ec7dc13440df9d3.png)
<--->
![新主题 paraiso-light](https://media.douchi.space/douchi/media_attachments/files/112/633/994/778/689/032/original/2a9a3157c4a773b9.png)
{{< /columns >}}

## 更新 inline markdown code 颜色
上面的更新 syntax highlighter 模版只会更新长代码区块 fenced code blocks 高亮（` ```代码``` `这种形式的一整个区块的代码），还有"\`代码\`"这种形式的 markdown inline 代码，我经常用到来表示专有名词。我的模版将它的 css 定义在了 `_markdown.scss` 中，本来是灰色的。我在 `_defaults.scss` 中加入了一个新的颜色变亮，把 `paraiso-light` 的背景色 `#e7e9db` 存为一个变量方便以后别的地方使用。

```scss
/* themes/hugo-book/assets/_defaults.scss */
--paraiso-light: #e7e9db;

/* themes/hugo-book/assets/_markdown.scss */
code {
  /* omitted other irrelevant fields */
  background: var(--paraiso-light);
}
```
## 未指定语言的代码块

我特地没有修改模版里没有指定语言使用 syntax highlighter fenced code blocks 的背景色，保留了原来的灰色，想说可以做其它用途：

```
hello world!
这是一段没有指定语言的 code block
```

如果想要修改这个颜色的话，在 inline code 同一个文件中修改即可：

```scss
/* themes/hugo-book/assets/_markdown.scss */
pre {
  /* omitted other irrelevant fields */
  background: var(--paraiso-light);
}
```

## 选择正确 syntax highlighter 语言
Hugo 的 syntax highlighter 似乎没有自动检测语言的功能，因此要正确按照各语言语法高亮，需要使用 markdown fenced code blocks 代码块规范的 syntax highlighting 在代码块开头标明语言，如：

```text
```javascript
/ * my code */
```

常见的语言诸如 `python`, `go`, `java` 之类的很好解决，绝大多数语言这里也都直接写文件后缀名即可，比如 `toml`, `scss` 等，不需要查文档直接写就好了。问题来到本非技术博主写最多代码的博客也就是博客装修系列，Hugo 的模版里经常有 `go` 和 `html` 混杂的情况，用两者任何一者都会造成其它的部分不能正确 highlight，很多地方还会被当成错误语法爆红，看起来很丑。虽然凑合也能用，但都开始改模版美化代码块了，就要一次做到底。

{{< columns >}}
```Go
// 当作 Go 处理
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
<--->
```html
<!-- 当作 html 处理 -->
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
{{< / columns >}}
在挑主题的时候刚好在 [Chroma Playground](https://swapoff.org/chroma/playground/) 发现 `Go HTML template` 竟然也是支持的语言，但直接这么写上去并不能有效识别，文档里也没轻易找到所有语言对应的 short name。用程序员常识推断，试了一下 `Go-HTML-Template`，果然就能正确识别了：

```Go-HTML-Template
<!-- 使用正确的 Go-HTML-Template 标记-->
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

---
论我为了拖延刷题都能干出什么无聊事儿，本来前两天随手改一下的事儿，现在变出了一整篇博客，都快要丧失非建站非折腾博主的荣誉称号了……