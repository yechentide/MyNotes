# 制御構文



## ループ



### for-in文

指定範囲から値を順に取り出す

```swift
for 定数 in 範囲 {/**/}
```

指定回数(n回)で繰り返す

```swift
for _ in 1...n {/**/}
```

コレクション(String, 配列, 辞書など)の値を順に取り出す

```swift
for 変数 in コレクション {/**/}

let dictionary = ["a":1, "b":2]
for (key, value) in dictionary { /*...*/ }
```

#### 飛び飛びで繰り返す：　stride()関数

```swift
for 定数 in stride(from:開始値, to:終了値, by:間隔){
   // ...
}
```

#### 条件付き

```swift
for 定数 in 範囲 where 条件 { /*...*/ }
```



### while文

条件式を囲む`( )`を省略できる

無限ループを作らないように注意すべき！

```swift
while (ループ条件){/**/}
```

repeat-while文は、最低でも一回は処理を実行する

```swift
repeat {
   // ...
} while (ループ条件)
```





## 条件分岐



### if文

条件式を囲む`( )`を省略できる

```swift
if (条件式) {
   // ...
} else if (条件式) {
   // ...
} else {
   // ...
}
```

ちなみに、条件式を`,`で区切って並べるのも良い

```swift
if a>0 && b>0 && c>0 {/**/}
if a>0, b>0, c>0 {/**/}
```



### switch文

```swift
switch 式 {
   case 値1:
   	// ...
   case 値2:
   	// ...
   case 値3, 値4, 値5:
   	// ...
   default:
   	// ...
}
```

* 値は、数値や文字列、範囲などが使える

* 式にタプルを与えるとき、caseの値もタプルで指定する

  部分的にマッチする場合、`(5...10, _)`のようにワイルドカードの`_`も使える

* 各ケースの最後に、`break`がなくてもswitch文を抜ける

  処理を次のcase文へ渡したい場合は、`break`の代わりに`fallthrough`キーワードを書く

* ワイルドカード＆下のバリューバインディングで、全てのケースを網羅できれば、

  `default`を省略できる

#### バリューバインディング

関数が引数を受け取るように、caseで評価する式の値を定数or変数で受け取ることもできる

```swift
let size = (4, 10)
switch size {
   case (0, 0):
   	print("000000")
   case (5...10, let h):
   	print("高さが\(h)です")
   default:
   	print("hhhhhh")
}
```

#### whereキーワード

バリューバインディング＆whereキーワードを一緒に使うと、

値の振り分けに条件を使えるようになる

```swift
let size = (45, 40, 100)
switch size {
   case let (w, h, _) where (w>=60)||(h>=60):
   	print("サイズが規定外です")
   case let (_, _, weight) where (weight>=80):
   	print("規定の重さを超えました")
   default:
   	print("規定サイズ内です")
}
```



### guard-else文

guard-else文のブロック内の処理は、**条件式を満たさない**時に実行する

中断処理を明確に示すための構文である

```swift
guard 条件式 else {
	// 条件式を満たさない時に実行する
   return
}
```

#### if文と比べる

```swift
func myFunc01(num:Int){
   if num<0 {return}
   print("Hello!")
}
func myFunc02(num:Int){
   guard num>=0 else {return}
   print("Hello!")
}
```



## その他



### 繰り返しのスキップや中断

* `continue`：次の回の繰り返しに進む

* `break`：残りの繰り返しを中断し、ループ処理から抜ける

* ループにラベルをつける：

  for-in, while, repeat-whileにラベルをつけられる

  ```swift
  xloop: for x in 0...3 {
     yloop: for y in 0...3 {
        
        if x<y{
           print("----------")
           continue xloop		// breakの場合だとxloopを抜ける
        }
        print((x, y))
        
     }
  }
  ```

  また、上の例において、`break xloop`とかくと、外側のループまで抜ける
  
* 上と同じように、if文やswitch文やdo文にもラベルをつけられる。

  これらの場合、breakのみ使える









