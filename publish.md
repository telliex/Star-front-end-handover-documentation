# 发布网站

不管是调整后的检视、新功能的开发后、抑或上线前，由于 JS 的编写采 ES6 方式 ，低阶的 IE 浏览器尚未全面支援，故需要经过转码，将 ES6 代码转为 ES5 代码。


以下几种情况，分别用于各个场景转码需求：

**SCSS 编译＋监控** - 监控 .scss 档，将代码编为 .css。

> \# commandline  
> glup watch

**开发版本发布** - 一次性将 ES6 代码转为 ES5 代码。

> \# commandline  
> npm run dev

**开发版本发布＋监控** - 一次性将 ES6 代码转为 ES5 代码后，监控 .es6 档，一有更动，即时针对异动的 .es6 档 转码成 .js 档。

> \# commandline  
> npm run dev:watch

**开发版本发布＋监控＋浏览器 auto reload** - 一次性将 ES6 代码转为 ES5 代码后，监控 .es6 档，一有更动，即时针对异动的 .es6 档 转码成 .js 档，同时让目标浏览器刷新（本机架站软件需开启）。

> \# commandline  
> npm run dev:addListener

**上线版发布** - 一次性将 ES6 代码转为 ES5 代码，同时再将 ES6 ,代码转为低阶浏览器可识别的 ES3 并压缩。

> \# commandline  
> npm run prod



