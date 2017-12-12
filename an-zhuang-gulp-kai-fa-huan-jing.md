# Gulp 使用

## 快速入門

如已全局安装过 gulp （npm install gulp -g），在执行下面步骤前先运行  npm rm -g gulp（移除全局 gulp 模块）。

1. 安裝 gulp command
> npm install -g gulp-cli
2. 全局安装 gulp：
> $ npm install -g gulp
3. 作为项目的开发依赖（devDependencies）
> $ npm install --save-dev gulp
4. 根目录下创建一个名为 gulpfile.js 的文件
```
gulp.task('default', function() {  // 'default' 默认任务名，运行命令时可省略，直接 `gulp` 即可，运行其他任务需要 `gulp taskname`
    // place code for your default task here
});
```
5. 运行 gulp：
> $ gulp


## Star gulp
```
var gulp = require('gulp');
var babel = require('gulp-babel');
var browserify = require('browserify'); //使用类似于 node 的 require() 的方式来组织浏览器端的 Javascript 代码
var babelify = require('babelify'); //將 ES6 转成 ES5
var source = require('vinyl-source-stream'); //将Browserify的bundle()的输出转换为Gulp可用的vinyl（一种虚拟文件格式）流
var buffer = require('vinyl-buffer'); //gulp-uglify 现在不支持 stream，而支持 buffer。vinyl-buffer 能将 stream 转为 buffer，让 gulp-uglify 能正常运行。
var uglify = require('gulp-uglify'); //压缩 JavaScript
var sourcemaps = require('gulp-sourcemaps'); //查看压缩后的 JS 代码所对应的行数时，source map 就能告诉你其相应代码在未压缩文件的所在行数
var cssnano = require('gulp-cssnano'); //压缩css文件
var rename = require('gulp-rename'); //重命名文件
var concat = require('gulp-concat'); //合并文件
var glob = require('glob'); //產出多文件
var es = require('event-stream'); //測試插件
var livereload = require('gulp-livreload'); //监听每个文件的变化
var path = require('path');

//scss 编译相关
var gulpSass = require('gulp-sass'); // 載入 gulp-sass
var gulpCompass = require('gulp-compass'); //編譯 CSS
var plumber = require('gulp-plumber'); // 避免出现错误时中断程式
var cleanCSS = require('gulp-clean-css'); //清除并压缩 css


gulp.task('watch', function() {
    gulp.watch('src/sass/*.scss', ['styles']);
});


gulp.task('styles', function() {
    gulp.src('./src/sass/*.*/*.scss') // sass 來源路徑
        .pipe(plumber({
            errorHandler: function(error) {
                console.log(error.message);
                this.emit('end');
            }
        }))
        .pipe(gulpCompass({
            project: __dirname,
            css: './public/css', // compass 輸出位置
            sass: 'src/sass/', // sass 來源路徑
            image: 'public/img', // 圖片來源路徑
            style: 'compressed', // CSS 處理方式，預設 nested（expanded, nested, compact, compressed）
            comments: false, // 是否要註解，預設(true)
            require: ['susy', 'breakpoint'], // 額外套件 susy
        }))
        .on('error', function(error) {
            // Would like to catch the error here 
        })
        .pipe(cleanCSS())
        .pipe(gulp.dest('./public/css')); // 輸出位置(非必要)
});

```

## 技術參考文檔
[gulp 中文網](https://www.gulpjs.com.cn/docs/getting-started/)