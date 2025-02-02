---
title: 小白快速搭建 WordPress 个人站点手把手教程
author: 椒盐豆豉
type: post
date: 2023-11-30T00:00:00+00:00
draft: true
url: /?p=318
categories:
  - Uncategorized

---
 

最近因为豆瓣审查步步紧闭走火入魔，很多朋友转战到了 Mastodon，但是苦于没有一个地方发布长文。虽然网上教程已经很多了，但对没有意愿和精力研究教程的朋友来说，有时候连关键词都不知道如何搜起，或者鉴选教程是否适合自己也需要一定背景知识。因此，本文旨在让这样的朋友一步一步跟着走下来搭建自己的站点，无需搜集信息。

<p class="has-large-font-size">
  Why wordpress
</p>

WordPress 是一个开源的内容管理框架。开源代表着它的源代码在互联网上免费、公开，任何人遵循开源协议都可以对其进行修改。

其实在互联网资源便利的今天，Wordpress 早已不是唯一的个人站点选择，但因为<a rel="noreferrer noopener" href="https://blog.douchi.space/?p=76" data-type="URL" data-id="https://blog.douchi.space/?p=76" target="_blank">我十几年前第一个 blog 就是从 WordPress 框架的供应商起步的</a>，看到它现在还生命力旺盛经久不衰有社群在维护也颇为感慨，因此无脑选择了它。

当然，现在个人站点也有很多其他流行的选择，自建如 github pages, 第三方托管如同样使用 wordpress 框架的 wordpress.com 和常年在 YouTube 上打广告的 squarespace、wix 等，完全封闭的如 medium、Tumblr 等，走极简“粘贴板”形式的 telegra.ph 和基于跟 Mastodon 一样基于 ActivityHub 但其实没有任何联动功能的剪贴板似的 writefreely 等等，优缺点各有不同，因为我没有全部尝试过，因此在下面简单分析一些我了解的平台和其相应适用的人群。

<p class="has-medium-font-size">
  剪贴板服务（telegra.ph, writefreely）
</p>

**优点**：

  * 最省心，注册即可用，几乎无需任何设置
  * 免费
  * Telegra.ph 随时打开都可以写，无需注册，且在 telegram channel 预览支持较好

**缺点**：

<ul id="block-1df83ed4-801c-41f3-9197-7efa3fd155b3">
  <li>
    完全没有社交属性，不能被 follow，只能靠在其他渠道发链接来被看到
  </li>
  <li>
    不能互动、评论
  </li>
  <li>
    你对自己产生的内容完全没有的“拥有权”，即你发出去的内容还是存在第三方的服务器上的，像 Facebook、豆瓣等普通社交网站一样。如果违反了跟服务商的协议，你的账户有可能被“封号”。
  </li>
  <li>
    没有定制功能，只能适用整齐划一的模版
  </li>
  <li>
    没有定制域名，即博客网址只能是 medium.com/@username
  </li>
  <li>
    毫无拓展性，没有 RSS 等站外订阅功能，只能供同站用户阅读
  </li>
  <li>
    几乎无法导出，也就是说将来换平台迁移非常麻烦
  </li>
</ul>

<p class="has-medium-font-size">
  全封闭博客（Medium，Tumblr 等）
</p>

**优点**：

  * 最省心，注册即可用，几乎无需任何设置
  * 庞大的社群和内容推送可以提供一定的社交属性
  * 免费

**缺点**：

  * 你对自己产生的内容完全没有的“拥有权”，即你发出去的内容还是存在第三方的服务器上的，像 Facebook、豆瓣等普通社交网站一样。如果违反了跟服务商的协议，你的账户有可能被“封号”。
  * 没有定制功能，只能适用整齐划一的模版
  * 没有定制域名，即博客网址只能是 medium.com/@username 
  * 毫无拓展性，没有 RSS 等站外订阅功能，只能供同站用户阅读
  * 几乎无法导出，也就是说将来换平台迁移非常麻烦

<p class="has-medium-font-size">
  第三方托管（wordpress.com，square space、wix 等）
</p>

此处注意 WordPress.com 与 wordpress.org 的区别。.com 是基于 WordPress 框架的第三方托管网站，跟 square space 等没有本质区别，都是“免费部分功能，高级功能收费”的盈利模式。Wordpress.org 则是开源框架 wordpress 的信息站点，本身不提供博客托管服务，也就是你的“内容”是不会存在 wordpress.org 上的。

**优点**：

  * 中等程度省心，只需要像所有社交网络一样注册账号、选择模版即可开始
  * 一定程度上的 customization（部分免费模版、一键购买域名等等）
  * 托管商提供的服务器安全和可靠性保护

**缺点**：

  * 你对自己产生的内容没有完全的“拥有权”，即你发出去的内容还是存在第三方的服务器上的，像 Facebook、豆瓣等普通社交网站一样。如果违反了跟服务商的协议，你的账户有可能被“封号”。
  * 免费服务通常可以定制的内容非常少，如不能完全定制模版、不能跑自己的广告和统计工具、存储空间有限制等，页面上还会有运营方的广告。
  * 付费服务也有一定限制，且是持续付出（一般是 subscription 制），总成本很可能高于自己购买域名和租赁服务器的价格。（如 WordPress.com 要 $4/month 来去除广告和 wordpress logo， $8/month 才能得到更多工具和存储空间；Squarespace 最便宜的付费服务也要 $12/month）

<div class="da-reactions-outer TpostID318">
  <div class="da-reactions-data da-reactions-container-async left" data-type="post" data-id="318" data-nonce="1d02d53fff" id="da-reactions-slot-post-318"> 
  
  <div class="da-reactions-static">
    <img src="http://blog.douchi.space/wp-content/plugins/da-reactions/assets/dist/loading.svg" alt="Loading spinner" width="48" height="48" style="width:48px; height:48px" />
  </div>
</div></div>