# ユーザーデフォルト

## ユーザーデフォルト

`UserDefaults`クラスの`standard`プロパティで、辞書のようにデータを管理している

### データの保存

```swift
let defaults = UserDefaults.standard
defaults.set(データ, forKey: "キー")
```

### データの読み込み

読み込むデータに応じて、メソッドを利用する

```swift
func bool(forKey: String) -> Bool
func integer(forKey: String) -> Int
func float(forKey: String) -> Float
func double(forKey: String) -> Double
func string(forKey: String) -> String?
func stringArray(forKey: String) -> [String]?
func array(forKey: String) -> [Any]?
func dictionaryRepresentation() -> [String : Any]
func dictionary(forKey: String) -> [String : Any]?
func url(forKey: String) -> URL?
func data(forKey: String) -> Data?
func object(forKey: String) -> Any?
```

### データの削除

```swift
func removeObject(forKey: String)
```

