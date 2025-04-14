---
title: 冲着生产力来，带着娱乐性走，曲面宽屏第二次尝试——Dell U4025QW
author: 椒盐豆豉
type: post
date: 2025-04-13T22:45:00-07:00
url: /curved-wide-sceen-dell-U4025QW/
categories:
  - 喜欢就买
tags:
  - review
  - tech
  - 消费主义陷阱
bookToc: true
bookComments: true
image: "https://media.douchi.space/douchi/media_attachments/files/113/649/940/703/956/861/original/320cd00f7f2a6d25.png"
---

从消费主义（暂时）毕业了好久没写测评了，也好久没写 [desk setup]({{< relref "/posts/2023-archive/2023-01-05-2023-desk-setup" >}}) 了，不过一是这两年生产力工具没有太大变化，二是前阵子写过 [Tech I use everyday]({{< relref "/posts/2024-12/4-tech-i-use-everyday" >}}) cover 掉了大部分 desk setup，就不赘述了，刚好一看新屏幕用了 4 个月了，流程也都稳定了，那就来直接写写这两年硬件年生产力工具最大的变化——[显示器](https://amzn.to/4gc1K3B)吧。

<!--more-->

## 换屏契机和选择
其实旧的那台 [LG 32UL950](https://amzn.to/3G92U3b) 是 2020 年刚开始居家办公的时候买的，也才将将用了不到 5 年（虽然以我的使用频率每天 8 小时+ 也算利用率很高了），也还算是满意—— 32 寸够大，16:9 4K 分辨率适配率高，不喜欢用双屏的我分屏看代码还是全屏打游戏看视频都不错。萌生了换屏的想法主要是因为：
- 导火索：去年底不知道是不是西雅图 storm 的时候电压不稳造成了点损坏，那阵子开始屏闪，给了我换屏的借口（不过后来又自己好了）
- 最重要的原因：屏幕没有自带 KVM，休息了大半年又回来工作有了切换个人电脑、工作电脑和个人 gaming PC 三台电脑的需求之后每次都要键盘、鼠标、屏幕按三个按钮，略嫌麻烦。并且因为都是蓝牙连接，有一定几率唤醒失败还得手动插拔/打开笔记本屏幕唤醒。
- 32 寸 16:9 的比例竖着的内容其实稍多，横向非常偶尔有三屏需求时候不够用。
- 屏幕高度决定了有一些阅读区域不在脖子最舒服的部分。

![之前服役了近 5 年的显示器](https://media.douchi.space/douchi/media_attachments/files/113/692/805/755/613/275/original/b222d4181f0e4b03.png)

其实对于无缝切换的问题，外接 KVM 应该是更经济实惠普适的选择，不过我嘛，消费主义借口，而且想说都什么年代了显示器应该有软件解决方案了吧。稍微一 research 发现还真有，心立刻就飞了。当然后来没有真的用上，这是后话。

最后选中的现在这台 [Dell U4025QW](https://amzn.to/4gc1K3B) 有如下一些卖点：
- 有软件分屏（PIP/PBP）支持，可以两台电脑同时显示和无缝拖拽。这是最初吸引我的功能（后来证明效果不佳）
- 自带 KVM，可以实现所有外接设备（摄像头、屏幕灯、麦克风、键盘鼠标等）无缝和所显示的电脑切换。而且它屏幕下面有个弹出框有 USB-A 和 USB-C 能直接从前面插非常方便。
- 21:9 的 40 寸 5K 屏，上下的高度刚好是最优的视线范围，不用再仰头低头造成脖子疲劳了。
- 曲面的曲率没有很大，观感会让你忘了是曲面但又能不费力地看到边缘内容。我非常不喜欢曲率大的曲面屏，这台曲率较小才列入了考虑范围。
- IPS black panel，画质不输 OLED 但没有 OLED 烧屏的问题。

## 一些前期 setup
- 因为屏幕自带 KVM hub，以前我都是蓝牙键鼠直连几台电脑然后用鼠标上的按键切换，现在就找出 receiver 直接接屏幕上了。一个比较令人无语的发现是我的鼠标是 [MX Master 3](https://amzn.to/39okewZ)，用的是罗技的老 unifying receiver（家里有），键盘是 [MX Keys Mini](https://amzn.to/4lubFVN)，用的是罗技新出的 [bolt receiver](https://amzn.to/4cwdMEx) ，然后这个新的东西它不兼容旧的设备你敢信……气得我差点想要一怒之下把鼠标也更新了。最后还是理智一下，把俩 receiver 都插屏幕上了。反正屏幕上口多……
- 后面虽然有多个 type-c，但其实只有一个是 thunderbolt 4 downstream 可以一线接电脑输入输出 + 140W 供电。
  - 这根线我接在了个人笔记本上（因为个人笔记本经常拔下来拿走）。
  - Windows PC 也好说，不插拔，直接接了 DP 口，键鼠我手动切换。
  - 公司电脑就只好接 upstream type-c 连屏幕走数据（键鼠摄像头和 hub 的数据）+ HDMI 线走视频 + 另外接一个 type-c 的电源。

这么折腾下来其实可能还不如使用外接 KVM 优雅。都什么年代了为什么这么贵的屏幕还不直接配 3 条 upstream thunderbolt 4……我只是想要两台 mac + 一台 windows PC 无缝衔接一个屏幕而已又不是想要天上的星星！这个需求很 niche 嘛？！{{< emoji "https://emojis.slackmojis.com/emojis/images/1643515632/16550/meow_googlytrash.png?1643515632" >}}

软件方面几个 quality of life improvement:
- [Monitor Control](https://github.com/MonitorControl/MonitorControl) - 键盘直接控制屏幕亮度和音量。
- [Youtube Windowed FullScreen](https://chromewebstore.google.com/detail/youtube-windowed-fullscre/gkkmiofalnjagdcjheckamobghglpdpm) - 屏幕竖向空间减少了浏览器那个大边框外加 YouTube outrageous 的 engagement hack 非要不竖全屏显示二是下面留白就很碍眼了，又不是所有视频都想全屏。搜了一下发现了这个 chrome 插件。
- 另外 M1 芯片推不了 120Hz 刷新率，有人发了[解锁 90hz 方法](https://www.reddit.com/r/ultrawidemasterrace/comments/1bciq31/dell_u4025qw_create_custom_edid_to_get_100_hz/)，不过我还没折腾。60Hz 刷刷网页看看 YouTube 够了，反正打游戏连的 PC 能推 120hz 就行。

## 单独说说分屏功能吧
### 令人失望的 PBP/PIP
一开始我对软件分屏抱以厚望。我想要的“生产力”主要功能就是在家摸鱼的时候小窗（ PBP 分屏或 PIP 浮窗）放副屏，这样就可以比如说主屏个人电脑看剧摸鱼副屏工作电脑看个 build 或者消息，或者反过来偶尔上班时候要查个个人信息不想在公司电脑上登陆就不用切换了直接小屏的个人电脑完成。

直接使用普通 PBP/PIP （旧的显示器其实也有）的问题是鼠标键盘要来回切换。这台显示器的卖点是软件可以直接让你无缝切换，就像一台电脑接了两台显示器一样，键盘移动到哪个屏幕位置就操纵的是哪台电脑（颇有苹果的 continuity 的意思）。要达成这个功能需要两台电脑都装上 Dell 的 device manager。这个软件还提供了一些快捷键预设（比如切换主屏副屏、切换键鼠所控制的屏幕、切换两个屏的比例等）看起来非常 handy。

但实际使用当中我发现体验不稳定导致实用性几乎没有：
- 跨屏有时能识别，有时识别不了，大多数时候识别不了。
- Device manager 的软件快捷键时而有反应时而无。
- 这个软件对屏幕的一切操作（切换比例，对调主副屏等）都是硬件上断联，再重新接入。就跟你把电脑拔了、睡眠、再插回去一样。而我们都知道这个操作并不是无缝的， 会有个几秒的延迟。

结果就是在用了几天之后我怒卸了两台机器上的 device manager，就当这个功能不存在了。

### 意外惊喜 Screen Partition 虚拟双屏
但是，意外的发现更实用的功能竟然是 screen partition：即把一台电脑的输出信号像接了两台显示器一样使用。这个就非常顺滑了，就像真的接了两台屏幕一样，所以拖拽和移动鼠标什么的都是无缝的。各个 partition 可以互相不受影响地全屏、调整分辨率等偏好，就像真的接了两台显示器一样。

我最常用的 use case 是打游戏的时候把屏幕分成 75%/25%：这样左边是一个接近 16:9 的游戏都可以完美适配全屏的正常 4K 屏，右边是一个竖屏可以放 discord 和网页等，全屏打游戏时候无需切屏和 overlay 就可以看消息或者等载入时候刷网页，再也不怕错过消息或者 overlay 影响观感/截图，也不用额外带 5K 的分辨率，还解决了有些游戏宽屏适配不佳可能会有黑边的问题。游戏里截出来的图就是完美的正常全屏效果：
![KCD2 细腻的画面在这个显示器上效果可太好了](https://media.douchi.space/douchi/media_attachments/files/114/253/485/950/975/597/original/b4fe5bd2a3aae51d.jpeg)

## 总结一下优缺点
### Pros
- 21:9 5K 屏完美生产力，两屏甚至三屏写码看文档再也没有 16:9 屏的局限。
- 高度刚好，曲率也刚好，没有曲面屏完美角度狭窄的问题，也没有 16:9 屏脖子累的问题，用了几个月觉得看东西真的轻松了很多，同样的空间更 accessible 地装下了更多信息。
- 自带 KVM 两台电脑都能共用摄像头和麦克风很方便。有了硬件连接唤醒电脑也比之前蓝牙唤醒更靠谱。
- 做了防反光处理的哑光屏之感真不错。IPS black 显示效果很好。
- Screen Partition 虚拟双屏打游戏时意外实用。
- 前置接口方便，偶尔要拷个东西直接插屏幕即可。
- 21:9 全屏看电影不要太爽，反倒是之前担心的 16:9/18:9 的两边黑边不大容易注意到。偶尔遇到分屏游戏用上全部的分辨率就更爽了。

![全屏打 Split Fiction 游刃有余视角更宽阔了](https://media.douchi.space/douchi/media_attachments/files/114/204/807/610/993/376/original/38cb48a330c5824d.jpeg)

### Cons
- 软件 PBP/PIP/Continuity 不尽如人意。
- Thunderbolt 4 upstream 只有一条，超过一台笔记本（因为台式机线多无所谓）就得多点线插了。
- 自带的音响不如前一台屏幕。我甚至考虑要不要再败套桌面小音箱了…… 但是：
- 横向占的空间更大，桌面空间更紧张了。

整体而言是比较满意的一次电子产品升级了。