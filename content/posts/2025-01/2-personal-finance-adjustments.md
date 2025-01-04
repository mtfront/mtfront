---
title: 重新自动化一下我的现金流 workflow
author: 椒盐豆豉
type: post
date: 2025-01-03T17:12:00-08:00
url: /personal-finance-adjustments/
categories:
  - 重启电脑
tags:
  - money
booktoc: false
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/111/840/617/521/484/222/original/1d935e5f3f116e9e.png
imageDes: "很久以前摄于加州一号公路"
---

我的上一份工作是一个月发两次工资（一年 24 次），因为时间固定，付房租、信用卡之类很方便。再之前的工作大多是两周发一次（一年 26 次），但现金收入没有结余太多，因此工作十年以来我都是工资打到 checking 账户，月初房租房贷自动付款，月末信用卡查账时候顺便手动付款，再有月初和月中两笔 recurring 定投，如果钱多出来再额外手动打入投资账户。

去年底入职新工作，恢复了两周一次发工资，外加现金流增加了，就感觉中间差值的时间让钱放在利率可以忽略不计的 checking 账户里有点亏，来回手动在 HYSA (high yeild saving account)和 checking 之间打又过于琐碎和麻烦。于是趁着新工作，一鼓作气把用了十年的现金流 workflow 连根拔起重整优化了一下。

<!--more-->

我主要做了如下改动：
- {{< tag "收入" >}} `Paycheck` Checking -> HYSA
- {{< tag "支出" >}} `信用卡` Checking -> HYSA，手动还款转为自动还款
- {{< tag "支出" >}} `房租` Checking -> HYSA，本来就是 BILT 信用卡付房租，跟着一起改了
- {{< tag "储蓄" >}} `定投` Checking -> HYSA
- {{< tag "储蓄" >}} `Emergency Fund` Checking 剩的钱多了手动打 HYSA -> HYSA 的池子里本来就有个“底”

现在两个 Checking 和 HYSA 两个账户各司其职（按大约金额大小排序）

|  Checking| HYSA |
|  - | - |
| {{< tag "支出" >}} 付房贷 | {{< tag "储备" >}} Emergency fund | 
| {{< tag "收入" >}} 收租 | {{< tag "收入" >}} 工资 |
| {{< tag "收入" >}} Venmmo、PayPal| {{< tag "支出" >}} 定投 |
| {{< tag "支出" >}} ATM 提款 | {{< tag "支出" >}} 房租（信用卡） | 
| {{< tag "支出" >}} 信用卡付不了的杂费 | {{< tag "支出" >}} 信用卡 | 
| {{< tag "收入" >}} Patreon/Kofi | {{< tag "收入" >}} 利息 |
| {{< tag "收入" >}} Affiliate | {{< tag "收入" >}} 银行给的各种 bonus |
| {{< tag "收入" >}} Misc | |

过去这么多年来都没做这个 automation 的原因是很多东西连在 checking 账户上，我的绝大多数信用卡也都是它家的还款方便，就总懒得改。但现金流赚不了利息的差额大了后就一鼓作气改成自动了，反正自动还款也无所谓账户在不在一家银行方不方便了。唯一的例外是房贷，因为房租是用 checking 收的所以房贷就放着没动，再加上上面列出的各种杂七麻八的收入，把 checking 账户平时的余额维持在一个比较低的能应对临时取款需求的数额即可。如果时间长了 running low 再手动从 HYSA 转账。

HYSA 这边就更无缝了。因为 emergency fund 本来就在里面，所以 buffer 很大，可以放心地让自动还款从里面扣不用盯着余额了。如果 HYSA 数额不断增长说明我近期没有消费，额外剩下来的钱再手动转入投资账户即可，但基本上调整好了之后几个月看一次即可，反正里面利率也不错多出来的钱放着也没有在 checking 里心疼。

具体操作方面：
- HYSA 我用的是 Marcus，加上 referral 现在是 4.9% 的 APY（0.25% * 4 为了简单计算约等于 1%）。之前介绍过很多遍了，打钱到 checking/投资账户也都是当天/1 business day 到账。我不需要从境外收钱（小红书上看到境外收钱被封号的），也没有用它当 debit 账户用过的需求不需要 branch，每年还基本都有存 10K 三个月送 100 的小羊毛，背靠高盛大银行不用担心野鸡 HYSA 跑路拿不回来钱（比如前阵子爆掉的 Yotta）满足我的需求刚好。几年前用惯它之后把其它乱七八糟的 HYSA 都 consolidate 到它一家了。新年 referral 名额又开了，感兴趣的用我的 [**referral code**](https://www.marcus.com/share/FAN-NS4-YMS9) 可以也得到 3 个月的 promotional APY.
- 定投账户用的还是 M1 Finance。其实要是 financial savvy 的话随便用投资账户都行，但大多数人定力不行能自由买卖就会瞎操作然后玩赌博投机而不是投资。M1 Finance 自己设置一个 funds 比率转账进去自动买的模式很适合定投。也是几年前用惯了之后就把除养老账户之外的所有花哨的投资账户都 consolidate 进来了。它的 referral bonus 浮动，现在是存 10K 返 $75 聊胜于无 [**referral code**](https://m1.finance/3k2CE5UGXvjS) 在此。不过定投这事儿说滥了的 time in market beats timing the market 在薅羊毛也适用，早规律投资早赚钱。

另外，新的一年了，大家记得 contribute to IRA & 调整 401K & HSA contribution. 恭喜发财！ {{< emoji "https://emojis.slackmojis.com/emojis/images/1643515259/12808/meow_dj.png?1643515259" >}}