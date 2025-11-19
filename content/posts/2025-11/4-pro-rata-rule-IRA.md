---
title: Pro-rata rule 和 backdoor roth IRA 在碰到 401K rollover 时的一些坑
author: 椒盐豆豉
type: post
date: 2025-11-18T23:16:00-08:00
url: /pro-rata-rule-IRA/
categories:
  - 重启电脑
tags:
  - money
booktoc: false
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/115/533/073/055/925/107/original/d768ed9a499b9fd7.jpg
imageDes: ""
---

今日上班摸鱼闲逛，突然看到 reddit 某个理财版在讨论 rollover 前雇主的 401K 和 pro-rata rule。定睛一看，卧槽好像我之前手贱瞎操作的时候掉进了这个坑，赶紧和 AI 老师们讨论一番来止损。以下是我的一些结论和操作。

<!--more-->
{{< hint "warning" >}}
⚠️免责申明：本人非 CPA 或税务相关专业，本文非税务建议，仅记录个人观点，如有税务问题请自行咨询税务专业人士。\
文中讨论美国税务，因此有大量中英夹杂，如果有晕夹症请尽早离开。
{{< / hint >}}


首先，**traditional IRA 里千万不要留 after-tax 的钱，要立刻去 roth IRA**，否则增长部分会被税。

“正常”情况下一般人是 contribute pre-tax 的钱到 traditional IRA（作为 401K 的 alternative），或者选择 after tax contribute to roth IRA 赚 tax free capital gain。但收入超过一定限制（2025 年限制是 single $150K family $236K）不能 contribute pre-tax IRA，所以则有了 after tax contribute to traditional IRA，然后再 convert to roth IRA，俗称 backdoor roth IRA.

Backdoor roth IRA 的时候特必须要注意 pro-rata rule，即有的 traditional IRA（包括 traditional, rollover IRA, SEP IRA, SIMPLE IRA 等等） 里的钱不管 pre-tax 还是 after-tax 都是一个 pool，整个池子会按比例变成 pre/after tax。

如果是这种 pre-after tax mixd traditional IRA 里的话，再做 backdoor roth IRA 的时候，相当于 本身走backdoor roth IRA contributete 的 after-tax dollars 有一部分要被当成 pre-tax 的钱而将来被再税一次了。 

因此，**如果要用 backdoor roth 的话，因为这个 pro-rata rule，基本上你的 traditional IRA 就不能当前雇主的 401K rollover destination 了**，否则以后 backdoor roth 会被 double tax。对于前雇主的 401K，有如下几种解决方案：
- 放在前雇主的 401K 里。适用于前雇主的 401K fee 不高且有你想要的投资选项的情况。缺点当然是你要一直开着多一个不能 contribute 的 401K 账户，且更新信息之类的可能不一定灵活。
- 把前雇主的 401K rollover 到新雇主的 401K plan。需要新雇主 401K 支持 roll-in，找 401K provider 客服可以问到。据说大多数主流 401K 提供商是支持的。
- 如果已经像我一样手贱把前雇主 401K rollover 到 traditional IRA了，补救方法是在 12/31 前再 reverse rollover 到现雇主的 401K plan。

401K plan 里选投资项目不灵活的问题如果在 fidelity 的话可以用 brokerage link 解决，setup 也比较简单。

此处注意，**常规操作中”把 401K rollover 到 traditional IRA“的这个选项，对于要用 backdoor roth IRA 的人来说因为 pro-rata rule 所以完全不适用**。你如果不给 context 直接在网上问怎么处理前雇主的 401K 的话经常得出可以 rollover 到 traditional IRA 的结论，我就掉进了这个坑。

也因为 pro-rata rule，所以为了简单起见，**traditional IRA 里千万不要混合 pre-tax 和 after-tax 的钱**。不论哪种情况，要么全是税前要么全是税后会简化很多操作。

以上是我理解的理论部分，下面是我的实际情况：
- for some reason，我的 traditional 401K 里有一万多刀 after-tax money. 这个数额可以在 tax return 的 form 8606 line 14 找到。
- 愚蠢如我，之前应该也 rollover 过前雇主的 401K，所以里面还有一部分 pre-tax 的钱，但是数额整体不多。（也就是说我过去几年的 backdoor roth 其实都白白交了一部分税）
- 今年我为了 consolidate 401K，把两个前雇主大大部头 401K 都 rollover 到了 traditional 401K。所以现在我 traditional IRA 里绝大部分钱是 pre-tax。如果我不今年之内发现，那我将来的 backdoor roth 基本就血亏白交了。

咨询了 chatGPT, claude 和 gemini 之后得出了我现在的补救措施：
- 当务之急，reverse rollover——把 traditional 401k 里的 pre-tax 钱全部都 rollover 到现雇主的 401K。此处感恩 fidelity 一贯靠谱的客服，一通电话之后搞清楚了流程：打电话找到 401K team 开一个 ticket，告诉他们 deposit slip 的准确数额。
- 因为 rollover 需要 liquidate（因为在 IRA 里所以都是 deferred tax 不影响今年税务）。我 pre-tax 占了绝大多数，方便起见把整个账户都 liquidate 了。
- Cash settle 了之后再打电话到 IRA 那边（fidelity 内部应该会给你 route 但今天的客服直接给了我个电话），告诉他们要 roll-in 401K，已经开了 deposit slip。
- pre-tax dollar 都挪走之后，把 traditional IRA 里所有钱都 convert to roth IRA。此处之前放着好多年（捶胸顿足）的 after tax gain 会被税，但及时止损更重要。
- 明年 traditional IRA 会恢复到 clean state，就可以正常只当作 backdoor roth 的通道了。

还不算太糟，只是损失了几年 backdoor roth 的免税 capital gain（六千多刀 * 边际税率 ～= 小几千） + 之前 pro-rata 被 double tax 掉的几年 backdoor roth（应该也小几千之类的？）。今年大搞 rollover 及时发现也算是不幸中的万幸了，未来的几十年 roth IRA 损失都提前预防掉了。

但这件事敲响了警钟：随着工作历史变长、雇主变多和使用的理财、税务手段增加，最简单的“常规”答案可能已经不适用我（和我的很多 peer）了。就 backdoor roth 已经算是常规了，rollover previous employer 401K to traditional roth 也相对常规，但 for whatever reason 我的 traditional IRA 里放着 after tax 的钱并且又手残把前雇主的 pre-tax 401K rollover 了而且又要用 backdoor roth 的情况很多常规指南就不 cover 了，即便每次操作前大致看过规则甚至问过 AI，也不一定能 cover 所有的 edge case。这次的 edge case 其实还没那么 edgy 就已经掉坑了。

Would having a tax professional preparing my tax help me caught this at year one of me having pre-tax dollar in IRA and limit the loss? probably. 但先前用这样的 tax professional 也因为 human error 少交一张表害我补过几千的利息和罚款。只能说是 pick your poision 了。

---

从来不跟 chatGPT 聊任何情绪类支持话题所以从来体会不到大家说的 AI 情绪稳定是很好的 emotional support ，直到今天我开始问这个问题一上来说 blahblahblah, am I screwed？

叉老师：Short answer: You're not screwed - but you do need to fix blahblahblah....

突然有被支持到。（顺便学了一些说话艺术……）