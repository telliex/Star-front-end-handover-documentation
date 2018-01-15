# 本机 Gulp 开发环境参数设置

Gulp.js 是一个自动化构建工具，开发者可以使用它在项目开发过程中自动执行常见任务。
这里使用 Gulp.js 来协助 SCSS 编译成 CSS 所需的实时自动化编译。

## Gulp 快速入門
---

如已全局安装过 Gulp `npm install gulp -g`，执行下面步骤前，请先运行  `npm rm -g gulp`（移除全局 Gulp 模块）。

1. 安裝 Gulp command
> \# commandline
> npm install -g gulp-cli
2. 全局安装 Gulp
> \# commandline
> $ npm install -g gulp
3. 作为项目的开发依赖（devDependencies）
> \# commandline
> $ npm install --save-dev gulp
4. 根目录下创建一个名为 gulpfile.js 的文件。
```
gulp.task('default', function() {  // 'default' 默认任务名，运行命令时可省略，直接 `gulp` 即可，运行其他任务需要 `gulp taskname`
    // place code for your default task here
});
```
5. 运行 Gulp
> \# commandline
> gulp

## SASS 环境设定
---
为在 Gulp 内可进行 SASS 编译，需先安装: 

### Step1.使用 Homebrew 安裝 Ruby

> \# commandline
> brew install ruby

### Step2.安裝 sass

> \# commandline
> gem install sass

### Step3.安裝 compass

> \# commandline
> gem install compass

### Step4.安裝 susy

> \# commandline
> gem install susy

### Step5.安裝 modular-scale

> \# commandline
> gem install modular-scale


## 使用 Gulp 進行 SCSS 的編譯工作
---

可实时监控 SCSS 档案，若档案有异动修改时即可编译出 CSS 档。
> \# commandline
> gulp watch

### Gulp Setting

> 文档路径：`/gulpfile.js`

```
//gulpfile.js

var gulp = require('gulp');
var babel = require('gulp-babel');
var browserify = require('browserify');   //使用类似于 node 的 require() 的方式来组织浏览器端的 Javascript 代码
var babelify = require('babelify');   //將 ES6 转成 ES5
var source = require('vinyl-source-stream');   //将Browserify的bundle()的输出转换为Gulp可用的vinyl（一种虚拟文件格式）流
var buffer = require('vinyl-buffer');   //gulp-uglify 现在不支持 stream，而支持 buffer。vinyl-buffer 能将 stream 转为 buffer，让 gulp-uglify 能正常运行。
var uglify = require('gulp-uglify');   //压缩 JavaScript
var sourcemaps = require('gulp-sourcemaps'); //查看压缩后的 JS 代码所对应的行数时，source map 就能告诉你其相应代码在未压缩文件的所在行数
var cssnano = require('gulp-cssnano');   //压缩css文件
var rename = require('gulp-rename');   //重命名文件
var concat = require('gulp-concat');   //合并文件
var glob = require('glob');   //產出多文件
var es = require('event-stream');   //測試插件
var path = require('path');

//scss 编译相关
var gulpCompass = require('gulp-compass');   //編譯 CSS
var plumber = require('gulp-plumber');   // 避免出现错误时中断程式
var cleanCSS = require('gulp-clean-css');   //清除并压缩 css


gulp.task('watch', function() {
    gulp.watch('src/sass/*.scss', ['styles']);
});


gulp.task('styles', function() {
    gulp.src('./src/sass/*.*/*.scss')   // sass 來源路徑
        .pipe(plumber({
            errorHandler: function(error) {
                console.log(error.message);
                this.emit('end');
            }
        }))
        .pipe(gulpCompass({
            project: __dirname,
            css: './public/css',   // compass 輸出位置
            sass: 'src/sass/',   // sass 來源路徑
            image: 'public/img',   // 圖片來源路徑
            style: 'compressed',   // CSS 處理方式，預設 nested（expanded, nested, compact, compressed）
            comments: false,   // 是否要註解，預設(true)
            require: ['susy', 'breakpoint'],   // 額外套件 susy
        }))
        .on('error', function(error) {
            // Would like to catch the error here 
        })
        .pipe(cleanCSS())
        .pipe(gulp.dest('./public/css'));   // 輸出位置(非必要)
});

```

## 技术文件参考资料
---

- [Gulp 中文網](https://www.gulpjs.com.cn/docs/getting-started/)