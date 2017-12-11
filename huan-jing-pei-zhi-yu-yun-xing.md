## 從 github 抓取
將 Star 項目的檔案從 github 抓回
> git clone https://github.com/b-x-b/star-dev-server.git

## 安裝開發相關插件
> cd star-dev-serve
> npm install （install 會照 package.json 設定進行)

## 分支
- master 推至正式機，發佈上線版本
- release 上線前的版本，用於 QA 檢查
- develop 主要開發分支所在
- feature 新功能的開發，最後併入 develop 分支

## 開發說明
- 開發都先會在 develop 分支進行，若有新功能，也會在 develop 分支開始 branch 新的 feature，完成後再 merge 回 develop 分支，develop 分支到一段落（如上線前），會 merge 到 release 分支，進行 QA 工作，驗證遇有問題，回到 develop 分支除錯，完成後再 merge 到 QA 分支供 QA 再檢視。若檢視皆通過，即可 merge 到 master 分支等待上線。
- 上線時先上欣和測試機 `sh1.shinho.com.cn`，確認無誤時，再更新正式機`http://shinho.com.cn/`。
- 每個分支都完成階段工作時皆要推至 github 管理，主機推檔也是從 github 拉檔方式進行。安全性考量，勿使用 ftp 上傳檔案。
- 每日下班時需提交今日的工作。
- 

## package.json
以下是 install 時所依賴的設定。 `scripts` 部分後面章節說明，下面主要提及所安裝插件的插件功用`devDependencies`、`dependencies`

```
{
  "private": true,
  "scripts": {
  //發佈（壓縮）
    "prod": "webpack --config webpack.prod.config.js",
  //開發偵聽（可同時編譯出檔案）
    "dev:watch": "webpack --config webpack.dev.config.js  --watch",  
    "dev-serverbuild": "node server.js",
    "lint": "eslint my-files.js",
  //開發 + livereview
    "dev:addListener": "browser-sync start --proxy 'http://laravel' --files './public/js/custom/*.js'"  
  },
  "devDependencies": {
  //babel (ES6 轉碼 ES5)
    "babel-cli": "^6.24.1",
    
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
  // ES6 present  
    "babel-preset-env": "^1.6.1",

    "browser-sync": "^2.18.13",

    "buble-loader": "^0.4.1",
  //清除 output 檔案，避免產出多餘的亂數檔名檔案  
    "clean-webpack-plugin": "^0.1.16",
  //CSS loader  
    "css-loader": "^0.28.7",
  //ES5 轉 ES4 (ES6 IE不支援，需藉 es3ify 再轉成 ES4)
    "es3ify-loader": "^0.2.0",
    "es3ify-webpack-plugin": "0.0.1",
  //可將 CSS 單獨打包  
    "extract-text-webpack-plugin": "^3.0.0",
  //可將圖片載入模組  
    "file-loader": "^0.11.2",
    
    
  //glup相關
    "gulp": "^3.9.1",
  //glup相關-babel轉換ES6   
    "gulp-babel": "^6.1.2",
  //glup相關-可以使用类似于 node 的 require() 的方式来组织浏览器端的 Javascript 代码
    "browserify": "^14.4.0",
  //glup相關-將 ES6 转成 ES5  
    "babelify": "^7.3.0",
  //glup相關-将Browserify的bundle()的输出转换为Gulp可用的vinyl（一种虚拟文件格式）流 
    "vinyl-source-stream": "^1.1.0",
  //glup相關-辅助工具
    "vinyl-buffer": "^1.0.0",
  //压缩 JavaScript
    "gulp-uglify": "^3.0.0",

  
    "glob": "^7.1.2",
    "gulp-autoprefixer": "^4.0.0",
  
 

    "babel-core": "^6.26.0",
    "babelify": "^7.3.0",
   
    
    
    "gulp-clean-css": "^3.9.0",
    "gulp-compass": "^2.1.0",
    "gulp-concat": "^2.6.1",
    "gulp-cssnano": "^2.1.2",
    "gulp-livereload": "^3.8.1",
    "gulp-notify": "^3.0.0",
    "gulp-plumber": "^1.1.0",
    "gulp-rename": "^1.2.2",
    "gulp-sass": "^3.1.0",
    "gulp-sourcemaps": "^2.6.0",
    "gulp-tap": "^1.0.1",
    
    "gulp-util": "^3.0.8",
    "html-loader": "^0.5.1",
    "html-webpack-plugin": "^2.30.1",
    "image-webpack-loader": "^3.4.0",
    "less": "^2.7.2",
    "less-loader": "^4.0.5",
    "minimatch": "^3.0.4",
    "node-sass": "^4.5.3",
    "postcss-loader": "^2.0.8",
    "sass-loader": "^6.0.6",
    "script-loader": "^0.7.1",
    "style-loader": "^0.18.2",
  //壓縮 js
    "uglify-es": "^3.1.0",
    "uglify-js-es6": "^2.8.9",
    "uglifyes-webpack-plugin": "^0.4.3",
    "uglifyjs-webpack-plugin": "^0.4.6",
    
    "url-loader": "^0.5.9",

  //webpack 
    "webpack": "^3.8.1",
  //webpack 發佈仪表盘  
    "webpack-dashboard": "^1.0.0-5",
  //即時熱  
    "webpack-dev-middleware": "^1.12.0",
    "webpack-dev-server": "^2.8.2",
    "webpack-hot-middleware": "^2.19.1"
  },
  "dependencies": {
    "babel-plugin-add-module-exports": "^0.2.1",
    "console-polyfill": "^0.3.0",
    "core-js": "^2.5.1",
    "es5-shim": "^4.5.9",
    "es6-promise": "^4.1.1",
    "fetch-ie8": "^1.5.0",
  // Tween  
    "gsap": "^1.20.2",
  //JS 主要函數庫
    "jquery": "^1.12.4",
  //base on jquery的網址指向功能
    "jquery-history": "^1.0.1",
  //base on jquery的 cookie 功能，
    "jquery.cookie": "^1.4.1",
  // KV 輪播  
    "owl.carousel": "^2.2.0",
  //捲動視差特效功能  
    "scrollmagic": "^2.0.5"
  }
}

```


### 環境配置

## 如何啟動

## 運行





# 參考資料

