---
title: WordPress All In One Wp Security (AIOS) locking cloudflare out
author: 椒盐豆豉
type: post
date: 2022-11-11T06:28:18+00:00
url: /wordpress-all-in-one-wp-security-aios-locking-cloudflare-out/
ig_es_is_post_notified:
  - 1
categories:
  - English
  - 重启电脑
tags:
  - debug
  - wordpress

---
#  WordPress All In One Wp Security (AIOS) locking cloudflare out

I&#8217;m going on a trip tomorrow and not gonna bring my computer, so I decided to take one last check at my WordPress site making sure everything is doing fine. Then I saw recently all the bot like high count visitors are from a narrow range of IP from Singapore. I thought it&#8217;s just some good old crawler draining up my server, so I casually added the range to All In One Wp Security (AIOS)&#8217;s blacklist manager.

Then, without refreshing, I realized I recently setup cloudflare for all my site cuz my other site was DDoS&#8217;ed the other day. Couldn&#8217;t this happen to be cloudflare&#8217;s proxy server right? So I hit refresh. 403. At the same time, my Better Uptime incident alert came.

Bummed by my own stupidity, I think I should just be able to ssh into the server, disable all the plugins as usual, and back to the game. Well, after renaming both `all-in-one-wp-security-and-firewall` and all plugins at `/var/www/html/wp-content/plugins/`, I&#8217;m still getting 403. Usually all the plugin related issue got solved at this step without needing to restart service, I&#8217;m not sure why this time it didn&#8217;t work.

So I start to Google something like AIOS self lockout, trying to find where does it store the blacklist that I can quickly manually edit by command line. No luck.

I tried to disable cloudflare proxy at cloudflare dashboard, no luck. And I&#8217;m too lazy to switch DNS provider back to where I was using before.

I started to poke around more in the plugin&#8217;s folder, and eventually found the file that did the trick: `/var/www/html/wp-content/plugins/all-in-one-wp-security-and-firewall/admin/wp-security-list-locked-ip.php`.Seems like the IPs are stored at a table called `AIOWPSEC_TBL_PERM_BLOCK`. I just commented out <a rel="noreferrer noopener" href="https://github.com/Arsenal21/all-in-one-wordpress-security/blob/master/all-in-one-wp-security/admin/wp-security-list-permanent-blocked-ip.php#L163" data-type="URL" data-id="https://github.com/Arsenal21/all-in-one-wordpress-security/blob/master/all-in-one-wp-security/admin/wp-security-list-permanent-blocked-ip.php#L163" target="_blank">the entire line</a> here in the `prepare_items()` function. Refresh, back online, removed the IP range from blacklist, uncomment the line.

So, that was just a small stupid incident on a random Thursday night 9pm before a trip. 乁། \* ❛ ͟ʖ ❛ \* །ㄏ

---
{{< hint danger >}}
If you find this blog useful and want to support my blog or have a coffee chat with me, feel free to:
{{< /hint >}}
{{< button href="https://www.patreon.com/bePatron?u=46962965" target="_blank">}}Become Patreon{{< /button >}}
{{< button href="https://ko-fi.com/S6S130C16" >}}Buy me a boba{{< /button >}}