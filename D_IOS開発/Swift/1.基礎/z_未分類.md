## 未分類



### カスタムオペレータ

数値と文字列を`+`演算子で簡単に連結できるように拡張する

```swift
func + (num:Int, str:String) -> String {
   return String(num) + str
}
```



### クロージャ

**クロージャの標準的な書式**

```swift
{(引数:型) -> (戻り値の型) in
   // 戻り値なしの時は -> Void in
   // ...
 	return 戻り値
}
```




```swift
numbers.map({ (number: Int) -> Int in
    let result = 3 * number
    return result
})
```

```swift
let mappedNumbers = numbers.map({ number in 3 * number })
print(mappedNumbers)
// Prints "[60, 57, 21, 36]"
```

```swift
let sortedNumbers = numbers.sorted { $0 > $1 }
print(sortedNumbers)
// Prints "[20, 19, 12, 7]"
```































