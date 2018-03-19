# 後端檔案架構說明


確認 mysql 之使用者須有新增/更新/寫入資料表之權限

## 環境設定

### 数据库
* 修改数据库设定 `/config/database.php` 
* 請開啟資料夾 `/public/img/` 寫入權限

数据库栏位 [DB](file/shinho_db.xlsx)

## Routing 設定
> 文档路径：/routes/web.php


#### 主控档案
```markdown
app 
├ Http
│  ├ Controllers
│  │  ├ font.php          # 前台档案
│  │  ├ ajax.php          # 前台 ajax
│  │  ├ adm.php           # 后台档案
│  │  └ admajax.php       # 后台 ajax
```

#### 主控档案运用模组
```markdown
app
 ├ Helpers
 │  ├ Helper.php          # 共用模组
 │  ├ admgroup.php        # 后台模组
 │  ├ brandgroup.php      # 品牌产品模組
 │  ├ careergroup.php     # 招聘模組
 │  └ newsgroup.php       # 新闻模组
```

#### 显示档案(view)
```markdown
resources
 ├ views
 │  ├ adm          # 后台档案
 │  ├ front        # 前台档案
 │  ├ layouts      # 框架档案
 │  └ errors       # 错误档案
 │  
```

