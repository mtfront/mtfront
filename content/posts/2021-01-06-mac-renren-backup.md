---
title: 备份整理人人网相册——重新 index 我遗失的记忆碎片
author: 椒盐豆豉
type: post
date: 2021-01-06T08:12:02+00:00
url: /mac-renren-backup/
categories:
  - 重启电脑
tags:
  - Memory
  - tutorial
bookToc: false
---
[花了一晚上把所有备份的人人照片日期整理好了](https://douchi.space/web/@mtfront/105506251925621875)，来写个手把手教程顺便纪念一下这个大工程。

整个大学几乎都在校内/人人兴盛过的，人人相册于我就像是整个大学时代的图像记忆，而换设备如吃饭的我平时我找照片全靠 Google photo 定位日期 + people/object search，所以大学的记忆就好像遗失了一样。

我曾经是个人人重度用户，访客 10 万+，相册上百个那种。因为数据太庞大，一直拖延着没备份。有好几次有空想要备份一下，却发现登陆不上去了，惊慌失措手慢无。最近我的一个移动硬盘又坏了，更引发了我对本地数据的恐慌。

还好，今天一下就登上人人了，在美国的访问速度也尚可，于是一鼓作气把照片全下载 + 整理日期 + 上传 Google photo，终于安心了。下面是傻瓜步骤:

1. Google search “人人备份”，第一条链接应该会带你去一个叫[”人人一键备份“](https://chrome.google.com/webstore/detail/%E4%BA%BA%E4%BA%BA%E4%B8%80%E9%94%AE%E5%A4%87%E4%BB%BD/efddmnffdanhlbgmmblkpfbllampcijp?hl=zh-CN)的 Chrome 插件。类似的 script GitHub 上也不少，这个插件毛病也不少（备份过程中不能离开页面，下载的照片没有日期，error handling 不好少数相册可能是空白），但使用门槛最低无需安装任何代码环境和 library。

2. 在 Chrome 插件部分点击该插件图标，会出现如下图示，点击“点我！去人人网”。登录人人网，确保自己在自己主页，此时此插件会变成如下样子：

![](https://lh3.googleusercontent.com/hyHKJiI6_ufPBbywLCNOjQ6FaRliQjJW9qLAfpb8dI198ICK7MaWR1UKedjfQKix-TuS9qnnELckfbeMDM1MoFQo=w640-h400-e365-rj-sc0x00ffffff)

![](https://lh3.googleusercontent.com/Oh-vidm_MlGIk0WYYWLkrQyjb8hw5lHSk_FM9aFQkIKkhKmQrdaQ70lI5rryaewkLFeDpVMJjDEAvMO6ejsn_s0w2A=w640-h400-e365-rj-sc0x00ffffff)

3. 点击“开始下载“。注意此过程**不要离开本页面也不要点击页面任何部位**，时刻晃一下鼠标阻止电脑休眠。

4. 下载完成后插件会自动保存一个 zip 文件在浏览器默认下载文件夹。解压该文件到理想地点。文件夹内有状态、日志和照片，此处我们只关心照片。

5. 照片内的子文件夹是按人人的相册分的，但是照片的最后修改日期和 exif 信息没有来。如果直接传到 Google Photo 上的话会全挤在“今天”，会非常不好检索。因此我们需要把照片的大致日期 restore。如果你平时只用一个相册，且不会写码去爬人人相册里的上传日期的话，you’re probably screwed， 只能手动修改日期了，也不用继续往下看本文了。而我本人相册是按事件分主题的，所以打算大致用相册最后一张照片日期来粗定位批量修改相册内的日期。

6. 有两样东西要改：1. 照片日期（必须）。2. 文件名（optional）。想改文件名是想自己检索起来方便，因为人人下载下来的文件名是个 random key.

7. 在人人网上寻找照片日期：去“我的相册”，一般一页只显示 40 个相册不方便检索。在浏览器地址栏把“limit=”后面的数字改成一个大于你总相册数量的数字，比如 250，点回车。这样你所有相册都会显示在同一个页面里。然后根据本地备份下来的相册名，cmd + F 用浏览器页内搜索就可以快速定位到该相册，然后 cmd + 鼠标点击在新窗口打开这个相册，随便点开一张照片定位大致上传日期。

8. （Optional）Mac 批量修改文件名：多选想要修改的文件，右键选择 rename/重命名，会出现如下选框。如果将来想要备份到 object storage 的话文件名里不要有空格、中文和_, – 之外的符号。我想要按日期命名，于是设置如下。

![](https://media.douchi.space/douchi/media_attachments/files/110/452/806/136/560/166/original/81ae4b4b5f6bf089.png)

9. 修改文件“最后修改日期”以供 Google photo 识别：Google search ‘bulk modify file modified date’ 前面几个出来的都是 Windows 的软件和 script，最后找了这篇 Mac [shell script](https://nishabe.medium.com/modifying-file-attribute-in-bulk-mac-osx-1723f19e5074)。稍微修改了一下如下：（很简单，手把手，不要看到 script/terminal/command line 就慌。

```
find YOUR-PHOTO-DIRECTORY -print | while read filename; do
touch -t DATE-IN-YYYYMMDDHHMM "$filename"
done
```

- 复制上面 script，打开 terminal（Mac spotlight 搜索：terminal），输入`vi bulk_modify_date.sh`，在键盘上敲入 `:i` 进入插入修改模式，cmd + v 粘贴上述代码（注意前面几个字符会被吞掉，记得补全）
- 在 Finder 里打开你下载备份的文件夹，右键要备份的相册的上一级文件夹选 get info。在“general -> where’ 后面找到你这个文件夹的路径，右键复制。注意路径里不可以有中文、空格、特殊符号等，如果有中文（通常是你的人人名字）就把中间的文件名修改成全英文+下划线的形式。
- 将上面 script 里的 `YOUR-PHOTO-DIRECTORY` 替换成你刚才复制的路径 + `/temp/`，比如 `/Users/username/Documents/renren_backup/temp/`。`DATE-IN-YYYYMMDDHHMM`替换成你之前找到的日期，比如`201002011800` 就是 2010 年 2 月 1 日 18 点。
- 点 ESC 退出编辑模式，在 terminal 输入 `:wq!` 回车保存并退出。
- 在 terminal 输入 `chmod a+x bulk_modify_date.sh` 把刚才的 script 变成可执行文件
- 从 finder 把这个 script 拖拽到 terminal 并回车试运行 script，此时应该会告诉你找不到 temp 这个文件。如果找不到 script 在哪的话，在 terminal 里输入 `open .` 会在 finder 打开 script 所在文件夹。

10. 做好了 script 之后回到刚才下载人人照片的文件夹，缓慢双击第一个要修改的相册重命名该文件夹，cmd c 复制当前相册名方便等下改回来。

11. 回到 terminal，用

!https://s.w.org/images/core/emoji/14.0.0/svg/2b06.svg

键回到前面运行过的命令，找到上一次运行 script 的那个命令。比如

```
/Users/username/bulk_edit_date.sh
```

，回车运行该命令。此时因为你已经把一个 temp，该命令应该能运行。顺手在 finder 里随便点一个图片确认修改日期有没有被改成你之前设定的日期。

12. 回到 Finder，重命名 temp 文件夹，cmd + v 粘贴回还在剪切板里的原本的相册中文名。

13. 对其他相册，重复 10 ～12 步。

14. 在 Google photo 新建一个 renren backup album，把所有改好日期的图片拖进去上传。

![](https://media.douchi.space/douchi/media_attachments/files/110/452/808/060/391/683/original/190731f4fe825694.png)

备份遗失在倒闭公司野鸡服务器上的记忆碎片到 second brain 成功！

恭喜你，现在像我一样找回了几年遗失的记忆，现在可以尽情享受 Google Photo AI 尬识别一些十年前的今天、大学同学们的人脸分类和黑历史们了。

---

Me right now:

（我年轻时候真的有那么喜欢自拍吗，好羞耻……但是年轻时候好瘦

（我操我大一居然还和男生牵着手上台迎新晚会唱过歌？

（我操我和女神的唯一情侣照差点忘了，幸亏今天勤快了！！！

---
{{< hint info >}}
如果您觉得本文对您有帮助，想支持我的博客创作，或者有特定的内容想要看到，或者干脆就想单独聊五毛钱，欢迎点击下面按钮成为我的金主：
{{< /hint >}}
{{< button href="https://www.patreon.com/bePatron?u=46962965" target="_blank">}}成为 Patreon 金主{{< /button >}}
{{< button href="https://ko-fi.com/S6S130C16" >}}在 Kofi 上给我买杯奶茶{{< /button >}}

{{< details "Migrated Comments" open >}}
### Comment by doggieeh on 2021-01-08 16:38:15 -0800
害怕 我宁可让它遗失掉 人人账号早都销了&#8230;

### Comment by Andres on 2021-12-18 16:40:13 -0800
人人又搞了改版，插件现在似乎是不能用了，唉。。。
{{< / details >}}