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
因为最近开始做[读书笔记剪报 channel](https://t.me/mtfront)，因此需要一些排序、过滤功能，以前偷懒直接纯文本粘贴的微信读书笔记就不好使了。索性写了个 script，[点此下载](https://github.com/mfcndw/weread-notion)。[点此 sponsor。](https://github.com/sponsors/mfcndw)

{{< hint danger >}}
***注意：本 script 仅在 MacOS 上测试过***，Windows 不知道有没有问题，就算有我猜轻微改一下能用，如果有试了的朋友欢迎告诉我。
{{< / hint >}}

## **Notion 最终效果：**

| Name | Highlight | Note | No. |
| --- | --- | --- | --- |
| 章节名 | 你的高亮/划线 | 你的笔记/想法 | 用来排序的序号 |

变成在 notion 的表格之后后续可以导出、自己加新 field 排序、filter 等，配合其他工具使用参见之前这篇中的效果：[读书笔记 workflow](https://blog.douchi.space/?p=1134#reading)。

## **如何使用**

1. 用 git clone 下载基本代码到你的 Mac 上
2. 进入微信读书->笔记，点击“导出”
3. 点击底部的“复制到剪切板”
4. 把剪贴板内容粘贴进一个 txt 文件
5. 在 Mac terminal 里 `weread.py [txt 文件地址]`来运行本工具，生成一个 csv 文件
6. 在 Notion 里创建一个数据库
7. 点击数据库右上角的’…’，选择’Merge with CSV’
8. 等待导入结束并刷新 Notion 页面
9. 再次点击’…’ -> ‘Sort’, 对’No.’ field 添加一个 Ascending sort
10. 如果笔记很少的话 Notion 可能会把你的笔记变成单选类型。点击数据库表头的’Note’部分将 property type 改成’Text’即可
11. 去掉无用的 Notion 默认生成的列，如 ‘Tags’

---
{{< hint danger >}}
如果您觉得本文对您有帮助，想支持我的博客创作，或者有特定的内容想要看到，或者干脆就想单独聊五毛钱，欢迎点击下面按钮成为我的金主：
{{< /hint >}}
{{< button href="https://www.patreon.com/bePatron?u=46962965" target="_blank">}}成为 Patreon 金主{{< /button >}}
{{< button href="https://ko-fi.com/S6S130C16" >}}在 Kofi 上给我买杯奶茶{{< /button >}}