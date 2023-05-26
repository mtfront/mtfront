---
title: 如何制作一款简单的 chrome 插件
author: 椒盐豆豉
type: post
date: 2022-07-19T07:44:08+00:00
url: /how-to-build-chrome-extension/
ig_es_is_post_notified:
  - 1
categories:
  - 重启电脑
tags:
  - career
  - patreon
  - software engineer
  - tutorial

---
<div id="ez-toc-container" class="ez-toc-v2_0_43 counter-hierarchy ez-toc-counter ez-toc-container-direction">
  <div class="ez-toc-title-container">
    <p class="ez-toc-title">
      Table of Contents
    </p>
    
    <span class="ez-toc-title-toggle"><a href="#" class="ez-toc-pull-right ez-toc-btn ez-toc-btn-xs ez-toc-btn-default ez-toc-toggle" area-label="ez-toc-toggle-icon-1"><label for="item-646f6ace954d4" aria-label="Table of Content"><span style="display: flex;align-items: center;width: 35px;height: 30px;justify-content: center;direction:ltr;"><svg style="fill: #b1a18b;color:#b1a18b" xmlns="http://www.w3.org/2000/svg" class="list-377408" width="20px" height="20px" viewBox="0 0 24 24" fill="none"><path d="M6 6H4v2h2V6zm14 0H8v2h12V6zM4 11h2v2H4v-2zm16 0H8v2h12v-2zM4 16h2v2H4v-2zm16 0H8v2h12v-2z" fill="currentColor"></path></svg><svg style="fill: #b1a18b;color:#b1a18b" class="arrow-unsorted-368013" xmlns="http://www.w3.org/2000/svg" width="10px" height="10px" viewBox="0 0 24 24" version="1.2" baseProfile="tiny"><path d="M18.2 9.3l-6.2-6.3-6.2 6.3c-.2.2-.3.4-.3.7s.1.5.3.7c.2.2.4.3.7.3h11c.3 0 .5-.1.7-.3.2-.2.3-.5.3-.7s-.1-.5-.3-.7zM5.8 14.7l6.2 6.3 6.2-6.3c.2-.2.3-.5.3-.7s-.1-.5-.3-.7c-.2-.2-.4-.3-.7-.3h-11c-.3 0-.5.1-.7.3-.2.2-.3.5-.3.7s.1.5.3.7z"/></svg></span></label><input  type="checkbox" id="item-646f6ace954d4" /></a></span>
  </div><nav>
  
  <ul class='ez-toc-list ez-toc-list-level-1 eztoc-visibility-hide-by-default' >
    <li class='ez-toc-page-1 ez-toc-heading-level-2'>
      <a class="ez-toc-link ez-toc-heading-1" href="https://blog.douchi.space/how-to-build-chrome-extension/#%E8%AE%BE%E5%AE%9A%E7%9B%AE%E6%A0%87" title="设定目标">设定目标</a>
    </li>
    <li class='ez-toc-page-1 ez-toc-heading-level-2'>
      <a class="ez-toc-link ez-toc-heading-2" href="https://blog.douchi.space/how-to-build-chrome-extension/#%E5%88%9B%E9%80%A0%E6%A1%86%E6%9E%B6" title="创造框架">创造框架</a>
    </li>
    <li class='ez-toc-page-1 ez-toc-heading-level-2'>
      <a class="ez-toc-link ez-toc-heading-3" href="https://blog.douchi.space/how-to-build-chrome-extension/#%E6%B7%BB%E5%8A%A0_popup_%E8%8F%9C%E5%8D%95" title="添加 popup 菜单">添加 popup 菜单</a>
    </li>
    <li class='ez-toc-page-1 ez-toc-heading-level-2'>
      <a class="ez-toc-link ez-toc-heading-4" href="https://blog.douchi.space/how-to-build-chrome-extension/#%E6%B7%BB%E5%8A%A0%E9%80%BB%E8%BE%91" title="添加逻辑">添加逻辑</a>
    </li>
    <li class='ez-toc-page-1 ez-toc-heading-level-2'>
      <a class="ez-toc-link ez-toc-heading-5" href="https://blog.douchi.space/how-to-build-chrome-extension/#%E6%B5%8B%E8%AF%95" title="测试">测试</a>
    </li>
    <li class='ez-toc-page-1 ez-toc-heading-level-2'>
      <a class="ez-toc-link ez-toc-heading-6" href="https://blog.douchi.space/how-to-build-chrome-extension/#%E5%8F%91%E5%B8%83" title="发布">发布</a>
    </li>
  </ul></nav>
</div>



短短几年时间，Chrome 作为一款在主流桌面操作系统（Windows，Mac）不内置的第三方浏览器，短短几年时间击败了所有竞争对手，以压倒性优势 <a rel="noreferrer noopener" href="https://gs.statcounter.com/browser-market-share/desktop/worldwide/" data-type="URL" data-id="https://gs.statcounter.com/browser-market-share/desktop/worldwide/" target="_blank">67% 的市场份额</a>稳居桌面端浏览器头把交椅。虽然近年来对其隐私方面顾虑层出不穷，一些 power user 也会试图寻找替代品（Brave，Duckduckgo 之类），但对于绝大多数网民来说还是浏览器的默认选择。

在前端技术越来强大的今天，普通 desktop 用户很多客户端操作都能被网页版替代。拥有庞大的潜在客户群，javascript 上手难度低，浏览器作为运行环境无需担心与系统交互与测试，有 chrome store 管理分发，安装过程也比客户端简单很多，chrome extension（插件）就成了一个对开发者和使用者都轻量、便捷的实用平台。

与此同时，chrome 插件的使用门槛也比让看到代码就头大的用户自己安装油猴 script 低很多，就像跟人安利 app 直接甩 play store 链接肯定比让人下载 apk 容易一样。还有同步的便利（我收到过好几次“为什么不写成油猴 script”的评论……代码就开源在那里，不想走 chrome store 且会用 script 的自然可以去用 script 嘛，反之 store 用户又不能从油猴 script 里轻易变出一个能同步的插件）。

这是拖后了半个月的作业<a rel="noreferrer noopener" href="https://www.patreon.com/posts/jun-2022-bo-ke-67369649" data-type="URL" data-id="https://www.patreon.com/posts/jun-2022-bo-ke-67369649" target="_blank">六月 patreon 博客票选胜出的命题</a>（说实话我完全没想到会有这么多人想看开发相关，论我的读者到底有多少码农）。欢迎金主们去<a href="https://www.patreon.com/posts/69280143" data-type="URL" data-id="https://www.patreon.com/posts/69280143" target="_blank" rel="noreferrer noopener">七月的投票选出接下来的命题：</a>

  * 我的信息摄取探索 2.0
  * 老年码农合理摸鱼经验总结
  * 非程序员掌握了也很有用的小 hack
  * 美国码农前半段职业发展道路（career ladder）

其实我不知道为什么大家会选这个主题，因为 <a rel="noreferrer noopener" href="https://developer.chrome.com/docs/extensions/mv3/getstarted/" data-type="URL" data-id="https://developer.chrome.com/docs/extensions/mv3/getstarted/" target="_blank">Chrome 官方的 Developer Guide</a> 写的还蛮清楚的，也给了现成的例子可以抄。不过既然金主们投了，我就来试图给平时不那么经常写程序，但是对自己开发插件有点兴趣的朋友们 TLDR 一下，用我写过的一个简单插件做为例子手把手走一遍开发简单 chrome 插件的过程。

<!--more-->

## <span class="ez-toc-section" id="%E8%AE%BE%E5%AE%9A%E7%9B%AE%E6%A0%87"></span>设定目标<span class="ez-toc-section-end"></span> {.wp-block-heading}

首先要确定的是，这个插件的功能是什么，它能使哪些用户受益，它的功能是否在浏览器内能够完成。对我来说，开发插件没有什么盈利目的，我也不会把写代码本身当成一项娱乐，因此写插件的唯一目的是自己需要用到这些功能。

我目前上架过两款 chrome 插件：

  * <a href="https://blog.douchi.space/kindle-notes-notion-exporter-chrome-extension/" target="_blank" rel="noreferrer noopener">Kindle Notes 轻松导出导入 Notion</a>
  * <a href="https://blog.douchi.space/mastodon-og-only/" target="_blank" rel="noreferrer noopener">长毛象主页“只看原创嘟文”Chrome Extension</a> 

Kindle notes 导出是我的第一个 chrome 插件，当时刚刚开始<a rel="noreferrer noopener" href="https://blog.douchi.space/information-consumption-reading-tracking-workflow/#reading" data-type="URL" data-id="https://blog.douchi.space/information-consumption-reading-tracking-workflow/#reading" target="_blank">构建自己的读书笔记</a>，手头的实体书都读完了开始试图导入电子版，写过一个自用的<a rel="noreferrer noopener" href="https://blog.douchi.space/we-read-notion-exporter-script/" data-type="URL" data-id="https://blog.douchi.space/we-read-notion-exporter-script/" target="_blank">微信读书笔记导入 Notion 的 python script </a>之后想要写一个 Kindle 的。但微信读书写 script 更偷懒是因为它的笔记导出方法是直接复制到剪切板，然后我再复制到本地文件里。而 Kindle notes 则集中在一个单独网页上，再手动复制下载多了一个步骤，与其找方法下载不如直接在网页处理，遂写成了 chrome 插件。其逻辑非常简单，就是直接 select 笔记条目的 html tag 然后生成一个 csv。

长毛象原创嘟文则是又有墙内用户大批出逃关注请求审不过来，我自己又不想接受只有转发的号关注，长毛象也只提供了 timeline 上 filter 转发而无法在主页和站外只看原创，因此动了写个插件的念头。逻辑跟 Kindle 的类似，找到转发嘟嘟的 html tag 然后直接 hide。

## <span class="ez-toc-section" id="%E5%88%9B%E9%80%A0%E6%A1%86%E6%9E%B6"></span>创造框架<span class="ez-toc-section-end"></span> {.wp-block-heading}

虽然说 developer guide 都是 start from scratch，但是相信大多数程序员都懒如我，最熟练的技能是 copy & paste。我的一般流程是找个足够简单但是能跑起来的例子，然后照葫芦画瓢开始改。网上有大把的开源 chrome extension 可以照抄，<a rel="noreferrer noopener" href="https://github.com/GoogleChrome/chrome-extensions-samples" data-type="URL" data-id="https://github.com/GoogleChrome/chrome-extensions-samples" target="_blank">chrome 官方也提供了一些范例</a>。

以我的 <a rel="noreferrer noopener" href="https://github.com/mtfront/kindle-notion" data-type="URL" data-id="https://github.com/mtfront/kindle-notion" target="_blank">Kindle note exporter</a> 为例子，其实只需要三个文件：

  * `manifest.json` 插件的配置文件，复制<a rel="noreferrer noopener" href="https://developer.chrome.com/docs/extensions/mv3/getstarted/#manifest" data-type="URL" data-id="https://developer.chrome.com/docs/extensions/mv3/getstarted/#manifest" target="_blank">官方教程例子</a>再根据自己要用到的 permission 稍加修改即可
  * `popup.html` 平时在浏览器里点击插件图标会弹出的操作框的 html 文件，随便放个空白页占位。
  * `popup.js` 执行相关逻辑的 javascript 文件

官方的例子还给了 `background.js` ，即在后台运行的代码。因为我的插件功能足够简单不需要后台运行，因此我没有添加。（我的 repo 里还有，估计是当时复制粘贴忘了删）

有了这三个基本文件之后你就可以在本地运行测试，chrome 本身也提供了非常简单的测试方法：

  1. 地址栏输入 `chrome://extensions` 打开插件管理页
  2. 打开右上角的“Developer Mode”选项
  3. 点击“Load unpacked“并且选择你存放刚才三个文件的文件夹

你的新插件就被载入到你本地的 chrome，并且可以实时测试啦。

## <span class="ez-toc-section" id="%E6%B7%BB%E5%8A%A0_popup_%E8%8F%9C%E5%8D%95"></span>添加 popup 菜单<span class="ez-toc-section-end"></span> {.wp-block-heading}

我对这个插件的设想是点击插件打开菜单小窗，上面有简单的实用指南，导出笔记的按钮，插件的 GitHub repo 链接，和我自己的网站链接。因为是自己用的实用工具所以不需要什么 fancy 效果，随手写了个 html table 排下这几段字和 table。配色则是用我喜欢的 IDE theme solarized light 抓取了对应的颜色。

此外，简单明了的 icon 也不能少，不然看着默认的灰色 icon 我都不想点开它测试。因为我的插件是导出 Kindle notes 到 CSV（以便导入 notion）， 我就拿来 Kindle 的 icon 和 notion 的 icon P 了这么一个 图标，竟然还挺满意的（icon 只需要 128 x 128 因此没做高清版）：

<div class="wp-block-image">
  <figure class="aligncenter size-large"><img decoding="async" loading="lazy" width="1024" height="236" src="https://s3.nl-ams.scw.cloud/mtfront-blog/2022/07/1-1024x236.png" alt="" class="wp-image-2027" srcset="https://s3.nl-ams.scw.cloud/mtfront-blog/2022/07/1-300x69.png 300w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/07/1-1024x236.png 1024w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/07/1-768x177.png 768w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/07/1-1536x355.png 1536w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/07/1-2048x473.png 2048w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/07/1-1600x369.png 1600w" sizes="(max-width: 1024px) 100vw, 1024px" /></figure>
</div>

写好 `popup.html` 之后，在 `manifest.json` 里，将图标和其点击动作指向刚刚写好的界面和 logo：

<pre class="wp-block-code"><code>"action": {
    "default_popup": "popup.html",
    "default_icon": {
        "128": "/images/logo.png"
    }
}</code></pre>

刷新 app，刚刚写好的页面正确显示，再进行一些 style 微调，保存所见即所得测试起来很方便，界面部分基本就写完了：

<div class="wp-block-image">
  <figure class="alignleft size-full"><img decoding="async" loading="lazy" width="836" height="706" src="https://s3.nl-ams.scw.cloud/mtfront-blog/2022/07/Screen-Shot-2022-07-19-at-12.08.10-AM.png" alt="" class="wp-image-2029" srcset="https://s3.nl-ams.scw.cloud/mtfront-blog/2022/07/Screen-Shot-2022-07-19-at-12.08.10-AM-300x253.png 300w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/07/Screen-Shot-2022-07-19-at-12.08.10-AM-768x649.png 768w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/07/Screen-Shot-2022-07-19-at-12.08.10-AM.png 836w" sizes="(max-width: 836px) 100vw, 836px" /></figure>
</div>

## <span class="ez-toc-section" id="%E6%B7%BB%E5%8A%A0%E9%80%BB%E8%BE%91"></span>添加逻辑<span class="ez-toc-section-end"></span> {.wp-block-heading}

我不想 deal with authorization & maintain login info，因此决定直接从网页爬去 note 内容。这就要保证用户点击 export 按钮的时候处在正确的页面：https://read.amazon.com/notebook 。在 `popup.js` 添加一个简单的 util function 检查 URL 即可。经过简单检索找到需要的 permission 和如何读取所在页面的 URL。

如果用户不在 note 页面，打开一个窗口将用户跳转去 note 页面即可。从我自己的使用习惯推断，打开插件的时候八成不在 note 页面。因此我又把 html 里 button 的默认 text 换成 go to notes，button onclick action 是跳转页面。

如果用户在 note 页面，button label 换成 export，action 此时需要写核心的导出笔记部分。打开 Kindle notes 网页版 inspect element 找找规律，找到 notes 的相应 tag，iterate 每行将 note 内容推进一个 array 里。

简单检索 chrome extension save csv file，发现一个挺聪明的自动下载方法：

  1. 将内容 join 成一个 Blob 
  2. create 一个看不见的 `<a>` element，把 link 指向刚刚创建的 blob。
  3. 激活这个 link 的 `click()` 事件。

<pre class="wp-block-code"><code>let csv = notes.map(i =&gt; i.join(",")).join("\n");
let csvFile = new Blob(&#91;csv], {type: "text/csv"});
let link = document.createElement("a");
link.download = title + ".csv";
link.href = window.URL.createObjectURL(csvFile);
document.body.appendChild(link);
link.click();</code></pre>

## <span class="ez-toc-section" id="%E6%B5%8B%E8%AF%95"></span>测试<span class="ez-toc-section-end"></span> {.wp-block-heading}

因为一切都是在浏览器中进行的，所以你可以轻松的 `alert`/`console.log` 大法。

打开 manage extension 页面，也可以看到你的测试插件的 error stack trace。

## <span class="ez-toc-section" id="%E5%8F%91%E5%B8%83"></span>发布<span class="ez-toc-section-end"></span> {.wp-block-heading}

如果你不打算在 chrome store 上架，那么恭喜你，你本地测试好的 developer mode 插件已经可以正常使用啦。

不过我还是建议大家上架一下，因为：

  1. 来都来了，说不定发布出去对别人也有用呢？
  2. google developer account 只需要终身 5 刀激活，不像 apple 要 100 刀的年费。买了不吃亏买了不上当。
  3. 上架之后就像其他插件一样可以跟着自己的 Google 账户同步，不用每个设备都重新安装了。

在 <a rel="noreferrer noopener" href="https://chrome.google.com/webstore/devconsole/" target="_blank">https://chrome.google.com/webstore/devconsole/</a> 注册了账号交了 5 刀保护费之后就可以发布插件了。发布插件过程也比较简单，把之前本地的文件打包成 zip 上传之后填一些信息即可。提交之后审核几天就会发邮件告诉你上架了，此时就可以像其他 web store 里的插件一样搜到或者直接链接了。

来都来了顺势给自己俩插件打个广告好了，如果有因为这篇文章发布了自己插件的朋友们也欢迎回来分享哦：

  * <a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/kindle-notes-exporter/ogdkdkhjpdgkaodokpammlabdaohebop" data-type="URL" data-id="https://chrome.google.com/webstore/detail/kindle-notes-exporter/ogdkdkhjpdgkaodokpammlabdaohebop" target="_blank">Kindle Notes Exporter</a>
  * <a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" data-type="URL" data-id="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" target="_blank">Original </a><a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" data-type="URL" data-id="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" target="_blank">M</a><a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" data-type="URL" data-id="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" target="_blank">a</a><a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" data-type="URL" data-id="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" target="_blank">s</a><a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" data-type="URL" data-id="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" target="_blank">t</a><a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" data-type="URL" data-id="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" target="_blank">o</a><a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" data-type="URL" data-id="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" target="_blank">d</a><a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" data-type="URL" data-id="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" target="_blank">o</a><a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" data-type="URL" data-id="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" target="_blank">n</a> <a href="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" data-type="URL" data-id="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" target="_blank" rel="noreferrer noopener"></a><a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" data-type="URL" data-id="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" target="_blank">Toots Only</a>

<hr class="wp-block-separator has-text-color has-background has-quaternary-background-color has-quaternary-color is-style-wide" />

如果您觉得本文对您有帮助，想支持我的博客创作，或者有特定的内容想要看到，或者干脆就想单独聊五毛钱，欢迎点击下面按钮成为我的金主：

<a href="https://www.patreon.com/bePatron?u=46962965" data-patreon-widget-type="become-patron-button">Become a Patron!</a>  
  


**<a rel="noreferrer noopener" href="https://afdian.net/@mtfront" target="_blank"><code>墙内赞助通道：爱发电</code></a>**

<div class="da-reactions-outer TpostID2025">
  <div class="da-reactions-data da-reactions-container-async left" data-type="post" data-id="2025" data-nonce="bb495d180b" id="da-reactions-slot-post-2025"> 
  
  <div class="da-reactions-static">
    <img src="http://blog.douchi.space/wp-content/plugins/da-reactions/assets/dist/loading.svg" alt="Loading spinner" width="48" height="48" style="width:48px; height:48px" />
  </div>
</div></div>

## Comments

### Comment by 马大头 on 2022-07-19 06:01:06 -0700
天啊，好有用！椒盐写得好清晰，对我这种“看到代码就头大”但又刚开始尝试用代码满足自己需求的人十分有启发！

### Comment by 椒盐鸵鸟 on 2022-07-19 08:00:14 -0700
很高兴对你有用！写出来插件了可以回来分享哈哈哈

### Comment by Doggieeh on 2022-07-19 21:57:58 -0700
椒老师写教程 梦回人人网