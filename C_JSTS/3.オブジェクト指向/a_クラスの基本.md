# クラスの基本



## クラス定義



### クラス宣言

関数宣言時に発生する`ホイスティング（巻き上げ）`は、クラス宣言時には発生しない
そのため、クラスを使用したい場合は必ずクラスを使用する前に、クラス宣言を行うことが必要となる

```javascript
class クラス名{
   // ...
}
```



### クラス式

式としてクラスを定義することができる

変数に代入するclass式は無名クラスでも名前つきクラスでも可能

```javascript
const 名前 = class {
  // ...
}
```



## メソッド定義



### コンストラクタ定義＆メソッド定義

```javascript
const fooclass = class {
	constructor(x, y) { /* コンストラクタ */
		this.x = x
		this.y = y
	}
   calc() {  /* メソッド */
		return this.x + this.y  /* x と y を足した値を返却する */
	}
}
```

JavaScript の関数がオーバライドできないことによる制約があるため、

コンストラクタは 1 つしか定義できない



### getter & setter

メソッド定義の前に、**`get`** や **`set`** というキーワードを付けると、

それぞれ ゲッターメソッド、セッターメソッドとして定義することができる

ゲッターだけを定義することで、リードオンリーなプロパティのように見せることができる

ゲッターを定義するときに、同じ名前のプロパティが実際にインスタンスのプロパティとして存在している必要がない

他のプロパティを処理して値を返すことができればい良い

```javascript
class Person {
  constructor(name) {
    this._name = name;
  }
  get name() {
    console.log('get name() has been called');
    return this._name;
  }
  set name(name) {
    console.log('set name() has been called');
    this._name = name;
  }
}

const obj = new Person('Maku');
obj.name = 'Hemu';  // セッターが呼び出される
console.log('Hello ' + obj.name);  // ゲッターが呼び出される
```



## クラスの使い方



### オブジェクトの作成

```javascript
var foo1 = new fooclass(10, 20)
```



### プロパティの取得＆設定

```javascript
var aaa = person.lastname;
var aaa = person["lastname"];
```



## staticメンバー



### 静的プロパティ

クラスに静的なプロパティを定義するときは、

従来と同様に `class` ブロックの外で `クラス名.プロパティ名` と定義する必要がある

```javascript
class Book {
  constructor(title) {
    this._title = (title === undefined) ? Book.defaultTitle : title;
  }
  get title() { return this._title; }
}

// 静的プロパティ
Book.defaultTitle = 'UNKNOWN';

const obj = new Book()
console.log(obj.title);  //=> UNKNOWN
```



### 静的メソッド

`class` ブロックの中でメソッド定義するときに、**`static`** キーワードを付けると、

そのメソッドは静的メソッドとなり、インスタンス化しなくても呼び出すことができるようになる

```javascript
class Point {
  constructor(x, y) {
    this._x = x;
    this._y = y;
  }

  static distance(p1, p2) {
    const dx = p1._x - p2._x;
    const dy = p1._y - p2._y;
    return Math.hypot(dx, dy);
  }
}

const p1 = new Point(0, 0);
const p2 = new Point(3, 4);
console.log(Point.distance(p1, p2));  //=> 5
```

























































