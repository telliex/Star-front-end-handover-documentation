# 後端檔案架構說明


確認 mysql 之使用者須有新增/更新/寫入資料表之權限

## 環境設定

### 数据库
* 修改数据库设定 `/config/database.php` 
* 請開啟資料夾 `/public/img/` 寫入權限

数据库栏位 [DB](file/shinho_db.xlsx)


## Routing 設定
> 文档路径：/routes/web.php


主控檔案

```markdown
app
/Http/Controllers/
├ font.php                                  # 前台檔案
├ ajax.php                                  # 前台ajax
├ adm.php                                   # 後台檔案
└ admajax.php                               # 後台ajax
```



/app/Http/Controllers/

-前台檔案 font.php

-前台ajax ajax.php

-後台檔案 adm.php

-後台ajax admajax.php



主控檔運用模組

/app/Helpers/

-共用模組 Helper.php

-後台模組 admgroup.php

-品牌產品模組 brandgroup.php

-招聘模組 careergroup.php

-新聞模組 newsgroup.php



顯示檔案(view)

/resources/views

-後台檔案  /adm

-前台檔案 /front

-框架檔案 /layouts

-錯誤檔案 /errors

