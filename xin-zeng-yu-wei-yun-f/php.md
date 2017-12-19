# PHP

Laravel 框架里，网页呈现的部份我们称为 view \(MVC 里的 V\)，所有的页面都是放置在 `/resources/views/`下，

* `/resources/views/layousts` 为网页的 templat 模版，  
  包含 `master.blade.php`\(主要的 templater 架构\)、`meta.blade.php`（网页 meta 资讯部分）、`header.blade.php`（网页 header 主副选单部分）、`footer.blade.php`（网页 footer 连结）,`keyvisual.blade.php`、`keyVisualCraftSlider.blade.php`、`keyVisualNewsSlider.blade.php`（banner key vision 轮播）

* `/resources/views/front` 为各网页

## 新增

新加入页面需求时，先将页面置于  
/resources/views/front/xxx.blade.php  
档案需以`.blade.php`结尾

### Route

设定新页面的 route  
位置: /routes/web.php

```
...
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
//新页面
Route::get('your/new/page/url','front@your-new-page-name');
```

### Controller

`/app/Http/Controllers/front.php`写入过 route 后所要呼叫的页面及傳入的参数

```
public function careergroup(Request $request,$job=''){//產品葉面
    if($job !=""){
      $c=explode('-',$job);
      if($c[0]=="recruiting"){//崗位需求
        if(count($c)<2 || $c[1]==""){
          return redirect('/careers/recruiting-1');
        }else{
          $to='social';
          return careergroup::recruiting($job,$to);
        }
      }else if($c[0]=="recruitingdetail"){//詳細
        return careergroup::recruitingdetail($job,2);
      }
    }else{//加入欣和
      $bas=DB::table('brandnew')->where('isopen','1')->orderby('sorting','DESC')->get();
      $brandall=json_decode(json_encode($bas), true);
      $itemp=Helper::get_insert();
      return view('front/careers')
      ->with("headertype","2")
      ->with("insert",$itemp)
      ->with("job","careers")
      ->with("brandall",$brandall)
      ->with("error","0");
    }
  }
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

* [meta 资讯](/file/meta-setting.xlsx)
* [API 规划](/file/star-api-setting.xlsx)



