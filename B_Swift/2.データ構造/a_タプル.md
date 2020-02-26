# タプル



## タプル



### タプル

複数の値を一つの値として扱う

異なる型を組み合わせることも可能

```swift
// 書式
(値1, 値2, 値3, ...)

// 例
let product = ("Swift", 2020)
let guest: (String, String, Int) = ("星野", "源", 1234)
```

普通の定数＆変数と同様、タプルも型推論や型アノテーションがある

値にラベルをつける：

```swift
// 書式
var 変数名: (ラベル:型, ラベル:型, ラベル:型, ...)
	 = (ラベル:値1, ラベル:値2, ラベル:値3, ...)

// 例
var user:(name:String, age:Int)
user.name = "星野"
user.age = 20
```



### 値の取り出し

* タプル形式で定数or変数を用意して取り出す

  ```swift
  let data = (1000, 80)
  let (price, tax) = data		// 取り出した！
  print(price+tax)				// 1080
  ```

  利用しない値は、`_`を使って捨てる。

  ```swift
  let data = (1000, 80)
  let (price, _) = data		// 取り出した！
  print(price)					// 1000
  ```

* index番号でアクセスする

  ```swift
  let data = (1000, 80)
  let price = data.0
  let tax = data.1
  print(price+tax)				// 1080
  ```

* ラベルでアクセスする

  ```swift
  let data = (price:1000, tax:80)
  let price = data.price
  let tax = data.tax
  print(price+tax)				// 1080
  ```

  