# UIProgressView



```swift
import UIKit

class ViewController: UIViewController {

    
     
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // 背景色を黒色にする.
        self.view.backgroundColor = UIColor.black

        // ProgressViewを作成する.
        let myProgressView: UIProgressView = UIProgressView(frame: CGRect(x:0, y:0, width:200, height:10))
        myProgressView.progressTintColor = UIColor.blue
        myProgressView.trackTintColor = UIColor.white

        // 座標を設定する.
        myProgressView.layer.position = CGPoint(x: self.view.frame.width/2, y: 200)

        // バーの高さを設定する(横に1.0倍,縦に2.0倍).
        myProgressView.transform = CGAffineTransform(scaleX: 1.0, y: 2.0)

        // 進捗具合を設定する(0.0~1.0).
        myProgressView.progress = 0.0

        // アニメーションを付ける.
        myProgressView.setProgress(1.0, animated: true)

        // Viewに追加する.
        self.view.addSubview(myProgressView)
    }
    
    
    
    
}

```

