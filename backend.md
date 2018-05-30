# 後端檔案架構說明


確認 mysql 之使用者須有新增/更新/寫入資料表之權限

## 環境設定

### 数据库
* 修改数据库设定 `/config/database.php` 
* 請開啟資料夾 `/public/img/` 寫入權限

数据库栏位 [DB](file/shinho_db.xlsx)

## Routing 設定
> 文档路径：/routes/web.php

```
// 中文版
Route::group(['domain' => 'cn.shinhoglobal.com'], function () {

Route::get('/','front@index');

//后台
Route::get('adm','adm@index');
Route::get('adm/{job?}','adm@indexin');

//后台 ajax
Route::post('admajax','admajax@indexp');
Route::get('admajax','admajax@index');

//后台登入
Route::post('adm', 'adm@index');
Route::post('adm/{tf?}', 'adm@indexin');

// ajax
Route::get('ajax','ajax@index');

//前台
//品牌-新聞
Route::get('brandgroup/{job?}/{val?}/{cnt}','front@brandgroup');

//品牌-內頁
Route::get('brandgroup/{job?}/{val?}','front@brandgroup');

//品牌-主頁
Route::get('brandgroup/{job?}','front@brandgroup');

//新聞
Route::get('news/',function () {return redirect('news/1');});
Route::get('news/{job?}','front@newsgroup');

//招聘
Route::get('careers/campus/{job?}','front@campusgroup');
Route::get('careers/{job?}','front@careergroup');
Route::get('careers/','front@careergroup');

//歷史

//聯繫欣和
Route::get('contactxinhe','front@contactxinhe');

//history
Route::get('about/history','front@history');

//社會關注
Route::get('about/focus','front@focus');

//社会责任
Route::get('about/csv','front@csv');

//欣和正在做
Route::get('about/business','front@business');

//關於欣和
Route::get('about','front@about');

//生产工艺
Route::get('about/process','front@crafts');

//生产工艺 - beanpaste
Route::get('about/process/beanpaste','front@beanpaste');

//生产工艺 - soysauce
Route::get('about/process/soysauce','front@soysauce');

//生产工艺 - vinegar
Route::get('about/process/vinegar','front@vinegar');

//生产工艺 - miso
Route::get('about/process/miso','front@miso');

//生产工艺 - spicypeanuts
Route::get('about/process/spicypeanuts','front@spicypeanuts');

});

// 英文版
Route::group(['domain' => 'en.shinhoglobal.com'], function () {
Route::get('/','front_en@index');

//后台
Route::get('adm','adm@index');
Route::get('adm/{job?}','adm@indexin');

//后台 ajax
Route::post('admajax','admajax@indexp');
Route::get('admajax','admajax@index');

//后台登入
Route::post('adm', 'adm@index');
Route::post('adm/{tf?}', 'adm@indexin');

// ajax
Route::get('ajax','ajax_en@index');

//前台
//品牌-新聞
Route::get('brandgroup/{job?}/{val?}/{cnt}','front_en@brandgroup');

//品牌-內頁
Route::get('brandgroup/{job?}/{val?}','front_en@brandgroup');

//品牌-主頁
Route::get('brandgroup/{job?}','front_en@brandgroup');

//新聞
Route::get('news/',function () {return redirect('news/1');});
Route::get('news/{job?}','front_en@newsgroup');

//招聘
Route::get('careers/campus/{job?}','front_en@campusgroup');
Route::get('careers/{job?}','front_en@careergroup');
Route::get('careers/','front_en@careergroup');

//歷史

//聯繫欣和
Route::get('contactxinhe','front_en@contactxinhe');

//history
Route::get('about/history','front_en@history');

//社會關注
Route::get('about/focus','front_en@focus');

//社会责任
Route::get('about/csv','front_en@csv');

//欣和正在做
Route::get('about/business','front_en@business');

//關於欣和
Route::get('about','front_en@about');

//生产工艺
Route::get('about/process','front_en@crafts');

//生产工艺 - beanpaste
Route::get('about/process/beanpaste','front_en@beanpaste');

//生产工艺 - soysauce
Route::get('about/process/soysauce','front_en@soysauce');

//生产工艺 - vinegar
Route::get('about/process/vinegar','front_en@vinegar');

//生产工艺 - miso
Route::get('about/process/miso','front_en@miso');

//生产工艺 - spicypeanuts
Route::get('about/process/spicypeanuts','front_en@spicypeanuts');

});
```


