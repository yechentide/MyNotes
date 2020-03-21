# 定数＆変数



## 定数



### 定数宣言

ES6から定数を宣言できるようになった

```javascript
const Name = value;
```

**宣言と同時に初期化する**



## 変数



### 変数宣言

```javascript
var x=2;
var pi=3.14;
var x=true;
let y=false;
let nname="Bill Gates";
let answer='Yes I am!';
```

var = variable(変えられる)
初期化されていない変数の値は、undefinedとなる
宣言の前に変数を使うと、その変数がグローバル変数となる
varで宣言した変数は、宣言場所によって、グローバル変数orローカル変数になる
なるべくグローバル変数を使わないこと！

ES6から`let`で変数を宣言できるようになった



### letとvarの違い

```javascript
let a = 10;      var b = 10;
```

どちらも変数を宣言しているが、変数のスコープが違う。
letはブロックスコープで、宣言をした{ }内のみ有効
varは関数スコープで、宣言をした関数内のみ有効



## 定数＆変数のルール



### 変数名の命名規則

* アルファベット
* 数字
* Unicode文字（漢字など）
* `_` `$`

先頭文字は数字がNG 予約語を使用禁止



### 変数名の記法

* キャメル記法

  userName

* パスカル記法

  UserName

* アンダースコア記法

  user_name



















