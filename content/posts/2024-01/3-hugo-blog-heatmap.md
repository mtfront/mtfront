---
title: 如何给 Hugo 博客添加热力图
author: 椒盐豆豉
type: post
date: 2024-01-04T10:56:00-08:00
url: /hugo-blog-heatmap/
categories:
  - 重启电脑
tags:
  - code
  - hugo
  - blog
  - project
  - tutorial
booktoc: true
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/111/699/816/751/626/673/original/4e609362db2eb6ad.png
imageDes: "热力图成品效果"
---

之前一直想给博客添加一个 GitHub/豆瓣风格的热力图。纯靠 GitHub commit history 的话因为有工作和 side project 的 commit，以及一篇文章可能会有多个 commit 改错字，并不能很好地体现博客实际的产量。但由于~~对用代码画图以及 hugo 语法不熟悉以及我太懒~~Hugo 文档写得太烂，外加搜了几分钟没找到现成好用的插件，就一直拖延掉了。这次终于着手改出来一个跟自己想要版本很接近的东西，希望对想加类似热力图的博主有帮助。（静态博客果然会不可避免地走上装修博主的道路吗……）

<!--more-->

为什么这次想起来倒腾呢？起因是看到博友[小球飞鱼的年终总结](https://mantyke.icu/weekly/2024/2023-goodbye/?utm_source=blog.douchi.space)上布袋戏热力图很像我想要的效果，问了之后得到了这篇 [Yibocat 的 hugo 文章热力图](https://yibocat.com/posts/jzrj/jzrj_4/?utm_source=blog.douchi.space)，代码和过程都非常详细，效果也跟我想要的很接近了，遂果断开始动手改造。不想看过程的可以直接跳转到后面的[全部代码](#全部代码)部分。

这个代码的基本逻辑是用 javascript 动态抓取所有文章的字数然后传入 echarts 中，所以每次计算都是在访问有热力图的页面时进行的。缺点是每次 build 都会重新计算整个博客不是按 incremental，而且每次访问都需要 javascript 重新计算数据；优点是复制到哪里都能用无需深挖 hugo 的 build 程序。跟我之前写的[给博客添加随机文章入口]({{< relref "/posts/2023-09/6-hugo-random-post" >}})是一个思路。考虑到一个博客最多也就几百篇甚至上千篇文章，对于现代浏览器而言不大用考虑性能问题，因此没有去采取 build time 生成静态数据的方法。

## 修改样式
大体样式教程中已经写得八九不离十，调整一下 margin 和 padding 等细节让我的热力图跟我的博客风格更搭。echart 的官方文档中给了很多可以定制样式的 option，而且文档是 json 形式的可以一比一直接转换到 option 里很容易看。我调整了 [Calendar](https://echarts.apache.org/en/option.html#calendar?utm_source=blog.douchi.space)、[Heatmap](https://echarts.apache.org/en/option.html#series-heatmap?utm_source=blog.douchi.space) 和 [visualMap](https://echarts.apache.org/en/option.html#visualMap?utm_source=blog.douchi.space) 中的一些参数。教程中没有的一些在官方文档里找到对我比较有用的参数有：

```javascript
visulMap {
  type: 'piecewise',  // 还可以变成 continuous，会想显示渐变的颜色而不是色块。
  splitNumber: 4,   // 可以改变要分几个区间
  text: ['千字', ''],   // 顶部图例的说明，[高， 低]
  inRange: {   
      color: ['#7aa8744c', '#7AA874' ] // 热力图中色块从低到高的颜色，我调成了我博客色调的绿色。
  },
}
calendar: {
  itemStyle: {    // 这是热力图每个小色块的 style
      color: '#F1F1F1',   // 色块背景色，即当天没有 data entry 时候的颜色。调成了 github 风格的灰色
      borderWidth: 2.5,   // 要做成途中空格效果的话就加了个宽的背景色边框
      borderColor: '#fff',
  },
  splitLine: {  // 每个月的分割线。我本来有，后来觉得分割没啥作用，调成了透明颜色。需要的话也可以根据官方文档里的选项修改线的风格
    lineStyle: {
      color: 'rgba(0, 0, 0, 0.0)',
    }
  }
},
```
此外，根据我的模版和手机测试调整了一下宽度计算。
```javascript
function getRangeArr() {
  const windowWidth = window.innerWidth;
  if (windowWidth >= 600) {
    return heatmap_width(12);
  } else if (windowWidth >= 400) {
    return heatmap_width(9);
  } else {
    return heatmap_width(6);
  }
}
```
修改完这些，就会大体得到一个跟我的热力图差不多风格的热力图。

## 获取 hugo 文章数据制作短代码
hugo 会在 parse html 的时候直接把它的 Go 代码数据填充进去。不过我当时直接复制教程代码做成短代码发现会造成无限循环。后来 debug 发现这应该是因为短代码放到文章里本身会影响字数统计。因此如果不是做成 partial 插在模版里，而是做成 shortcode 插入文章的话，需要加一些条件排除这种互相调用的可能。

根据你决定把热力图放哪，解决方法也不止这一种。本质是排除掉 `{{ .WordCount }},`在文本内容中的循环调用。因为我的热力图是打算放在 doc 而不是 post 里的，因此循环的时候只抽取 post 类型的文档，然后把短代码放入 doc 类型里:
```Go
{{ range ((where .Site.RegularPages "Type" "post")) }}
```

为了简洁，我把字数单位换成了千字：
```Go
{{ div .WordCount 1000.0 | lang.FormatNumber 1 }}
```

除了字数之外，我还抽取了文章的标题和链接，方便稍后取用：
```Go
{{ .RelPermalink}}  // link
{{ .Title }}  // title
```

## 增加点击模块跳转文章功能
首先 echarts 文档发现了点击的 event handler：
```javascript
myChart.on('click', function(params) {...})
```
通过实验发现 `params` 里有很多有用信息，如 `componentType === 'series'`可以限定到对于数据小块而不是标题、图例等的点击。

但我发现`params.data`在 heatmp 中只接收二维数组，即一开始 push 进去的`[日期，数值]`。如果超过二维的话图表将无法正常显示。但我们需要拿到的除了字数（放在了数值里）还有文章对应的标题和链接才能实现点击跳转。

因此，此处最后决定一开始提取数据的时候放到一个 `dataMap` 里，把日期、标题、 链接、字数等 metadata 都放进去。然后传入 heatmap 时再单独把数据提取到一个二维数组之中。需要用数据的时候只需用 `data` 的第一个元素（日期）作为 key 从 `dataMap` 中抓去其它的 metadata。

最后的提取数据代码如下：
```javascript
var dataMap = new Map();
{{ range ((where .Site.RegularPages "Type" "post")) }}
  var key = {{ .Date.Format "2006-01-02" }};
  var value = dataMap.get(key);
  var wordCount = {{ div .WordCount 1000.0 | lang.FormatNumber 1 }};
  var link = {{ .RelPermalink}};
  var title = {{ .Title }};
  
  // multiple post in same day, chose the longer one to store metadata 
  // we can also store all post and sum up the value, but seems like an overkill
  if (value == null || wordCount > value[0]) {
    dataMap.set(key, {wordCount, link, title});
  }
{{- end -}}
```
其中有个小 edge case：如果一天有多篇文章的话，取字更多的。我一开始设计的时候本来想把多篇文章字数加起来，后来想说反正只能跳转一个，就不把这个数据结构搞得过于复杂了。

传入 echarts 的时候再把日期和字数 从 `dataMap` 中取出来即可：
```javascript
var data = [];
for (const [key, value] of dataMap.entries()) {
  data.push([key, value.wordCount]);
}
```

有了全局的 `dataMap`，就可以在 `click` event 里从 `params` 取出日期再从 `dataMap` 里取出需要跳转的链接，然后添加点击跳转的功能了：
```javascript
myChart.on('click', function(params) {
  if (params.componentType === 'series') {
    const post = dataMap.get(params.data[0]);
    const link = window.location.origin + post.link;
    window.open(link, '_blank').focus();
  }
});
```

## 调整 tooltip 样式
echarts 提供了鼠标悬停在数据小块上可以定制显示的 tooltip 的功能。在 `option` 里加入如下代码，显示“标题 ｜ 字数”。
```javascript
tooltip: {
  formatter: function (p) {
    const post = dataMap.get(p.data[0]);
    return post.title + ' | ' + post.wordCount + ' 千字';
  }
},
```

## 全部代码
到此定制基本大功告成了。代码的框架源自前面提到的 [Yibocat 的 hugo 文章热力图](https://yibocat.com/posts/jzrj/jzrj_4/?utm_source=blog.douchi.space)教程，我做了如下修改：
- 样式
- 点击跳转对应文章
- tooltip 显示文章标题和字数

{{< details "下面是我博客上的全部代码" >}}

```javascript
<div id="heatmap" style="
  max-width: 600px;
  height: 180px;
  padding: 2px;
  text-align: center;"
></div>
<script src="https://cdn.jsdelivr.net/npm/echarts@5.3.0/dist/echarts.min.js"></script>
<script type="text/javascript">
  var chartDom = document.getElementById('heatmap');
  var myChart = echarts.init(chartDom);
  window.onresize = function() {
      myChart.resize();
  };
  var option;

  // echart heatmap data seems to only support two elements tuple
  // it doesn't render when each item has 3 value
  // it also only pass first 2 elements when reading event param
  // so here we build a map to store additional metadata like link and title
  // map format {date: [wordcount, link, title]}
  // for more information see https://blog.douchi.space/hugo-blog-heatmap
  var dataMap = new Map();
  {{ range ((where .Site.RegularPages "Type" "post")) }}
    var key = {{ .Date.Format "2006-01-02" }};
    var value = dataMap.get(key);
    var wordCount = {{ div .WordCount 1000.0 | lang.FormatNumber 1 }};
    var link = {{ .RelPermalink}};
    var title = {{ .Title }};
    
    // multiple posts in same day, chose the longer one
    // can also store all posts and use sum as value, but seems like an overkill
    if (value == null || wordCount > value[0]) {
      dataMap.set(key, {wordCount, link, title});
    }
  {{- end -}}

  var data = [];
  for (const [key, value] of dataMap.entries()) {
    data.push([key, value.wordCount]);
  }
  
  var startDate = new Date();
  var year_Mill = startDate.setFullYear((startDate.getFullYear() - 1));
  var startDate = +new Date(year_Mill);
  var endDate = +new Date();

  var dayTime = 3600 * 24 * 1000;
  startDate = echarts.format.formatTime('yyyy-MM-dd', startDate);
  endDate = echarts.format.formatTime('yyyy-MM-dd', endDate);

  // change date range according to months we want to render
  function heatmap_width(months){             
    var startDate = new Date();
    var mill = startDate.setMonth((startDate.getMonth() - months));
    var endDate = +new Date();
    startDate = +new Date(mill);

    endDate = echarts.format.formatTime('yyyy-MM-dd', endDate);
    startDate = echarts.format.formatTime('yyyy-MM-dd', startDate);

    var showmonth = [];
    showmonth.push([
        startDate,
        endDate
    ]);
    return showmonth
  };

  function getRangeArr() {
    const windowWidth = window.innerWidth;
    if (windowWidth >= 600) {
      return heatmap_width(12);
    } else if (windowWidth >= 400) {
      return heatmap_width(9);
    } else {
      return heatmap_width(6);
    }
  }

  option = {
    title: {
        top: 0,
        left: 'center',
        text: '博客废话产量'
    },
    tooltip: {
      formatter: function (p) {
        const post = dataMap.get(p.data[0]);
        return post.title + ' | ' + post.wordCount + ' 千字';
      }
    },
    visualMap: {
        min: 0,
        max: 10,
        type: 'piecewise',
        orient: 'horizontal',
        left: 'center',
        top: 30,
        
        inRange: {   
          //  [floor color, ceiling color]
          color: ['#7aa8744c', '#7AA874' ] 
        },
        splitNumber: 4,
        text: ['千字', ''],
        showLabel: true,
        itemGap: 20,
    },
    calendar: {
        top: 80,
        left: 20,
        right: 4,
        cellSize: ['auto', 12],
        range: getRangeArr(),
        itemStyle: {
            color: '#F1F1F1',
            borderWidth: 2.5,
            borderColor: '#fff',
        },
        yearLabel: { show: false },
        // the splitline between months. set to transparent for now.
        splitLine: {
          lineStyle: {
            color: 'rgba(0, 0, 0, 0.0)',
            // shadowColor: 'rgba(0, 0, 0, 0.5)',
            // shadowBlur: 5,
            // width: 0.5,
            // type: 'dashed',
          }
        }
    },
    series: {
        type: 'heatmap',
        coordinateSystem: 'calendar',
        data: data,
    }
  };
  myChart.setOption(option);
  myChart.on('click', function(params) {
    if (params.componentType === 'series') {
      const post = dataMap.get(params.data[0]);
      const link = window.location.origin + post.link;
      window.open(link, '_blank').focus();
    }
});
</script> 
```
{{< / details >}}

![](https://media.douchi.space/douchi/media_attachments/files/111/699/816/751/626/673/original/4e609362db2eb6ad.png)
把我的成品仍在 [now 页面了]({{< relref "/docs/now" >}})，感兴趣的朋友可以去看看对不对胃口。如果对代码做了什么优化改进也欢迎在此留言分享。

{{< support >}}