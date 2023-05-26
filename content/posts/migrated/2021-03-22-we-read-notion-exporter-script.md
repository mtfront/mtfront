---
title: 微信读书笔记导入 Notion 工具
author: 椒盐豆豉
type: post
date: 2021-03-23T00:07:07+00:00
url: /we-read-notion-exporter-script/
categories:
  - 重启电脑
tags:
  - code
  - project
  - reading
  - tutorial

---
因为最近开始做<a rel="noreferrer noopener" href="https://t.me/mtfront" data-type="URL" data-id="https://t.me/mtfront" target="_blank">读书笔记剪报 channel</a>，因此需要一些排序、过滤功能，以前偷懒直接纯文本粘贴的微信读书笔记就不好使了。索性写了个 script，<a rel="noreferrer noopener" href="https://github.com/mfcndw/weread-notion" data-type="URL" data-id="https://github.com/mfcndw/weread-notion" target="_blank">点此下载</a>。<a href="https://github.com/sponsors/mfcndw" data-type="URL" data-id="https://github.com/sponsors/mfcndw" target="_blank" rel="noreferrer noopener">点此 sponsor。</a>

<p class="has-quaternary-background-color has-background">
  <em><strong>注意：本 script 仅在 MacOS 上测试过</strong></em>，Windows 不知道有没有问题，就算有我猜轻微改一下能用，如果有试了的朋友欢迎告诉我。
</p>

## [][1]Notion 最终效果： {.wp-block-heading}<figure class="wp-block-table">

| Name | Highlight | Note    | No.     |
| ---- | --------- | ------- | ------- |
| 章节名  | 你的高亮/划线   | 你的笔记/想法 | 用来排序的序号 |</figure> 

## [][2] {.wp-block-heading}

变成在 notion 的表格之后后续可以导出、自己加新 field 排序、filter 等，配合其他工具使用参见之前这篇中的效果：<a rel="noreferrer noopener" href="https://blog.douchi.space/?p=1134#reading" data-type="URL" data-id="https://blog.douchi.space/?p=1134#reading" target="_blank">读书笔记 workflow</a>。

## 如何使用 {.wp-block-heading}

<ol start="0">
  <li>
    用 git clone 下载基本代码到你的 Mac 上
  </li>
  <li>
    进入微信读书->笔记，点击“导出”
  </li>
  <li>
    点击底部的“复制到剪切板”
  </li>
  <li>
    把剪贴板内容粘贴进一个 txt 文件
  </li>
  <li>
    在 Mac terminal 里 <code>weread.py [txt 文件地址]</code>来运行本工具，生成一个 csv 文件
  </li>
  <li>
    在 Notion 里创建一个数据库
  </li>
  <li>
    点击数据库右上角的&#8217;&#8230;&#8217;，选择&#8217;Merge with CSV&#8217;
  </li>
  <li>
    等待导入结束并刷新 Notion 页面
  </li>
  <li>
    再次点击&#8217;&#8230;&#8217; -> &#8216;Sort&#8217;, 对&#8217;No.&#8217; field 添加一个 Ascending sort
  </li>
  <li>
    如果笔记很少的话 Notion 可能会把你的笔记变成单选类型。点击数据库表头的&#8217;Note&#8217;部分将 property type 改成&#8217;Text&#8217;即可
  </li>
  <li>
    去掉无用的 Notion 默认生成的列，如 &#8216;Tags&#8217;
  </li>
</ol>

<hr class="wp-block-separator has-text-color has-background has-quaternary-background-color has-quaternary-color is-style-wide" />

如果您觉得本文对您有帮助，想支持我的博客创作，或者有特定的内容想要看到，或者干脆就想单独聊五毛钱，欢迎点击下面按钮成为我的金主：

<a href="https://www.patreon.com/bePatron?u=46962965" data-patreon-widget-type="become-patron-button">Become a Patron!</a>  
  


**<a rel="noreferrer noopener" href="https://afdian.net/@mtfront" target="_blank"><code>墙内赞助通道：爱发电</code></a>**

<div class="da-reactions-outer TpostID1431">
  <div class="da-reactions-data da-reactions-container-async left" data-type="post" data-id="1431" data-nonce="d0c1edefc0" id="da-reactions-slot-post-1431"> 
  
  <div class="da-reactions-static">
    <img src="http://blog.douchi.space/wp-content/plugins/da-reactions/assets/dist/loading.svg" alt="Loading spinner" width="48" height="48" style="width:48px; height:48px" />
  </div>
</div></div>

 [1]: https://github.com/mfcndw/weread-notion#notion-%E6%9C%80%E7%BB%88%E6%95%88%E6%9E%9C
 [2]: https://github.com/mfcndw/weread-notion#%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8