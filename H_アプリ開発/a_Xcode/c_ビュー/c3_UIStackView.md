# UIStackView



## 説明

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



## コードで生成

```swift
import UIKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        // ビューを準備する
        let view1 = UIView()
        view1.backgroundColor = .lightGray
        let view2 = UIView()
        view2.backgroundColor = .gray
        let photo1 = UIImageView(image: UIImage(named:"img1.jpg"))
        let photo2 = UIImageView(image: UIImage(named:"img2.jpg"))
        let photo3 = UIImageView(image: UIImage(named:"img3.jpg"))
        photo1.contentMode = .scaleAspectFill
        photo1.clipsToBounds = true
        photo2.contentMode = .scaleAspectFill
        photo2.clipsToBounds = true
        photo3.contentMode = .scaleAspectFill
        photo3.clipsToBounds = true
        
        // スタックビューを作る
        let rect = CGRect(x: 0, y: 0, width: 300, height: 600)
        let stackView = UIStackView(frame: rect)
        stackView.axis = .vertical
        stackView.distribution = .fillEqually
        stackView.spacing = 10
        
        // スタックビューにビューを追加
        stackView.addArrangedSubview(view1)
        stackView.addArrangedSubview(view2)
        stackView.addArrangedSubview(photo1)
        stackView.addArrangedSubview(photo2)
        stackView.addArrangedSubview(photo3)
        
        // スタックビューを画面中央に表示する
        stackView.center = self.view.center
        self.view.addSubview(stackView)
        
        
    }


}
```

