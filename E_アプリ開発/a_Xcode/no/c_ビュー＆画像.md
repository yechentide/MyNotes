## ビュー＆画像



### アプリ起動時に最初に表示する画面

View ControllerのAttributesインスペクタで、

`Is Intitial View Controller`にチェックを入れる



### ビューの作成＆表示

ルートビューは`self.view`で参照し（`self`は省略可）、`addSubview()`で追加する

```swift
let label = UILabel()
label.text = "ラベルだ"
// ラベル領域
label.frame = CGRect(x:80, y:150, width:110, height:21)
// 背景色＆文字色
label.backgroundColor = UIColor.orange
label.textColor = UIColor.white

```

サブビューの作成は上と同じ。`UIView()`で作って、`frame`と`background`で座標＆サイズ＆背景色を指定する



### 画像の表示

* `UIImageView()`か`UIImageView(framez:rect)`で作る

   ```swift
   // 表示座標また指定するので、とりあえず(0,0)に設定する
   let rect = CGRect(x:0, y:0, width:300, height:200)
   let imageView = UIImageView(frame:rect)
   ```

* 画像データを指定

   ```swift
   imageView.contentMode = .scaleAspectFit
   imageView.image = UIImage(named: "aaa.jpg")
   ```

* 画面に表示する

   ```swift
   // イメージビューの座標をルートビューの中央に設定
   imageView.center = self.view.center
   self.view.addSubview(imageView)
   ```

* 画像のクリッピング

   ```swift
   // 画像を縮小せず中央に配置
   imageView.contentMode = .center
   // イメージビューをはみ出ないように、クリップして表示する
   imageView.clipsToBounds = true
   ```
   
   サブビューにも同じようなことができる。
   
   その時、スーパービューの`clipsToBounds`を`true`にする
   
* 画像のパターン表示

   ```swift
   let img = UIImage(named: "stars.png")
   self.view.backgroundColor = UIColor(patternImage: img!)
   ```



### ビューの座標＆領域

ビューのプロパティ：

* `center`：　x座標とy座標を持つ`CGPoint型`
* `frame`：　ビューの領域を示す`CGRect型`
  1. `frame.origin`：変更可能。左上の座標を示す`CGPoint型`
  2. `frame.size`：　変更可能。幅と高さを示す`CGSize型`
  3. `frame.mixX`：　read-only。左上の座標x。yについても同様
  4. `frame.midX`：　read-only。中心の座標x。yについても同様
  5. `frame.maxX`：　read-only。右下の座標x。yについても同様
  6. `frame.width`：  read-only。幅
  7. `frame.height`：read-only。高さ
* `bounds`：　ビューが占める矩形の縦横サイズ。`CGRect型`だが位置は常に(0,0)とする

#### ローカル座標の変換

上の`center`や`frame`はローカル座標なので、

スーパービューが違う、２つのビューの間で座標を調整する時、`convert()`を使う

```swift
// view1の座標ptをview2の座標系に変える
view1.convert(pt, to:view2)
// view2の座標ptをview1の座標系に変える
view1.convert(pt, from:view2)
```



### スタックビュー

水平方向に並べる`Horizontal Stack View`と垂直方向に並べる`Vertical Stack View`を組み合わせると、

複雑なレイアウトも可能になる

```swift
// スタックビューの作成
let rect = CGRect(x: 0, y: 0, width: 300, height: 600)
let stackView = UIStackView(frame: rect)
stackView.axis = .vertical      // 縦積み
stackView.distribution = .fillEqually
stackView.spacing = 10
stackView.addArrangedSubview(view1)
```



### テーブルビュー

テキストや画像を行で表示するビューである。

上下にスクロールでき、行をタップして選択できる。

テーブルは複数のセクションに分けることができる

```swift
let sectionTitle = ["タイトル1", "タイトル2", "タイトル3"]
let section0 = [("テキスト","説明"), ("テキスト","説明")]
let section1 = [("テキスト","説明"), ("テキスト","説明"), ("テキスト","説明")]
let section2 = [("テキスト","説明"), ("テキスト","説明"), ("テキスト","説明")]
let tableData = [section0, section1, section2]

class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        let myTableView = UITableView(frame: view.frame, style: .grouped)
        myTableView.delegate = self
        myTableView.dataSource = self
        view.addSubview(myTableView)
    }
    
    /*　UITableViewDataSourceプロトコル */
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        // セクションごとの行数を決める
        let sectionData = tableData[section]
        return sectionData.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        // セルを作る
        let cell = UITableViewCell(style: .subtitle, reuseIdentifier: "cell")
        let sectionData = tableData[(indexPath as NSIndexPath).section]
        let cellData = sectionData[(indexPath as NSIndexPath).row]
        cell.textLabel?.text = cellData.0
        cell.detailTextLabel?.text = cellData.1
        return cell
    }
    
    func numberOfSections(in tableView: UITableView) -> Int {
        // セクションの個数を決める
        return sectionTitle.count
    }
    
    func tableView(_ tableView: UITableView, titleForHeaderInSection section: Int) -> String? {
        // セクションのタイトルを決める
        return sectionTitle[section]
    }
    
    /* UITableViewDelegateデリゲートメソッド */
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        // 行がタップされると実行される
        let title = sectionTitle[indexPath.section]
        let sectionData = tableData[indexPath.section]
        let cellData = sectionData[indexPath.row]
        print("\(title)\(cellData.1)")
        print("\(cellData.0)")
    }
    
}
```



### スクロールビュー

















