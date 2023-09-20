---
title: Add random post picker to Hugo without json index
author: 椒盐豆豉
type: post
date: 2023-09-20T01:06:00+00:00
url: /hugo-random-post-en/
categories:
  - 重启电脑
  - English
tags:
  - code
  - project
  - tutorial
  - hugo 
  - blog
bookToc: false

---

I want to add a random article picker to my blog as another way to discover past posts, aside from categories and tags on the right side and making it easier on mobile. 

I couldn't find a simple enough solution that suits my needs after brief Googling. The options I found were either to [randomize at build time](https://geekthis.net/post/hugo-random-numbers/), which means the article doesn't change with each click or refresh, or to generate a JSON index, which I had trouble with probably because my lack of understanding of Hugo. 

I thought such a simple feature should be achievable with just JS + HTML, so I decided to write my own. Performance shouldn't be an issue for a blog with a few tens to thousands of articles. Here's a solution I came up with for reference.

<!--more-->

My requirements:
- Dynamic randomization, a different article should show up with each click/refresh. (No build time randomization!)
- Flexibile enough to use in both menu and posts.

```
// themes/{my-theme}/layouts/partials/docs/random.html
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
<a class="random" onclick='goToRandomPost()'>Feeling lucky?</a>
```
I got lazy and directly modified the window location as redirect. If you need more data to render post info, change `window.location` row according to your needs. Just standard JS won't expand here.

For the shortcode version of the script is exactly the same. The rendering part has two additional parameters for customization. The first one controls the displayed text, and the second controls whether it's a link or button.

```
// themes/{my-theme}/layouts/shortcodes/random.html
{{- if eq (index .Params 1) "button"}}
  <a onclick='goToRandomPost()' class="book-btn">{{ index .Params 0}}</a>
{{- else -}}
  <a onclick='goToRandomPost()' style="cursor: pointer;">{{ index .Params 0}}</a>
{{- end -}}
```


Compared to the JSON index generation version that ranks high in Google search results（[[1]](https://discourse.gohugo.io/t/how-to-get-a-random-post-link/28957)[[2]](https://kevinquinn.fun/blog/add-a-random-page-button-to-hugo-site/)), this solution has the following advantages for me IMO:
1. More flexible and simpler to set up. No need to debug different template configs, just copy and paste these two files and it's good to go.
2. The logic is easy to modify and you can see the changes immediately without regenerating the index.
3. It's more expandable feature wise, such as adding the number of posts, recommending related posts within the same tag, etc.

Now that you're here：{{< random "Pick the next post for me" "button" >}}

[Read Chinese version of this post here.]({{< relref "/posts/2023-09/6-hugo-random-post" >}})

---

{{< hint info >}}
If you find this blog useful and want to support my blog or have a coffee chat with me, feel free to:
{{< /hint >}}
{{< button href="https://www.patreon.com/bePatron?u=46962965" target="_blank">}}Become Patreon{{< /button >}}
{{< button href="https://ko-fi.com/S6S130C16" >}}Buy me a boba{{< /button >}}
