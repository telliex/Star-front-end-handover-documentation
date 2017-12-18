# 文档架构说明

## 根目錄資料夾與文檔說明

![](/assets/doc.png)

| 目錄 | 功能說明 |
| :--- | :--- |
| app | 此目錄為專案的核心目錄，專案的程式邏輯皆會放置在裡面。 |
| bootstrap | 放置框架的啟動程式碼，內含一個 cache 目錄放置由框架產生的快取以提高效能。 |
| config | 放置框架以及其他元件的設定檔案。 |
| database | 放置資料庫的資料表結構及基礎資料的目錄。 |
| node\_modules | node.js 使用的 Plugins。 |
| public ![](/images/star.png) | 專案網站的根目錄，放置靜態檔案，而其中的 index.php 則是整個應用程式的進入點。 |
| resources ![](/images/star.png) | 其中資料夾為 views、lang、assets，分別放了視圖檔案、語系檔案及預先編譯才能使用的資源檔案。 |
| routes |  |
| src ![](/images/star.png) |  |
| storage | ?? |
| tests | ?? |
| vendor | 此目錄由 Composer 建立，所有透過 Composer 安裝的元件皆放於此。 |

| 檔案 | 功能說明 |
| :--- | :--- |
| .env | 專案的環境檔案，會依照伺服器環境不同而有差異，Laravel 在執行時會將環境檔案載入，若是發生無環境檔案的錯誤可透過複製環境檔案範例重新建立此檔案。 |
| .env.example | Laravel 所提供的環境檔案範例 |
| artisan | artisan 的主程式進入點，也因此 artisan 只能在此專案目錄下操作。 |
| composer.json | Composer 檔案，描述所使用的 php 套件資訊及版本 |
| composer.lock | Composer 檔案，描述該專案所下載的 php 套件資訊及版本 |
| package.json |  |
| .babelrc |  |
| glupfile.js |  |
| webpack.config.js |  |
| webpack.dev.config.js |  |
| webpack.devserver.config.js |  |
| webpack.prod.config.js |  |

## Public 資料夾文檔說明

Public 資料夾為網站根目錄指向位置，網站內靜態檔案及所嵌入的檔案均放置於此。

> 路徑: root/public

```markdown
public
  ├ robots-develop.txt                       # 禁止搜索引擎爬蟲收錄測試機的 robots.txt 檔案
  ├ robots.txt                               # 搜索引擎爬蟲收錄正式機的 robots.txt 檔案
  ├ admfile                                  # 後台所使用的靜態檔案均放置於此
  ├ capw                                     # 後台登入驗證所使用的數字圖片
  ├ css                                      # 轉譯後的 CSS 樣式表
  │ └ vendor                                 # 轉譯後的套件樣式，所需页面再將樣式嵌入
  ├ font                                     # 自訂的 icon font 樣式
  ├ fontawesome                              # 首頁使用的 fontawesome icon font
  ├ img                                      # 網站所使用的靜態圖片
  │ ├ about                                  # 選單「關於欣和」所使用的靜態圖片
  │ ├ brandgroup                             # 選單「品牌家族」所使用的靜態圖片
  │ ├ careers                                # 選單「加入欣和」所使用的靜態圖片
  │ ├ contact                                # 選單「聯繫欣和」所使用的靜態圖片
  │ ├ error                                  # 「錯誤頁面」所使用的靜態圖片
  │ ├ icon                                   # 「全站 icon 圖示」所使用的靜態圖片
  │ └ title                                  # 「全站標題」所使用的靜態圖片
  ├ js                                       # 轉譯後的 JS 檔案
  ├ pdf                                      # 網站所使用的 PDF 檔案
  ├ favicon.ico                              # 网站或网页相关联的图标          
  ├ error-403.html
  ├ error-404.html
  ├ error-500.html
  ├ error-403.html
  ├ index.php
  ├ sitemap.xml                              # 提供給搜索引擎收錄页面的檔案                                       
  └ web.config
```

## Resources 資料夾文檔說明

> 路徑: root/resources

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

## Src 資料夾文檔說明

> 路徑: root/src

```markdown
src
├ js
├ lib
├ map
└ sass
```

.env 專案環境設置檔案  
.env.example 專案環境設置檔案範例

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



