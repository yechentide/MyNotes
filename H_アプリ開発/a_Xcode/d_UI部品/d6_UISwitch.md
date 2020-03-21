# UISwitch



## プロパティ

* isOn



## コードで生成する

```swift
import UIKit

class ViewController: UIViewController {
    
    private var myLabel: UILabel!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // 背景色をCyanに設定する.
        self.view.backgroundColor = UIColor.cyan

        // Swicthを作成する.
        let mySwicth: UISwitch = UISwitch()
        mySwicth.layer.position = CGPoint(x: self.view.frame.width/2, y: self.view.frame.height - 200)
        // Swicthの枠線を表示する.
        mySwicth.tintColor = UIColor.black
        // SwitchをOnに設定する.
        mySwicth.isOn = true
        // SwitchのOn/Off切り替わりの際に、呼ばれるイベントを設定する.
        mySwicth.addTarget(self, action: #selector(ViewController.onClickMySwicth(sender:)), for: .valueChanged)
        // SwitchをViewに追加する.
        self.view.addSubview(mySwicth)

        // On/Offを表示するラベルを作成する.
        myLabel = UILabel(frame: CGRect(x:0,y:0,width:150,height:150))
        myLabel.backgroundColor = UIColor.orange
        myLabel.layer.masksToBounds = true
        myLabel.layer.cornerRadius = 75.0
        myLabel.textColor = UIColor.white
        myLabel.shadowColor = UIColor.gray
        myLabel.font = UIFont.systemFont(ofSize: 30.0)
        myLabel.textAlignment = NSTextAlignment.center
        myLabel.layer.position = CGPoint(x: self.view.bounds.width/2,y: 200)
        myLabel.text = "On"
        // ラベルをviewに追加
        self.view.addSubview(myLabel)
        
    }
    
    @objc internal func onClickMySwicth(sender: UISwitch){

        if sender.isOn {
            myLabel.text = "On"
            myLabel.backgroundColor = UIColor.orange
        }
        else {
            myLabel.text = "Off"
            myLabel.backgroundColor = UIColor.gray
        }
    }
    

    
}

```



