### 色々なオブジェクト

```javascript
var a = new String();
var b = new Number();
var c = new Boolean();
var d = new Array();
var e = new Object();
```



### 定義方法

* new演算子

   new演算子で、既存のオブジェクトから新しく同じ構造を持つオブジェクトを作れる

   ```javascript
   var Name = new Object();
   var obj2 = new obj1();
   ```

* オブジェクトリテラル

   ```javascript
   var person = {
       // keyの名前は""で囲まなくても良い
       "firstname":"Bill",
       "lastname":"Gates",
       "id":5566,
       "hello": function(){}
   };
   ```

* create()メソッド

   ```javascript
   var ob2 = Object.create( obj1 );
   // この時、プロパティの内容がコピーされて、共有される
   // obj2の値を変えれば、obj1の値も変わる
   ```



### 使い方

* プロパティのアクセス

   ```javascript
   var aaa = person.lastname;
   var aaa = person["lastname"];
   ```

* プロパティの追加

   ```javascript
   /*存在しないプロパティにそのまま代入すればよい*/
   
   // プロパティを持ってるかを調べる方法は
   obj01.hasOwnProperty(Name);
   ```

* プロパティの削除

   `delete obj01.Name;`

* 全てのプロパティを配列にする

   ```javascript
   var aaa = Object.keys(obj01)
   // keys()はスタティックメソッド
   ```

* メソッドの追加

   プロパティの追加と同じく、値を関数にするだけ



### 階層化

オブジェクトリテラルを階層化する

* 定義

   ```javascript
   var customers = {
       "c001":{
           "name": "aaa",
           "class":{
               "eng": 95,
               "math": 55
           }
       },
       "c002":{
           "name": "bbb",
           "class":{
               "eng": 66,
               "math": 74
           }
       }
   }
   ```

* アクセス

   ```javas
   customers.a001.name;
   customers["a001"]["name"];
   ```

* 参照

   ```javas
   var obj1 = {};
   // obj1を変えれば、obj2に反映する
   var obj2 = obj1;
   ```

* 他objectのメソッドの利用

   1. `call()` で

      ```javascript
      var obj1 = {  name:"1",greet:function(){},greet2:function(age,from){}  };
      var obj2 = {  name:"2"  };
      obj1.greet.call(obj2);                  // obj2がobj1のメソッドを借りて使う
      obj1.greet2.call(obj2, 6, "Japan");     // 2個目以降はメソッドの引数
      ```

   2. `apply()` で

      ```javascript
      // callと似ている。第２引数は配列
      var param = [6, "Japan"];
      obj1.greet2.apply(obj2, param);
      ```





### 自動型変換

プリミティブ型にはメソッドを持たないが、 

それに対してプロパティorメソッドを使うと、 

自動的に対応するオブジェクト型のインスタンスに変換される。

```javascript
var str = "JavaScript";
console.log("長さ：" + str.length);			// 長さ：10
console.log( str.toUpperCase() );			// JAVASCRIPT
var num = 31.9959;
console.log( num.toExponential(2) );		// 3.20e+1
// 数値型	----> Numberオブジェクト
// 文字列型	----> Stringオブジェクト
// 真偽値型	----> Booleanオブジェクト
```

































