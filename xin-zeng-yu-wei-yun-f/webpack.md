# webpack

## 新增

新增页面时，需更动 **webpack.dev.config.js** & **webpack.prod.config.js**
```
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
```




