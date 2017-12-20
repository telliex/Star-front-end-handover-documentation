# Laravel 开发环境参数设置

Laravel 是一套富有表达性且具有简洁语法的网页应用程式框架，减少开发过程中的不便，提供了验证(authentication)、路由(routing)、sessions、快取(caching) 等开发过程中经常用到的工具或功能。

主机若未安装 laravel 可运行的环境，请依下面步骤安装：

## CentOS 更新

> \# commandline
> yum -y update

## 安裝 Centos 擴充資源庫

> \# commandline
> yum -y install epel-release
> yum -y update
> yum clean all
    
## 安裝 Mariadb 數據庫

> yum -y install httpd mariadb-server mariadb 
    
## 安裝 PHP

> yum -y install php56w php56w-mysql php56w-mcrypt php56w-dom php56w-mbstring
    
## 啟動服務器

> \# commandline
> // 啟動 Apache   
> systemctl start httpd
>   
> // 將 Apache 設為常駐
> systemctl enable httpd
>    
> // 啟動 數據庫
> systemctl start mariadb
>    
> // 將 mariadb 設為常駐
> systemctl enable mariadb
  
## 安裝 Composer - Laravel 框架使用 Composer 來管理其相依性

> \# commandline
> curl -sS https://getcomposer.org/installer | php
> mv composer.phar /usr/bin/composer
> chmod +x /usr/bin/composer

## 安裝 git 並取回 Laravel 框架

> \# commandline
> yum -y install git
> cd /var/www/
> git clone https://github.com/laravel/laravel.git

## 安裝 Laravel 相關套件

> \# commandline
> cd /var/www/laravel
> composer install 

## 設定環境
### 調整資料夾權限

> \# commandline
> chown -R apache:apache /var/www/laravel
> chmod -R 755 /var/www/laravel

### 設定 Laravel 環境變數

> \# commandline
> cd /var/www/laravel
> mv .env.example .env

### .env 設定

```
APP_ENV=local
APP_KEY=base64:PllGKlCqZSwTJKGyGacEN8FEJeEt0Jlyx1n8xMea3Iw=
APP_DEBUG=true
APP_LOG_LEVEL=debug
APP_URL=http://localhostDB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=homestead
DB_USERNAME=homestead
DB_PASSWORD=secretBROADCAST_DRIVER=log
CACHE_DRIVER=file
SESSION_DRIVER=file
QUEUE_DRIVER=syncREDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379MAIL_DRIVER=smtp
MAIL_HOST=mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
PUSHER_APP_ID= PUSHER_KEY= PUSHER_SECRET=
```

## 修改 /etc/httpd/conf/httpd.conf

```
ServerName test.myproject.com
DocumentRoot /var/www/laravel/publicAllowOverride All
```

重啟服務器

> \# commandline
> systemctl restart httpd

## 技術參考文檔

- [Laravel 中文文檔](https://docs.golaravel.com/docs/5.0/installation/)
- [How to Install the PHP Laravel Framework on CentOS 7](https://hostpresto.com/community/tutorials/how-to-install-the-php-laravel-framework-on-centos-7/)




