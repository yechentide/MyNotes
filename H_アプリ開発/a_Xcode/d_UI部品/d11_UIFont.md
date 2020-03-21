# UIFont



## コードで生成

```swift
import UIKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // 小さめのフォントの文字列をラベルに表示する.
        let mySmallLabel: UILabel = UILabel(frame: CGRect(x: 25, y: 0, width: 300, height: 150))
        mySmallLabel.font = UIFont.systemFont(ofSize: UIFont.smallSystemFontSize)
        mySmallLabel.text = "小さめのフォント"
        self.view.addSubview(mySmallLabel)

        // システムの標準のフォントサイズの文字列をラベルを表示する.
        let myNormalLabel: UILabel = UILabel(frame: CGRect(x: 25, y: 30, width: 200, height: 150))
        myNormalLabel.font = UIFont.systemFont(ofSize: UIFont.systemFontSize)
        myNormalLabel.text = "システム標準のフォントサイズ"
        self.view.addSubview(myNormalLabel)

        // UIButton用のフォントサイズの文字列をラベルに表示する.
        let myButtonLabel: UILabel = UILabel(frame: CGRect(x: 25, y: 60, width: 300, height: 150))
        myButtonLabel.font = UIFont.systemFont(ofSize: UIFont.buttonFontSize)
        myButtonLabel.text = "UIButtonのフォントサイズ"
        self.view.addSubview(myButtonLabel)

        // カスタムしたフォントサイズ(20)の文字列をラベルに表示する.
        let myCustomLabel: UILabel = UILabel(frame: CGRect(x: 25, y: 90, width: 300, height: 150))
        myCustomLabel.font = UIFont.systemFont(ofSize: CGFloat(20))
        myCustomLabel.text = "ポイント20のフォントサイズ"
        self.view.addSubview(myCustomLabel)

        // Italic Sysrem Fontの文字列をラベルに表示する.
        let myItalicLabel: UILabel = UILabel(frame: CGRect(x: 25, y: 150, width: 300, height: 150))
        myItalicLabel.font = UIFont.italicSystemFont(ofSize: UIFont.labelFontSize)
        myItalicLabel.text = "Italicフォント"
        self.view.addSubview(myItalicLabel)

        // Boldの文字列をラベルに表示する.
        let myBoldLabel: UILabel = UILabel(frame: CGRect(x: 25, y: 180, width: 300, height: 150))
        myBoldLabel.font = UIFont.boldSystemFont(ofSize: UIFont.labelFontSize)
        myBoldLabel.text = "Boldフォント"
        self.view.addSubview(myBoldLabel)

        // Arialの文字列をラベルに表示する.
        let myArialLabel: UILabel = UILabel(frame: CGRect(x: 25, y: 230, width: 300, height: 150))
        myArialLabel.font = UIFont(name: "ArilHebew", size: UIFont.labelFontSize)
        myArialLabel.text = "ArialHebrew"
        self.view.addSubview(myArialLabel)
        
        
    }

    

    
    
    
}

```

