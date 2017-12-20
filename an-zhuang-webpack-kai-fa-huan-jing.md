# Webpack 开发环境参数设置

Webpack 是一个现代 JavaScript 应用程序的模块打包器(module bundler)。当 Webpack 处理应用程序时，它会递归地构建一个依赖关系图(dependency graph)，其中包含应用程序需要的每个模块，然后将所有这些模块打包成一个或多个bundle。

使用 Webpack 来协助 ES6 模块的管理，管理开发与发布两套版本的输出
- 开发：js 程序码未压缩（方便开发时除错） 
- 发布：js 程序码优化压缩，去除 consol,进行 ES6 转 ES5 的编码（适应不支援 ES6 语法的低阶浏览器，如 IE） 

## Webpack 快速入門

首先要安装 Node.js， Node.js 自带了软件包管理器 npm，Webpack 需要 Node.js v0.6 以上支持，建议使用最新版 Node.js。

1. 用 NPM 安装全局 Webpack
> \# commandline
> npm install webpack -g
2. 进入项目目录，用 npm 安装目录 Webpack
> \# commandline
> npm install webpack --save-dev
3. Webpack 在执行的时候，默认情况下，会搜索当前目录的`webpack.config.js`文件，文件设定下面说明

## Webpack 工作原理

ECMAScript 6 (简称 ES6)是新一代 Javascript ，可行模组化管理 js ，增加效能。但尚有低阶浏览器不支援，所以需要有 Babel 这样的转码器进行转码。Webpack 本身不只可以将 Babel 的转码用放进自动化流程，其实还有许多如程序码压缩、SCSS 编译等功能，在开发上缩短了许多时间。使用的设定可透过 `/webpack.config.js` 设置


## Webpack config setting

### 预設


 Webpack 设定档

> 文档路径：/webpack.config.js

为了更通用，我们将此设定档再分为 dev(开发)和 prod(上线)两版本，应用于开发与上线两种版本输出

```
module.exports = function(env) {
  return require(`./webpack.${env}.config.js`)
}
```

### 开发版 Webpack 设定档 

> 文档路径：/webpack.dev.config.js

```
const path = require('path');   //通用 Windows 和 MAC OS 档案系统  
const webpack = require('webpack'); 
const node_modules_dir = path.resolve(__dirname, 'node_modules');   //webpack 插件放置路径(透过 npm 安装)
const js_dir = path.resolve(__dirname, "src/lib");   //webpack js 组件路径 
const ExtractTextPlugin = require("extract-text-webpack-plugin");
const WebpackDevServer = require('webpack-dev-server');
const CleanWebpackPlugin = require('clean-webpack-plugin');   // 清除不需要的暂存档

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
                    'style-loader',   // 這個會後執行 (順序很重要)
                    'css-loader'   // 這個會先執行
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
            // js 模块引用列表
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
        // 针对 ES6 模块管理引用名称
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

### 上线版 Webpack 设定档 

> 文档路径：/webpack.prod.config.js

```
const path = require('path');   //通用 Windows 和 MAC OS 档案系统 
const webpack = require('webpack');
const node_modules_dir = path.resolve(__dirname, 'node_modules');   //webpack 插件放置路径(透过 npm 安装)
const js_dir = path.resolve(__dirname, "src/lib"); //webpack js 组件路径 
const ExtractTextPlugin = require("extract-text-webpack-plugin");
const UglifyJSPlugin = require('uglifyjs-webpack-plugin');   // 压缩插件引用
const CleanWebpackPlugin = require('clean-webpack-plugin');   // 清除不需要的暂存档
const es3ifyPlugin = require('es3ify-webpack-plugin');   // ES5 再转码，IE 低阶浏览器可识别
// dashboard 
const Dashboard = require('webpack-dashboard');
const DashboardPlugin = require('webpack-dashboard/plugin');
const dashboard = new Dashboard();


module.exports = {
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
    },
    output: {
        filename: '[name].js',
        // 所输出的档名
        path: path.resolve(__dirname, 'public/js/custom'),
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
                    'style-loader',  // 這個會後執行 (順序很重要)
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
            }
        ]
    },
    resolve: {
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
        // 针对 ES6 模块管理引用名称
        new webpack.ProvidePlugin({
            $: 'jquery',
            jQuery: 'jquery',
            'window.jQuery': 'jquery',
            'root.jQuery': 'jquery',
            'owlCarousel' : 'carousel',
            ScrollMagic : 'ScrollMagic',
        }),
        // 打包压缩时去掉 console.log
        new UglifyJSPlugin({
            compress: { screw_ie8: false , warnings: false},
            mangle: { except: ['$'],screw_ie8: false },
            output: {
                screw_ie8: false
            },
            support_ie8: true
        }),
        // dashboard
        new DashboardPlugin(dashboard.setData),

        // 清除多馀的档案
        new CleanWebpackPlugin(['./public/js/custom/'], {
            "verbose": true,
            "exclude": []
        }),
        // 输出低阶浏览器可识别的程序码
        new es3ifyPlugin()
    ]
}
```

## Babel

刚提到的 ES6 代码转为 ES5 代码，这部份的运作上需要另一支 Babel 设定档进行设定。

> 文档路径: /.babelrc

```
{
    "presets": [
    	["env",
    	{
    		"targets":{
    			"browsers": ["last 2 versions", "ie >= 7"] 
    		},
    		"useBuiltIns": true,

    	}]
    ],
    "plugins": ["transform-es3-member-expression-literals","transform-es3-property-literals"]    //针对低阶浏览器通用
} 
```




## 技術參考文檔

- [webpack](https://doc.webpack-china.org/concepts/)