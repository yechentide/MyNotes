## Apache



### インストール

```
# yum -y install httpd
```



### 基本

* ドキュメントルートは、`/var/www/html`

* 設定ファイルは、`/etc/httpd/conf/httpd.conf`

   設定ファイル中の主な項目：

   |      項目      |                             説明                             |
   | :------------: | :----------------------------------------------------------: |
   |   ServerRoot   |         設定ファイルなどを配置するトップディレクトリ         |
   |     Listen     |                 Apacheの待ち受けるポート番号                 |
   |      User      |           Apacheの実行ユーザー。デフォルトはapache           |
   |     Group      |           Apacheの実行グループ。デフォルトはapache           |
   |  ServerAdmin   | Apacheの管理者。管理者のメールアドレスの指定。デフォルトでもOK |
   |   ServerName   |                        Webサーバー名                         |
   |  DocumentRoot  |                      ドキュメントルート                      |
   | DirectoryIndex |                    インデックスファイル名                    |

* 設定を変えたら、構文チェック

   ```
   # httpd -t
   ```

* Apacheの起動

   ```
   # systemctl start httpd.service
   # systemctl enable httpd.service
   ```

* ファイヤウォールの設定

   デフォルトではWebサーバーへのアクセスは許可されていない場合もある

   ```
   # firewall-cmd --permanent --add-service=http
   # firewall-cmd --reload
   ```



### アクセスログ

場所：	`/var/log/httpd/access_log`

* １行につき１アクセス情報が記録されている

   アクセス元IP, 認証ユーザー, アクセス日時, アクセスしたページ, 使用したブラウザ

* アクセスが成功したかどうかは、「HTTP/1.1」の後ろにある「200」という数値で判別

   |            数値             |                 意味                 |
   | :-------------------------: | :----------------------------------: |
   |          200 (OK)           |         リクエストが成功した         |
   |     401 (Unauthorized)      | ユーザー認証が必要なページで失敗した |
   |       403 (Forbidden)       |       アクセスが禁止されている       |
   |       404 (Not Found)       | リクエストされたファイルが存在しない |
   | 500 (Internal Server Error) |    サーバー内部でエラーが発生した    |



### エラーログ

場所：	`/var/log/httpd/error_log`

各種のエラーのほか、Apacheが起動したり終了したりした時の内部的な動作も記録される



### パスワード認証の設定

**ダイジェスト認証**と**基本認証(BASIC認証)**がある。

基本認証(BASIC認証)：あらかじめApacheに user&pass を登録しておき、特定のディレクトリ以下にアクセスがあれば認証を求める仕組み



登録方法：

```
htpasswd [-c] パスワードファイル名 ユーザー名
```

-c は初回だけにつける、パスワードファイルが作成される

パスワードファイルの内容が流出しないように、権限を変える

```
# chown apache パスワードファイル名
# chgrp apache パスワードファイル名
# chmod 600 パスワードファイル名
```

次に、どの範囲に対して基本認証を適用するかを設定

`/etc/httpd/conf.d/auth.conf`を編集する。なければ作る。

下のものを入力：

```
<Directory "/var/www/html">
	AuthType Basic
	AuthName "Private Area"
	AuthUserFile パスワードファイルの絶対パス
	Require valid-user
</Directory>
```

<Directory> 〜 </Directory>の間のものは、

特定のディレクトリ以下に適用する設定を書く(ここでは/var/www/html)

* AuthType			BASICを指定する基本認証
* AuthName		  この認証名(認証windowに表示)
* AuthUserFile	  パスワードファイル名
* Require			    認証ユーザー(valid-userなら、passファイル内の全ユーザー)

```
# systemctl reload httpd.service
```





























