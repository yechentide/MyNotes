# UISegmentedControl



## 説明

複数の選択肢に分割された部品（ラジオボタンのような機能）



## プロパティ

* selectedSegmentIndex



## コードで生成

```swift
import UIKit

class ViewController: UIViewController {

    private let mySegLabel: UILabel = UILabel(frame: CGRect(x:0,y:0,width:150,height:150))
     
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // 表示する配列を作成する.
        let myArray: NSArray = ["Red","Blue","Green"]

        // SegmentedControlを作成する.
        let mySegcon: UISegmentedControl = UISegmentedControl(items: myArray as [AnyObject])
        mySegcon.center = CGPoint(x: self.view.frame.width/2, y: 400)
        mySegcon.backgroundColor = UIColor.gray
        mySegcon.tintColor = UIColor.white

        // イベントを追加する.
        mySegcon.addTarget(self, action: #selector(ViewController.segconChanged(segcon:)), for: .valueChanged)

        // Viewに追加する.
        self.view.addSubview(mySegcon)

        // Labelを作成する.
        mySegLabel.backgroundColor = UIColor.white
        mySegLabel.layer.masksToBounds = true
        mySegLabel.layer.cornerRadius = 75.0
        mySegLabel.textColor = UIColor.white
        mySegLabel.shadowColor = UIColor.gray
        mySegLabel.font = UIFont.systemFont(ofSize: 30.0)
        mySegLabel.textAlignment = NSTextAlignment.center
        mySegLabel.layer.position = CGPoint(x: self.view.bounds.width/2,y: 200)

        // Viewの背景色をCyanにする.
        self.view.backgroundColor = UIColor.cyan

        // Viewに追加する.
        self.view.addSubview(mySegLabel);
    }
    
    
    /* SwgmentedControlの値が変わったときに呼び出される. */
    @objc internal func segconChanged(segcon: UISegmentedControl){

        switch segcon.selectedSegmentIndex {
        case 0:
            mySegLabel.backgroundColor = UIColor.red

        case 1:
            mySegLabel.backgroundColor = UIColor.blue

        case 2:
            mySegLabel.backgroundColor = UIColor.green

        default:
            print("Error")
        }
    }
    
}

```



