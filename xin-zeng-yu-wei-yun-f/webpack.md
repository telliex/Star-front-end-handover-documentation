# webpack

## 新增网页页面

新增页面时，需更动 **webpack.dev.config.js**（开发） & **webpack.prod.config.js**（上线）

```
...
entry: {
        // 多頁面入口，针对不同页面 js 进行添加，.es6 转 .js (es6 转码)
        'global': './src/js/global.es6',
        'lyt-about-csv': './src/js/lyt-about-csv.es6',
        'lyt-about-business': './src/js/lyt-about-business.es6',
        'lyt-about-focus': './src/js/lyt-about-focus.es6',
        'lyt-about-history': './src/js/lyt-about-history.es6',
        'lyt-about-crafts': './src/js/lyt-about-crafts.es6',
        'lyt-about': './src/js/lyt-about.es6',
        'lyt-brand-attitude': './src/js/lyt-brand-attitude.es6',
        'lyt-brand-group': './src/js/lyt-brand-group.es6',
        'lyt-brand-index': './src/js/lyt-brand-index.es6',
        'lyt-brand-news-list': './src/js/lyt-brand-news-list.es6',
        'lyt-brand-prod-detail': './src/js/lyt-brand-prod-detail.es6',
        'lyt-brand-prod-list': './src/js/lyt-brand-prod-list.es6',
        'lyt-brand-prod-print': './src/js/lyt-brand-prod-print.es6',
        'lyt-brand-recipe-detail': './src/js/lyt-brand-recipe-detail.es6',
        'lyt-brand-recipe-list': './src/js/lyt-brand-recipe-list.es6',
        'lyt-brand-topic': './src/js/lyt-brand-topic.es6',
        'lyt-careers-camp-recruiting-list': './src/js/lyt-careers-camp-recruiting-list.es6',
        'lyt-careers-recruiting-list': './src/js/lyt-careers-recruiting-list.es6',
        'lyt-careers': './src/js/lyt-careers.es6',
        'lyt-news-detail': './src/js/lyt-news-detail.es6',
        'lyt-news-list': './src/js/lyt-news-list.es6',
        'lyt-recipedetail': './src/js/lyt-recipedetail.es6',
        //加入对应的 js 名称及路径
        'new-js-name': './src/js/new-js-name.es6',
    },
...
```
如此开发与上线编译时才能正确够过 webpack 编译 ES6。


## 新增网页引用 js modeule

页面加入 js modeule 的引用，若名称无法在 js 模塊系統內被引用，可添加以下设置
```
...
resolve: {
        // 使用的扩展名
        alias: {
            // 模块别名列表
            "jquery$": js_dir + "/jquery.js",
            "jquery.history$": js_dir + "/jquery.history.js",
            "jquery.cookie$": js_dir + "/jquery.cookie.js",
            "carousel$": js_dir + "/owlcarousel/owl.carousel.js",
            "jqRotate$": js_dir + "/jQueryRotate.js",
            "jqMobile$": js_dir + "/jquery.mobile.min.js",
            "TweenLite$": node_modules_dir + '/gsap/src/uncompressed/TweenLite.js',
            "TweenMax$": node_modules_dir + '/gsap/src/uncompressed/TweenMax.js',
            "TimelineLite$": node_modules_dir + '/gsap/src/uncompressed/TimelineLite.js',
            "TimelineMax$": node_modules_dir + '/gsap/src/uncompressed/TimelineMax.js',
            "ScrollMagic$": node_modules_dir + '/scrollmagic/scrollmagic/uncompressed/ScrollMagic.js',
            "animation$": node_modules_dir + '/scrollmagic/scrollmagic/uncompressed/plugins/animation.gsap.js',
            "debug.addIndicators$": node_modules_dir + '/scrollmagic/scrollmagic/uncompressed/plugins/debug.addIndicators.js',
            //加入对应的 js 名称路径
            "newJsModuleName":js/module/location/newJs.js
        }

    },
...

```

## 技術參考文檔

- [webpack](https://doc.webpack-china.org/concepts/)

