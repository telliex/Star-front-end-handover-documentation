# 文档架构说明

整包程式码采针对 Laravel 框架再加入一些方便开发发布的结构。主要结构说明如下：
<br/>


## 根目录资料夹与文档说明
---

![](/assets/doc.png)
<br/>

| 目录 | 功能说明 |
| :- | :--- |
| app | 此目录为专案的核心目录，专案的程式逻辑皆会放置在里面。 |
| bootstrap | 放置框架的启动程式码，内含一个 cache 目录放置由框架产生的快取以提高效能。 |
| config | 放置框架以及其他元件的设定档案。 |
| database | 放置资料库的资料表结构及基础资料的目录。 |
| node\_modules | node.js 使用的 Plugins。 |
| public ![](/images/star.png) | 专案网站的根目录，放置静态档案，而其中的 index.php 则是整个应用程式的进入点。 |
| resources ![](/images/star.png) | 其中资料夹为 views、lang、assets，分别放了视图档案、语系档案及预先编译才能使用的资源档案。 |
| routes | Routes 设定档案。 |
| src ![](/images/star.png) | SCSS、ES6 预先编译才能使用的资源档案。 |
| storage | 目录包含编译后的 Blade 模板、基于文件的 session、文件缓存和其它框架生成的文件。 |
| tests | 目录包含自动化测试。 |
| vendor | 此目录由 Composer 建立，所有透过 Composer 安装的元件皆放于此。 |

| 档案 | 功能说明 |
| :- | :--- |
| .env | 专案的环境档案，会依照伺服器环境不同而有差异，Laravel 在执行时会将环境档案载入，若是发生无环境档案的错误可透过复制环境档案范例重新建立此档案。 |
| .env.example | Laravel 所提供的环境档案范例。 |
| artisan | artisan 的主程式进入点，也因此 artisan 只能在此专案目录下操作。 |
| composer.json | Composer 档案，描述所使用的 php 套件资讯及版本。 |
| composer.lock | Composer 档案，描述该专案所下载的 php 套件资讯及版本。 |
| package.json | npm install 设置档 |
| .babelrc | Babel 编译时使用的模组设定 |
| glupfile.js | Glup 自动化设定档 |
| webpack.config.js | Webpack 设定档 |
| webpack.dev.config.js | Webpack 开发设定档 |
| webpack.devserver.config.js | Webpack 开发时加入 devserver 设定档 |
| webpack.prod.config.js | Webpack 上线前发布设定档 |

<br/>


## app 资料夹文档说明
---

app 资料夹下的 `/Helpers` 与 `Http/Controllers`,放置。

> 文档路径: `app/Helpers`
> 文档路径: `app/Http/Controllers`


```markdown
app
├ Helpers                                 # 数据处理相关
│ ├ admgroup.php                          # 后台资料数据处理
│ ├ brandgroup_en.php                     # 英文版 品牌内页相关数据处理
│ ├ brandgroup.php                        # 中文版 品牌内页相关数据处理
│ ├ careergroup_en.php                    # 英文版 招聘内页相关数据处理
│ ├ careergroup.php                       # 中文版 招聘内页相关数据处理
│ ├ Helper_en.php                         # 英文版 不分类内页功能处理
│ ├ Helper.php                            # 中文版 不分类内页功能处理
│ ├ newsgroup_en.php                      # 英文版 欣和动态＆品牌动态内页数据处理
│ └ newsgroup.php                         # 中文版 欣和动态＆品牌动态内页数据处理
└ Http                            
  └ Controllers                           # 页面 router 后，对应处理动作 
    ├ adm.php                             # 后台页面 controller
    ├ admajax.php                         # 后台页面 ajax 呼叫
    ├ ajax_en.php                         # 英文版 ajax 呼叫 
    ├ ajax.php                            # 中文版 ajax 呼叫 
    ├ Controller.php                      # 系统预设页面
    ├ front_en.php                        # 英文版页面 controller
    ├ front.php                           # 中文版页面 controller
    ├ HelloWorldController.php            # 系统预设 HelloWorld 页面
    └ LocaleController.php                # 设置语系切换命名空间

```
<br/>


## Public 资料夹文档说明
---

Public 资料夹为网站根目录指向位置，网站内静态档案及所嵌入的档案均放置于此。

> 文档路径: `/public`

```markdown
public
├ robots-develop.txt                    # 禁止搜索引擎爬虫收录测试机的 robots.txt 档案
├ robots.txt                            # 搜索引擎爬虫收录正式机的 robots.txt 档案
├ admfile                               # 后台所使用的静态档案均放置于此
├ capw                                  # 后台登入验证所使用的数字图片
├ css                                   # 转译后的 CSS 样式表
│ └ vendor                              # 转译后的套件样式，所需页面再将样式嵌入
├ font                                  # 自订的 icon font 样式
├ fontawesome                           # 首页使用的 fontawesome icon font
├ img                                   # 网站所使用的静态图片
│ ├ about                               # 选单「关于欣和」所使用的静态图片
│ ├ brandgroup                          # 选单「品牌家族」所使用的静态图片
│ ├ careers                             # 选单「加入欣和」所使用的静态图片
│ ├ contact                             # 选单「联系欣和」所使用的静态图片
│ ├ error                               # 「错误页面」所使用的静态图片
│ ├ icon                                # 「全站 icon 图示」所使用的静态图片
│ └ title                               # 「全站标题」所使用的静态图片
├ js                                    # 转译后的 JS 档案
├ pdf                                   # 网站所使用的 PDF 档案
├ favicon.ico                           # 网站或网页相关联的图标
├ index.php                             # Laravel 应用程式的进入点，非普遍定义的首页
├ sitemap.xml                           # 提供给搜索引擎收录页面的档案
└ web.config                            # 设定 Laravel rewrite rule

```
<br/>
## Resources 资料夹文档说明
---

Resources 资料夹内为 `views`、`lang`、`assets`，分别放了视图档案、语系档案及预先转译才能使用的资源档案。目前仅使用 views 资料夹存放 Laravel Blade 样板引擎，前台页面都存放在此。

> 文档路径: `/resources`

```markdown
resources
├ assets                                # Laravel 框架：预先转译才能使用的资源档案，目前不使用
├ lang                                  # Laravel 框架：语系档案，放置多语系内容
│  ├ en                                 # Laravel 框架：语系档案，英文语系内容
│  └ zh_cn                              # Laravel 框架：语系档案，中文语系内容
└ views                                 # Laravel 框架：视图档案，存放 Laravel Blade 样板引擎，前台页面都存放在此

```
* 若需新增或运维网站内容请参考：[1.5.3 新增与运维 - PHP](/maintain/maintain-php.md) 


<br/>
## Resources 资料夹文档说明
---

Resources 资料夹内为 `views`、`lang`、`assets`，分别放了视图档案、语系档案及预先转译才能使用的资源档案。目前仅使用 views 资料夹存放 Laravel Blade 样板引擎，前台页面都存放在此。

> 文档路径: `/resources`

```markdown
resources
├ assets                                # Laravel 框架：预先转译才能使用的资源档案，目前不使用
├ lang                                  # Laravel 框架：语系档案，放置多语系内容
│  ├ en                                 # Laravel 框架：语系档案，英文语系内容
│  └ zh_cn                              # Laravel 框架：语系档案，中文语系内容
└ views                                 # Laravel 框架：视图档案，存放 Laravel Blade 样板引擎，前台页面都存放在此

```
* 若需新增或运维网站内容请参考：[1.5.3 新增与运维 - PHP](/maintain/maintain-php.md) 


<br/>

## routes 资料夹文档说明
---

routes 资料夹为 laravel router 设定

> 文档路径: `/routes`

```markdown
routes
├ api.php                                   # app 路由，应用 api 中间件组
├ console.php                               
└ web.php                                   # 网页路由，应用 web 中间件组

```

说明：
- `routes/web.php` 中英文版的 router 皆会在此设定。

## 延伸参考
---

* 若需新增或运维样式请参考：[1.5.1 新增与运维 - CSS](/maintain/maintain-css.md)
* 若需新增或运维交互动效请参考：[1.5.2 新增与运维 - JavaScript](/maintain/maintain-js.md)