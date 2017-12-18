# webpack 开发环境参数设置
webpack 是一个现代JavaScript 应用程序的模块打包器(module bundler)。当webpack 处理应用程序时，它会递归地构建一个依赖关系图(dependency graph)，其中包含应用程序需要的每个模块，然后将所有这些模块打包成一个或多个bundle。

使用 webpack 来协助 ES6 模块的管理，管理开发与发布两套版本的输出
- 开发：js 程序码未压缩（方便开发时除错） 
- 发布：js 程序码优化压缩，去除 consol,进行 ES6 转 ES5 的编码（适应不支援 ES6 语法的低阶浏览器，如 IE） 

## Webpack 快速入門

## Gulp setting
`/webpack.config.js` 已此档将设定档分为 dev(开发)和 prod(发布)两版本

```
module.exports = function(env) {
  return require(`./webpack.${env}.config.js`)
}
```


`/webpack.dev.config.js`

```
const path = require('path');
const webpack = require('webpack');
const node_modules_dir = path.resolve(__dirname, 'node_modules');
const js_dir = path.resolve(__dirname, "src/lib");
const ExtractTextPlugin = require("extract-text-webpack-plugin");
const WebpackDevServer = require('webpack-dev-server');
const CleanWebpackPlugin = require('clean-webpack-plugin');
const es3ifyPlugin = require('es3ify-webpack-plugin');

module.exports = {
    devtool: 'source-map',
    devServer: {
        hot: true,
        quiet: true,
        compress: true,
        inline: true,
        contentBase: path.join(__dirname, "public"),
    },
    // 通过在浏览器调试工具(browser devtools)中添加元信息(meta info)增强调试
    entry: {
        // 单页应用(SPA)：一个入口起点，多页应用(MPA)：多个入口起点。
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
    },
    output: {
        filename: '[name].js',
        // 所输出的档名
        path: path.resolve(__dirname, 'public/js/custom/'),
        // 所有输出文件的目标路径
        sourceMapFilename: "../../../src/map/[file].map"
    },
    module: {
        rules: [
            // 模块规则（配置 loader、解析器等选项）
            {
                loader: 'babel-loader',
                test: /\.(es6|js)$/,
            },
            {
                loader: 'es3ify-loader',
                test: /\.(es6|js)$/,
                include: /\/node_modules\//,
                enforce: "post"
            },
            {
                test: /\.css$/,
                use: [
                    'style-loader', // 這個會後執行 (順序很重要)
                    'css-loader' // 這個會先執行
                ]
            },
            {
                test: /\.(png|svg|jpg|gif)$/,
                use: ['file-loader']
            },
            {
                test: /\.(woff|woff2|eot|ttf|otf)$/,
                use: ['file-loader']
            },
        ]
    },
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
            "slick$": js_dir + "/slick/slick.js",
        }

    },
    plugins: [
        // 清除 js 资料夹
        new webpack.ProvidePlugin({
            $: 'jquery',
            jQuery: 'jquery',
            'window.jQuery': 'jquery',
            'root.jQuery': 'jquery',
            'owlCarousel': 'carousel',
            ScrollMagic: 'ScrollMagic',
        }),
        // 清除多馀的档案
        new CleanWebpackPlugin(['./public/js/custom/'], {
            "verbose": true,
            "exclude": []
        }),
    ]

}

```



## 技術參考文檔
- [webpack](https://doc.webpack-china.org/concepts/)