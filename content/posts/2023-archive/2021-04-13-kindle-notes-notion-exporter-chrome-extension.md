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

**[点此到 Chrome extension store 下载](https://chrome.google.com/webstore/detail/kindle-notes-exporter/ogdkdkhjpdgkaodokpammlabdaohebop)**

![](https://user-images.githubusercontent.com/5817602/113990452-53e9f780-9806-11eb-8d48-5471aaab27c6.png)

与我之前的[微信读书导出工具](../we-read-notion-exporter-script/)类似。不过微信读书那个工具需要会用命令行和装 Python，本工具只要有 chrome 就能用。

（注：由于没有美区之外的 Kindle 账号我无法测试 i18n，本插件暂时只支持美区 Kindle 账号，如果有人愿意测试的话欢迎提交 pull request）

A chrome plugin that export kindle notes to a notion compatible csv file.

This plugin will convert the current selected kindle notes to a notion compatible csv file.

Made for [my reading notes channel](https://t.me/mtfront) because filtering and sorting is just much more easier this way.

## **Output table format in Notion:**

| Name | Highlight | Note | No. |
| --- | --- | --- | --- |
| Chapter | Underlined highlights | Notes/thoughts | Index used to sort |

## **How to use:**

1. Install this chrome extension.
2. Click the extension icon in chrome.
3. The pop up will prompt you to kindle note page if you’re not already in.
4. Select the note you want to export and click an export. Browser will start to download the csv.
5. In Notion, create a table (can be either inline or entire page)
6. Click the ‘…’ on right top cornor of your table, chose “Merge with CSV”
7. Wait for import to complete and refresh the notion page
8. Click the ‘…’->sort, add an ascending sort on ‘No.’ (why does stupid notion import in random order?)
9. Notion may convert your ‘Note’ column to ‘Type’. Simply click on the header and change property type to ‘Text’
10. Remove default unsed fields like “tags”

{{< support >}}