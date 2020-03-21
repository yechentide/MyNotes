# UITableView



## 説明

テキストや画像を行で表示するビューである。

上下にスクロールでき、行をタップして選択できる。

テーブルは複数のセクションに分けることができる



## コードで生成

```swift
import UIKit

class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {
    
    // Tableで使用する配列を設定する
    private let myItems: NSArray = ["TEST1", "TEST2", "TEST3"]
    private var myTableView: UITableView!

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // 一番上のStatus Barの高さを取得する.
        let barHeight: CGFloat = UIApplication.shared.statusBarFrame.size.height
        // Viewの高さと幅を取得する.
        let displayWidth: CGFloat = self.view.frame.width
        let displayHeight: CGFloat = self.view.frame.height
        // TableViewの生成(Status barの高さをずらして表示).
        myTableView = UITableView(frame: CGRect(x: 0, y: barHeight, width: displayWidth, height: displayHeight))

        // Cell名の登録をおこなう.
        myTableView.register(UITableViewCell.self, forCellReuseIdentifier: "MyCell")
        // DataSourceを自身に設定する.
        myTableView.dataSource = self
        // Delegateを自身に設定する.
        myTableView.delegate = self

        // Viewに追加する.
        self.view.addSubview(myTableView)
        
        
    }

    
    /* Cellの総数を返す. */
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return myItems.count
    }
    
    /* Cellに値を設定する */
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        // 再利用するCellを取得する.
        let cell = tableView.dequeueReusableCell(withIdentifier: "MyCell", for: indexPath as IndexPath)

        // Cellに値を設定する.
        cell.textLabel!.text = "\(myItems[indexPath.row])"

        return cell
    }
    
    /* Cellが選択された際に呼び出される */
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        print("Num: \(indexPath.row)")
        print("Value: \(myItems[indexPath.row])")
    }

    
    
    
}
```



## 複数のセクション

```swift
import UIKit

class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {
    
    // Tableで使用する配列を定義する.
    private let myiPhoneItems: NSArray = ["iOS9","iOS8", "iOS7", "iOS6", "iOS5", "iOS4"]
    private let myAndroidItems: NSArray = ["5.x", "4.x", "2.x", "1.x"]
    // Sectionで使用する配列を定義する.
    private let mySections: NSArray = ["iPhone", "Android"]
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // Status Barの高さを取得を.する.
        let barHeight: CGFloat = UIApplication.shared.statusBarFrame.size.height

        // Viewの高さと幅を取得する.
        let displayWidth: CGFloat = self.view.frame.width
        let displayHeight: CGFloat = self.view.frame.height

        // TableViewの生成( status barの高さ分ずらして表示 ).
        let myTableView: UITableView = UITableView(frame: CGRect(x: 0, y: barHeight, width: displayWidth, height: displayHeight - barHeight))
        // Cell名の登録をおこなう.
        myTableView.register(UITableViewCell.self, forCellReuseIdentifier: "MyCell")
        // DataSourceの設定をする.
        myTableView.dataSource = self
        // Delegateを設定する.
        myTableView.delegate = self

        // Viewに追加する.
        self.view.addSubview(myTableView)
        
        
    }
    
    
    /* セクションの数を返す. */
    func numberOfSections(in tableView: UITableView) -> Int {
        return mySections.count
    }

    /* セクションのタイトルを返す. */
    func tableView(_ tableView: UITableView, titleForHeaderInSection section: Int) -> String? {
        return mySections[section] as? String
    }

    /* テーブルに表示する配列の総数を返す. */
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        if section == 0 {
            return myiPhoneItems.count
        } else if section == 1 {
            return myAndroidItems.count
        } else {
            return 0
        }
    }
    
    /* Cellに値を設定する. */
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {

        let cell = tableView.dequeueReusableCell(withIdentifier: "MyCell", for: indexPath)

        if indexPath.section == 0 {
            cell.textLabel?.text = "\(myiPhoneItems[indexPath.row])"
        } else if indexPath.section == 1 {
            cell.textLabel?.text = "\(myAndroidItems[indexPath.row])"
        }

        return cell
    }
    
    /* Cellが選択された際に呼び出される. */
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        if indexPath.section == 0 {
            print("Value: \(myiPhoneItems[indexPath.row])")
        } else if indexPath.section == 1 {
            print("Value: \(myAndroidItems[indexPath.row])")
        }
    }
    

    
}

```

```swift
import UIKit


// テーブルビューに表示するデータ
let sectionTitle = ["チョウ目", "バッタ目", "コウチュウ目"]
let section0 = [("キタテハ","タテハチョウ科"),("クロアゲハ","アゲハチョウ科")]
let section1 = [("キリギリス","キリギリス科"),("ヒナバッタ","バッタ科"),("マツムシ","マツムシ科")]
let section2 = [("ハンミョウ","ハンミョウ科"),("アオオサムシ","オサムシ科"),("チビクワガタ","クワガタムシ科")]
let tableData = [section0, section1, section2]


class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource  {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // テーブルビューを作る
        let myTableView:UITableView!
        myTableView = UITableView(frame: view.frame, style: .grouped)
        // テーブルビューのデリゲートを設定する
        myTableView.delegate = self
        // テーブルビューのデータソースを設定する
        myTableView.dataSource = self
        // テーブルビューを表示する
        view.addSubview(myTableView)
    }
    
    
    /*　UITableViewDataSourceプロトコル */
    // セクションの個数を決める
    func numberOfSections(in tableView: UITableView) -> Int {
        return sectionTitle.count
    }

    // セクションごとの行数を決める
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        let sectionData = tableData[section]
        return sectionData.count
    }

    // セクションのタイトルを決める
    func tableView(_ tableView: UITableView, titleForHeaderInSection section: Int) -> String? {
        return sectionTitle[section]
    }

    // セルを作る
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = UITableViewCell(style: .subtitle, reuseIdentifier: "cell")
        let sectionData = tableData[(indexPath as NSIndexPath).section]
        let cellData = sectionData[(indexPath as NSIndexPath).row]
        cell.textLabel?.text = cellData.0
        cell.detailTextLabel?.text = cellData.1
        return cell
    }

    /* UITableViewDelegateデリゲートメソッド */
    // 行がタップされると実行される
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        let title = sectionTitle[indexPath.section]
        let sectionData = tableData[indexPath.section]
        let cellData = sectionData[indexPath.row]
        print("\(title)\(cellData.1)")
        print("\(cellData.0)")
    }



}
```



## ボタン拡張

```swift
import UIKit

class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {

    var myItems: [String] = ["TEST1", "TEST2", "TEST3"]
    var myTableView: UITableView = UITableView()
     
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // Status Barの高さを取得.
        let barHeight: CGFloat = UIApplication.shared.statusBarFrame.size.height

        // Viewの高さと幅を取得.
        let displayWidth: CGFloat = self.view.frame.width
        let displayHeight: CGFloat = self.view.frame.height

        // TableViewの生成( status barの高さ分ずらして表示 ).
        myTableView.frame = CGRect(x: 0, y: barHeight, width: displayWidth, height: displayHeight - barHeight)

        // Cellの登録.
        myTableView.register(UITableViewCell.self, forCellReuseIdentifier: "MyCell")

        // DataSourceの設定.
        myTableView.dataSource = self

        // Delegateを設定.
        myTableView.delegate = self

        // Viewに追加する.
        self.view.addSubview(myTableView)
    }
    
    
    /* Cellが選択された際に呼び出される. */
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        print("Num: \(indexPath.row)")
        print("Value: \(myItems[indexPath.row])")
    }

    /* Cellの総数を返す. */
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        print("numberOfRowsInSection")
        return myItems.count
    }

    /* Editableの状態にする. */
    func tableView(_ tableView: UITableView, canEditRowAt indexPath: IndexPath) -> Bool {
        print("canEditRowAtIndexPath")

        return true
    }

    /* 特定の行のボタン操作を有効にする. */
    func tableView(_ tableView: UITableView, commit editingStyle: UITableViewCell.EditingStyle, forRowAt indexPath: IndexPath) {
        print("commitEdittingStyle:\(editingStyle)")
    }

    /* Cellに値を設定する. */
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        print("cellForRowAtIndexPath")

        let cell: UITableViewCell = tableView.dequeueReusableCell(withIdentifier: "MyCell", for: indexPath as IndexPath)
        //tableView.dequeueReusableCellWithIdentifier("MyCell", forIndexPath: indexPath as IndexPath)

        cell.textLabel?.text = "\(myItems[indexPath.row])"

        return cell
    }

    /* Buttonを拡張する. */
    func tableView(_ tableView: UITableView, editActionsForRowAt indexPath: IndexPath) -> [UITableViewRowAction]? {

        // Shareボタン.
        let myShareButton: UITableViewRowAction = UITableViewRowAction(style: .normal, title: "Share") { (action, index) -> Void in

            tableView.isEditing = false
            print("share")

        }
        myShareButton.backgroundColor = UIColor.blue

        // Archiveボタン.
        let myArchiveButton: UITableViewRowAction = UITableViewRowAction(style: .normal, title: "Archive") { (action, index) -> Void in

            tableView.isEditing = false
            print("archive")

        }
        myArchiveButton.backgroundColor = UIColor.red

        return [myShareButton, myArchiveButton]
    }
    
}
```





































