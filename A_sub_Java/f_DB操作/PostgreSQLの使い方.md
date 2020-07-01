# PostgreSQLの使い方





## 基本情報



### インストール先 (MacのHomeBrewを使った場合)

```shell
/usr/local/var/postgres
```



### 起動

```mysql
postgres -D /usr/local/var/postgres
```



### 接続

```mysql
psql -U dbstudent test -L /Users/yechentide/Downloads/db0604.log

-U		ユーザー指定
-d		データーベース指定
-L		ログ指定
```



### シェルコマンド

```shell
psql -U yechentide -l			### データベース一覧
createdb -U yechentide test	### testというデータベースを作る
```



### 接続中のコマンド

```shell
\h					### SQLのヘルプ
\?					### psqlコマンドのヘルプ
\d					### テーブル一覧
\d テーブル名		### テーブルの情報
\d+ テーブル名	### テーブルの詳細情報
\q					### 接続終了

\copy テーブル to ファイル名		### テキストファイルとして書き出す(tabで区切っている)
\copy テーブル from ファイル名	### tabで区切ったファイルから読み込む
\copy テーブル from ファイル名 using delimiters ','
```





## ユーザー関連



### 現在のユーザー

```mysql
SELECT USER;
```



### ユーザー作成

```mysql
CREATE USER ユーザ名 PASSWORD 'パスワード';
```



### ユーザー削除

```mysql
DROP USER 消したいユーザ名;
```



### ユーザー一覧

```mysql
SELECT usename FROM pg_user;
```



### パスワード変更(管理者で実行)

```mysql
ALTER USER ユーザ名 PASSWORD '新パスワード';
```





## データ型







## テーブル関連



### テーブル作成

```mysql
create table priceTable(name TEXT, price INTEGER);
```

```mysql
CREATE TABLE maker(
makercode CHAR(3) NOT NULL,
makername TEXT DEFAULT '未登録',
PRIMARY KEY (makercode)
);

CREATE TABLE maker(
makercode CHAR(3) PRIMARY KEY,
makername TEXT DEFAULT '(未登録)'
);
```

```mysql
CREATE TABLE テーブル名(
   
主キー CHAR(5) NOT NULL,
項目 TEXT NOT NULL,
項目 INTEGER CHECK (自身>=50),
項目 DATE NOT NULL,
外部キー CHAR(3) NOT NULL,
   
PRIMARY KEY (主キー),
UNIQUE (重複を許さない項目),
FOREIGN KEY (外部キー) REFERENCES 他のテーブル(外部キー)
   
);
```



### テーブル削除

```mysql
DROP TABLE テーブル;
```





## レコード関連



### 関数

* `SUM(項目,式など)`
* `AVG(項目,式など)`
* `MIN(項目,式など)` `MAX(項目,式など)`
* `LOWER(項目)`
* `SUBSTRING(項目, 1, 2)`  =  最初の２文字



### 条件式

* `price*0.9`  =  `CAST(price AS FLOAT)*0.9`
* =：`=`   ≠：`<>`
* `WHERE 項目 BETWEEN 値1 AND 値2`  =  `WHERE 値1<=項目 AND 項目<=値2`
* `WHERE 項目 IN (値1, 値2, 値3)`  =  `WHERE 項目=値1 OR 項目=値2 OR 項目=値3`
* `WHERE hanbaitanka>shiiretanka+90`
* `WHERE makercode IS NULL`   `WHERE makercode IS NOT NULL`



### テーブル結合

```mysql
SELECT name,place,price FROM pricetable NATURAL JOIN departmenttable;

SELECT pricetable.name, departmenttable.place, pricetable.price
FROM pricetable, departmenttable
WHERE pricetable.name=departmenttable.name;

### LEFT JOIN
SELECT uriage.uriageno, hinmoku.hinmokuname, hinmoku.hinmokucode
FROM hinmoku LEFT JOIN uriage ON hinmoku.hinmokucode=uriage.hinmokucode
ORDER BY uriage.uriageno ASC;
```



### 基本のデータ抽出

```mysql
SELECT * FROM pricetable;
SELECT name,price FROM pricetable;
SELECT name AS 品名,price AS 値段 FROM pricetable;
SELECT hanbaitanka*uriagesuryo FROM uriage;
```



### 並べ替え

```mysql
SELECT hinmokucode, hanbaitanka FROM hinmoku ORDER BY hanbaitanka;		昇順(デフォルト)
SELECT hinmokucode, hanbaitanka FROM hinmoku ORDER BY hanbaitanka ASC;	昇順
SELECT hinmokucode, hanbaitanka FROM hinmoku ORDER BY hanbaitanka DESC;	降順

SELECT hinmokucode, uriageno, hinmokuname, uriagedate FROM hinmoku NATURAL JOIN uriage
ORDER BY hinmokucode ASC, uriagedate DESC;
```



### データ件数

```mysql
SELECT makercode, COUNT(*) FROM hinmoku GROUP BY makercode;
SELECT makercode, COUNT(*) FROM hinmoku GROUP BY makercode HAVING COUNT(*)=2;

SELECT COUNT( DISTINCT makercode ) FROM hinmoku;			### DISTINCTで重複を除く
```



### データ文字列

```mysql
SELECT hinmokucode, hinmokuname FROM hinmoku WHERE hinmokuname LIKE '%A4';		%は任意の長さの文字
SELECT hinmokucode, hinmokuname FROM hinmoku WHERE hinmokuname LIKE '%A_';		_は任意の１つの文字

SELECT hinmokuname || ' (' || hanbaitanka || '円)' AS 商品の販売単価 FROM hinmoku;	連結(１列になる)
```



### 副問合せ

```mysql
SELECT hinmokuname FROM hinmoku WHERE hinmokucode IN
   (SELECT hinmokucode FROM uriage WHERE uriagedate='2004-5-10');
SELECT hinmokuname From hinmoku WHERE hinmokucode NOT IN
   (SELECT hinmokucode FROM uriage WHERE uriagedate BETWEEN '2004-5-10' AND '2004-5-12');
```



### レコード追加

```mysql
INSERT INTO pricetable VALUES ('ノート',100);
INSERT INTO newhinmoku (SELECT * FROM hinmoku);
```



### レコードの更新

```mysql
UPDATE pricetable SET price=price-10000 WHERE name='ノートパソコン';
UPDATE hinmoku SET hanbaitanka=400, shiiretanka=280 WHERE hinmokucode='LL001';

UPDATE newhinmoku SET hanbaitanka=hanbaitanka*1.2 WHERE hinmokucode IN (SELECT hinmokucode FROM uriage);
```



### レコードの削除

```mysql
DELETE FROM テーブル;							### 全削除
DELETE FROM テーブル WHERE 項目='値';

DELETE FROM newhinmoku WHERE hinmokucode NOT IN (SELECT hinmokucode FROM uriage);
```





## ビュー



### ビュー作成

```mysql
CREATE VIEW hinmokuhanbaitanka AS
	SELECT hinmokucode, hinmokuname, hanbaitanka FROM hinmoku;
```



### ビューの削除

```mysql
DROP VIEW hinmokuhanbaitanka;
```





## インデックス



### インデックス作成

```mysql
CREATE INDEX hinmokuindex ON hinmoku(hinmokucode, makercode);
```



### インデックス削除

```mysql
DROP INDEX hinmokuindex;
```





## 権限



### 権限付与

```mysql
GRANT SELECT ON オブジェクト TO ユーザ名;	### SELECT権限のみ与える
GRANT ALL ON オブジェクト TO ユーザ名;		### 全権限を与える
```



### 権限剥奪

```mysql
REVOKE SELECT ON オブジェクト FROM ユーザ名;
```













































