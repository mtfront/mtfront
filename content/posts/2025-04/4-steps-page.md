---
title: 也搞了一个展示行走数据的页面
author: 椒盐豆豉
type: post
date: 2025-04-19T20:45:00-07:00
url: /steps-page/
categories:
  - 关我屁事
  - 重启电脑
tags:
  - Blog
  - Code
  - Tutorial
  - PSA
booktoc: true
bookComments: true
image: "https://media.douchi.space/douchi/media_attachments/files/114/368/219/569/028/263/original/e406eefc50296df9.png"
imageDes: "跬步数据热力图"
---

某日我在闲逛博客访客，然后就逛到了一个[博客](https://viazure.cc/posts/life/monthly-review-202503/?utm_source=blog.douchi.space)上酷炫的热力图。本[热力图爱好者]({{< relref "/posts/2024-01/3-hugo-blog-heatmap" >}})立刻 be like I WANT ONE! 一番挖掘后发现了 [running_page](https://github.com/yihong0618/running_page) 这个开源项目，可以导入 Garmin/Strava 等多种数据。立刻 fork 了一个折腾了一下给自己也搭起来了。今天有时间了折腾成了自己理想的样子，也来记录一下自己使用过程中遇到的问题和改进，顺便给大家安利一下来一起互鸡锻炼！先上页面：

## [steps.douchi.space](https://steps.douchi.space?utm_source=blog)

<!--more-->

## 初始版本选择
一开始我无脑 fork 了 [running_page](https://github.com/yihong0618/running_page) 的原版，sync 了 garmin 数据，折腾好之后发现了如下一些问题：
- 对室内跑步机不支持，因为我主要是室内跑步，这是我最大的问题（后来发现是默认 script 选项的问题）
- 支持的运动类型比较狭窄，kayak、骑行、游泳等不支持
- 对非中国的地理位置 title parse 不佳，各个地方的跑步、hiking 等都变成了较为无聊的”morning run“
- 深色模式我不喜欢

后来看了一下官方主页上分享自己页面的 repo，选择了支持了多种运动类型的且有一定定制性的 [ben-29 版本](https://github.com/ben-29/workouts_page/tree/master)。

## 基础配置修改
我使用了了 github pages，其它地方找着官方文档改即可，下面是一些非必须但是我建议修改的地方：
```yml
# .github/workflows/run_data_sync.yml
# 不修改的话每次 sync 数据都会生成一个新的 commit，比较 messy
SAVE_DATA_IN_GITHUB_CACHE: true 

# 一些 privacy 相关的建议打开模糊数据
IGNORE_RANGE
IGNORE_START_END_RANGE
```

```typescript
// src/utils/const.ts
const PRIVACY_MODE = true;
```

## 本地测试
可以看官方文档，但有些地方可能 outdated 了，我的建议是直接去看 `.github/workflows/run_data_sync.yml` 里自己对应的步骤来 run，确保本地和 workflow 运行的代码是一致的。以下 `${{}}` `$`中的变量均是前一步中从平台获取的，替换即可。

拿我要同步 Garmin 的数据为例：在 `.github/workflows/run_data_sync.yml` 搜索:
-  `'garmin'` 找到对应步骤，运行 `python run_page/garmin_sync.py ${{ secrets.GARMIN_SECRET_STRING }} --fit`。注意原版没有加 `--fit`，我发现加载出来的 GPX 数据是不支持显示跑步机的，改为下载 `.fit` 数据即可。
- `env.RUN_TYPE != 'pass'`：这一步是生成各种 svg 文件的，第一次 push 和在本地调试样式的时候要用到。

## 我的一些 customization
我改的也比较 messy 就不开源了，代码更难找到。大体说一下改了什么：

### Garmin 选择 fit 数据
像前面一步说的，默认的 `.gpx` 文件会忽略跑步机的数据。 `.fit` 文件则没有问题。将 `.github/workflows/run_data_sync.yml` 中修改添加 `--fit`：
```yml
python run_page/garmin_sync.py ${{ secrets.GARMIN_SECRET_STRING }} --fit
```

### 同时同步两个数据源
默认的 workflow 只能选定一个数据源。而我早年用的是 fitbit 和三星（同步到了 starva），近几年才换的 Garmin，所以两者都需要。在上一项后面那一行紧接着添加 strava 的同步 script：
```yml
python run_page/strava_sync.py ${{ secrets.STRAVA_CLIENT_ID }} ${{ secrets.STRAVA_CLIENT_SECRET }} ${{ secrets.STRAVA_CLIENT_REFRESH_TOKEN }}
```

### 颜色
{{< wrap "https://media.douchi.space/douchi/media_attachments/files/114/368/193/175/379/941/original/08804b02a8306084.png" >}}
`ben-29` 版本虽然提供了一些定制，但基本是基于 dark mode 的前提的，如果要大改颜色的话只修改 `const.ts`中的配色是不够的。原版中的颜色有的使用了变量有的是直接 hard code 在 ts 文件里有的在 css 里，比较难找。我挨个 inspect element，找到不对的颜色，然后全局搜索这个颜色替换。

以及生成 grid 和 github style heatmap 的时候颜色用的是 `const.ts` 里的颜色，但
- github heatmap 那个小方块的底的颜色 hardcode 在 `run_page/gpxtrackposter/github_drawer.py` 里。
- 环状图的颜色则在 `run_page/gpxtrackposter/poster.py` 中，改掉 `background`, `track`, `spcecial`, `special`, `text`. 

基本上把配色换成了 [solarized](https://ethanschoonover.com/solarized/?utm_source=blog.douchi.space)，对不喜欢深色模式的我来说顺眼多了。


### 简化 location stat，放入 total 页面
这个项目有一个城市统计的功能，人不在中国或者也不在别的城市跑步的话占地方又没什么用，在 `src/components/LocationStat/index.tsx` 中 comment 掉了 `CitiesStat` `PeriodStat` 和 `YearStat`，简化之后在 `src/pages/index.tsx` 中就不按 zoom level 放 `LocationStat` 了，直接变成加到 Total 页面里的 `YearStat` 前面。

`src/components/LocationStat/LocationSummary.tsx` 中的省份和 cities 也都直接 comment 掉。

### 年度环状图样式修改
`src/components/YearStat/index.tsx` 中去掉 `hovered`，以及宽度样式 `w-4/6` -> `w-[100%]`

### 时区
全局搜索 `Asia/Shanghai` `TIMEZONE_OFFSET` 替换成本地时区值。

### gitignore
在原有基础上添加：
```text
node_modules
run   # 我的虚拟环境
FIT_OUT_local_backup    # workflow 会生成 cache，本地源文件我就备份起来了。
```

## Last but not least，选名字！
原版叫 running page，但我的 hiking 散步什么的也不少，外加跑步其实主要是室内也没在 map data 上体现出来，再叫 running page 就不合适了。

在给本博客添加这个页面的链接时候灵机一动，就叫它`「跬步」`了。那域名顺理成章就变成 `steps.douchi.space` 了。

之前在[「2023 年了你为什么需要写博客」]({{< relref "/posts/2023-08/5-2023-why-you-need-a-blog" >}})写到“输出赋予了很多事意义”，后来博友们总结的更好“输出倒逼输入”。有了这个积跬步的展示页面之后，以后跑步徒步好像也更有动力了呢！

![看着数据成就感满满](https://media.douchi.space/douchi/media_attachments/files/114/368/199/277/845/128/original/7e6f45d0ab7a288d.png)