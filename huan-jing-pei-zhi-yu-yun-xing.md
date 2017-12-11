## 從 github 抓取

將 Star 項目的檔案從 github 抓回
> git clone https://github.com/b-x-b/star-dev-server.git

## 安裝插件
> cd star-dev-serve
> npm install



## package.json

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
    "babel-core": "^6.26.0",
    "babel-loader": "^7.1.2",
    "babel-plugin-transform-es2015-modules-simple-commonjs": "^0.3.0",
    "babel-plugin-transform-es3-member-expression-literals": "^6.22.0",
    "babel-plugin-transform-es3-property-literals": "^6.22.0",
    "babel-plugin-transform-runtime": "^6.23.0",
    "babel-polyfill": "^6.26.0",
    "babel-preset-env": "^1.6.1",
    "babel-preset-es2015": "^6.24.1",
    "babel-preset-es2015-loose": "^8.0.0",
    "babel-runtime": "^6.26.0",
    "babelify": "^7.3.0",
    "browser-sync": "^2.18.13",
  //js壓縮
    "browserify": "^14.4.0",
    "buble-loader": "^0.4.1",
    "clean-webpack-plugin": "^0.1.16",
    "cross-env": "^5.0.5",
    "css-loader": "^0.28.7",
 // ES5 轉 ES4 (ES6 IE不支援，需藉 es3ify 再轉成 ES4)
    "es3ify-loader": "^0.2.0",
    "es3ify-webpack-plugin": "0.0.1",
    "event-stream": "^3.3.4",
    "exports-loader": "^0.6.4",
    "extract-text-webpack-plugin": "^3.0.0",
    "file-loader": "^0.11.2",
    "glob": "^7.1.2",
  //glup (scss 編議 css) 
    "gulp": "^3.9.1",
    "gulp-autoprefixer": "^4.0.0",
    "gulp-babel": "^6.1.2",
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
    "gulp-uglify": "^3.0.0",
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
    "uglify-es": "^3.1.0",
    "uglify-js-es6": "^2.8.9",
    "uglifyes-webpack-plugin": "^0.4.3",
    "uglifyjs-webpack-plugin": "^0.4.6",
    "url-loader": "^0.5.9",
    "video.js": "^6.2.8",
    "vinyl-buffer": "^1.0.0",
    "vinyl-source-stream": "^1.1.0",
    "webpack": "^3.8.1",
    "webpack-dashboard": "^1.0.0-5",
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
    "gsap": "^1.20.2",
    "jquery": "^1.12.4",
    "jquery-history": "^1.0.1",
    "jquery.cookie": "^1.4.1",
    "owl.carousel": "^2.2.0",
    "scrollmagic": "^2.0.5"
  }
}

```


### 環境配置

## 如何啟動

## 運行





# 參考資料

