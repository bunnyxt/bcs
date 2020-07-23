## apache2

### 安装apache2

```shell
sudo apt-get install apache2
```

### 安装php

安装最新版php

```shell
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt install php
```

安装php模块

```shell
sudo apt-get install libapache2-mod-php
sudo apt-get install php-gd php-mysql
```

ref: [ubuntu下安装配置apache2与php](https://www.cnblogs.com/yshyee/p/10444865.html)

### 配置文件

总配置文件为`/etc/apache2/apache2.conf`。与Windows版本不同，Ubuntu这里该配置文件使用`IncludeOptional`选项包含其他一系列配置文件，共同组成完整的配置文件。

按照我的习惯，所有网站放在`/var/www`下，每个子域名开一个文件夹。根据此习惯，该总配置文件需要修改`/var/www/`中的`AllowOverride All`

```
<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>
```

### 配置sites

先在`/etc/apache2/sites-avaliavle`文件夹添加`.conf`文件，再在`/etc/apache2/sites-enabled`文件夹里创建文件的软链接即可。

一个常用的HTTP配置文件模板如下，包括跳转到HTTPS链接

```shell
<VirtualHost *:80>
        ServerName tdd.bunnyxt.com

        DocumentRoot /var/www/tdd

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        RewriteEngine on
        RewriteCond   %{HTTPS} !=on
        RewriteRule   ^(.*)  https://%{SERVER_NAME}$1 [L,R]

</VirtualHost>
```

HTTPS配置文件如下。根据习惯，ssl证书放置在`/etc/httpd/ssl/<your-site-url>`文件夹里
```shell
<VirtualHost 0.0.0.0:443>
        DocumentRoot /var/www/tdd

        ServerAdmin bunnyxt@outlook.com
        ServerName tdd.bunnyxt.com:443

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLEngine on

        SSLCertificateFile      /etc/httpd/ssl/tdd.bunnyxt.com/2_tdd.bunnyxt.com.crt
        SSLCertificateKeyFile   /etc/httpd/ssl/tdd.bunnyxt.com/3_tdd.bunnyxt.com.key
        SSLCertificateChainFile /etc/httpd/ssl/tdd.bunnyxt.com/1_root_bundle.crt

</VirtualHost>
```

### 配置mods

为了实现SSL和rewrite功能，需要启用mod。可以直接使用`sudo a2enmod <mod-name>`启用mod。

```shell
sudo a2enmod ssl  # enable ssl
sudo a2enmod rewrite  # enable rewrite
sudo a2enmod proxy  # enable proxy
```

另外，也可以像配置sites一样，可以在`/etc/apache2/mods-enabled`文件夹下创建需要启用的mod的软链接。

```shell
ln -s ../mods-available/proxy_http.load .  # 开启HTTP代理/反向代理
```

### 反向代理

作用：将URL映射到本地其他端口上，例如`api.bunnyxt.com/tdd/v2/`映射到`localhost:1437`（本地Spring后端程序运行的端口）上。

首先需要开启对应的mods

```shell
ln -s ../mods-available/proxy_http.load .  # 开启HTTP代理/反向代理
```

之后在`sites-avaliable`里的`conf`文件中添加配置，例如`api.bunnyxt.com`的配置文件

```shell
ProxyRequests Off
ProxyMaxForwards 100
ProxyPreserveHost On

ProxyPass /tdd/v2/ http://127.0.0.1:1437/
ProxyPassReverse /tdd/v2/ http://127.0.0.1:1437/

ProxyPass /tdd/v3/ http://127.0.0.1:1438/
ProxyPassReverse /tdd/v3/ http://127.0.0.1:1438/

<Proxy *>
        Order Deny,Allow
        Allow from all
</Proxy>
```

### 用户与权限

apache2默认用户为`www-data`，属于`www-data`用户组。如果出现啥问题的话，可能需要修改用户。
