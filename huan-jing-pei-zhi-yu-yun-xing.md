# 开发环境配置
## 安装本机开发架站软体
- Mac OS - [MAMP](https://www.mamp.info/en/)
- Windows - [XAMPP](https://www.apachefriends.org/zh_tw/index.html)

## 从 github 抓取
将 Star 项目开发档案从 github 抓回
> git clone https://github.com/b-x-b/star-dev-server.git

## 安装开发时依赖的相关插件
install 会照 package.json 设定进行,安装项目会用到的 plugin
> cd star-dev-serve
> npm install 


## 启动开发架站软体
将网站根目录指向 `/public` ， Host 名称设为 laravel (http://laravel/)

## 分支
- master 推至正式机，发佈上线版本
- release 上线前的版本，用于 QA 检查
- **develop 主要开发分支所在**
- feature 新功能的开发，最后併入 develop 分支

## 开发说明
- 开发都先会在 develop 分支进行，若有新功能，也会在 develop 分支开始 branch 新的 feature，完成后再 merge 回 develop 分支，develop 分支到一段落（如上线前），会 merge 到 release 分支，进行 QA 工作，验证遇有问题，回到 develop 分支除错，完成后再 merge 到 QA 分支供 QA 再检视。若检视皆通过，即可 merge 到 master 分支等待上线。
- 上线时先上欣和测试机 `sh1.shinho.com.cn`，确认无误时，再更新正式机`http://shinho.com.cn/`。
- 每个分支都完成阶段工作时皆要推至 github 管理，主机推档也是从 github 拉档方式进行。安全性考量，勿使用 ftp 上传档案。
- 每日下班时需提交今日的工作。

## package.json
以下是 install 时所依赖的设定。 `scripts` 部分后面章节说明，下面主要提及所安装插件的插件功用`devDependencies`、`dependencies`

```
{
    "private": true,
    "scripts": {
  //发佈（压缩）
    "prod": "webpack --config webpack.prod.config.js",
  //开发侦听（可同时编译出档案）
    "dev:watch": "webpack --config webpack.dev.config.js --watch",
    "dev-serverbuild": "node server.js",
    "lint": "eslint my-files.js",
  //开发 + livereview
    "dev:addListener": "browser-sync start --proxy 'http://laravel' --files './public/js/custom/*.js'"
    },
    "devDependencies": {
  //babel (ES6 转码 ES5)
    "babel-cli": "^6.24.1",
  //代码需要调用Babel的API进行转码，就要使用babel-core模块
    "babel-core": "^6.26.0",
    "babel-loader": "^7.1.2",
    "babel-plugin-transform-es2015-modules-simple-commonjs": "^0.3.0",
  //使 IE8 接受 default or catch 关键字
    "babel-plugin-transform-es3-member-expression-literals": "^6.22.0",
    "babel-plugin-transform-es3-property-literals": "^6.22.0",
  //转换新的 API，比如 Promise，以及 Object.assign、Array.from 等方法
    "babel-runtime": "^6.26.0",
    "babel-plugin-transform-runtime": "^6.23.0",
  //使用ES6的API
    "babel-polyfill": "^6.26.0",
  //ES6 present
    "babel-preset-env": "^1.6.1",
  //页面刷新插件
    "browser-sync": "^2.18.13",
  //清除 output 档案，避免产出多馀的乱数档名档案
    "clean-webpack-plugin": "^0.1.16",
  //CSS loader
    "css-loader": "^0.28.7",
  //es3ify解决es3环境兼容
    "es3ify-loader": "^0.2.0",
    "es3ify-webpack-plugin": "0.0.1",
  //可将 CSS 单独打包
    "extract-text-webpack-plugin": "^3.0.0",add-module-exports
  //可将图片载入模组
    "file-loader": "^0.11.2",
  //glup相关
    "gulp": "^3.9.1",
  //glup相关-babel转换ES6
    "gulp-babel": "^6.1.2",
  //glup相关-可以使用类似于 node 的 require() 的方式来组织浏览器端的 Javascript 代码
    "browserify": "^14.4.0",
  //glup相关-将 ES6 转成 ES5
    "babelify": "^7.3.0",
  //glup相关-将Browserify的bundle()的输出转换为Gulp可用的vinyl（一种虚拟文件格式）流
    "vinyl-source-stream": "^1.1.0",
  //glup相关-辅助工具
    "vinyl-buffer": "^1.0.0",
  //glup相关-压缩 JavaScript
    "gulp-uglify": "^3.0.0",
  //glup相关-查看压缩后的 JS 代码所对应的行数时，source map 就能告诉你其相应代码在未压缩文件的所在行数
    "gulp-sourcemaps": "^2.6.0",
  //glup相关-压缩css文件
    "gulp-cssnano": "^2.1.2",
  //glup相关-重新命名文件
    "gulp-rename": "^1.2.2",
  //glup相关-合并文件
    "gulp-concat": "^2.6.1",
  //glup相关-产出多文件
    "glob": "^7.1.2",
  //glup相关-测试插件
    "event-stream": "^3.3.4",
  //glup相关-监听每个文件的变化
    "gulp-livereload": "^3.8.1",
  //glup相关-载入 gulp-sass
    "gulp-sass": "^3.1.0",
  //glup相关-编译scss
    "gulp-compass": "^2.1.0",
  //glup相关-避免出现错误时中断程式
    "gulp-plumber": "^1.1.0",
  //glup相关-清除并压缩 css
    "gulp-clean-css": "^3.9.0",
    "minimatch": "^3.0.4",
  //各个loader
    "node-sass": "^4.5.3",
    "sass-loader": "^6.0.6",
    "script-loader": "^0.7.1",
    "style-loader": "^0.18.2",
    "less": "^2.7.2",
    "image-webpack-loader": "^3.4.0",
    "less-loader": "^4.0.5",
    "url-loader": "^0.5.9",
    "html-loader": "^0.5.1",
    "buble-loader": "^0.4.1",
  //压缩 js
    "uglify-es": "^3.1.0",
    "uglify-js-es6": "^2.8.9",
    "uglifyes-webpack-plugin": "^0.4.3",
    "uglifyjs-webpack-plugin": "^0.4.6",
  //webpack
    "webpack": "^3.8.1",
  //webpack 发佈仪表盘
    "webpack-dashboard": "^1.0.0-5",
  //即时热插拔
    "webpack-dev-middleware": "^1.12.0",
    "webpack-dev-server": "^2.8.2",
    "webpack-hot-middleware": "^2.19.1"
  },
"dependencies": {
    "babel-plugin-add-module-exports": "^0.2.1",
  //Browser console polyfill. Makes it safe to do console.log().  
    "console-polyfill": "^0.3.0",
    "core-js": "^2.5.1",
    "es5-shim": "^4.5.9",
    "es6-promise": "^4.1.1",
    "fetch-ie8": "^1.5.0",
  // Tween
    "gsap": "^1.20.2",
  //JS 主要函数库
    "jquery": "^1.12.4",
  //base on jquery的网址指向功能
    "jquery-history": "^1.0.1",
  //base on jquery的 cookie 功能，
    "jquery.cookie": "^1.4.1",
  // KV 轮播
    "owl.carousel": "^2.2.0",
  //捲动视差特效功能
    "scrollmagic": "^2.0.5"
  }
}

```

## 技術參考資料

-[完整开发档案原始档]()
