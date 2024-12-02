---
title: Mastodon 长毛象服务器迁移教程（非 Docker）
author: 椒盐豆豉
type: post
date: 2024-12-01T21:49:00-08:00
url: /mastodon-migration-tutorial/
categories:
  - 重启电脑
tags:
  - mastodon
  - tutorial
booktoc: true
bookComments: true
image: https://blog.joinmastodon.org/2018/06/why-activitypub-is-the-future/ezgif-2-60f1b00403.gif
imageDes:  "image from Mastodon blog https://blog.joinmastodon.org/2018/06/why-activitypub-is-the-future/"
---

今年黑五 contabo 打折薅便宜服务器终身折扣又磨刀霍霍又迁移了。忘了为啥上次迁移那么顺利，这次因为官方 document 写得不清楚和自己操作失误一开始有点小问题折腾了两回，索性再写一个直接复制粘贴（尽量）无废话流程教程好了。

<!--more-->

## Contabo 体验
这段是去年底到今年底用 contabo 的体验，不想选购服务器只想看教程的可以直接跳到下一章。

我一开始自己建站是临时起意，不喜欢折腾因此直接跟着当时手头的小白教程用了 digitalocean 的预装 mastodon image 稳定性和 GUI 的易用性都不错就三年再也没动过身，不过随着升级和用户增多最便宜的服务器越来越不够用，升了几回配置之后月费高达 18 刀，而且性能也不够用要不时重启，再下一档 24 刀觉得有点不划算，遂在去年底我克服了惰性心理把我的 [mastodon 实例迁移]({{< relref "/posts/2023-12/9-mastodon-migration" >}})到了便宜大碗的 contabo 上，服务器成本砍到了原来的 1/3。

其实当时一开始看的是另一家比较小众的服务器供应商，价钱更便宜但体量较小测评网站上似乎也有 availability 的抱怨，稍微了搜了几家测评之后选了 fediverse 似乎有很多实例在用、评分也高一些的 contabo。

入手前已知它家 availability 会低一些，一年会碰到那么一两次 30 分钟的 maintenance。过去一年确实碰到了两次，还会提前告知，觉得这个价格完全可以接受。另一个缺点是管理界面确实非常原始，一登录进去就理解了钱省在了哪里。不过鉴于我买的最便宜的 VPS 也比我之前用的性能高不少（4 核 CPU 6G RAM 200G SSD，之前在 digitalocean 的印象中是 2 核 2G RAM 160G SSD），跑个 1000 人的长毛象完全不用像以前一样时不时看 CPU usage，也无需加 swap 了，因此没有 fancy 洁面也无所谓了，一年都登录不了几回。

今年黑五收到它们折扣促销邮件，我用的最便宜服务器（跑我这个 1000 人小长毛象实例绰绰有余）一年也能省 25 刀（原价 5.5 + 美国服务器 location surcharge 1.15 = 6.65. 打折 4.95 免 location surcharge 免 setup 外加年费折扣 -5.5），折扣还是终身的，还比原来多了 200G SSD。过去一年用得挺满意，犯懒纠结 2 秒之后就立刻入手了准备迁移了。

## 准备工作
因为我自己的站有一些修改不是用原装的，外加服务器也只做长毛象一个用途，因此 docker 多加一层徒增麻烦没有优势，我就还是使用非 docker 安装了。官网的[安装教程](https://docs.joinmastodon.org/admin/install/?utm_source=blog.douchi.space)和[迁移教程](https://docs.joinmastodon.org/admin/migrating/?utm_source=blog.douchi.space)中有一些小细节有疏漏/模糊导致我踩了些坑，因此手把手把我的迁移过程放过来，如果跟我一样是非 docker 到非 docker 迁移的话希望可以行对行直接复制粘贴无脑操作。

- 确保你能 ssh 到旧服务器和新服务器上，以下的所有命令行服务都是在 terminal 中运行。
- 确保你手边有能随时复制粘贴的新服务器 IP 地址
- 确保你能登入你的 DNS 管理商（我这里是 cloudflare）以便更新 DNS record
- **重要⚠️** 因为很多命令都要 run 很长时间，直接裸 SSH session 的话电脑休眠就会断掉，因此强烈建议使用 `screen`（Linux 自带）或者 `tmux`（使用 `apt install tmux` 安装）**运行所有下面命令**，否则很容易丢失进度。我使用的是 `tmux`，如果断网需要重连的话只需要用 `tmux a` 就能恢复上一个 session。

因为这个过程中最耗时的工作是备份 postgres 和恢复备份，因此要最短化总迁移/服务下线时间的话我建议先在旧机器上开始 postgres 备份工作，而不是提前准备好新机器。以下的流程是按我这个多线操作的过程来的。

## 迁移流程
以下用 `旧` 和 `新` 区分命令是在旧服务器还是新服务器上运行。`root` 和 `mastodon` 区分是在服务器上以 `root` 用户还是 `mastodon` 用户（既 `su - mastodon` 之后）运行命令。如果要从 `mastodon` 用户退出到 `root` 的话使用 `exit` 即可。

1. `旧` `root` 停止长毛象服务 `systemctl stop 'mastodon-*.service'` - 运行之后你现有的长毛象服务会下线，登陆网址会投出 `502` error。
2. `旧` `mastodon` 备份你的数据库 `pg_dump -Fc mastodon_production -f backup.dump`。我这里没有为数据库用户设置密码，如果你设置了的话请参考[官网教程](https://docs.joinmastodon.org/admin/migrating/#dump-and-load-postgresql?utm_source=blog.douchi.space)暂时去掉密码省事。这个过程需要一定时间，此时可以去新服务器上开始安装操作：
3. `新` `root` 运行[官网教程](https://docs.joinmastodon.org/admin/install/?utm_source=blog.douchi.space)上的所有安装。我这里全复制过来就不区分是什么了，想分步查看的话可以去原教程看。
```shell
apt install -y curl wget gnupg apt-transport-https lsb-release ca-certificates
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_20.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list
wget -O /usr/share/keyrings/postgresql.asc https://www.postgresql.org/media/keys/ACCC4CF8.asc
echo "deb [signed-by=/usr/share/keyrings/postgresql.asc] http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/postgresql.list
apt update
apt install -y \
  imagemagick ffmpeg libvips-tools libpq-dev libxml2-dev libxslt1-dev file git-core \
  g++ libprotobuf-dev protobuf-compiler pkg-config gcc autoconf \
  bison build-essential libssl-dev libyaml-dev libreadline6-dev \
  zlib1g-dev libncurses5-dev libffi-dev libgdbm-dev \
  nginx nodejs redis-server redis-tools postgresql postgresql-contrib \
  certbot python3-certbot-nginx libidn11-dev libicu-dev libjemalloc-dev
corepack enable
adduser --disabled-password mastodon
```
5. `新` `root` 配置 postgres。
   - 根据你的机器配置在 [pgTune](https://pgtune.leopard.in.ua/#/?utm_source=blog.douchi.space) 上生成 postgres 配置文件，然后
   - 修改本机上的 `/etc/postgresql/17/main/postgresql.conf` 文件（不熟悉 vim 操作的话可以去简单学习一下或者自行搜索别的 linux 上的文本编辑器）
   - 运行 `systemctl restart postgresql` 重启 postgres 使新设置生效
   - `sudo -u postgres psql` 在 prompt 里输入 `CREATE USER mastodon CREATEDB;` 创建新数据库用户，然后 `\q` 退出。
6. `新` `mastodon`（用 `su - mastodon` 登入几步前新创建的 mastodon 用户之后）下载 Mastodon 代码并且放到 `live` 文件夹下（也可以不叫这个名字，但是官方的所有命令都是叫这个名字所以为了方便直接复制就好没必要改名）。
   - `git clone https://github.com/mastodon/mastodon.git live && cd live` 此处注意如果你运行的是自己修改过的版本而不是官方原版的话，把 github 那个链接换成你自己 repo 的即可。
   - 然后换到你现在在用的版本 `git checkout {YOUR_BRANCH}`。（官方教程给的是自动抓到稳定最新版，但我一直有 customize 而且有点嫌弃最新版的 UI 所以是自己的 branch。
7. `新` `mastodon` 继续安装各种 dependency，这里就不分步了，感兴趣它们是干嘛的可以自己去看官方。
```shell
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec bash
git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
RUBY_CONFIGURE_OPTS=--with-jemalloc rbenv install
bundle config deployment 'true'
bundle config without 'development test'
bundle install -j$(getconf _NPROCESSORS_ONLN)
yarn install
``` 
8. `旧` `mastodon` 此时旧服务器上备份应该差不多结束了，把 backup 文件复制到新服务器上。这个步骤顺序可以和 7 互换。`rsync -azv ./backup.dump root@{新服务器 IP}:/home/mastodon/live/backup.dump`
9. `新` `mastodon` 在新服务器上建立新 database `createdb -T template0 mastodon_production`
10. `新` `mastodon` 恢复备份 `pg_restore -Fc -j {CPU 核数} -U mastodon -n public --no-owner --role=mastodon -d mastodon_production backup.dump`。这一步会花很久，我 4 核 CPU 5.8G 左右的 dump 数据恢复了大概一个半小时，与此同时可以在旧服务器上拷贝一些文件过来，不会互相影响：
11. `旧` `root` （如果在 mastodon 用户里的话用 `exit` 退出先）保存 redis。
```shell
redis-cli
SAVE
EXIT
systemctl stop redis-server.service
```
12. `旧` `root` 复制下列文件到新服务器上。
   - Redis `rsync -avz /var/lib/redis/ root@{新服务器 IP}:/var/lib/redis/`
   - Nginx 配置 `rsync -avz /etc/nginx/sites-available/ root@{新服务器 IP}:/etc/nginx/sites-available/`
   - SSL 证书，官网教程用的是 let's encryypt 生成免费证书并且自动 renew，但我的出了些问题总要手动修复，于是用的是 cloudflare 生成的 10 年证书，省事多了。我把证书存放在了 `/etc/cloudflare/`文件下，直接复制过去 `rsync -avz /etc/cloudflare/ root@{新服务器 IP}:/etc/cloudflare/`。旧站 nginx 已经在用同一个证书了，无需重新生成或者修改配置。
   - mastodon 配置文件：`mastodon`(切换用户 `su - mastodon && cd live`) `rsync -avz ./.env.production root@{新服务器 IP}:/home/live/.env/production`
   - 如果你的媒体文件没有使用 object storage 的话还需要复制 `/public/system/ ` 下面的文件。用了 object storage （推荐）的话可以跳过这一步。
13. `新` `root` 等漫长的 `pg_restore` 运行完之后进行如下操作：
   - Nginx 链接 `ln -s /etc/nginx/sites-available/{你的站名} /etc/nginx/sites-enabled/{你的站名}`，每个人配置不一样，反正就 `sites-available` 下你有的都创建一遍链接就好。
   - 给 mastodon 用户文件读写权限 `chmod o+x /home/mastodon`
   - 重启 `nginx` `systemctl restart nginx`
   - 复制 systemd `cp /home/mastodon/live/dist/mastodon-*.service /etc/systemd/system/`
14. `新` `mastodon` compile assets `cd live && RAILS_ENV=production bundle exec rails assets:precompile`
15. `新` `root` 启动服务！
```shell
systemctl daemon-reload
systemctl start redis-server  
systemctl enable --now mastodon-web mastodon-sidekiq mastodon-streaming  
systemctl restart nginx
```
16. 在你的 DNS 管理商里将 DNS record 更新到新服务器 IP。此时你的新服务器已经正常上线可以使用了！无需等待后面几步完成。
17. `新` `mastodon` 重建 feeds。 `cd live && RAILS_ENV=production ./bin/tootctl feeds build`。注意这一步是在更新了 DNS 之后进行的，否则可能会无法 generate。官方教程没说，我第一次迁移完还没更新 DNS 就运行了这一步，结果生成不了，还以为我迁移的有问题。
18. `新` `mastodon` 如果使用 elasticsearch 的话要重新 deploy index `RAILS_ENV=production ./bin/tootctl search deploy`

## 后记
长毛象迁移过程相对容易，除了耗时之外其实比升级还即插即用。我的站点 `pg_dump` 后 5.8G 的大小，两边服务器都是 4 核 6G RAM + SSD，按照上面的平行操作耗时总计一个半小时左右（不包括重建 feed 时间）。最容易出错的地方也无非是哪些命令在哪个用户下运行，database 备份，以及 nginx & SSL 的配置。为了让自己和大家下次迁移因为官方 document 写得不明确而做无用功踩坑，这次就把自己迁移的全过程记录下来了，希望以后平行迁移能省心一些。

之前实例站点更新是在 discord 上的，但确实这种必须要帐号登录的平台做公开状态更新很不合适，不常用这个 app 的总不能专门为了看更新就下个 app 吧，基本每次迁移/maintenance 都有人在别的平台问站是不是挂了。感觉还是得用未登录可见有网页版的比较合适。

也顺便跟风搞了个 [bluesky 账号](https://bsky.app/profile/mtfront.bsky.social)，下次迁移/maintain 时候搞个静态页面 redirect 过去方便看状态更新好了。（X 是肯定不会用的，telegram 虽然网页版可见但还是不是 web first，其实之前有 threads 账号，不过跟个人 IG 绑定就确实不大适合做线上身份分割。Bluesky 先用着试试看吧就）