## コードのメモ



### 画面の色を変更

```swift
view.backgroundColor = UIColor.blue
```



### ファイルの読み取り

```swift
let path = NSHomeDirectory() + "/Documents/hoge.txt"

do {
	let str = try String.init(contentsOfFile: path, encoding: String.Encoding.utf8)
	let lines = str.components(separatedBy: "\r\n")
	for i in 0..<lines.count {
		print("\(i+1)行目：\t\(lines[i])")
	}
}
```



### ディレクトリのファイル一覧

```swift
let path = NSHomeDirectory() + "/Documents"
do {
	let items = try FileManager.default.contentsOfDirectory(atPath: path)
	print(items)
} catch let error {
	print("error: \(error)")
}
```



### UIColor

各引数はCGFloat型、範囲は`0.0~1.0`。178.5/255=0.7

```swift
UIColor(red:0.7, green:0.6, blue:0.7, alpha:0.5)
```











































