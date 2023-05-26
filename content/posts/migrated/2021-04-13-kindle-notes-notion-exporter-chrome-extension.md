---
title: Kindle Notes 轻松导出导入 Notion —— 我的第一个 chrome extension
author: 椒盐豆豉
type: post
date: 2021-04-13T21:20:04+00:00
url: /kindle-notes-notion-exporter-chrome-extension/
categories:
  - 重启电脑
tags:
  - code
  - project
  - reading
  - tutorial

---
 

经过一周多的审核，我的第一个 chrome extension 终于上线啦！完全免费、开源，不收集任何用户信息，导出 csv 文件可导入 Notion 或任何可导入 csv 的笔记系统。跟 readwise 说再见。

<p class="has-large-font-size">
  <a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/kindle-notes-exporter/ogdkdkhjpdgkaodokpammlabdaohebop" data-type="URL" data-id="https://chrome.google.com/webstore/detail/kindle-notes-exporter/ogdkdkhjpdgkaodokpammlabdaohebop" target="_blank"><strong>点此到 Chrome extension store 下载</strong></a>
</p><figure class="wp-block-image is-resized">

<img decoding="async" loading="lazy" src="https://user-images.githubusercontent.com/5817602/113990452-53e9f780-9806-11eb-8d48-5471aaab27c6.png" alt="Screen Shot 2021-04-08 at 1 04 09 AM" width="640" height="371" /> </figure> 

与我之前的<a rel="noreferrer noopener" href="https://blog.douchi.space/?p=1431" data-type="post" data-id="1431" target="_blank">微信读书导出工具</a>类似。不过微信读书那个工具需要会用命令行和装 Python，本工具只要有 chrome 就能用。

版权归作者所有，任何形式转载请联系作者。  
作者：椒盐豆豉（来自豆瓣）  
来源：https://www.douban.com/note/800152192/

<p class="has-quaternary-background-color has-background">
  （注：由于没有美区之外的 Kindle 账号我无法测试 i18n，本插件暂时只支持美区 Kindle 账号，如果有人愿意测试的话欢迎提交 pull request）
</p>

<!--more-->

A chrome plugin that export kindle notes to a notion compatible csv file.

This plugin will convert the current selected kindle notes to a notion compatible csv file.

Made for&nbsp;[my reading notes channel][1]&nbsp;because filtering and sorting is just much more easier this way.

## [][2]Output table format in Notion: {.wp-block-heading}<figure class="wp-block-table">

| Name    | Highlight             | Note           | No.                |
| ------- | --------------------- | -------------- | ------------------ |
| Chapter | Underlined highlights | Notes/thoughts | Index used to sort |</figure> 

## [][3]How to use: {.wp-block-heading}

<ol start="0">
  <li>
    Install this chrome extension.
  </li>
  <li>
    Click the extension icon in chrome.
  </li>
  <li>
    The pop up will prompt you to kindle note page if you&#8217;re not already in.
  </li>
  <li>
    Select the note you want to export and click an export. Browser will start to download the csv.
  </li>
  <li>
    In Notion, create a table (can be either inline or entire page)
  </li>
  <li>
    Click the &#8216;&#8230;&#8217; on right top cornor of your table, chose &#8220;Merge with CSV&#8221;
  </li>
  <li>
    Wait for import to complete and refresh the notion page
  </li>
  <li>
    Click the &#8216;&#8230;&#8217;->sort, add an ascending sort on &#8216;No.&#8217; (why does stupid notion import in random order?)
  </li>
  <li>
    Notion may convert your &#8216;Note&#8217; column to &#8216;Type&#8217;. Simply click on the header and change property type to &#8216;Text&#8217;
  </li>
  <li>
    Remove default unsed fields like &#8220;tags&#8221;
  </li>
</ol>

<hr class="wp-block-separator has-text-color has-background has-quaternary-background-color has-quaternary-color is-style-wide" />

如果您觉得本文对您有帮助，想支持我的博客创作，或者有特定的内容想要看到，或者干脆就想单独聊五毛钱，欢迎点击下面按钮成为我的金主：

<a href="https://www.patreon.com/bePatron?u=46962965" data-patreon-widget-type="become-patron-button">Become a Patron!</a>  
  


**<a rel="noreferrer noopener" href="https://afdian.net/@mtfront" target="_blank"><code>墙内赞助通道：爱发电</code></a>**

<div class="da-reactions-outer TpostID1481">
  <div class="da-reactions-data da-reactions-container-async left" data-type="post" data-id="1481" data-nonce="99ea46fab8" id="da-reactions-slot-post-1481"> 
  
  <div class="da-reactions-static">
    <img src="http://blog.douchi.space/wp-content/plugins/da-reactions/assets/dist/loading.svg" alt="Loading spinner" width="48" height="48" style="width:48px; height:48px" />
  </div>
</div></div>

 [1]: https://t.me/mtfront
 [2]: https://github.com/mfcndw/kindle-notion#output-table-format-in-notion
 [3]: https://github.com/mfcndw/kindle-notion#how-to-use