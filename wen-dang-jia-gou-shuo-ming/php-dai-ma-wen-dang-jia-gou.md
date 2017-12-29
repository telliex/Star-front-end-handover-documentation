# PHP 前端文档架构

Laravel 框架里，网页呈现的部份我们称为 view (MVC 里的 V)，所有的页面都是放置在 `/resources/views/`下:



## errors 资料夹
---

> 文档路径: `/resources/views/errors/*.blade.php`

针对下面的 HTTP 状态有对应页面

- 403.blade.php - 没有权限访问此站，服务器收到请求但拒绝提供服务。
- 404.blade.php - 目标页面不存在
- 500.blade.php - 伺服器遇到了一個未曾預料的狀況，導致了它無法完成對請求的處理。
- 503.blade.php - 臨時的伺服器維護或者過載，伺服器當前無法處理請求。



## front 资料夹
---
主为构成网站各页面主要内容
> 文档路径: `/resources/views/front`




brand.blade.php




campusprocess.blade.php

campusrecruitingdetail.blade.php

contactxinhe.blade.php

brandgroup.blade.php - 品牌家族
    brand.blade.php - 品牌页
    attitude.blade.php - 饮食态度
        recipelist.blade.php - 菜谱列表
            recipedetail.blade.php - 菜谱详情
    prodlist.blade.php - 产品列表
        proddetail.blade.php - 产品详情
    brandnewslist.blade.php - 品牌动态清单
        newsdetail.blade.php - 品牌动态详情
careers.blade.php - 加入欣和
    recruiting.blade.php - 社会招聘
    campusrecruiting.blade.php - 校园招聘
        campusitinerary.blade.php - 宣讲会







about.blade.php -  关于欣和
    history.blade.php - 欣和历史
    business.blade.php -  欣和正在做
    face.blade.php - 欣和关注
    crafts.blade.php - 生产工艺
        miso.blade.php - 味噌生产工艺
        beanpaste.blade.php - 原酿酱生产工艺
        soysauce.blade.php - 酱油生产工艺
        vinegar.blade.php  - 苹果醋生产工艺
        spicypeanuts.blade.php - 麻辣花生生产工艺
    csv.blade.php - 社会责任

focus.blade.php - 



newslist.blade.php





recruitingdetail.blade.php
shinhoprod.blade.php
shinhoprodprint.blade.php
shinhoprodsample.blade.php


topic.blade.php




## layouts 资料夹
---
> 文档路径: `/resources/views/layouts`

