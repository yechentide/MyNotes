### LAMPサーバーとは

L: Linux

A: Apache

M: MySQL / MariaDB

P: PHP / Python / Perl / Ruby?





## MariaDB



### インストール

```
# dnf -y install mariadb-server
# dnf list installed | grep mariadb |sort
```



### 設定

日本語が正しく扱えるように、設定ファイルを変更

```
vim /etc/my.cnf
```

４行目に `character-set-server=utf8` を追加

```
# systemctl start mariadb
# systemctl enable mariadb
```

次にDatabaseとuserを追加する

```
# mysql
> create database wordpress default character set utf8;
> grant all on wordpress.* to wordpress@localhost identified by 'password';
```





## PHP



### インストール

```
# dnf -y install php php-mysqlnd php-pecl-json php-mbstring php-intl
# systemctl restart httpd
```

php-mbstring  ：　日本語などのマルチバイト文字を扱うためのパッケージ

php-gd  ：　画像ライブラリを扱うパッケージ

php-mysql  ：　PHPとMySQL/MariaDBを連係させるパッケージ

```
$ php --version
```

PHPがApacheより後でインストールしたなら、Apacheを再起動

```
# systemctl restart httpd.service
```





## WordPress



### インストール

```
$ cd /var/www/html
$ wget https://ja.wordpress.org/latest-ja.tar.gz
$ tar xvf latest-ja.tar.gz
$ chown -R apache:apache .
```

































