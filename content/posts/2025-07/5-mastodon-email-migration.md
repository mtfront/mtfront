---
title: 如何迁移 Mastodon SMTP 邮件服务 
author: 椒盐豆豉
type: post
date: 2025-07-15T23:46:00-07:00
url: /mastodon-email-migration/
categories:
  - 重启电脑
tags:
  - mastodon
  - tutorial
booktoc: true
bookComments: true
image: https://douchi.space/oops.gif
---

前两天收到 Sendgrid 的邮件通知，其每天可以发 100 封邮件的免费 plan 即将终结。我的长毛象实例使用了 Sendgrid 的邮件服务，也关闭了所有邮件通知，用不到付费 plan，但有一些基础的邮件还是需要邮件服务的，比如忘记密码、注册邮箱确认等。在大家的推荐下决定转到免费 plan 还是能发每天 100 封的 mailgun。

长毛象设置 SMTP 看似简单但每次都有些小步骤会忘掉，要试错几下才能设置好，记得上次 setup 就卡了一阵。既然刚设置完记忆犹新，顺手来写一篇手把手教程好了。

<!--more-->

## 注册 Mailgun 免费账户
这里注意有个坑是点 `mailgun.com` 右上角的“start for free“进去是不会给免费版选项的，只有 free trial，而 https://www.mailgun.com/pricing/ 页面则有免费 plan，常规注册即可，无需填写信用卡。

## 配置 DNS
登入 mailgun 之后
1. Verify 邮箱
2. 可以忽略 get started 页面，直接点进侧边栏的 sending -> domains
3. 点击右上角“Add new domain“。这个直接填你自己长毛象的二级域名 + 一个随意的前缀即可。比如我的长毛象域名是 `douchi.space`，这里的域名就填 `mg.douchi.space`。此处 mg 可以替换成任何字段。
4. 添加后点击进入这个域名，直接去 `DNS records`页面，把所有 record （Authentication records 需要点击生成）添加到你的 DNS 管理服务（如 GoDaddy, Cloudflare, Namecheap 等等）。这里以 Cloudflare 为例：
   - 登入 cloudflare 之后点进自己的 domain -> DNS
   - 点击"Add record"，把 mailgun DNS records 页面里给你的**所有值**一一添加。此处 mailgun 的 value 对应 cloudflare 的 content。
   - 其它值都按默认选即可，只有 `CNAME` 注意不要勾选“proxied“，proxy status 应该是`DNS only`，否则无法验证。
   - 即便你不需要 tracking & receiving，这几个 record 也是要填的，否则无法验证 DNS。
5. 全部填入后，在 mailgun 的页面点击左上角的“verify”。需要所有值的 status 都变成绿色的`Active`才可以进行下一步。有几个值可能要等几分钟。

## 生成 SMTP credentials
DNS 成功 verify 之后会收到 mailgun 的邮件确认。之后进入 `DNS settings` 下的 `SMTP credentials` tab:
1. 点击“Add new SMTP user`。这里随意给你想要长毛象实例的系统发件人取个名字，比如 admin, notif, noreply 之类的。
2. 生成密码。注意这个密码只会显示一次，保存好等会儿要用。

## 配置长毛象 SMTP
SSH 进自己的长毛象服务器后：
1. `su - mastodon` 登入 mastodon 用户，`cd live`进入长毛象 repo
2. 用你喜欢的编辑器打开配置文件 `.env.production`
3. 因为是迁移邮件服务，所以你的配置文件里应该已经有如下一些值了，修改成你新的 mailgun credentials 并保存
    ```python
    SMTP_SERVER=smtp.mailgun.org
    SMTP_PORT=587
    SMTP_LOGIN={login} # 刚才 mailgun 里生成的 SMTP user 的"login“，看起来像个邮件
    SMTP_PASSWORD={password} # 刚才保存的 password
    SMTP_AUTH_METHOD=plain  # unchanged
    SMTP_OPENSSL_VERIFY_MODE=none # unchanged
    SMTP_FROM_ADDRESS={login} # 可以是刚才的 login，这个会是你的长毛象系统通知邮件的发件人地址
    ```
4. 控制台 `exit` 退出 mastodon 用户回到 root
5. 重启长毛象服务
   ```bash
   sudo systemctl restart mastodon-web
   sudo systemctl restart mastodon-streaming
   sudo systemctl restart mastodon-streaming.service
   sudo systemctl restart mastodon-sidekiq
   ```

## 测试邮件效果 & debug
最简单的方法是打开一个 incognito 浏览器窗口，然后用自己的邮件尝试 reset password。不在邮件里点 reset 的话就不会真的 reset，适合测试。自己能收到重设密码邮件的话说明设置成功了。

如果邮件没有被正确发送，可能是 configuration 哪里出了问题。最简单的 debug 方法是在长毛象设置中进入 `Sidekiq` -> `Retries` 看 failed event。Error message 一般会告诉你是什么问题，看不懂的丢进 chatGPT 即可。我碰到的问题有：
- `Free plan can only send test email`: 没有设置 custom domain 直接用了 mailgun 给的 test domain.
- `Domain not verifed`：等几分钟确认 `Domain settings` 里都是绿色小勾勾 verify 了，并且点进 `Setup` tab 会有选项，收到 mailgun 的确认邮件之后再重试。
- `From address not valid`: 忘了修改 `.env.production`中的`SMTP_FROM_ADDRESS`.

祝大家迁移顺利成功薅上资本家羊毛！