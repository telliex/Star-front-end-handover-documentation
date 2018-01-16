# 效能优化

## schema.org
---

标记于 HTML 页面上的 schemas 标记，能帮助搜索引擎理解网页上的信息，从而让搜索结果内容更丰富，用户搜索到的页面也就更精准。

标记 **schema.org** 有许多方法，如下：

* MicroData
* MicroFormat
* RDFa ![](/images/star.png)
* JSON LD

欣和官网选用 **RDFa** 格式标记，详细标记方法[请见](http://schema.org/docs/datamodel.html)。标注 [schema.org](https://schema.org/docs/full.html) 标签后，需通过[结构化资料测试工具](https://search.google.com/structured-data/testing-tool/u/0/)检测，确认无错误提示，再更新于代码中。

### 相关连结与文档
* [schema.org 标记文档](https://schema.org/docs/full.html)
* [結構化資料測試工具](https://search.google.com/structured-data/testing-tool/u/0/)

<br/>

## 圖片壓縮
---

为了提升网站效能，在设计提供官网静态图片之后，都需要经过图片压缩程序。请设计提供**无压缩品质的图片**，使用 [compressor.io](https://compressor.io/) 线上图片压缩网站。
<br/>
> 線上工具連結：[https://compressor.io/](https://compressor.io/)

![](/images/compressor.png)

### 注意事項

1. 请设计提供**无压缩品质的图片**
2. 如图所示，有两个模式可以选择，一个是 **Lossy 失真模式**，另一个是 **Lossless 不失真模式**，Lossless 不失真模式仅提供给 JPG 与 PNG 档案使用，根据下表档案类型对应该选择的压缩模式。

| 图片档案类型 | 使用压缩模式 |
| :--- | :--- |
| JPG | 优先选用 Lossless 模式；比对 Lossless 模式与 Lossy 模式的档案大小，若差异很大，且图片品质在设计可接受的范围，选用相对应压缩模式。 |
| PNG | 优先选用 Lossless 模式；比对 Lossless 模式与 Lossy 模式的档案大小，若差异很大，且图片品质在设计可接受的范围，选用相对应压缩模式。 |
| SVG | Lossy 失真模式 |

<br/>

## Sitemap
---

Sitemap 可方便网站管理员通知搜索引擎他们网站上有哪些可供抓取的网页。最简单的 Sitemap 形式，就是XML 文件，在其中列出网站中的网址以及关于每个网址的其他元数据（上次更新的时间、更改的频率以及相对于网站上其他网址的重要程度为何等），以便搜索引擎可以更加智能地抓取网站。

在有新的开发程序上正式主机**之后**，使用线上产生 Sitemap 工具产出最新的 Sitemap，并检查档案内**时间格式**是否有错误，确认无误后，将档案上传至正式主机的 `/public/sitemap.xml`，并提交此档案给产品经理提交给各个搜索引擎。如谷歌、百度。 

> 文档路径: `/public/sitemap.xml`
> 線上工具連結: [https://freesitemapgenerator.com/](https://freesitemapgenerator.com/)

<br/>

## robots.txt
---
Robots 协议 (也称为爬虫协议、机器人协议等) 的全称是**网络爬虫排除标准** (Robots Exclusion Protocol)，网站通过Robots协议告诉搜索引擎哪些页面可以抓取，哪些页面不能抓取。

当一个搜索蜘蛛访问一个站点时，它会首先检查该站点根目录下是否存在 robots.txt，如果存在，搜索机器人就会按照该文件中的内容来确定访问的范围；如果该文件不存在，所有的搜索蜘蛛将能够访问网站上所有没有被口令保护的页面。

在有新的开发程序上正式主机之前，必须与产品经理确认这次更新版本是否有需要屏蔽搜索引擎的页面，例如：后台、个人会员资料、测试机代码档案等。

欣和官网分别对应正式主机与测试主机有不同的 robots.txt 档案：

> 正式主机文档路径: `/public/robots.txt`

```
User-agent: *
Disallow: /event2016/
Disallow: /adm

User-agent: AdsBot-Google

Disallow: /event2016/
Disallow: /adm
```

> 测试主机文档路径: `/public/robots-develop.txt`

```
User-agent: *
Disallow: /

User-agent: AdsBot-Google
Disallow: /
```

**网站被搜索引擎屏蔽对网站排名影响很大，请再三确认是否屏蔽该网址。**







