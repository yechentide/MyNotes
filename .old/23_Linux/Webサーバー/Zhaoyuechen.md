# Apache2＋SSL構築メモ

## シェル環境

* zshをインストール
* プラグインを導入

## Wordpress

```shell
# timedatectl set-timezone Asia/Tokyo

# apt update
# apt -y update

# apt -y install apache2
# systemctl enable apache2
# systemctl start apache2

# apt -y install php7.2 php7.2-mysql

# apt -y install mariadb-server mariadb-client
# systemctl enable mariadb
# systemctl start mariadb

# cd /var/www/html
# wget https://ja.wordpress.org/latest-ja.tar.gz
# tar xvf latest-ja.tar.gz
# chown -R www-data:www-data .

# mariadb
CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8;
GRANT ALL ON wordpress.* TO wordpress@localhost IDENTIFIED BY 'password';
```

終わったら、Wordpressの初期設定を行う

* WordPress アドレス (URL)：https://zhaoyuechen.tk

* サイトアドレス (URL)：https://zhaoyuechen.tk

* phpの設定：/etc/php/7.2/apache2/php.ini

    ```shell
    memory_limit = 128M
    post_max_size = 8M
    upload_max_filesize = 2M
    ```

## Let's Encrypt

000-default.conf

```shell
ServerAdmin ryuuji2333@gmail.com
DocumentRoot /var/www/html/wordpress
ServerName zhaoyuechen.tk
ServerAlias www.zhaoyuechen.tk
```

default-ssl.conf

```shell
ServerAdmin ryuuji2333@gmail.com
DocumentRoot /var/www/html
```

証明書の生成

```shell
# apt -y install python3-certbot-apache
# certbot --apache
```

証明書の場所

```shell
/etc/letsencrypt
```

## 自動更新

