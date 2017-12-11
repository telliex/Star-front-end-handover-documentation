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




## 參考
[gulp 中文網](https://www.gulpjs.com.cn/docs/getting-started/)