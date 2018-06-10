# Linux Ubuntu16.04(Laravel + PHP + Apache)
## 安裝 Apache
Step 1. 更新套件檔案清單
```
apt-get update
```
Step 2. 安裝 Apache
```
apt-get install apache2
```
Step 3. 啟動 Apache
```
/etc/init.d/apache2 start
```

## 安裝 PHP
Step 1. 安裝Python Software Package
- PHP 7.1不是由官方提供，因此須添加"PPA"以便輕鬆安裝
```
apt-get install python-software-properties
add-apt-repository ppa:ondrej/php
```
Step 2. 更新套件檔案清單
```
apt-get update
```
Step 3. 安裝PHP擴展元件
```
apt-get install php7.1 php7.1-xml php7.1-mbstring php7.1-mysql php7.1-json php7.1-curl php7.1-cli php7.1-common php7.1-mcrypt php7.1-gd libapache2-mod-php7.1 php7.1-zip
```

## 安裝 Composer
使用curl 指令下載 composer.phar 並移至 /usr/local/bin/ 目錄下(改名為composer)
```
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
chmod +x /usr/local/bin/composer
```

## 安裝 Laravel
移至網頁目錄並給予 html 目錄權限後安裝 laravel 專案
```
cd /var/www/
chmod -R 777 html/
cd html/
composer create-project laravel/laravel MyProject --prefer-dist
chmod -R 777 /var/www/html/MyProject/
```

## 常見問題 
- Routes 除了/之外其他 Page 顯示 Not Found

將 /etc/init.d/apache2/apache2.conf 文件中的 AllowOverride None 改為 AllowOverride Al
```
<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride All
	Require all granted
</Directory>
```

- Routes 使用 post(put、delete) 頁面顯示 The page has expired due to inactivity. Please refresh and try again.

Laravel 提供簡單防護方法防止跨網站請求偽造（CSRF）攻擊

Laravel 會自動產生一個 CSRF token，在網頁裡 form 應該包含一個隱藏的 CSRF token 欄位進行 CSRF 請求驗證

一般 PHP
```
<?php echo csrf_field(); ?>
```
Blade 模板語法
```
{{ csrf_field() }}
```
meta 標籤
```
<meta name="csrf-token" content="{{ csrf_token() }}"/>
```
## Reference
[網址移除P](http://blog.tonycube.com/2015/01/laravel-23-public.html)
