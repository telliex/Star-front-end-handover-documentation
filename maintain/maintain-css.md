# 新增与運維 - CSS

## CSS 代码文档运用

---

| 档案名称 | 说明 |
| :--- | :--- |
| global.scss | 全站样式 |
| global-org.scss | 首页样式 |
| errors.scss | 403、404、500、503 错误页面样式 |

在欣和官网上目前使用到的三个主样式，分别为 `global.scss`、`global-org.scss`、`errors.scss`，各个主样式依照需求 `@import` 所需的文档与套件；而在 `@import` 的顺序上与转译后的代码顺序有关，依序如下：

1. 样式框架、各浏览器样式重置 \(使用 compass 预设版本\)
2. 依照官网需求各浏览器样式重置参数、全站使用的样式变数、Susy 栅栏设定
3. 全站通用样式、全站继承样式模块代码、全站混合指令样式代码
4. 模组样式
5. 元件样式
6. 页面样式
7. 套件样式
<br/>
<br/>

> 以 `global.scss` 文档为例

```css
// 样式框架、各浏览器样式重置 (使用 compass 预设版本)
@import "compass";
@import "compass/reset";
@import "compass/css3";
@import "susy";
@import "breakpoint";

// 依照官网需求各浏览器样式重置参数、全站使用的样式变数、Susy 栅栏设定
@import "base/variables";                                    
@import "base/grid-setting";
@import "base/base-style-setting";    

// 全站通用样式、全站继承样式模块代码、全站混合指令样式代码
@import "generic/extend";  
@import "generic/maxin";  
@import "generic/common";      

// 模组样式
@import "modules/module-button";
@import "modules/module-subtitle";
@import "modules/module-anchor";   
@import "modules/module-topic-info";  
@import "modules/module-article";   
@import "modules/module-recipe-list";
@import "modules/module-prod-list"; 
@import "modules/module-news-list"; 
@import "modules/module-search-bar";
@import "modules/module-selectbox"; 
@import "modules/module-checkbox"; 

// 元件样式
@import "partials/support-mess";  
@import "partials/pre-loader"; 
@import "partials/header";
@import "partials/footer"; 
@import "partials/breadcrumb";
@import "partials/key-visual";
@import "partials/go-top"; 
@import "partials/topics-recommend";
@import "partials/careers-temp"; 

// 页面样式
@import "layout/about";
@import "layout/about-history";
@import "layout/about-business";     
@import "layout/about-csv";
@import "layout/about-focus";
@import "layout/about-crafts";
@import "layout/contact";
@import "layout/careers";
@import "layout/careers-progress";
@import "layout/careers-itinerary";
@import "layout/careers-recruiting-list";
@import "layout/careers-recruiting-detail";
@import "layout/news-list";
@import "layout/news-detail"; 
@import "layout/brand-attitude";
@import "layout/brand-topic"; 
@import "layout/brand-recipe-list"; 
@import "layout/brand-recipe-detail";
@import "layout/brand-prod-list";
@import "layout/brand-prod-detail";
@import "layout/brand-index";
@import "layout/brand-group";

// 套件样式
@import "vendor/fontello";
```
详细档案说明请参考：[1.4.1 文档架构说明 - CSS 样式文档架构](/document-architecture/document-architecture-css.md)
<br/>

### base 内文档的运用

#### base-style-setting.scss

各个浏览器预设样式并不一致，在建立 `global.scss`、`global-org.scss`、`errors.scss` 等主样式档案时，使用 SCSS 预设版本的 `@import "compass/reset"`将各个浏览器预设样式设定相同属性，便于未来开发减少样式上的差异；此外在 `base-style-setting.scss` 依照官网需求调整了样式重置的参数，这里的样式若需要调整更动，会改变全站 html tag 的样式，若非全站统一更动样式需求，请勿修改此档案。

#### grid-setting.scss

官网所使用的 Susy 栅栏框架设定，若非全站统一更动样式需求，请勿修改此档案。

* [Susy 2.2 中文文檔](https://www.w3cplus.com/preprocessor/susy-docs.html) 

#### variables.scss

依照官网的 Style Guideline 建置全站的变数档案，若非全站统一更动样式需求，请勿修改此档案。之后新增与运维样式，都需要使用 `variables.scss` 内的变数；若有大量重复的参数，可依照分类建立新的变数值。
<br/>
> 文档路径: `/src/sass/base/variables.scss`

```css
// 字型设定 Font Setting
$base-font-family                  : "Hiragino Sans GB","Microsoft YaHei","WenQuanYi Micro Hei",sans-serif;
$base-highlight-font-family        : "Times New Roman";
$base-font-size                    : 16px;
$base-line-height                  : 2em;
$base-letter-spacing               : 0.05em;
$base-box-line-height              : $base-line-height * 0.75;    // 专属于模块型样式里的行高

// 字型设定 Font Setting for IE
$base-px-line-height               : 32px;
$base-px-letter-spacing            : 0.8px;
$base-px-box-line-height           : 24px;  

// 官网两大主色 Color Setting
$maincolor-highlight               : #ef4632;
$maincolor-sec-highlight           : #fbaa1e;

// 文字颜色设定 Font Color
$base-fontcolor-bright             : #fff;
$base-fontcolor-lighten            : #a8a8a8;
$base-fontcolor-darken             : #666;
$base-fontcolor-deepdark           : #484848;
$base-fontcolor-highlight          : $maincolor-highlight;
$base-fontcolor-sec-highlight      : $maincolor-sec-highlight;

// 字型大小设定 Font Size
$base-fontsize-xlarge              : 2rem;            // 32px
$base-fontsize-large               : 1.375rem;        // 22px
$base-fontsize-mid                 : 1rem;            // 16px
$base-fontsize-small               : 0.875rem;        // 14px
$base-fontsize-ssmall              : 0.75rem;         // 12px

// 字型大小设定 Font Size for IE
$base-px-fontsize-xlarge           : 32px;            // 32px
$base-px-fontsize-large            : 22px;            // 22px
$base-px-fontsize-mid              : 16px;            // 16px
$base-px-fontsize-small            : 14px;            // 14px
$base-px-fontsize-ssmall           : 12px;            // 12px

// 底色设定 Background

$base-bgcolor-lighten              : #fff;
$base-bgcolor-darken               : #f8f8f8;
$base-bgcolor-dark                 : #000;
$base-bgcolor-heightlight          : $maincolor-highlight;

// 边线设定 Border
$base-border-color-lighten         : #ebebeb;
$base-border-color-darken          : #999;
$base-border-color-bright          : #fff;
$base-border-color-heightlight     : #ef4632;

// 元件设定 Elements
$header-bgcolor                    : #fff;
$deskop-bgcolor                    : #fff;
$mobile-bgcolor                    : #f8f8f8;

$base-title-fontcolor              : #484848;
$base-content-fontcolor            : #666;

$base-link-fontcolor               : $maincolor-highlight;
$base-link-fontcolor-hover         : lighten($maincolor-highlight,30%);

$base-button-bgcolor               : $maincolor-highlight;
$base-button-hover-bgcolor         : lighten($maincolor-highlight,20%);

$animation-gutter                  : 350px;    // Scroll 动效需要调整元件的高度

$content-text-width                : 640px;    // 文章内容宽度 

// 浏览器宽度设定 Screen Setting
$anchor-width                      : 1360px;
$fullscreen-width                  : 1200px;
$desktop-width                     : 960px;
$tablet-width                      : 768px;
```
<br/>

### generic 内文档的运用

#### common.scss

定义全站框架宽度与交互效果。根据欣和官网 Style Guideline 全站框架宽度分别定义为三种维度：

1. 手机 ( < 768px )
![](/images/grid-01.jpg)
2. 平板 ( >= 768px & < 960px )
![](/images/grid-02.jpg)
3. 桌机 ( >= 960px )
![](/images/grid-03.jpg)

依照这三个维度，定义出三种全站框架的宽度，分别为 `%container-width`、`%content-width`、`%box-width`；全站在定义平板与桌机宽度一致为平板 90%、桌机 960px，三种全架框架的宽度的差异在手机应用。

<br/>
> 文档路径: `/src/sass/generic/common.scss`

```css
// 全站容器宽度 container width 94vw

%container-width{
    width: 94%;
    width: 94vw;
    margin: 0 auto;
    @include box-sizing(border-box);
    @include breakpoint($tablet-width){
        width: 90%;
    }

    @include breakpoint($desktop-width){
        width: $desktop-width;
    }

    @media \0screen\,screen\9{ 
        width: $desktop-width;
    }
}

// 全站内容宽度 content width 84vw

%content-width{
    width: 84%;
    width: 84vw;
    margin: 0 auto;
    @include box-sizing(border-box);
    @include breakpoint($tablet-width){
        width: 90%;
    }

    @include breakpoint($desktop-width){
        width: $desktop-width;
    }

    @media \0screen\,screen\9{ 
        width: $desktop-width;
    }
}

// 全站模块宽度

%box-width{
    width: 90%;
    width: 84vw;
    margin: 0 auto;
    @include box-sizing(border-box);

    @include breakpoint($desktop-width){
        width: $desktop-width;
    }

    @media \0screen\,screen\9{ 
        width: $desktop-width;
    }
}

// 全站上下边距

%container-gutter{
    padding: 8% 0;
    padding: 8vw 0;
    @include breakpoint($tablet-width){
        padding: 50px 0;
    }

    @media \0screen\,screen\9{ 
        padding: 50px 0;
    }
}

// 鼠标滑入效果 hover

@mixin hover-opacity{
    @include opacity(0.8);
}

@mixin hover-transition($part:all){
    @include transition($part .3s ease-in-out);

    @media \0screen\,screen\9{ 
       @include transition-property(none); 
    }
}

// 标题图 title img

%title-brand-topics{ // 代表人物
    @media \0screen\,screen\9{ 
        background-image: url(/img/title/title-brand-topics.png);
    }
    background-image: url(/img/title/title-brand-topics.svg);
}

%title-brand-all-recipes{ // 所有菜譜
    @media \0screen\,screen\9{ 
        background-image: url(/img/title/title-brand-all-recipes.png);
    }
    background-image: url(/img/title/title-brand-all-recipes.svg);
}
...

// 图标 icon
%icon-map-marker{
    @media \0screen\,screen\9  { 
        background-image: url(/img/icon/map-marker.png);
    }
    background-image: url(/img/icon/map-marker.svg);
}

%icon-phone{
    @media \0screen\,screen\9  { 
        background-image: url(/img/icon/phone.png);
    }
    background-image: url(/img/icon/phone.svg);
}
...
```

#### extend.scss

将样式经常设定的代码编写为继承样式代码，未来在开发新的网站时，也能继续使用此继承样式。

> 文档路径: /src/sass/generic/extend.scss

```css
//清除浮動

%clearfix{    
    zoom:1;
    overflow:hidden;
}

%clearfix-both{
    &:after{
        display: table;
        content: " ";
        after: " ";
         line-height: 0;
        clear: both;
    }
}

// 輔助 maxin add-content

%add-content{
    content:" ";
    position: absolute;
    display: block;
    zoom:1;
    overflow:hidden;
}

// 將字推出

%text-hidden{
    white-space: nowrap;
    text-indent: 200%;
    overflow: hidden;
}

%text-overflow{
    text-overflow: ellipsis;
    white-space : nowrap;
    overflow: hidden;
}

// media query hidden

.mobile-hidden{
    display: none;
    @include breakpoint($tablet-width){
        @include inline-block; 
    }

    @media \0screen\,screen\9{ 
        @include inline-block; 
    }
}

.tablet-hidden{
    display: none;
    @include breakpoint($desktop-width){
        @include inline-block;
    }

    @media \0screen\,screen\9{ 
        @include inline-block; 
    }
}
```

#### maxin.scss
将样式经常设定的代码编写为混合指令样式代码，未来在开发新的网站时，也能继续使用此混合指令样式代码。

> 文档路径: `/src/sass/generic/maxin.scss`

```css
@mixin add-content($width:100%,$height:auto){ 
    @extend %add-content;
    width:$width;
    height: $height;

    @media \0screen\,screen\9{ 
        content:" ";
        position: absolute;
        display: block;
        zoom:1;
        overflow:hidden;
    }
}

@mixin clearfloat($width:auto){
    @if $width == auto{
        width: auto;
    }@else{
        width: $width;
    }

    float: none;
    margin: 0;
}
```
<br/>

### modules 内文档的运用

将欣和官网经常使用的元件进行样式模组化，一个 .scss 档案分别代表一个模组元件，命名为 `modules-*`，目前有的模组元件如下：

| 档案名称 | 说明 |
| :--- | :--- |
| _module-anchor.scss | 作者模组样式 |
| _module-article.scss | 文章模组样式 |
| _module-button.scss | 按钮模组样式 |
| _module-checkbox.scss | 多选模组样式 |
| _module-news-list.scss | 新闻列表模组样式 |
| _module-prod-list.scss | 产品列表模组样式 |
| _module-recipe-list.scss | 菜谱列表模组样式 |
| _module-search-bar.scss | 搜寻模组样式 |
| _module-selectbox.scss | 下拉选单模组样式 |
| _module-subtitle.scss | 主标题模组样式 |
| _module-tab.scss | 页签模组样式 |
| _module-topic-info.scss | 主题介绍模组样式 |


#### module-button.scss

#### module-news-list.scss

#### module-prod-list.scss

#### module-recipe-list.scss

#### module-topic-info.scss
主题介绍模组样式有一個 list-line 變數 ( on / off )：

| list-line:on | list-line:off |
| :--- | :--- |
| **直式列表多則**主題介紹 | **單則**主題介紹 |
|  |  |

> 文黨路徑: `/src/modules/_module-topic-info.scss`
> list-line:on 參考網址: http://shinho.com.cn/brandgroup/liuyuexian/attitude
> list-line:off 參考網址:http://shinho.com.cn/brandgroup/liuyuexian/recipedetail-17

``` css
@mixin topic-info($list-line:off){
	&-list, &-box{
		background: $base-bgcolor-lighten;
	}

	&-box{
		margin-bottom: 50px;
		@extend %container-width;
	}
…
}
```
## 新增与修改

**Step 1.** 新增专属于该页面的 scss 档案至 `/src/sass/layouts`
**Step 2.** 将该页面的 scss 档案 import 到 `global.scss` 主样式

```css
// 页面样式
…
@import "layout/brand-prod-detail";
@import "layout/brand-index";
@import "layout/brand-group";
// 新增于此
…
```
**Step 3.** 于该页面的 scss 档案内撰写样式
**Step 4.** 使用 Gulp 套件，将 SCSS 档案编译成 CSS 
>\# commandline  
> gulp watch

若尚未安装 Gulp 套件请参考：[1.3.2 开发环境设置 - 本机 Gulp 开发环境参数设置](/setting-gulp.md)