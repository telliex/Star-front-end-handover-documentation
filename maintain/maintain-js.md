# 新增与運維 - Javascript

## 为什么使用 ES6 
---
ES6 模块是**编译时加载**，效率要比 CommonJS 模块的**运行时加载**方式高。将来服务器和浏览器都会支持 ES6 模块格式。
<br/>



## ES6 语法
---
通过 export 命令显式指定输出的代码，再通过 import 命令输入。一个模块就是一个独立的文件。该文件内部的所有变量，外部无法获取。外部的 JS 函数库如 JQuery , ScrollMagic 也是一支独立档，亦可算是一个模组载入使用。

### export

```
var firstName = 'Michael';
function multiply(x, y) {
    return x * y;
    };
var year = 1958;

export { firstName, multiply, year };
```

### import

```
import { firstName, multiply, year } from './profile';
```
<br/>



## ES6 使用
---

网站各页面 JS 汇入有两支，一支是所有页面通用的 `global.js`，另一支是针对个页面自己独立的 JS 档 `lyt-xxx.es6`，简单的介绍架构如下：

### 通用 JS

> 文档路径：`/src/js/global.js`
> 属性：各页面通用
> 功能：如下方注解
> 载入的模块：
> `/src/js/base.js.js`
> `/src/js/browser.js`
> `/src/js/generic.js`
> `/src/js/maxin.js`
> `/src/js/partical.js`

```
import 'jquery';                          // 载入 jQuery 模块
import 'jquery.history';                  // 载入 jquery.history 模块
import 'jquery.cookie';                   // 载入 jquery.cookie 模块，用於提示使用者更新浏览器版本
import  {browserType} from './browser';   // 判断 IE 浏览器版本
import 'ScrollMagic';                     // ScrollMagic 视窗卷动互动插件
import 'animation';                       // 辅助 ScrollMagic 视窗卷动互动插件。用于动画呈现
import 'debug.addIndicators';             // 辅助 ScrollMagic 视窗卷动互动插件。用于开发或 debug 情境
import 'TweenMax';                        // 辅助 ScrollMagic 视窗卷动互动插件。
import 'TimelineMax';                     // 辅助 ScrollMagic 视窗卷动互动插件。
import { viewport } from './maxin';       // 回传视窗宽度
import { globalBrowserChecker } from './base';  // 判断浏览器状态,如桌机或是手机、是否为 IE8、是否为 modern browser、是否支援 Flash
import { videoSize, lowBrowserSupportMess, creatSMController, resetSMController, globalReset } from './generic';    // scrollMagic 物件的建立与移除、alert 安装 flash 提示、alert 更新浏览器提示
import { globalPartical } from './partical';  // 主副选单定位功能、GoToTop 功能、手机汉堡选单呈现、页面 loading 时淡出、

```

**Owl Carousel**、**Slick** 及 **ScrollMagic** 的使用请见下方参考资料。


### 各页面 JS

> 功能：各页面内效果
> 文档路径：
> `/src/js/global.es6`                             
> `/src/js/lyt-about-csv.es6`                     
> `/src/js/lyt-about-business.es6`               
> `/src/js/lyt-about-focus.es6`                  
> `/src/js/lyt-about-history.es6`                 
> `/src/js/lyt-about-crafts.es6`                 
> `/src/js/lyt-about.es6`                         
> `/src/js/lyt-brand-attitude.es6`                
> `/src/js/lyt-brand-group.es6`                    
> `/src/js/lyt-brand-index.es6`                      
> `/src/js/lyt-brand-news-list.es6`                 
> `/src/js/lyt-brand-prod-detail.es6`              
> `/src/js/lyt-brand-prod-list.es6`                 
> `/src/js/lyt-brand-prod-print.es6`              
> `/src/js/lyt-brand-recipe-detail.es6`               
> `/src/js/lyt-brand-recipe-list.es6`              
> `/src/js/lyt-brand-topic.es6`                    
> `/src/js/lyt-careers-camp-recruiting-list.es6`   
> `/src/js/lyt-careers-recruiting-list.es6`         
> `/src/js/lyt-careers.es6`                           
> `/src/js/lyt-itinerary.es6`                       
> `/src/js/lyt-news-detail.es6`                     
> `/src/js/lyt-news-list.es6`                       
> `/src/js/lyt-recipedetail.es6`                    


```
import '../lib/owlcarousel/assets/owl.carousel.min.css';   // 载入 owl carousel 模块 CSS 样式
import '../lib/owlcarousel/assets/owl.theme.default.min.css';   // owl carousel 模块 CSS 样式
import '../lib/owlcarousel/assets/animate.css';     // owl carousel 模块 animate CSS 样式

import 'jquery';  // 载入 jQuery 模块
import 'carousel'; // 载入 owl carousel KV 轮播插件模块
import 'slick';  // video 淡入淡出插件模块  
import 'ScrollMagic';                     // ScrollMagic 视窗卷动互动插件
import 'animation';                       // 辅助 ScrollMagic 视窗卷动互动插件。用于动画呈现
import 'debug.addIndicators';             // 辅助 ScrollMagic 视窗卷动互动插件。用于开发或 debug 情境
import 'TweenMax';                        // 辅助 ScrollMagic 视窗卷动互动插件。
import 'TimelineMax';                     // 辅助 ScrollMagic 视窗卷动互动插件。
import * as share from './share.es6';   // 载入 Ajax 模块

```
* 详细档案说明请参考：[1.4.2 文档架构说明 - Javascript 代码文档架构](/document-architecture/document-architecture-js.md)

Owl Carousel、Slick 及 ScrollMagic 的使用请见下方参考资料。
<br/>

## 技术文件参考资料
---

- [Module 的语法](http://es6.ruanyifeng.com/#docs/module)
- [Owl Carousel](https://owlcarousel2.github.io/OwlCarousel2/)
- [Slick](http://kenwheeler.github.io/slick/)
- [ScrollMagic](http://scrollmagic.io/)
