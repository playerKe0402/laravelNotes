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

