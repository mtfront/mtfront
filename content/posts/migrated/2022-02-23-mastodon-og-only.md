---
title: 长毛象主页“只看原创嘟文”Chrome Extension
author: 椒盐豆豉
type: post
date: 2022-02-23T08:11:20+00:00
url: /mastodon-og-only/
ig_es_is_post_notified:
  - 1
categories:
  - 重启电脑
tags:
  - code
  - mastodon
  - project
  - tutorial

---
我把前两天做的能快速在长毛象主页“只看原创嘟文”的小代码转成一个 Chrome extension 啦。<a rel="noreferrer noopener" href="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" data-type="URL" data-id="https://chrome.google.com/webstore/detail/original-toots-only/jmkgmhecpnacpoilpekodceagbidllnj" target="_blank">Google 居然一天就审核通过了！点击这里安装 chrome 插件</a>。

使用方法：

  1. 进入 mastodon 主页（1.1.0 版本新增）或者别人在别人实例上的主页（URL 例如： douchi.space/@mtfront 这种格式的，一般点别人用户名/头像两次可以打开的那个）
  2. 点本 extension 打开界面，然后点 Hide/Show 按钮
  3. 如果对方转嘟过多，你可能需要手动载入更多嘟文再点本按钮，因为是前端 hack 只能 filter 已经载入的嘟嘟。

v1.1.0 版本已添加 timeline filter 更新，Chrome store 审核通过后会自动更新。

<s>timeline filter 的话因为动态载入和所用 class 不大一样需要稍微修改而且不能取消 hide（除非刷新页面），所以我昨天犹豫了一下没加这个功能，大家想要的话可以跟我说。油猴插件同理。</s>

<s>以 Google 审核的尿性 估计还要一周左右才会上架，<a rel="noreferrer noopener" href="https://github.com/mtfront/mastodon-og-only" data-type="URL" data-id="https://github.com/mtfront/mastodon-og-only" target="_blank">想要尝鲜的话可以直接下载代码安装</a>.</s>

<s>不用 git 的话<a rel="noreferrer noopener" href="https://github.com/mtfront/mastodon-og-only/blob/master/mastodon-og-only-v1.0.0.zip" data-type="URL" data-id="https://github.com/mtfront/mastodon-og-only/blob/master/mastodon-og-only-v1.0.0.zip" target="_blank">直接下载这个 zip 然后解压缩</a>.</s>

<s><a rel="noreferrer noopener" href="https://developer.chrome.com/docs/extensions/mv3/getstarted/#unpacked" data-type="URL" data-id="https://developer.chrome.com/docs/extensions/mv3/getstarted/#unpacked" target="_blank">load unpacked extension 方法</a>.</s>

<s>想更无缝/在 Chrome 账户上多器材同步的话就等 chrome store 上架版本吧，到时候我会再来吆喝一声的。</s>

<div class="da-reactions-outer TpostID1868">
  <div class="da-reactions-data da-reactions-container-async left" data-type="post" data-id="1868" data-nonce="620e64821c" id="da-reactions-slot-post-1868"> 
  
  <div class="da-reactions-static">
    <img src="http://blog.douchi.space/wp-content/plugins/da-reactions/assets/dist/loading.svg" alt="Loading spinner" width="48" height="48" style="width:48px; height:48px" />
  </div>
</div></div>