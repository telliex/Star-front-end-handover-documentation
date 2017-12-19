#文档架构说明

## 根目录资料夹与文档说明

![](/assets/doc.png)

| 目录 | 功能说明 |
| :--- | :--- |
| app | 此目录为专案的核心目录，专案的程式逻辑皆会放置在里面。 |
| bootstrap | 放置框架的启动程式码，内含一个 cache 目录放置由框架产生的快取以提高效能。 |
| config | 放置框架以及其他元件的设定档案。 |
| database | 放置资料库的资料表结构及基础资料的目录。 |
| node\_modules | node.js 使用的 Plugins。 |
| public ![](/images/star.png) | 专案网站的根目录，放置静态档案，而其中的 index.php 则是整个应用程式的进入点。 |
| resources ![](/images/star.png) | 其中资料夹为 views、lang、assets，分别放了视图档案、语系档案及预先编译才能使用的资源档案。 |
| routes | |
| src ![](/images/star.png) | |
| storage | ?? |
| tests | ?? |
| vendor | 此目录由 Composer 建立，所有透过 Composer 安装的元件皆放于此。 |

| 档案 | 功能说明 |
| :--- | :--- |
| .env | 专案的环境档案，会依照伺服器环境不同而有差异，Laravel 在执行时会将环境档案载入，若是发生无环境档案的错误可透过复制环境档案范例重新建立此档案。 |
| .env.example | Laravel 所提供的环境档案范例 |
| artisan | artisan 的主程式进入点，也因此 artisan 只能在此专案目录下操作。 |
| composer.json | Composer 档案，描述所使用的 php 套件资讯及版本 |
| composer.lock | Composer 档案，描述该专案所下载的 php 套件资讯及版本 |
| package.json | ? |
| .babelrc | ? |
| glupfile.js | ? |
| webpack.config.js | ? |
| webpack.dev.config.js | ? |
| webpack.devserver.config.js | ? |
| webpack.prod.config.js | ? |

## Public 资料夹文档说明

Public 资料夹为网站根目录指向位置，网站内静态档案及所嵌入的档案均放置于此。

> 路径: root/public

```markdown
public
├ robots-develop.txt # 禁止搜索引擎爬虫收录测试机的 robots.txt 档案
├ robots.txt # 搜索引擎爬虫收录正式机的 robots.txt 档案
├ admfile # 后台所使用的静态档案均放置于此
├ capw # 后台登入验证所使用的数字图片
├ css # 转译后的 CSS 样式表
│ └ vendor # 转译后的套件样式，所需页面再将样式嵌入
├ font # 自订的 icon font 样式
├ fontawesome # 首页使用的 fontawesome icon font
├ img # 网站所使用的静态图片
│ ├ about # 选单“关于欣和”所使用的静态图片
│ ├ brandgroup # 选单“品牌家族”所使用的静态图片
│ ├ careers # 选单“加入欣和”所使用的静态图片
│ ├ contact # 选单“联系欣和”所使用的静态图片
│ ├ error # “错误页面”所使用的静态图片
│ ├ icon # “全站 icon 图示”所使用的静态图片
│ └ title # “全站标题”所使用的静态图片
├ js # 转译后的 JS 档案
├ pdf # 网站所使用的 PDF 档案
├ favicon.ico # 网站或网页相关联的图标
├ error-403.html # 403 错误页面
├ error-404.html # 404 错误页面
├ error-500.html # 500 错误页面
├ error-503.html # 503 错误页面
├ index.php # Laravel 应用程式的进入点，非普遍定义的首页
├ sitemap.xml # 提供给搜索引擎收录页面的档案
└ web.config # 设定 Laravel rewrite rule
```

## Resources 资料夹文档说明

> 路径: root/resources

```markdown
resources
├ assets
├ lang
└ views
├ adm
├ errors
├ front
├ layouts
├ vendor
└ welcome.blade.php
```

## Src 资料夹文档说明

> 路径: root/src

```markdown
src
├ js
├ lib
├ map
└ sass
```

.env 专案环境设置档案
.env.example 专案环境设置档案范例

package.json

#### babel

* .babelrc

#### glup

* glupfile.js

#### webpack

* webpack.config.js
* webpack.dev.config.js
* webpack.devserver.config.js
* webpack.prod.config.js


