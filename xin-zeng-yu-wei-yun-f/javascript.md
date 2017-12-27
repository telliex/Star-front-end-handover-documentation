# Javascript

Javascript 采 ES6 模组，

> 功能：各页面通用，主副选单定位、判断浏览器、cookie、
> 文档路径：/src/js/global.js
> 载入的模块：/src/js/base.js.js
>           /src/js/browser.js
>           /src/js/generic.js
>           /src/js/maxin.js
>           /src/js/partical.js




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


> 功能：主副选单定位、判断浏览器、cookie、
> 文档路径：/src/js/global.js



## 技术文件参考资料
---

