# Gulp 使用

## 快速入門

1. 安裝 gulp command
> npm install -g gulp-cli
2. 全局安装 gulp：
> $ npm install -g gulp
3. 作为项目的开发依赖（devDependencies）
> $ npm install --save-dev gulp

4. 根目录下创建一个名为 gulpfile.js 的文件
```
var gulp = require('gulp');
gulp.task('default', function() {
  // 将你的默认的任务代码放在这
});
```
5. 运行 gulp：
> $ gulp



## 參考
[gulp 中文網](https://www.gulpjs.com.cn/docs/getting-started/)