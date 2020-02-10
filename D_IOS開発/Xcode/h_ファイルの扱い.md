# ファイルの扱い





## ユーザーデフォルト

アプリごとにサンドボックスが作られている

他のアプリのサンドボックスにアクセスできない

データは辞書型のように、キーと値のペアで保存される。

削除は`removeObject(forKey:)`

保存は値の型と関係なく、`set(_:forKey:)`

読込は値の型により違うメソッドを利用する

* `object(forKey:) -> Any?`
* `string(forKey:) -> String?`
* `array(forKey:) -> [Any]?`
* `dictionary(forKey:) -> [String:Any]?`
* `data(forKey:) -> Data?`
* `stringArray(forKey:) -> [String]?`
* `integer(forKey:) -> Int?`
* `float(forKey:) -> Float?`
* `double(forKey:) -> Double?`
* `bool(forKey:) -> Bool?`
* `url(forKey:) -> URL?`

```swift
let defaults = UserDefaults.standard
defaults.set(......)
......
```





## テキストファイル



### IOS標準ディレクトリ：ファイルの保存場所

|        主なディレクトリ        |                            使い方                            | iTunesにバックアップされる |
| :----------------------------: | :----------------------------------------------------------: | :------------------------: |
|               ~/               |                       使ってはいけない                       |             ✖️              |
|          ~/Documents/          |        ユーザードキュメント、データファイルを保存する        |             ⭕️              |
|       ~/Documents/Inbox/       |         読み取り、削除のみ(外部アプリから配置される)         |             ⭕️              |
|           ~/Library/           |            ユーザーに公開しないファイルを管理する            |             ⭕️              |
|       ~/Library/Caches/        |  いつでも作り直せるファイル。システムに削除されることがある  |             ✖️              |
| ~/Library/Application Support/ | 設定ファイル、テンプレートなどアプリ固有のデータファイルを保存 |             ⭕️              |
|             ~/tmp/             | 一時的に保管に使い、不要になったら削除。システムに削除されることがある |             ✖️              |



### 保存

* 保存先のパスを作る

  ```swift
  let path = NSHomeDirectory() + "/Documents/xxx.txt"
  ```

* 保存する

  ```swift
  let textData = "..................."
  do {
  	try textData.write(toFile: path, atomically: true, encoding: String.Encoding.utf8)
  } catch let error as NSError {
  	print("保存に失敗\n\(error)")
  }
  ```

  

### 読み込む

```swift
do {
	let textData = try String(contentsOfFile: path, encoding: String.Encoding.utf8)
	// ...
} catch let error as NSError {
	print()
}
```



### ファイルのチェック

```swift
let fileManager = FileManager.default
guard (FileManager.fileExists(atPath: path)==true) else {
	return
}
```



































