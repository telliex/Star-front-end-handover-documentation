# Javascript 代码文档架构

## JS 资料夹
---
> 文档路径: `/src/js`  
> 转译后路径: `/pubic/js`

```markdown
js                                        
├ base.js                                   # 侦测各种状态的 JS 代码
├ browser.js                                # 判断浏览器类型的 JS 代码
├ generic.js                                # 站内组件的 JS 代码
├ maxin.js                                  # 模组的 JS 代码
├ partical.js                               # 元件的 JS 代码
├ global.es6                                # 全站共同版型的 JS 代码，每个页面都有使用
├ ie-debug.es6                              # 适配 IE 的修正代码
├ lyt-about-business.es6                    #「关于欣和我们正在做」business.blade.php 的 ES6 代码
├ lyt-about-crafts.es6                      #「关于欣和生产工艺」crafts.blade.php 的 ES6 代码
├ lyt-about-csv.es6                         #「关于欣和社会责任」csv.blade.php 的 ES6 代码
├ lyt-about-focus.es6                       #「关于欣和欣和关注」focus.blade.php 的 ES6 代码
├ lyt-about-history.es6                     #「关于欣和欣和历史」history.blade.php 的 ES6 代码
├ lyt-about.es6                             #「关于欣和首页」about.blade.php 的 ES6 代码
├ lyt-brand-attitude.es6                    #「品牌饮食态度」attitude.blade.php 的 ES6 代码
├ lyt-brand-group.es6                       #「品牌家族」brandgroup.blade.php 的 ES6 代码
├ lyt-brand-index.es6                       #「品牌首页」brand.blade.php 的 ES6 代码
├ lyt-brand-news-list.es6                   #「品牌动态列表」brandnewslist.blade.php 的 ES6 代码
├ lyt-brand-prod-detail.es6                 #「品牌产品详情」proddetail.blade.php 的 ES6 代码
├ lyt-brand-prod-list.es6                   #「品牌产品列表」prodlist.blade.php 的 ES6 代码
├ lyt-brand-recipe-detail.es6               #「品牌菜谱详情」recipedetail.blade.php 的 ES6 代码
├ lyt-brand-recipe-list.es6                 #「品牌菜谱列表」recipelist.blade.php 的 ES6 代码
├ lyt-brand-topic.es6                       #「品牌主题」topic.blade.php 的 ES6 代码
├ lyt-careers-camp-recruiting-list.es6      #「加入欣和校园招聘模版」campusitinerary.blade.php、campusprocess.blade.php、campusrecruiting.blade.php 的 ES6 代码
├ lyt-careers-recruiting-detail.es6         #「加入欣和招聘详情」recruitingdetail.blade.php、campusrecruitingdetail.blade.php 的 ES6 代码
├ lyt-careers-recruiting-list.es6           #「加入欣和招聘列表」campusrecruiting.blade.php、recruiting.blade.php 的 ES6 代码
├ lyt-careers.es6                           #「加入欣和首页」careers.blade.php 的 ES6 代码
├ lyt-news-detail.es6                       #「欣和动态详情」newsdetail.blade.php 的 ES6 代码
├ lyt-news-list.es6                         #「欣和动态列表」newslist.blade.php 的 ES6 代码
└ share.es6                                 # Ajax 动态资料串接档案
```
### 相关连结与文档
* 若需新增或运维交互动效请参考：[1.5.2 新增与运维 - JavaScript](/xin-zeng-yu-wei-yun-f/javascript.md)

<br/>
## Lib 资料夹
---
> 文档路径: `/src/lib`

```markdown
lib
├ owlcarousel                               # JavaScript 轮拨套件
├ slick                                     # JavaScript 轮拨套件
├ animation.gsap.min.js                     # JavaScript 动画库，與 ScrollMagic 一起使用
├ debug.addIndicators.min.js                # ScrollMagic Debug 套件
├ jquery.cookie.js                          # cookie 读取、写入、删除插件
├ jquery.history.js                         # JavaScript 新增浏览记录套件
├ jquery.js                                 # JavaScript 框架
├ jquery.mobile.min.js                      # JavaScript 框架 for Mobile                        # 
├ ScrollMagic.min.js                        # JS 动画库，與 ScrollMagic 一起使用
└ TweenMax.min.js                           # JS 动画库，與 ScrollMagic 一起使用
```
### 相关连结与文档

* 若新增 JavaScript 套件至该页面请参考：[1.5.2 新增与运维 - JavaScript](/maintain/maintain-js.md)
* 若新增 JavaScript 套件至 Webpack 请参考：[1.5.4 新增与运维 - Webpack:新增网页引用 JS Module](/maintain/maintain-webpack.md)





