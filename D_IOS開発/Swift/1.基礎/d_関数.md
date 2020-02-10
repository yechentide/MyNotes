## 関数



### 定義場所

通常、関数を定義するコードはクラス定義の中に書く＝クラスのメソッド



### 関数定義

1. 引数がない関数

   ```swift
   func 関数名() -> 戻り値の型 {
      // ...
      return 戻り値
   }
   ```

2. 戻り値がない関数（書き方は３通り）

   ```swift
   func 関数名() { /*----------*/ }
   func 関数名() -> Void { /*----------*/ }
   func 関数名() -> () { /*----------*/ }
   ```

3. 引数がある関数

   ```swift
   func 関数名(引数:型, 引数:型, ...) -> 戻り値の型 {
      // ...
      return 戻り値
   }
   ```

4. 引数の個数を指定しない（可変長引数）

   ```swift
   // 型指定の後ろに ... をつける
   func 関数名(配列名:型...) -> () {}

   let result = 関数名(ラベル: 値, 値, 値, ...)
   ```

5. 引数に初期値を設定する（省略できる引数）

   ```swift
   // 初期値が設定された引数は、関数を呼び出す際に省略できる
   // 初期値が指定してあれば、順番に関係なく省略できる
   func 関数名(引数:型=値, ...) -> () {}
   ```

6. 複数の戻り値がある関数（タプルを利用）

   ```swift
   // 戻りのタプルには、値の型と同時に、ラベルを指定できる
   func 関数名() -> (戻り値の型, 戻り値の型,){
      // ...
      return (値, 値)
   }
   func 関数名() -> (ラベル1:戻り値の型, ラベル2:戻り値の型,){
      // ...
      return (値, 値)
   }

   print("\(関数名().ラベル1)")
   ```

7. 関数の多重定義（オーバーロード）

   引数名や引数の個数、引数の型が違うと別の関数として扱われる

8. 関数はネストできる。

   ネストした関数は、自分の外部関数の変数をアクセスできる

9. 関数は、他の関数を戻り値にできる

   ```swift
   func makeIncrementer() -> ((Int) -> Int) {
       func addOne(number: Int) -> Int {
           return 1 + number
       }
       return addOne
   }
   var increment = makeIncrementer()
   increment(7)
   ```

10. 関数は、他の関数を引数にもできる

    ```swift
    func hasAnyMatches(list: [Int], condition: (Int) -> Bool) -> Bool {
        for item in list {
            if condition(item) {
                return true
            }
        }
        return false
    }
    func lessThanTen(number: Int) -> Bool {
        return number < 10
    }
    var numbers = [20, 19, 7, 12]
    hasAnyMatches(list: numbers, condition: lessThanTen)
    ```



### 抜ける前に実行される処理

defer文を定義すれば、関数を抜ける前に必ず実行される

中断処理やエラーハンドリング処理などで有効

```swift
func half(num:Double) {
   // 最後に必ず実行する
   defer {
      print("計算終了")
   }
   // 中断処理
   guard num>=0 else {return}
   let halfNum = num/2
   print("\(num)の半分は\(halfNum)")
}
```

一つの関数内で複数のdefer文を定義できる

後から定義したものから順に実行される



### 外部引数名をつける

1. 引数に外部引数名をつける

   ```swift
   func 関数名(外部引数名 引数:型) -> () {}
   
   関数名(外部引数名: 値)
   ```
   
2. 呼び出す際に引数名を省略する

   ```swift
   func 関数名(_ 引数:型) -> () {}
   
   関数名(値)
   ```





### よく使う関数

|            関数            |                戻り値                 |
| :------------------------: | :-----------------------------------: |
|        arc4random()        |           1以上の整数の乱数           |
| arc4random()_uniform(数値) |        0〜(数値-1)の整数の乱数        |
|         ceil(数値)         |         小数点以下を切り上げ          |
|        floor(数値)         |         小数点以下を切り捨て          |
|        round(数値)         |         小数点以下を四捨五入          |
|         fmax(a, b)         |            大きい方の数値             |
|         fmin(a, b)         |            小さい方の数値             |
|         fmod(x, y)         |               x/yの余り               |
|           abs(x)           |               xの絶対値               |
|          sqrt(x)           |               xの平方根               |
|         pow(x, y)          |                xのy乗                 |
|           sin(θ)           |                サイン                 |
|           cos(θ)           |               コサイン                |
|           tan(θ)           |             タンジェント              |
|          asin(θ)           |             アークサイン              |
|          acos(θ)           |            アークコサイン             |
|          atan(θ)           |          アークタンジェント           |
|        atan2(y, x)         | 点(0,0)と点(x,y)を結ぶ直線の傾き角度θ |

* rounded()メソッド

   `round(数値)`と違って、`rounded()`は`num.rounded()`のように使う

   rounded()メソッドの引数には丸め方を指定できる

   |          丸め方          |                    説明                     |
   | :----------------------: | :-----------------------------------------: |
   |        指定を省略        |                  四捨五入                   |
   |           .up            |                  切り上げ                   |
   |          .down           |                  切り捨て                   |
   |      .awayFromZero       |             0から遠い値に丸める             |
   |       .towardZero        |              0に近い値に丸める              |
   |     .toNearestOrEven     |    近い値に丸める。距離が同じなら偶数を     |
   | .toNearestOrAwayFromZero | 近い値に丸める。距離が同じなら0から遠い値を |

   



















