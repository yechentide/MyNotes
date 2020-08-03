# ファイル出入力

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

## ファイル操作

### パス

* `NSHomeDirectory()`：それぞれのアプリが利用できるホームディレクトリを取得

    ```swift
    NSHomeDirectory()+"/Document/test.txt"
    ```

### ファイルの保存場所

個々のアプリが利用できるのは、自分のホームディレクトリのみ
iOSでは標準のディレクトリが決まっている
| 主なディレクトリ               | 使い方                                                       | iTunesにバックアップされる |
| ------------------------------ | ------------------------------------------------------------ | :------------------------: |
| ~/                             | ホームディレクトリ  使ってはいけない                       |             ❌              |
| ~/Documents/                   | ユーザー書類、データファイルを保存                           |             ◯              |
| ~/Documents/Inbox/             | 読み取り＆削除のみ(外部から配置される)                       |             ◯              |
| ~/Library/                     | ユーザーに公開しないファイルを管理する                       |             ◯              |
| ~/Library/Caches/              | いつでも作り直せるファイル  システムに削除されることがある |             ❌              |
| ~/Library/Application Support/ | 設定ファイル、テンプレートなど、  アプリ固有のデータファイルを保存する |             ◯              |
| ~/tmp/                         | 一時的の保管に使い、不要になったら削除する  システムに削除されることがある |             ❌              |

### 書き込み

Stringの`write(toFile: atomically: encoding:)`メソッドを使えば良い
ファイルの保存は失敗する可能性があるので、例外処理に組み込む
第２引数のatomicallyをtrueにすると、書き出し中に異常終了してもファイルが壊れないように、
一時ファイルを使って書き込む処理を行う

```swift
do{
    try str.write(toFile: "パス", atomically: true, encoding: String.Encoding.utf8)
}catch let error as NSError{
    print(error)
}
```

### 読み込み

`String(contentsOfFile: encoding:)`メソッドを使う
書き込みと同じく、例外処理に組み込む

```swift
do{
    let data = try String(contentsOfFile: "パス", encoding: String.Encoding.utf8)
}catch let error as NSError{
    print(error)
}
```

### ファイルの存在チェック

```swift
let fileManager = FileManager.default
guard ( fileManager.fileExists(atPath:"パス")==true ) else {
    return
}
if fileManager.fileExists(atPath:path)==true {
    print("存在する")
}
```
