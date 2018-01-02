# 开发环境配置

## 本机开发环境
---

### Step0.安装环境所需软体

- [Node.js](https://nodejs.org/en/)
- [Git](https://git-scm.com/)
- XCode - Mac OS 使用者需加安装

### Step1.安装本机开发用架站软体

以下为推荐的架站工具，同性质的其他工具可替代。

- Mac OS - [MAMP](https://www.mamp.info/en/)

  ▼ 留意 **PHP version 5.6** 及 Root 的路径需指向 `/public` ，如下圖：

  ![MAMP](/images/MAMP-image.jpg)
  
  ▼ 设定为 **80 port** ，如下圖：
  
  ![MAMP](/images/MAMP-image2.jpg)


- Windows - [XAMPP](https://www.apachefriends.org/zh_tw/index.html)

  ▼ 预设为 **80 port** ，把 Apache & MySQL 打開，如下圖：
  
  ![XAMPP](/images/xampp-image.jpg)

安装完后，开启架站软体（MAMP 或 XAMPP），确认工具可正常使用。

### Step2.从 github 抓取档案

将从 [Star Github](https://github.com/b-x-b/star-dev-server)  fork 回来的 Github Repositories  复制档案到本机

> \# commandline
> git clone https://github.com/b-x-b/star-dev-server.git

或

> \# commandline
> git clone https://github.com/shinho-github-name/star-dev-server.git   # 仅示意，非切确 URL

### Step3.安装开发时依赖的相关插件

install 指令会参照 `package.json` 罗列的配置，进行安装所需的 plugin
> \# commandline
> cd star-dev-serve
> npm install 

### Step4.启动开发架站软体

设置架站软体（MAMP 或 XAMPP），将网站根目录指向 `/public` ， Host 名称设为 laravel  `http://laravel/` （可自行命名）

### Step5.汇入数据库

1. 架站软件中建立数据库，名称为 **shinhowebsite** 
2. 抓取当天官网的数据库
> \# commandline
> scp -r -P 1212 www@116.62.117.96:/dockerfile/shinho/app/sqlbak/  /Users/使用者名称/欲放置的资料夹
3. 汇入数据库

  > **[info] For info**
  > 密码洽欣和春涛

### Step6.汇入图档

1. 抓取官网数据库用图
> \# commandline
> scp -r -P 1212  www@116.62.117.96:/dockerfile/shinho/app/star-dev-server/public/img/up /Users/使用者名称/欲放置的资料夹
2. 将抓下来的图放进开发环境 '/public/img/up' 内

  > **[info] For info**
  > 密码洽欣和春涛

### Step7.建立 .env

> 文档路径：/.env

此档在本机开发时实为重要，上线版本是不需要的**(也勿放上)**。`.env` 檔案不應該被提交到應用程式的版本控制系統，因為每個使用應用程式的開發人員或伺服器可能需要不同的環境設定。。若 clone 回来的档案没有此档，请自行建立。内容如下：

##### Mac OS - MAMP

```
APP_ENV=local
APP_KEY=base64:C4s5VyTWCyzuZkwgUuh7NUqWNdYmWGj7pnxaxPVj4s4=
APP_DEBUG=true
APP_LOG_LEVEL=debug
APP_URL=http://localhost

DB_SOCKET=/Applications/MAMP/tmp/mysql/mysql.sock     
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=shinhowebsite    //  加入资料库名称
DB_USERNAME=shinhowebsite    //  填入架站软体数据库使用者名称
DB_PASSWORD=12345678    //  填入架站软体数据库使用者密码

BROADCAST_DRIVER=log
CACHE_DRIVER=file
SESSION_DRIVER=file
QUEUE_DRIVER=sync

 {% em color="#ff0000" %}REDIS_HOST=127.0.0.1{% endem %}
REDIS_PASSWORD=null
REDIS_PORT=6379

MAIL_DRIVER=smtp
MAIL_HOST=mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null

PUSHER_APP_ID=
PUSHER_KEY=
PUSHER_SECRET=
```

##### Windows - XAMPP

```
APP_ENV=local
APP_KEY=base64:C4s5VyTWCyzuZkwgUuh7NUqWNdYmWGj7pnxaxPVj4s4=
APP_DEBUG=true
APP_LOG_LEVEL=debug
APP_URL=http://localhost

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=shinhowebsite    //  加入资料库名称
DB_USERNAME=shinhowebsite    //  填入架站软体数据库使用者名称
DB_PASSWORD=12345678    //  填入架站软体数据库使用者密码

BROADCAST_DRIVER=log
CACHE_DRIVER=file
SESSION_DRIVER=file
QUEUE_DRIVER=sync

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

MAIL_DRIVER=smtp
MAIL_HOST=mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null

PUSHER_APP_ID=
PUSHER_KEY=
PUSHER_SECRET=

```

#### 工作原理
Laravel 框架的所有設定都存放於 config 目錄中，env() 中第一個參數是 .env 檔案中的設定鍵值名稱，第二個參數是預設值，若讀取不到環境設定鍵值則會使用預設值

> 'debug' => env('APP_DEBUG', false),

### Step8.启动开发架站软体

▼ 打开浏览器连接 `http://laravel/` 出现官网首页表成功。

![frontpage](/images/shinho-website-frontpage.png)


## 如何进行开发
---

### git 分支

复制回的档案，分支规划如下

- master 推至正式机，发佈上线版本
- release 上线前的版本，用于 QA 检查
- **develop 主要开发分支所在**
- feature 未来新功能的开发，最后併入 develop 分支

### Git 视觉化管理工具

以图形介面的 Git 管理工具可增加工作效率，推荐使用

- Mac OS - [SourceTree](https://www.sourcetreeapp.com/)
- Windows - [tortoisegit](https://tortoisegit.org/)

### 开发说明

- 开发都先会在 develop 分支进行，若有新功能，也会在 develop 分支开始 branch 新的 feature，完成后再 merge 回 develop 分支，develop 分支开发到一段落（如上线前），会 merge 到 release 分支，进行 QA 工作，验证遇有问题，回到 develop 分支除错，完成后再 merge 到 QA 分支，让 QA team 再检视。若检视皆通过，即可 merge 到 master 分支等待上线。
- 各分支的修改皆需推至远端 Github 上，进行版本管理。
- 一般阶段性功能的上机检视工作，登入开发机，从主机将档案从 Github 拉回，`git pull`。
- 上线前先上欣和测试机 `sh1.shinho.com.cn`，确认无误时，再更新正式机`http://shinho.com.cn/`。
- 每个分支都完成阶段工作时皆要推至 github 管理，主机推档也是从 github 拉档方式进行。安全性考量，勿使用 ftp 上传档案。
- 每日下班时需提交今日的工作至 GitHub 上。

## package.json
---

以下是 install 时所依赖的设定。 `scripts` 部分后面章节说明，下面主要提及所安装插件的插件功用`devDependencies`、`dependencies`

```
{
    "private": true,
    "scripts": {
  // 发佈（压缩）
    "prod": "webpack --config webpack.prod.config.js",
  // 开发侦听（可同时编译出档案）
    "dev:watch": "webpack --config webpack.dev.config.js --watch",
    "dev-serverbuild": "node server.js",
    "lint": "eslint my-files.js",
  // 开发 + livereview
    "dev:addListener": "browser-sync start --proxy 'http://laravel' --files './public/js/custom/*.js'"
    },
    "devDependencies": {
  // babel (ES6 转码 ES5)
    "babel-cli": "^6.24.1",
  //代码需要调用Babel的API进行转码，就要使用babel-core模块
    "babel-core": "^6.26.0",
    "babel-loader": "^7.1.2",
    "babel-plugin-transform-es2015-modules-simple-commonjs": "^0.3.0",
  // 使 IE8 接受 default or catch 关键字
    "babel-plugin-transform-es3-member-expression-literals": "^6.22.0",
    "babel-plugin-transform-es3-property-literals": "^6.22.0",
  // 转换新的 API，比如 Promise，以及 Object.assign、Array.from 等方法
    "babel-runtime": "^6.26.0",
    "babel-plugin-transform-runtime": "^6.23.0",
  // 使用ES6的API
    "babel-polyfill": "^6.26.0",
  // ES6 present
    "babel-preset-env": "^1.6.1",
  // 页面刷新插件
    "browser-sync": "^2.18.13",
  // 清除 output 档案，避免产出多馀的乱数档名档案
    "clean-webpack-plugin": "^0.1.16",
  // CSS loader
    "css-loader": "^0.28.7",
  // es3ify解决es3环境兼容
    "es3ify-loader": "^0.2.0",
    "es3ify-webpack-plugin": "0.0.1",
  // 可将 CSS 单独打包
    "extract-text-webpack-plugin": "^3.0.0",add-module-exports
  // 可将图片载入模组
    "file-loader": "^0.11.2",
  // glup相关
    "gulp": "^3.9.1",
  // glup相关-babel转换ES6 
    "gulp-babel": "^6.1.2",
  // glup相关-可以使用类似于 node 的 require() 的方式来组织浏览器端的 Javascript 代码
    "browserify": "^14.4.0",
  // glup相关-将 ES6 转成 ES5
    "babelify": "^7.3.0",
  // glup相关-将Browserify的bundle()的输出转换为Gulp可用的vinyl（一种虚拟文件格式）流
    "vinyl-source-stream": "^1.1.0",
  // glup相关-辅助工具
    "vinyl-buffer": "^1.0.0",
  // glup相关-压缩 JavaScript
    "gulp-uglify": "^3.0.0",
  // glup相关-查看压缩后的 JS 代码所对应的行数时，source map 就能告诉你其相应代码在未压缩文件的所在行数
    "gulp-sourcemaps": "^2.6.0",
  // glup相关-压缩css文件
    "gulp-cssnano": "^2.1.2",
  // glup相关-重新命名文件
    "gulp-rename": "^1.2.2",
  // glup相关-合并文件
    "gulp-concat": "^2.6.1",
  // glup相关-产出多文件
    "glob": "^7.1.2",
  // glup相关-测试插件
    "event-stream": "^3.3.4",
  // glup相关-监听每个文件的变化
    "gulp-livereload": "^3.8.1",
  // glup相关-载入 gulp-sass
    "gulp-sass": "^3.1.0",
  // glup相关-编译scss
    "gulp-compass": "^2.1.0",
  // glup相关-避免出现错误时中断程式
    "gulp-plumber": "^1.1.0",
  // glup相关-清除并压缩 css
    "gulp-clean-css": "^3.9.0",
    "minimatch": "^3.0.4",
  // 各个loader
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
  // 压缩 js
    "uglify-es": "^3.1.0",
    "uglify-js-es6": "^2.8.9",
    "uglifyes-webpack-plugin": "^0.4.3",
    "uglifyjs-webpack-plugin": "^0.4.6",
  // webpack
    "webpack": "^3.8.1",
  // webpack 发佈仪表盘
    "webpack-dashboard": "^1.0.0-5",
  // 即时热插拔
    "webpack-dev-middleware": "^1.12.0",
    "webpack-dev-server": "^2.8.2",
    "webpack-hot-middleware": "^2.19.1"
  },
"dependencies": {
    "babel-plugin-add-module-exports": "^0.2.1",
  // Browser console polyfill. Makes it safe to do console.log().  
    "console-polyfill": "^0.3.0",
    "core-js": "^2.5.1",
    "es5-shim": "^4.5.9",
    "es6-promise": "^4.1.1",
    "fetch-ie8": "^1.5.0",
  // Tween
    "gsap": "^1.20.2",
  // JS 主要函数库
    "jquery": "^1.12.4",
  // base on jquery的网址指向功能
    "jquery-history": "^1.0.1",
  // base on jquery的 cookie 功能，
    "jquery.cookie": "^1.4.1",
  // KV 轮播
    "owl.carousel": "^2.2.0",
  // 捲动视差特效功能
    "scrollmagic": "^2.0.5"
  }
}

```

## 技术文件参考资料
---

- [完整开发档案原始档]()
