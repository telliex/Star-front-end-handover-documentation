# 文档架构说明

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
| storage | ?? |
| tests | ?? |
| vendor | 此目录由 Composer 建立，所有透过 Composer 安装的元件皆放于此。 |

| 档案 | 功能说明 |
| :- | :--- |
| .env | 专案的环境档案，会依照伺服器环境不同而有差异，Laravel 在执行时会将环境档案载入，若是发生无环境档案的错误可透过复制环境档案范例重新建立此档案。 |
| .env.example | Laravel 所提供的环境档案范例。 |
| artisan | artisan 的主程式进入点，也因此 artisan 只能在此专案目录下操作。 |
| composer.json | Composer 档案，描述所使用的 php 套件资讯及版本。 |
| composer.lock | Composer 档案，描述该专案所下载的 php 套件资讯及版本。 |
| package.json | ? |
| .babelrc | Babel? |
| glupfile.js | Glup? |
| webpack.config.js | Webpack? |
| webpack.dev.config.js | Webpack? |
| webpack.devserver.config.js | Webpack? |
| webpack.prod.config.js | Webpack? |

<br/>
## Public 资料夹文档说明
---
Public 资料夹为网站根目录指向位置，网站内静态档案及所嵌入的档案均放置于此。

> 文档路径: `/public`

```markdown
public
├ robots-develop.txt                        # 禁止搜索引擎爬虫收录测试机的 robots.txt 档案
├ robots.txt                                # 搜索引擎爬虫收录正式机的 robots.txt 档案
├ admfile                                   # 后台所使用的静态档案均放置于此
├ capw                                      # 后台登入验证所使用的数字图片
├ css                                       # 转译后的 CSS 样式表
│ └ vendor                                  # 转译后的套件样式，所需页面再将样式嵌入
├ font                                      # 自订的 icon font 样式
├ fontawesome                               # 首页使用的 fontawesome icon font
├ img                                       # 网站所使用的静态图片
│ ├ about                                   # 选单「关于欣和」所使用的静态图片
│ ├ brandgroup                              # 选单「品牌家族」所使用的静态图片
│ ├ careers                                 # 选单「加入欣和」所使用的静态图片
│ ├ contact                                 # 选单「联系欣和」所使用的静态图片
│ ├ error                                   # 「错误页面」所使用的静态图片
│ ├ icon                                    # 「全站 icon 图示」所使用的静态图片
│ └ title                                   # 「全站标题」所使用的静态图片
├ js                                        # 转译后的 JS 档案
├ pdf                                       # 网站所使用的 PDF 档案
├ favicon.ico                               # 网站或网页相关联的图标
├ error-403.html                            # 403 错误页面
├ error-404.html                            # 404 错误页面
├ error-500.html                            # 500 错误页面
├ error-503.html                            # 503 错误页面
├ index.php                                 # Laravel 应用程式的进入点，非普遍定义的首页
├ sitemap.xml                               # 提供给搜索引擎收录页面的档案
└ web.config                                # 设定 Laravel rewrite rule
```
<br/>
## Resources 资料夹文档说明
---
Resources 资料夹内为 `views`、`lang`、`assets`，分别放了视图档案、语系档案及预先转译才能使用的资源档案。目前仅使用 views 资料夹存放 Laravel Blade 样板引擎，前台页面都存放在此。

> 文档路径: `/resources`

```markdown
resources
├ assets                                    # Laravel 框架：预先转译才能使用的资源档案，目前不使用
├ lang                                      # Laravel 框架：语系档案，目前尚未使用到此功能
└ views                                     # Laravel 框架：视图档案，存放 Laravel Blade 样板引擎，前台页面都存放在此
```
* 若需新增或运维网站内容请参考：[1.5.3 新增与运维 - PHP](/xin-zeng-yu-wei-yun-f/php.md) 


<br/>
## Src 资料夹文档说明
---
Src 资料夹存放预先转译才能使用的资源档案，例如：SCSS、ES6。无论样式或交互动效，转译前档案都在此。

> 文档路径: `/src`

```markdown
src
├ js                                        # JavaScript(ES6) 档案
├ lib                                       # JavaScript 套件档案
├ map                                       # JavaScript 转换代码前后位置的信息文件
└ sass                                      # CSS(SCSS) 档案
```
* 若需新增或运维样式请参考：[1.5.1 新增与运维 - CSS](/xin-zeng-yu-wei-yun-f/css.md)
* 若需新增或运维交互动效请参考：[1.5.2 新增与运维 - JavaScript](/xin-zeng-yu-wei-yun-f/javascript.md)