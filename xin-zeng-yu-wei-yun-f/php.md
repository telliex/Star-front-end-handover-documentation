# PHP

## 新增

### Route

设定新页面的 route
位置: /routes/web.php
```
Route::get('about/process/spicypeanuts','front@your-new-page-name');
```

## 维运

#### 全站 template

新增或修改全站通用的 js，如 vue.js 等
位置: /resources/views/layouts/master.blade.php

#### Meta

新增或修改页面 meta 资讯
位置: /resources/views/layouts/meta.blade.php

```
//在 if 判断是后面追加上新页面名称与相关 meta 讯息

else if($job=="your-new-page-name"){
  $title="your-new-page-title - 关于欣和 ｜ 欣和官网";
  $des="your-new-page-description";
  $image="/img/about/your-new-page-img.png";
  $kwords="";
}

```

#### Header

修改或新增 header 区块上次选单顺序与名称连结
位置: /resources/views/layouts/header.blade.php

#### Footer

修改或新增 footer 区块上连结与名称
位置: /resources/views/layouts/footer.blade.php






## 技術參考文檔

- [meta 资讯](/file/meta-setting.xlsx)
- [API 规划](/file/star-api-setting.xlsx)




