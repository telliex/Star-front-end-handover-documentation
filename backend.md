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
```
#### 主控档案
```markdown
app 
├ Http
│  ├ Controllers
│  │  ├ font.php          # 前台档案
│  │  ├ ajax.php          # 前台 ajax
│  │  ├ adm.php           # 后台档案
│  │  └ admajax.php       # 后台 ajax
```

#### 主控档案运用模组
```markdown
app
 ├ Helpers
 │  ├ Helper.php          # 共用模组
 │  ├ admgroup.php        # 后台模组
 │  ├ brandgroup.php      # 品牌产品模組
 │  ├ careergroup.php     # 招聘模組
 │  └ newsgroup.php       # 新闻模组
```

#### 显示档案(view)
```markdown
resources
 ├ views
 │  ├ adm                 # 后台档案 
 │  ├ front               # 前台档案  
 │  ├ layouts             # 框架档案
 │  └ errors              # 错误档案 
```

