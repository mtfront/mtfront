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
# How to setup RSS for notion blog using Zapier
RSS has became an almost obsolete concept that most of my friends nowadays never heard of, which is a shame. It’s simple, clean, accessible with correct setup, and most importantly, a highly productive system for information consumption.

## **Why do you need RSS**

Compared to other information consumption form like feed from certain platforms (e.g. Instagram, Twitter) or newsletter, RSS (or atom) has a few clear advantages for consumers:

1. No sponsored content inserted and pretending to normal content in your feed.
2. You choose when to read rather getting newsletter pushed to a folder that you never get back to.
3. No personal information is collected when subscribing. Like receiving broadcast, publisher has no way to trace receiver.
4. No self-righteous algorithm telling you what order you should be reading your feed and making you miss the content you’re interested.
5. User friendly interface provided by Modern RSS clients like Inoreader or Feedly making subscribe and manage feed really easy.

As a content creator, making your site available through RSS means that:

1. More users will know when you have new content, no matter what platforms they usually use. Indie blogs are hard to keep track of without a universal feed, you can’t expect your readers to bookmark your website among tons of other blogs they’re interested in and check all of them everyday.
2. Less readers miss your content because they happen to not scrolling the social platform you’re on the exactly the moment you post.
3. Better performance on reader side and less stress on your server. RSS consuming platforms pull your content once and store on their platform, instead of your server feeding each individual visitor.

While popular blog/news website still generate RSS feed and are easy to subscribe, some of the content creators in this new era choose to publish their blog on non-conventional platform, like notion.

Notion blog is easy to setup and much more flexible than some simple article posting platform like telegra.ph or medium. Thanks to notion’s database system, content creators can customize their page with various views, filters and templates. Also it’s free for personal use. The only downside is, it doesn’t come with RSS feed.

Fortunately, automation workflow platform like Zapier provides an easy and free (for now) solution so that your notion blog (or frankly, any notion database) can generate RSS feed.

## **Step by step tutorial of generating RSS feed for notion blog using Zapier**

[You can directly copy and edit this zapier template I setup](https://zapier.com/shared/1f9c57a92e22060d33bd891696adaa0402c9b647) to generate RSS for your notion blog. It has a trigger and an action:

1. Anytime a new database item is created in notion (, then):
2. Create item in feed in RSS by Zapier

Most of the steps should be prefilled, but here’s a step by step walkthrough:

1. Connect your notion account to your Zapier account.
2. Choose the database that your blog (or whatever notion database you want to generate RSS for)
3. Select the fields you wan to edit in RSS by Zapier. I’d at least choose:
    1. Feed URL (this will be the RSS URL you give to your reader to subscribe to, for example if you put in “**my-rss-feed**“, your reader will subscribe to `https://zapier.com/engine/rss/{some random id zapier generates for you}/**my-rss-feed**` )
    2. Feed Title (this will be your blog’s title showing up in reader’s feed, for example, “xxx’s blog”)
    3. Item Title (this will be each blog’s title, e.g. “Today’s blog post”)
    4. Source URL (this provides reader an URL to check the original blog post on your notion blog, e.g. the link to the specific post in your notion)
    5. Content (the content your reader’s getting in their feed)
    6. Automatically Truncate Messages over 10kb?
4. Map fields between your customized notion blog and RSS standard format. Zapier will prompt you to choose fields from your actual database.
    1. For example: on the left, is what my notion blog looks like. On the right is what I would fill in the Zapier workflow.
    2. Notice that this workflow triggers the moment notion got saved, if you put anything that can be empty on the “Content” field in zapier, it may result workflow failure. So instead of putting the whole blog post content, which you maybe still writing when the entry got saved and triggered in zapier, I would just either finish writing on another page and copy & paste at once, or just put some field you’ll surely fill in the moment you create the entry in notion, for example in my case, the affiliate link to the product I’m reviewing.

left: Notion database; Right: Zapier setting

!https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.07.58-AM-707x1024.png

!https://s3.nl-ams.scw.cloud/mtfront-blog/2022/03/Screen-Shot-2022-03-28-at-1.06.31-AM-1332x1300.png

## **Test your RSS engine**

Once these are filled in, you can hit “send test”, this will trigger an event as if you created a new entry in your notion blog, and you can copy the Feed URL Zapier gave you to see if it’s correctly generated, for example `https://zapier.com/engine/rss/{some random id zapier generates for you}/**my-rss-feed**`

You can paste this URL directly in your browser, it should look something like this:

```
This XML file does not appear to have any style information associated with it. The document tree is shown below.
<rss xmlns:atom="http://www.w3.org/2005/Atom" version="2.0">
<channel>
<title>椒盐鸵鸟剁手安利数据库</title>
<link>https://zapier.com/</link>
<description>This feed is powered by Zapier's handy RSS service.</description>
<atom:link href="https://zapier.com/engine/rss/12037671/mtfront-shopping-reviews" rel="self"/>
<lastBuildDate>Mon, 28 Mar 2022 08:22:21 +0000</lastBuildDate>
<item>
<title>解压玩具 Dough Ball</title>
<link>https://www.notion.so/Dough-Ball-9179bca799e84073addec6c8b9618bff</link>
<description>https://amzn.to/3IwBi3D</description>
<dc:creator xmlns:dc="http://purl.org/dc/elements/1.1/">mtfront</dc:creator>
<guid isPermaLink="false">yH0ymBWn80Fdq0w4</guid>
</item>
</channel>
</rss>
```

This, is of course not very human readable. But don’t worry, that’s just for the convenience of RSS clients which needs a standard input format to display you the content. To get a human friendly result, open your favorite RSS client ([inoreader](https://www.inoreader.com/) for me), click “add new”, choose “feed” then paste your feed URL.

Your engine is **NOT** live until you send the test and save the zapier!

## **Let your readers know!**

Now you’ve successfully created RSS feed for your notion blog. **Next, remember to provide this feed URL in your notion page to let your readers know RSS feed is available for this notion blog**.

Since it’s generated by third party (zapier) and didn’t come with Notion natively, explicitly tell your readers it’s available is vital, as user can’t just copy and paste the blog’s url into their rss client and get feed automatically like they can for specialized blog platform like wordpress, a lot of popular github based static blogs or a lot of news website.

This is the universal RSS icon. Usually pasting this icon with your feed URL should be sufficient to remind reader where to subscribe (attaching my real blog’s rss not my notion’s. I don’t use notion to blog). [![](/rss.png)](https://blog.douchi.space/?feed=rss2)

## **Now, enjoy writing!**

---
{{< hint danger >}}
If you find this blog useful and want to support my blog or have a coffee chat with me, feel free to:
{{< /hint >}}
{{< button href="https://www.patreon.com/bePatron?u=46962965" target="_blank">}}Become Patreon{{< /button >}}
{{< button href="https://ko-fi.com/S6S130C16" >}}Buy me a boba{{< /button >}}