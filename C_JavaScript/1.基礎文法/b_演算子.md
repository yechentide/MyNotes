# 演算子



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


