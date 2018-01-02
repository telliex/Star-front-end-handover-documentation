# 新增与運維 - PHP

**Blade** 是 Laravel 所提供的簡單且強大的模板引擎，Blade 視圖檔案使用 **.blade.php** 做為副檔名，且通常儲存於  `resources/views` 資料夾。

- `/resources/views/layouts` 为网页的 template 模版，
包含 `master.blade.php`(主要的 template 架构)、`meta.blade.php`（网页 meta 资讯部分）、`header.blade.php`（网页 header 主副选单部分）、`footer.blade.php`（网页 footer 连结）,`keyvisual.blade.php`、`keyVisualCraftSlider.blade.php`、`keyVisualNewsSlider.blade.php`（banner key vision 轮播）
- `/resources/views/front` 放置各子网页

## Template
---

以下可以由两个 .blade.php 档说明 laravel 里 template 的用法

> 表示引用母页面
> 文档路径：/resources/views/layouts/master.blade.php

```
<!DOCTYPE html>
<html lang="cmn-Hans">
<head>
  // 将 /resources/views/layouts/meta.blade.php 的程式码导入（网页 mata 部分）
  @include('layouts.meta')  
  
  // @yield 在母页面使用,供子页面继承此母页面时，以 @section('headInsert') 区块内容取代此 @yield('headInsert')
  @yield('headInsert')
  
  // 将 /resources/views/layouts/inserttop.blade.php 的程式码导入（网页 head 第三方 js 部分,如百度,谷歌程式码）
  @include('layouts.inserttop') 
  
  // 载入全站通用的 CSS
  <link rel="stylesheet" href="{{ asset('/css/global.css?').str_random(10) }}">
  
  <!--[if lt IE 9]>
  
  // IE9 以下浏览器，载入 html5shiv.js ，辨识 HTML5 tag
  <script src="//cdnjs.cloudflare.com/ajax/libs/html5shiv/3.6.2/html5shiv.js"></script>
  
  // 让不支持 Media Query 的浏览器支持查询。
  <script src="https://oss.maxcdn.com/libs/respond.js/1.3.0/respond.min.js"></script>
  
  // 设置 IE hack 的 CSS
  <link rel="stylesheet" href="{{ asset('/css/ie.css?') }}">
  
  <![endif]-->
</head>
<body @yield('dataNav') vocab="http://schema.org/" typeof="WebPage">
  <section id="pre-loader"><img src="{{ asset('/img/loading.gif') }}" alt="Loading"></section>
  <div class="wrapper">
  // 将 /resources/views/layouts/header.blade.php 的程式码导入
  @include('layouts.header')

    <main class="container @yield('classContainer')" property="@yield('schemaContainer')">
      // @yield 在母页面使用,供子页面继承此母页面时，以 @section('keyVisual') 区块内容取代此 @yield('keyVisual')
      @yield('keyVisual')
      // @yield 在母页面使用,供子页面继承此母页面时，以 @section('mainContent') 区块内容取代此 @yield('mainContent')
      @yield('mainContent')
      <a href="#" class="go-top-btn" title="回顶部"><i class="icon-arrow-light-top"></i><span>回顶部</span></a>
    </main>
    
    
  // 将 /resources/views/layouts/footer.blade.php 的程式码导入（网页 footer 部分）  
  @include('layouts.footer')
  </div>

// 针对 IE9 以下浏览器不支援 ES6 模块系统，提供载入
<!--[if lt IE 9]> 
<script src="{{ asset('/js/html5shiv.min.js') }}"></script>
<script src="{{ asset('/js/jquery.js') }}"></script>
<script src="{{ asset('/js/jquery.history.js') }}"></script>
<script src="{{ asset('/js/jquery.cookie.js') }}"></script>

//  低阶浏览器使用者提示下载 alert
 <script>
 $("body").append('<section id="isNSupport">您好，<br/><br/>我们侦测到您目前使用的浏览器版本，可能会有无法执行网站的部分功能，与无法正常浏览内容的情形！<br/>为让您有更好的阅览与使用体验，建议您可以：<br/>1.更新<a href="https://www.microsoft.com/zh-hk/download/Internet-Explorer-11-for-Windows-7-details.aspx" target="_blank">IE</a>浏览器版本 <br/>2.使用 <a href="https://www.google.com/chrome/browser/desktop/" target="_blank">Chrome</a> 或 <a href="https://moztw.org/firefox/download/latest-osx.html" target="_blank">Firefox</a> 浏览器开启网站</section>');        
</script>
<![endif]-->

<!--[if lt IE 9]>
<script src="{{ asset('/js/jquery.pseudo.js') }}"></script>
<script src="{{ asset('/js/selectivizr-min.js') }}"></script>
<![endif]--> 
<script src="{{ asset('/js/custom/global.js') }}"></script>

  // 子页面中引入 ＠section("jsInsert") 内容
  @yield('jsInsert')
  
  // 将 /resources/views/layouts/insertbottom.blade.php 的程式码导入（网页 footer 第三方 js 部分,如百度,谷歌程式码）
  @include('layouts.insertbottom')
  
</body>
</html>
```

> 表示引用子页面
> 文档路径：/resources/views/front/careers.blade.php

```
// 继承 master.blade.php 母页面
@extends('layouts.master')

// 将以下 @section('headInsert') 几夹带的内容,置换继承母页面内 @yield('headInsert')位置
@section('headInsert')
	{{-- <link rel="stylesheet" href="{{ asset('/css/vendor/carousel/owl.carousel.css') }}">
    <link rel="stylesheet" href="{{ asset('/css/vendor/carousel/owl.theme.default.css') }}">
    <link rel="stylesheet" href="{{ asset('/css/vendor/carousel/animate.css') }}"> --}}
@endsection

// 将以下 @section('section', 'data-main-nav="2"')第二个参数的内容放进母页面取代 @yield('section'）
@section('section', 'data-main-nav="2"')

// 将以下 @section('schemaContainer', 'mainContentOfPage')第二个参数的内容放进母页面取代 @yield('schemaContainer'）
@section('schemaContainer', 'mainContentOfPage')

// 将以下 @section('keyVisual')的内容放进母页面取代 @yield('keyVisual'）
@section('keyVisual')
    // 放进 /resources/views/layouts/keyvisual.blade.php 内容，并传入变数值
    @include('layouts.keyvisual', ['DT' => asset('/img/kv-careers.jpg'),'M' => asset('/img/kv-careers-m.jpg'),'ALT' => '加入欣和'])
@endsection

// 将以下 @section('mainContent')的内容放进母页面取代 @yield('mainContent'）
@section('mainContent')
	<section class="career-about">
		...内容
	</section>
@stop

// 将以下 @section('jsInsert') 夹带的内容,置换继承母页面内 @yield('jsInsert')位置
@section('jsInsert')
	<script src="{{ asset('/js/custom/lyt-careers.js') }}"></script>
@endsection
```

说明:
- `asset` 自根目录开始找寻路径
- `@section()` 子页面内使用，替会母页面内的 `@yield`
- `@yield` 母页面内使用，让子页面内的 `@section()` 可以继承后替换


## 维护
---

#### 全站 template

新增或修改全站通用的线上 CDN url
> 文档路径：/resources/views/layouts/master.blade.php

#### Meta

新增或修改页面 meta 资讯
> 文档路径：/resources/views/layouts/meta.blade.php

```
// 在 if 判断是后面追加上新页面名称与相关 meta 讯息

else if($job=="your-new-page-name"){
  $title="your-new-page-title - 关于欣和 ｜ 欣和官网";
  $des="your-new-page-description";
  $image="/img/about/your-new-page-img.png";
  $kwords="";
}

```

#### Header

修改或新增 header 区块上次选单顺序与名称连结
> 文档路径：/resources/views/layouts/header.blade.php

#### Footer

修改或新增 footer 区块上连结与名称
> 文档路径：/resources/views/layouts/footer.blade.php

## 技术文件参考资料
---

- [meta 资讯](/file/meta-setting.xlsx)
- [API 规划](/file/star-api-setting.xlsx)




