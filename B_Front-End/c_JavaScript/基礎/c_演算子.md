### 条件演算子

```javascript
変数  =  条件  ?  値1  :  値2  ;
// 条件がtrueの時は値1を返す、falseの時は値2を返す
```



### ==と===の違い

```javascript
// 両方とも値が等しいかどうかを判断する比較演算子だが、「===」の方が厳密
    "123" == 123		// true
    "123" === 123		// false
//  !=と!==についても同じ
    "123" != 123		// false
    "123" !== 123		// true 
// プリミティブ型とオブジェクト型の比較
    // プリミティブ型：値を比較
    // オブジェクト型：同じインスタンス稼動かを比較
        var o1 = new String("JavaScript");
        var o2 = new String("JavaScript");
        var o3 = o2;
        o1 == o2		// false
        o1 === o2		// false
        o3 == o2		// true
        o3 === o2		// true
    // プリミティブ型とオブジェクト型を比較
        var s1 = "JavaScript";
        var o1 = new String("JavaScript");
        o1 == s1		// true
        o1 === s1		// false
```



### 型チェック

```javascript
typeof(引数)
// 引数がオブジェクト型の時は"object"を、文字列型の時は"string"を、
// 数値型の時は"number"を、真偽値型の時は"boolean"を戻す
var Name = typeof value;
```



### 型変換

```javascript
arseInt( value );
parseFloat( value );
String( value );
// 文字列 --> 整数
var int01 = parseInt("123")				// "123",10	と同じ
var int02 = parseInt("111",2)			// 2進数を10進数に変換
// 文字列 --> 浮動小数点数
var float01 = parseFloat("3.14")		// = 3.14
var float02 = parseFloat("4.11js31")	// = 4.11 (js以降は無視される)
//条件式で数値と文字列を比較するとき、自動的に文字列を数値に変える
// 数値　 --> 文字列
123 + ""
String(値)
```



### タイマー

```javascript
// 一定時間ごとに指定した関数を実行させる。第２引数の単位はミリ秒
setInterval(func01, 1000);
// setInterval()で開始したタイマーを停止する
let timer = setInterval(func01, 1000);
clearInterval(timer);
```



### リアルタイム処理

```javascript
// 10msec間隔で関数を実行
setInterval(関数名,10)
   
// 上の記述方法と同じだが、こっちは関数内に書く
setTimeout(関数名,10)

/* 違い */
// setIntervalは、呼出先の関数の処理が終わってなくても、時間がくると呼び出す。
// よほど思い処理でないと変わらないのだが、setTimeoutの方が安全
```