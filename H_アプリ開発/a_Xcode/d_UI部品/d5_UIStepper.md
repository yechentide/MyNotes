# UIStepper



## 説明

`+` `-`ボタンで数値をアップダウンさせる部品



## プロパティ

* value：　Double型。
* minimumValue：　Double型。
* maximumValue：　Double型。
* stepValue：　Double型。
* autorepeat：　Bool型。長押しの時の動き



## コードで生成する

```swift
import UIKit

class ViewController: UIViewController {
    
    private let myStepLabel: UILabel = UILabel(frame: CGRect(x:0,y:0,width:150,height:150))
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // Viewの背景色を青にする.
        self.view.backgroundColor = UIColor.cyan
        
        // Stepperの作成する.
        let myStepper: UIStepper = UIStepper()
        myStepper.center = CGPoint(x:self.view.frame.width/2, y:400)
        myStepper.backgroundColor = UIColor.gray
        myStepper.tintColor = UIColor.white
        myStepper.addTarget(self, action: #selector(ViewController.stepperOneChanged(stepper:)), for: .valueChanged)
        // 最小値, 最大値, 規定値の設定をする.
        myStepper.minimumValue = 0
        myStepper.maximumValue = 100
        myStepper.value = 50
        // ボタンを押した際に動く値の.を設定する.
        myStepper.stepValue = 10
        // Viewに追加する.
        self.view.addSubview(myStepper)

        // Labelを作成する.
        myStepLabel.backgroundColor = UIColor.blue
        myStepLabel.layer.masksToBounds = true
        myStepLabel.layer.cornerRadius = 75.0
        myStepLabel.textColor = UIColor.white
        myStepLabel.shadowColor = UIColor.gray
        myStepLabel.font = UIFont.systemFont(ofSize: 30.0)
        myStepLabel.textAlignment = NSTextAlignment.center
        myStepLabel.layer.position = CGPoint(x: self.view.bounds.width/2,y: 200)
        myStepLabel.text = "\(myStepper.value)"
        // viewにLabelを追加.
        self.view.addSubview(myStepLabel)
        
        
    }
    
    /* Stepperの値が変わったときに呼び出される. */
    @objc internal func stepperOneChanged(stepper: UIStepper){
        myStepLabel.text = "\(stepper.value)"
    }
    

    
}

```

