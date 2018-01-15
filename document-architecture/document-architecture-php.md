# PHP 前端文档架构

Laravel 框架里，网页呈现的部份我们称为 view \(可以设想为 MVC 里的 V\)，所有的页面都是放置在 `/resources/views/` 里，前端的部份如下：
<br/>


## Errors 资料夹

---

> 文档路径: `/resources/views/errors/*.blade.php`

针对下面的 HTTP 状态有对应页面

* 403.blade.php - 没有权限访问此站，服务器收到请求但拒绝提供服务。
* 404.blade.php - 目标页面不存在
* 500.blade.php - 伺服器遇到了一個未曾預料的狀況，導致了它無法完成對請求的處理。
* 503.blade.php - 臨時的伺服器維護或者過載，伺服器當前無法處理請求。

<br/>


## Front 资料夹

---

> 主为构成网站各页面主要内容  
> 文档路径: `/resources/views/front`

```
face.blade.php - 首页
├ base.js                                   # 侦测各种状态的 JS 代码
│
├ brandgroup.blade.php                      # 品牌家族
├ brand.blade.php - 品牌页
├ attitude.blade.php - 饮食态度
├ topic.blade.php - 饮食态度内文    
├ recipelist.blade.php - 菜谱列表
├ recipedetail.blade.php - 菜谱详情            
├ prodlist.blade.php - 产品列表
├ proddetail.blade.php - 产品详情
├ shinhoprod.blade.php - 产品产 PDF
├ shinhoprodprint.blade.php - 产品列印
├ brandnewslist.blade.php - 品牌动态清单
├ newsdetail.blade.php - 品牌动态详情
├ careers.blade.php - 加入欣和
├ recruiting.blade.php - 社会招聘
│    │    └ recruitingdetail.blade.php - 岗位详情
│    └ campusrecruiting.blade.php - 校园招聘
│         │  └ campusrecruitingdetail.blade.php - 岗位详情
│         ├ campusitinerary.blade.php - 宣讲会
│         └ campusprocess.blade.php - 招聘流程
│
├ about.blade.php -  关于欣和
│    ├ history.blade.php - 欣和历史
│    ├ business.blade.php -  欣和正在做
│    ├ focus.blade.php - 欣和关注
│    ├ crafts.blade.php - 生产工艺
│    │    ├ miso.blade.php - 味噌生产工艺
│    │    ├ beanpaste.blade.php - 原酿酱生产工艺
│    │    ├ soysauce.blade.php - 酱油生产工艺
│    │    ├ vinegar.blade.php  - 苹果醋生产工艺 
│    │    └ spicypeanuts.blade.php - 麻辣花生生产工艺
│    └ csv.blade.php - 社会责任
│
├ newslist.blade.php - 欣和动态
└ contactxinhe.blade.php - 关于欣和
```
<br/>


## Layouts 资料夹

---

> 主为为构成 template 的区块  
> 文档路径: `/resources/views/layouts`

```
master.blade.php - template 主框架
├ meta.blade.php - meta 区块内容
├ header.blade.php - 构成 header 主选单子选单
├ keyvisual.blade.php - KV 轮播样式1 （基本款）
├ keyvisualcraftslider.blade.php - KV 轮播样式2 （生产工艺页面使用）
├ keyvisualnewsslider.blade.php - KV 轮播样式3 （新闻页面使用）
├ functions.blade.php - 针对部分功能所写 function 
│ └ isIE() - IE & HAUWEI 手机 不支援 <picture> 标签 ，吐可支援的 tag
├ inserttop.blade.php -  网页 header 可插入 js 区块
├ insertbottom.blade.php -  网页 footer 可插入 js 区块
└ footer.blade.php - footer 连结
```

`master.blade.php`详细说明见 [1.5.3 PHP](/maintain/maintain-php.md)

