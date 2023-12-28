---
title: 大瓣 - 增大豆瓣短评输入框
author: 椒盐豆豉
type: post
date: 2023-12-28T13:33:00-08:00
url: /daban/
categories:
  - 重启电脑
tags:
  - code
  - project
bookToc: false
image: https://media.douchi.space/douchi/media_attachments/files/111/659/317/497/235/308/original/cbce4a3b9d2677ae.jpg
imageDes:  "我的天才大瓣 marketing 图"
---

## [去 chrome 商店下载大瓣](https://chrome.google.com/webstore/detail/%E5%A4%A7%E7%93%A3/mmnbgabhkhglibggedoaebkhmpbodnkk)
然后到桌面端网页版豆瓣短评页面点一下那个插件图标就可以把短评框变大。我觉得我起名和 marketing banner 都是小天才（逃

<!--more-->

昨晚写剧评的时候被豆瓣那个窄窄的输入框烦到了，光写还好说，要编辑的时候就痛苦面具，于是打开 console log 就随手把高度改了。然后想说写都写了每次都改麻烦，其实本质上就` document.getElementById("comment").style.height = "300px"`一行代码。本来想着写个油猴插件就完事了，结果被运行条件搞得有点烦，还是熟悉的 chrome 插件吧。但也确实每次屁大点代码都要水个插件有点烦，思考是不是搞个整合体，但现在写过的东西功能又没多少 UI 整一起也有点莫名其妙就先这样吧。



{{< support >}}