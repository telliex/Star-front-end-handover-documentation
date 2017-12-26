# CSS

## CSS 代码文档运用

---

在欣和官网上目前使用到的三个主样式，分别为 `global.scss`、`global-org.scss`、`errors.scss`，各个主样式依照需求 `@import` 所需的文档与套件；而在 `@import` 的顺序上与转译后的代码顺序有关，依序如下：

1. 样式框架、各浏览器样式重置 \(使用 compass 预设版本\)
2. 依照官网需求各浏览器样式重置参数、全站使用的样式变数、Susy 栅栏设定
3. 全站通用样式、全站继承样式模块代码、全站混合指令样式代码
4. 模组样式
5. 元件样式
6. 页面样式
7. 套件样式

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

### base 内文档的运用

#### base-style-setting.scss

各个浏览器预设样式并不一致，在建立 `global.scss`、`global-org.scss`、`errors.scss` 等主样式档案时，使用 SCSS 预设版本的 `@import "compass/reset"`将各个浏览器预设样式设定相同属性，便于未来开发减少样式上的差异；此外在 `base-style-setting.scss` 依照官网需求调整了样式重置的参数，这里的样式若需要调整更动，会改变全站 html tag 的样式，若非全站统一更动样式需求，请勿修改此档案。

#### grid-setting.scss

官网所使用的 Susy 栅栏框架设定，若非全站统一更动样式需求，请勿修改此档案。

* [Susy 2.2 中文文檔](https://www.w3cplus.com/preprocessor/susy-docs.html) 

#### variables.scss

依照官网的 Style Guideline 建置全站的变数档案，若非全站统一更动样式需求，请勿修改此档案。之后新增与运维样式，都需要使用 `variables.scss` 内的变数；若有大量重复的参数，可依照分类建立新的变数值。

```css
// 字型设定 Font Setting
$base-font-family                  : "Hiragino Sans GB","Microsoft YaHei","WenQuanYi Micro Hei",sans-serif;
$base-highlight-font-family        : "Times New Roman";
$base-font-size                    : 16px;
$base-line-height                  : 2em;
$base-letter-spacing               : 0.05em;
$base-box-line-height              : $base-line-height * 0.75;

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

### generic 内文档的运用

#### common.scss
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

// 全站边距

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
```
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

```
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

@mixin arrow($direct:down,$arrow-size:8px,$bg-color:$base-bgcolor-lighten,$border-color:$base-border-color-lighten){
	&:before,&:after{
		content:" ";
		position: absolute;
		display: block;
		width: 0;
		height: 0;
		zoom:1;
		overflow:hidden;
		left: 50%;
		margin-left: $arrow-size * -1;
	}

	&:before{
		border: $bg-color $arrow-size solid;
		z-index: 10;
		@if $direct == up{
			top: $arrow-size * -2;
			border-color: transparent transparent $bg-color transparent;
		}@else{
			bottom: $arrow-size * -2;
			border-color: $bg-color transparent transparent transparent;
		}
	}
	&:after{
		border: $border-color $arrow-size + 2 solid;
		margin-left: ($arrow-size + 2) * -1;
		z-index: 0;
		@if $direct == up{
			top: ($arrow-size + 2) * -2;
			border-color: transparent transparent $border-color transparent;
		}@else{
			bottom: ($arrow-size + 2) * -2;
			border-color: $border-color transparent transparent transparent;
		}
	}
}

```

### modules

#### module-button

#### module-news-list.scss

#### module-prod-list.scss

#### module-recipe-list.scss

#### module-topic-info.scss

## 新增



