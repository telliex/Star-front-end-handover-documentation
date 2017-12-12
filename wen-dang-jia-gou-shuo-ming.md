# 文檔架構說明

Laravel 的目錄結構

## 文檔目錄架構

### 根目錄資料夾與文檔說明

| 目錄及檔案 | 功能說明 |
| :--- | :--- |
| app | 此目錄為專案的核心目錄，專案的程式邏輯皆會放置在裡面。 |
| bootstrap | 放置框架的啟動程式碼，內含一個 cache 目錄放置由框架產生的快取以提高效能。 |
| config | 放置框架以及其他元件的設定檔案。 |
| database | 放置資料庫的資料表結構及基礎資料的目錄。 |
| public ![](/images/star.png) | 專案網站的根目錄，放置靜態檔案，而其中的 index.php 則是整個應用程式的進入點。 |
| resources ![](/images/star.png) | 其中資料夾為 views、lang、assets，分別放了視圖檔案、語系檔案及預先編譯才能使用的資源檔案。 |
| vendor | 此目錄由 Composer 建立，所有透過 Composer 安裝的元件皆放於此。 |

|  |  |
| :--- | :--- |
| .env | 專案的環境檔案，會依照伺服器環境不同而有差異，Laravel 在執行時會將環境檔案載入，若是發生無環境檔案的錯誤可透過複製環境檔案範例重新建立此檔案。 |
| .env.example | Laravel 所提供的環境檔案範例 |
| artisan | artisan 的主程式進入點，也因此 artisan 只能在此專案目錄下操作。 |
| composer.json | Composer 檔案，描述所使用的 php 套件資訊及版本 |
| composer.lock | Composer 檔案，描述該專案所下載的 php 套件資訊及版本 |

## 

## Public 資料夾文檔說明

網站根目錄指向此目錄內

## Resources 資料夾文檔說明

## Src 資料夾文檔說明

.env 專案環境設置檔案  
.env.example 專案環境設置檔案範例\`\`\`\`

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



