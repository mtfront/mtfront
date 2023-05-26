---
title: How to setup RSS for notion blog using Zapier
author: 椒盐豆豉
type: post
date: 2022-03-28T08:41:23+00:00
url: /rss-for-notion-zapier/
ig_es_is_post_notified:
  - 1
categories:
  - English
  - 重启电脑
tags:
  - tech
  - tutorial

---
<div id="ez-toc-container" class="ez-toc-v2_0_43 counter-hierarchy ez-toc-counter ez-toc-container-direction">
  <div class="ez-toc-title-container">
    <p class="ez-toc-title">
      Table of Contents
    </p>
    
    <span class="ez-toc-title-toggle"><a href="#" class="ez-toc-pull-right ez-toc-btn ez-toc-btn-xs ez-toc-btn-default ez-toc-toggle" area-label="ez-toc-toggle-icon-1"><label for="item-646f6ace24f86" aria-label="Table of Content"><span style="display: flex;align-items: center;width: 35px;height: 30px;justify-content: center;direction:ltr;"><svg style="fill: #b1a18b;color:#b1a18b" xmlns="http://www.w3.org/2000/svg" class="list-377408" width="20px" height="20px" viewBox="0 0 24 24" fill="none"><path d="M6 6H4v2h2V6zm14 0H8v2h12V6zM4 11h2v2H4v-2zm16 0H8v2h12v-2zM4 16h2v2H4v-2zm16 0H8v2h12v-2z" fill="currentColor"></path></svg><svg style="fill: #b1a18b;color:#b1a18b" class="arrow-unsorted-368013" xmlns="http://www.w3.org/2000/svg" width="10px" height="10px" viewBox="0 0 24 24" version="1.2" baseProfile="tiny"><path d="M18.2 9.3l-6.2-6.3-6.2 6.3c-.2.2-.3.4-.3.7s.1.5.3.7c.2.2.4.3.7.3h11c.3 0 .5-.1.7-.3.2-.2.3-.5.3-.7s-.1-.5-.3-.7zM5.8 14.7l6.2 6.3 6.2-6.3c.2-.2.3-.5.3-.7s-.1-.5-.3-.7c-.2-.2-.4-.3-.7-.3h-11c-.3 0-.5.1-.7.3-.2.2-.3.5-.3.7s.1.5.3.7z"/></svg></span></label><input  type="checkbox" id="item-646f6ace24f86" /></a></span>
  </div><nav>
  
  <ul class='ez-toc-list ez-toc-list-level-1 eztoc-visibility-hide-by-default' >
    <li class='ez-toc-page-1 ez-toc-heading-level-2'>
      <a class="ez-toc-link ez-toc-heading-1" href="https://blog.douchi.space/rss-for-notion-zapier/#Why_do_you_need_RSS" title="Why do you need RSS">Why do you need RSS</a>
    </li>
    <li class='ez-toc-page-1 ez-toc-heading-level-2'>
      <a class="ez-toc-link ez-toc-heading-2" href="https://blog.douchi.space/rss-for-notion-zapier/#Step_by_step_tutorial_of_generating_RSS_feed_for_notion_blog_using_Zapier" title="Step by step tutorial of generating RSS feed for notion blog using Zapier">Step by step tutorial of generating RSS feed for notion blog using Zapier</a>
    </li>
    <li class='ez-toc-page-1 ez-toc-heading-level-2'>
      <a class="ez-toc-link ez-toc-heading-3" href="https://blog.douchi.space/rss-for-notion-zapier/#Test_your_RSS_engine" title="Test your RSS engine">Test your RSS engine</a>
    </li>
    <li class='ez-toc-page-1 ez-toc-heading-level-2'>
      <a class="ez-toc-link ez-toc-heading-4" href="https://blog.douchi.space/rss-for-notion-zapier/#Let_your_readers_know" title="Let your readers know!">Let your readers know!</a>
    </li>
    <li class='ez-toc-page-1 ez-toc-heading-level-2'>
      <a class="ez-toc-link ez-toc-heading-5" href="https://blog.douchi.space/rss-for-notion-zapier/#Now_enjoy_writing" title="Now, enjoy writing!">Now, enjoy writing!</a>
    </li>
  </ul></nav>
</div>

RSS has became an almost obsolete concept that most of my friends nowadays never heard of, which is a shame. It&#8217;s simple, clean, accessible with correct setup, and most importantly, a highly productive system for information consumption. 

## <span class="ez-toc-section" id="Why_do_you_need_RSS"></span>Why do you need RSS<span class="ez-toc-section-end"></span> {.wp-block-heading}

Compared to other information consumption form like feed from certain platforms (e.g. Instagram, Twitter) or newsletter, RSS (or atom) has a few clear advantages for consumers:

  1. No sponsored content inserted and pretending to normal content in your feed.
  2. You choose when to read rather getting newsletter pushed to a folder that you never get back to.
  3. No personal information is collected when subscribing. Like receiving broadcast, publisher has no way to trace receiver.
  4. No self-righteous algorithm telling you what order you should be reading your feed and making you miss the content you&#8217;re interested.
  5. User friendly interface provided by Modern RSS clients like Inoreader or Feedly making subscribe and manage feed really easy.

As a content creator, making your site available through RSS means that:

  1. More users will know when you have new content, no matter what platforms they usually use. Indie blogs are hard to keep track of without a universal feed, you can&#8217;t expect your readers to bookmark your website among tons of other blogs they&#8217;re interested in and check all of them everyday.
  2. Less readers miss your content because they happen to not scrolling the social platform you&#8217;re on the exactly the moment you post.
  3. Better performance on reader side and less stress on your server. RSS consuming platforms pull your content once and store on their platform, instead of your server feeding each individual visitor.

While popular blog/news website still generate RSS feed and are easy to subscribe, some of the content creators in this new era choose to publish their blog on non-conventional platform, like notion.

Notion blog is easy to setup and much more flexible than some simple article posting platform like telegra.ph or medium. Thanks to notion&#8217;s database system, content creators can customize their page with various views, filters and templates. Also it&#8217;s free for personal use. The only downside is, it doesn&#8217;t come with RSS feed.

Fortunately, automation workflow platform like Zapier provides an easy and free (for now) solution so that your notion blog (or frankly, any notion database) can generate RSS feed.

<!--more-->

## <span class="ez-toc-section" id="Step_by_step_tutorial_of_generating_RSS_feed_for_notion_blog_using_Zapier"></span>Step by step tutorial of generating RSS feed for notion blog using Zapier<span class="ez-toc-section-end"></span> {.wp-block-heading}

<a rel="noreferrer noopener" href="https://zapier.com/shared/1f9c57a92e22060d33bd891696adaa0402c9b647" data-type="URL" data-id="https://zapier.com/shared/1f9c57a92e22060d33bd891696adaa0402c9b647" target="_blank">You can directly copy and edit this zapier template I setup</a> to generate RSS for your notion blog. It has a trigger and an action:

  1. Anytime a new database item is created in notion (, then):
  2. Create item in feed in RSS by Zapier

Most of the steps should be prefilled, but here&#8217;s a step by step walkthrough:

  1. Connect your notion account to your Zapier account.
  2. Choose the database that your blog (or whatever notion database you want to generate RSS for)
  3. Select the fields you wan to edit in RSS by Zapier. I&#8217;d at least choose: 
      1. Feed URL (this will be the RSS URL you give to your reader to subscribe to, for example if you put in &#8220;**my-rss-feed**&#8220;, your reader will subscribe to `https://zapier.com/engine/rss/{some random id zapier generates for you}/<strong>my-rss-feed</strong>` )
      2. Feed Title (this will be your blog&#8217;s title showing up in reader&#8217;s feed, for example, &#8220;xxx&#8217;s blog&#8221;)
      3. Item Title (this will be each blog&#8217;s title, e.g. &#8220;Today&#8217;s blog post&#8221;)
      4. Source URL (this provides reader an URL to check the original blog post on your notion blog, e.g. the link to the specific post in your notion)
      5. Content (the content your reader&#8217;s getting in their feed)
      6. Automatically Truncate Messages over 10kb? 
  4. Map fields between your customized notion blog and RSS standard format. Zapier will prompt you to choose fields from your actual database. 
      1. For example: on the left, is what my notion blog looks like. On the right is what I would fill in the Zapier workflow. 
      2. Notice that this workflow triggers the moment notion got saved, if you put anything that can be empty on the &#8220;Content&#8221; field in zapier, it may result workflow failure. So instead of putting the whole blog post content, which you maybe still writing when the entry got saved and triggered in zapier, I would just either finish writing on another page and copy & paste at once, or just put some field you&#8217;ll surely fill in the moment you create the entry in notion, for example in my case, the affiliate link to the product I&#8217;m reviewing.<figure class="wp-block-gallery has-nested-images columns-default wp-block-gallery-375 is-layout-flex"> <figure class="wp-block-image size-large">

<img decoding="async" loading="lazy" width="707" height="1024" data-id="1894" src="https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.07.58-AM-707x1024.png" alt="" class="wp-image-1894" srcset="https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.07.58-AM-207x300.png 207w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.07.58-AM-707x1024.png 707w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.07.58-AM-768x1112.png 768w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.07.58-AM-1061x1536.png 1061w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.07.58-AM.png 1390w" sizes="(max-width: 707px) 100vw, 707px" /> </figure> <figure class="wp-block-image size-large"><img decoding="async" loading="lazy" width="1332" height="2084" data-id="1893" src="https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.06.31-AM-1332x1300.png" alt="" class="wp-image-1893" srcset="https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.06.31-AM-192x300.png 192w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.06.31-AM-1332x1300.png 654w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.06.31-AM-768x1202.png 768w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.06.31-AM-982x1536.png 982w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.06.31-AM-1309x2048.png 1309w, https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.06.31-AM.png 1332w" sizes="(max-width: 1332px) 100vw, 1332px" /></figure> <figcaption class="blocks-gallery-caption wp-element-caption">left: Notion database; Right: Zapier setting</figcaption></figure> 

## <span class="ez-toc-section" id="Test_your_RSS_engine"></span>Test your RSS engine<span class="ez-toc-section-end"></span> {.wp-block-heading}

Once these are filled in, you can hit &#8220;send test&#8221;, this will trigger an event as if you created a new entry in your notion blog, and you can copy the Feed URL Zapier gave you to see if it&#8217;s correctly generated, for example `https://zapier.com/engine/rss/{some random id zapier generates for you}/<strong>my-rss-feed</strong>`

You can paste this URL directly in your browser, it should look something like this:

<pre class="wp-block-code"><code>This XML file does not appear to have any style information associated with it. The document tree is shown below.
&lt;rss xmlns:atom="http://www.w3.org/2005/Atom" version="2.0"&gt;
&lt;channel&gt;
&lt;title&gt;椒盐鸵鸟剁手安利数据库&lt;/title&gt;
&lt;link&gt;https://zapier.com/&lt;/link&gt;
&lt;description&gt;This feed is powered by Zapier's handy RSS service.&lt;/description&gt;
&lt;atom:link href="https://zapier.com/engine/rss/12037671/mtfront-shopping-reviews" rel="self"/&gt;
&lt;lastBuildDate&gt;Mon, 28 Mar 2022 08:22:21 +0000&lt;/lastBuildDate&gt;
&lt;item&gt;
&lt;title&gt;解压玩具 Dough Ball&lt;/title&gt;
&lt;link&gt;https://www.notion.so/Dough-Ball-9179bca799e84073addec6c8b9618bff&lt;/link&gt;
&lt;description&gt;https://amzn.to/3IwBi3D&lt;/description&gt;
&lt;dc:creator xmlns:dc="http://purl.org/dc/elements/1.1/"&gt;mtfront&lt;/dc:creator&gt;
&lt;guid isPermaLink="false"&gt;yH0ymBWn80Fdq0w4&lt;/guid&gt;
&lt;/item&gt;
&lt;/channel&gt;
&lt;/rss&gt;</code></pre>

This, is of course not very human readable. But don&#8217;t worry, that&#8217;s just for the convenience of RSS clients which needs a standard input format to display you the content. To get a human friendly result, open your favorite RSS client (<a rel="noreferrer noopener" href="https://www.inoreader.com/" data-type="URL" data-id="https://www.inoreader.com/" target="_blank">inoreader</a> for me), click &#8220;add new&#8221;, choose &#8220;feed&#8221; then paste your feed URL.

<p class="has-quaternary-background-color has-background">
  Your engine is <strong>NOT</strong> live until you send the test and save the zapier!
</p>

## <span class="ez-toc-section" id="Let_your_readers_know"></span>Let your readers know!<span class="ez-toc-section-end"></span> {.wp-block-heading}

Now you&#8217;ve successfully created RSS feed for your notion blog. **Next, remember to provide this feed URL in your notion page to let your readers know RSS feed is available for this notion blog**. 

Since it&#8217;s generated by third party (zapier) and didn&#8217;t come with Notion natively, explicitly tell your readers it&#8217;s available is vital, as user can&#8217;t just copy and paste the blog&#8217;s url into their rss client and get feed automatically like they can for specialized blog platform like wordpress, a lot of popular github based static blogs or a lot of news website.

This is the universal RSS icon. Usually pasting this icon with your feed URL should be sufficient to remind reader where to subscribe (attaching my real blog&#8217;s rss not my notion&#8217;s. I don&#8217;t use notion to blog): 

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://blog.douchi.space/?feed=rss2" target="_blank" rel="noreferrer noopener"><img decoding="async" loading="lazy" width="150" height="150" src="https://blog.douchi.space/wp-content/uploads/2020/11/600px-Generic_Feed-icon.svg_-150x150.png" alt="RSS" class="wp-image-248" srcset="https://blog.douchi.space/wp-content/uploads/2020/11/600px-Generic_Feed-icon.svg_-300x300.png 300w, https://blog.douchi.space/wp-content/uploads/2020/11/600px-Generic_Feed-icon.svg_-150x150.png 150w, https://blog.douchi.space/wp-content/uploads/2020/11/600px-Generic_Feed-icon.svg_.png 600w" sizes="(max-width: 150px) 100vw, 150px" /></a></figure>
</div>

## <span class="ez-toc-section" id="Now_enjoy_writing"></span>Now, enjoy writing!<span class="ez-toc-section-end"></span> {.wp-block-heading}

<hr class="wp-block-separator has-text-color has-background has-tertiary-background-color has-tertiary-color" />

If you find this blog useful and want to support my blog, feel free to:

<a href="https://www.patreon.com/bePatron?u=46962965" data-patreon-widget-type="become-patron-button">Become a Patron!</a>  


<div class="da-reactions-outer TpostID1890">
  <div class="da-reactions-data da-reactions-container-async left" data-type="post" data-id="1890" data-nonce="5f45d6851e" id="da-reactions-slot-post-1890"> 
  
  <div class="da-reactions-static">
    <img src="http://blog.douchi.space/wp-content/plugins/da-reactions/assets/dist/loading.svg" alt="Loading spinner" width="48" height="48" style="width:48px; height:48px" />
  </div>
</div></div>