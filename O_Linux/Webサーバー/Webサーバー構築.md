# Webサーバー構築





## 最初の設定

```bash
# vim /etc/ssh/sshd_config
	PermitRootLogin no
	PasswordAuthentication yes
# systemctl restart sshd
# passwd
# adduser yechen
# echo "OvO" > /etc/hostname
# timedatectl set-timezone Asia/Tokyo
# dnf -y update
# reboot

# dnf -y install zsh util-linux-user
# which zsh
# chsh -s $(which zsh)
# chsh -s $(which zsh) yechen
$ git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"
$ setopt EXTENDED_GLOB
for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
  ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
done
$ vim ~/.zpreztorc
	zstyle ':prezto:module:prompt' theme 'pure'
	'syntax-highlighting' \
   'autosuggestions' \
$ source ~/.zpreztorc
```





## MariaDB



### インストール

```
# dnf install -y mariadb-server mariadb mariadb-devel
# dnf list installed | grep mariadb
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





## SSL/TLS化



### よく使われる証書

* CloudFlare Inc ECC CA-2

* Let's Encrypt Authority X3



### 事前にエラー対策

[Let's Encrypt導入前に準備すべきこと](https://qiita.com/iwamot/items/ca8173df1dd6f18c42dd)

1. バーチャルホストの設定

   ```bash
   エラー：
   Unable to find a virtual host listening on port 80 which is currently needed for Certbot to prove to the CA that you control your domain. Please add a virtual host for port 80.
   解決法：
   /etc/httpd/conf/httpd.conf　に<VirtualHost>を追加
   
   vim /etc/httpd/conf/httpd.conf
   
   NameVirtualHost *:80
   <VirtualHost *:80>
   ServerAdmin root@zhaoyuechen.tk
   DocumentRoot /var/www/html
   ServerName zhaoyuechen.tk
   RewriteEngine on
   </VirtualHost>
   Include /etc/httpd/conf/httpd-le-ssl.conf
   LoadModule rewrite_module modules/mod_rewrite.so
   ```

2. mod_rewriteの有効化

   ```bash
   エラー：
   Syntax error on line 1 of /etc/httpd/conf.d/le_http_01_challenge_pre.conf:
   Invalid command 'RewriteEngine', perhaps misspelled or defined by a module not included in the server configuration
   解決法：
   /etc/httpd/conf/httpd.confのmod_rewriteを有効に
   
   vim /etc/httpd/conf/httpd.conf
   LoadModule rewrite_module modules/mod_rewrite.so
   ```

3. mod_sslの設定

   ```bash
   エラー：
   HTTPSをリッスンするようにはなったものの、自己署名証明書が有効という問題への対策
   解決法：
   vim /etc/httpd/conf.d/ssl.confで<VirtualHost _default_:443>セクションをまるごと削除する
   ```



### 導入

[Let’s EncryptによるSSLサーバー証明書の取得、自動更新設定（2019年1月版）](https://inaba-serverdesign.jp/blog/20190205/lets_encrypt_ssl_certificate_update.html)

[Let's Encryptの証明書の取得・設定](https://qiita.com/RubiLeah-com/items/c2252a6c42f60fc3677b)

1. Let’s Encryptクライアントのインストール

   ```bash
   cd /usr/local/
   git clone https://github.com/certbot/certbot
   cd /usr/local/certbot/
   ./certbot-auto --debug
   ./certbot-auto --version
   ```

2. Let’s Encrypt証明書取得

   ```bash
   ./certbot-auto --authenticator standalone --installer apache -d zhaoyuechen.tk --pre-hook "apachectl stop" --post-hook "apachectl start"
   ```









certbot-auto --authenticator standalone --installer apache -d zhaoyuechen.tk --pre-hook "apachectl stop" --post-hook "apachectl start"



certbot-auto certonly --agree-tos --webroot --webroot-path /var/www/html -d zhaoyuechen.tk -d www.zhaoyuechen.tk



certbot-auto certonly --webroot -w /var/www/html --email ryuuji2333@gmail.com -d zhaoyuechen.tk -d www.zhaoyuechen.tk



certbot certonly --webroot -w /var/www/html --email ryuuji2333@gmail.com -d zhaoyuechen.tk -d www.zhaoyuechen.tk









certbot-auto --apache -w /var/www/html --email ryuuji2333@gmail.com -d zhaoyuechen.tk -d www.zhaoyuechen.tk





certbot-auto --authenticator standalone --installer apache -w /var/www/html --email ryuuji2333@gmail.com -d zhaoyuechen.tk -d www.zhaoyuechen.tk





















