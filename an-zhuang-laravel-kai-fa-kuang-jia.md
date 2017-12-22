# Laravel 开发环境参数设置

Laravel 是一套富有表达性且具有简洁语法的网页应用程式框架，减少开发过程中的不便，提供了验证(authentication)、路由(routing)、sessions、快取(caching) 等开发过程中经常用到的工具或功能。

主机若未安装 laravel 可运行的环境，请依下面步骤安装：

## Laravel 开发环境安装
---

### Step0.CentOS 更新

> \# commandline
> yum -y update

### Step1.安裝 Centos 擴充資源庫

> \# commandline
> yum -y install epel-release
> yum -y update
> yum clean all
    
### Step2.安裝 Mariadb 數據庫

> yum -y install httpd mariadb-server mariadb 
    
### Step3.安裝 PHP

> yum -y install php56w php56w-mysql php56w-mcrypt php56w-dom php56w-mbstring
    
### Step4.啟動服務器

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
  
### Step5.安裝 Composer - Laravel 框架使用 Composer 來管理其相依性

> \# commandline
> curl -sS https://getcomposer.org/installer | php
> mv composer.phar /usr/bin/composer
> chmod +x /usr/bin/composer

### Step6.安裝 git 並取回 Laravel 框架

> \# commandline
> yum -y install git
> cd /var/www/
> git clone https://github.com/laravel/laravel.git

### Step7.安裝 Laravel 相關套件

> \# commandline
> cd /var/www/laravel
> composer install 

## 设定环境
---

### Step1. 调整资料夹权限

> \# commandline
> chown -R apache:apache /var/www/laravel
> chmod -R 755 /var/www/laravel

### Step2.设定 Laravel 环境变数

> \# commandline
> cd /var/www/laravel
> mv .env.example .env


### Step3.修改 httpd.conf

> 文档路径：/etc/httpd/conf/httpd.conf

```
ServerName test.myproject.com
DocumentRoot /var/www/laravel/publicAllowOverride All
```

### Step4.重启服务器

> \# commandline
> systemctl restart httpd

## 技术文件参考资料
---

- [Laravel 中文文檔](https://docs.golaravel.com/docs/5.0/installation/)
- [How to Install the PHP Laravel Framework on CentOS 7](https://hostpresto.com/community/tutorials/how-to-install-the-php-laravel-framework-on-centos-7/)




