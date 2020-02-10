SSL/TLS 導入



SSL:

CloudFlare Inc ECC CA-2

Let's Encrypt Authority X3



ryuuji2333@gmail.com



/* ------------------------------ 事前準備 ------------------------------ */

https://qiita.com/iwamot/items/ca8173df1dd6f18c42dd



\1. バーチャルホストの設定

Unable to find a virtual host listening on port 80 which is currently needed for Certbot to prove to the CA that you control your domain. Please add a virtual host for port 80.  の対策



vim /etc/httpd/conf/httpd.confで<VirtualHost>を追加



NameVirtualHost *:80



<VirtualHost *:80>

ServerAdmin root@zhaoyuechen.tk

DocumentRoot /var/www/html

ServerName zhaoyuechen.tk

RewriteEngine on

</VirtualHost>

Include /etc/httpd/conf/httpd-le-ssl.conf



LoadModule rewrite_module modules/mod_rewrite.so



\2. mod_rewriteの有効化

Syntax error on line 1 of /etc/httpd/conf.d/le_http_01_challenge_pre.conf:

Invalid command 'RewriteEngine', perhaps misspelled or defined by a module not included in the server configuration

の対策



vim /etc/httpd/conf/httpd.confでmod_rewriteを有効に



LoadModule rewrite_module modules/mod_rewrite.so





\3. mod_sslの設定

HTTPSをリッスンするようにはなったものの、自己署名証明書が有効という問題への対策



vim /etc/httpd/conf.d/ssl.confで<VirtualHost _default_:443>セクションをまるごと削除する







/* ------------------------------ 導入 ------------------------------ */

https://inaba-serverdesign.jp/blog/20190205/lets_encrypt_ssl_certificate_update.html

https://qiita.com/RubiLeah-com/items/c2252a6c42f60fc3677b



\1. Let’s Encryptクライアントのインストール

cd /usr/local/

git clone https://github.com/certbot/certbot

cd /usr/local/certbot/

./certbot-auto --debug

./certbot-auto --version



\2. Let’s Encrypt証明書取得



./certbot-auto --authenticator standalone --installer apache -d zhaoyuechen.tk --pre-hook "apachectl stop" --post-hook "apachectl start"