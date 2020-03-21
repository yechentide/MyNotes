# UIButton



## プロパティ

* isEnabled：　ture/false。ボタンの有効・無効
* layer.masksToBounds：　ture/false。角丸にする時にtrueと設定
* layer.cornerRadius：　角丸の半径



## メソッド

* setImage()：　ラベルの横に表示する画像

  反映されるために、カスタムタイプのボタンを作る必要がある

  ```swift
  let aBUtton = UIButton(type: .custom)
  aButton.setImage(image1, for:.normal)
  aButton.setImage(image2, for:.highlighted)
  ```



## コードで生成

```swift
import UIKit

class ViewController: UIViewController {
    
    private var myButton: UIButton!

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // Buttonを生成する.
        myButton = UIButton()
        // ボタンのサイズ.
        let bWidth: CGFloat = 200
        let bHeight: CGFloat = 50
        // ボタンのX,Y座標.
        let posX: CGFloat = self.view.frame.width/2 - bWidth/2
        let posY: CGFloat = self.view.frame.height/2 - bHeight/2
        // ボタンの設置座標とサイズを設定する.
        myButton.frame = CGRect(x: posX, y: posY, width: bWidth, height: bHeight)
        // ボタンの背景色を設定.
        myButton.backgroundColor = UIColor.red
        // ボタンの枠を丸くする.
        myButton.layer.masksToBounds = true
        // コーナーの半径を設定する.
        myButton.layer.cornerRadius = 20.0

        
        // タイトルを設定する(通常時).
        myButton.setTitle("ボタン(通常)", for: .normal)
        myButton.setTitleColor(UIColor.white, for: .normal)
        // タイトルを設定する(ボタンがハイライトされた時).
        myButton.setTitle("ボタン(押された時)", for: .highlighted)
        myButton.setTitleColor(UIColor.black, for: .highlighted)

        
        // ボタンにタグをつける.
        myButton.tag = 1

        // イベントを追加する
        myButton.addTarget(self, action: #selector(ViewController.onClickMyButton(sender:)), for: .touchUpInside)

        // ボタンをViewに追加.
        self.view.addSubview(myButton)
    }


    /* ボタンのイベント */
    @objc internal func onClickMyButton(sender: UIButton) {
        print("onClickMyButton:");
        if let title = sender.currentTitle {
            print("sender.currentTitle: \(title)")
        }else{
            print("sender.currentTitle: none")
        }
        print("sender.tag: \(sender.tag)")
    }
    
}
```





## 色々なボタンを生成

```swift
import UIKit

class ViewController: UIViewController {
    
    private var myInfoDarkButton: UIButton!
    private var myInfoLightButton: UIButton!
    private var myAddButton: UIButton!
    private var myDetailButton: UIButton!
    private var mySystemButton: UIButton!

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // ボタンを生成.
        myInfoDarkButton = UIButton(type: .infoDark)
        myInfoLightButton = UIButton(type: .infoLight)
        myAddButton = UIButton(type: .contactAdd)
        myDetailButton = UIButton(type: .detailDisclosure)
        mySystemButton = UIButton(type: .system)

        // Systemボタン以外のボタンの位置を指定する
        let posX: CGFloat = self.view.frame.width/2
        myInfoDarkButton.layer.position = CGPoint(x: posX, y: 50)
        myInfoLightButton.layer.position = CGPoint(x: posX, y: 100)
        myAddButton.layer.position = CGPoint(x: posX, y: 150)
        myDetailButton.layer.position = CGPoint(x: posX, y: 200)

        // Systemボタンのサイズ.
        let sWidth: CGFloat = 200
        let sHeight: CGFloat = 50
        // Systemボタンの配置するx,y座標
        let sposX: CGFloat = self.view.frame.width/2 - sWidth/2
        let sposY: CGFloat = 250
        // Systemボタンに配置するx,y座標とサイズを設定.
        mySystemButton.frame = CGRect(x: sposX, y: sposY, width: sWidth, height: sHeight)
        // Systemボタンにタイトルを設定する.
        mySystemButton.setTitle("MySystemButton", for: .normal)

        // タグを設定する.
        myInfoDarkButton.tag = 1
        myInfoLightButton.tag = 2
        myAddButton.tag = 3
        myDetailButton.tag = 4
        mySystemButton.tag = 5

        // イベントを追加する
        myInfoDarkButton.addTarget(self, action: #selector(ViewController.onClickMyButton(sender:)), for: .touchDown)
        myInfoLightButton.addTarget(self, action: #selector(ViewController.onClickMyButton(sender:)), for: .touchDown)
        myAddButton.addTarget(self, action: #selector(ViewController.onClickMyButton(sender:)), for: .touchDown)
        myDetailButton.addTarget(self, action: #selector(ViewController.onClickMyButton(sender:)), for: .touchDown)
        mySystemButton.addTarget(self, action: #selector(ViewController.onClickMyButton(sender:)), for: .touchDown)

        // ボタンをViewに追加する.
        self.view.addSubview(myInfoDarkButton)
        self.view.addSubview(myInfoLightButton)
        self.view.addSubview(myAddButton)
        self.view.addSubview(myDetailButton)
        self.view.addSubview(mySystemButton)
        
        
    }

    /* ボタンのイベント */
    @objc internal func onClickMyButton(sender: UIButton) {
        print("onClickMyButton:");
        if let title = sender.currentTitle {
            print("sender.currentTitle: \(title)")
        }else{
            print("sender.currentTitle: none")
        }
        print("sender.tag: \(sender.tag)")
    }
    
    
}
```



## プルンプルンするボタン

```swift
import UIKit

class ViewController: UIViewController {

    var myButton: UIButton!
     
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // ボタンを作成する.
        myButton = UIButton()
        myButton.frame = CGRect(x:0,y:0,width:100,height:100)
        myButton.backgroundColor = UIColor.green
        myButton.layer.masksToBounds = true
        myButton.setTitle("ボタン", for: .normal)
        myButton.setTitleColor(UIColor.white, for: .normal)
        myButton.layer.cornerRadius = 50.0
        myButton.layer.position = CGPoint(x: self.view.frame.width/2, y:self.view.frame.height/2)

        // TouchDownの時のイベントを追加する.
        myButton.addTarget(self, action: #selector(ViewController.onDownButton(sender:)), for: .touchDown)

        // TouchUpの時のイベントを追加する.
        myButton.addTarget(self, action: #selector(ViewController.onUpButton(sender:)), for: [.touchUpInside,.touchUpOutside])

        // 背景色を黒に設定する.
        self.view.backgroundColor = UIColor.black

        // ボタンをViewに追加する.
        self.view.addSubview(myButton);
    }
    
    
    /* ボタンイベント(Down) */
    @objc func onDownButton(sender: UIButton){
        //UIView.animateWithDuration
        UIView.animate(withDuration: 0.06,

                                   // アニメーション中の処理.
            animations: { () -> Void in

                // 縮小用アフィン行列を作成する.
                self.myButton.transform = CGAffineTransform(scaleX: 0.9, y: 0.9)

            })
        { (Bool) -> Void in

        }
    }

    /* ボタンイベント(Up) */
    @objc func onUpButton(sender: UIButton){
        UIView.animate(withDuration: 0.1,

                                   // アニメーション中の処理.
            animations: { () -> Void in

                // 拡大用アフィン行列を作成する.
                self.myButton.transform = CGAffineTransform(scaleX: 0.4, y: 0.4)

                // 縮小用アフィン行列を作成する.
                self.myButton.transform = CGAffineTransform(scaleX: 1.0, y: 1.0)

            })
        { (Bool) -> Void in

        }
    }
    
}
```





## カスタマイズボタン

```swift
import UIKit

class ViewController: UIViewController {

    
     
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        let myButton = MyButton(frame: CGRect(x:50, y:50, width:100, height:100))
        myButton.setTitle("ボタン", for: .normal)
        myButton.setTitleColor(UIColor.black, for: .normal)
        myButton.addTarget(self, action: #selector(ViewController.onClickMyButton(sender:)), for: .touchUpInside)

        self.view.addSubview(myButton)
        
    }
    
    
    /* ボタンイベント. */
    @objc func onClickMyButton(sender: UIButton){
        print("onClickMyButton:")
        print("sender.currentTitile: \(sender.currentTitle!)")
    }
    
}

class MyButton: UIButton {

    var myStatus: ButtonStatus!
    enum ButtonStatus {
        case Normal
        case TouchBegan
        case TouchEnded
    }

    required init(coder aDecoder: NSCoder) {
        super.init(coder: aDecoder)!
    }

    override init(frame: CGRect) {
        super.init(frame: frame)
        myStatus = .Normal
    }
    override func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?) {
        super.touchesBegan(touches, with: event)

        myStatus = .TouchBegan
        self.setNeedsDisplay()
    }

    override func touchesEnded(_ touches: Set<UITouch>, with event: UIEvent?) {
        super.touchesEnded(touches, with: event)

        myStatus = .TouchEnded
        self.setNeedsDisplay()
    }

    override func draw(_ rect: CGRect) {

        let width = rect.width, height = rect.height

        if myStatus == .Normal || myStatus == .TouchEnded {
            // 色の定義.
            let color = UIColor(red: 0.081, green: 1.000, blue: 0.421, alpha: 1.000)

            // ボタンの形状を定義.
            let path = makeNormalPath(width: width, height: height)
            color.setFill()
            path.fill()
            path.lineWidth = 0
            path.stroke()

        } else if myStatus == .TouchBegan {
            // 色の定義.
            let color = UIColor(red: 1.000, green: 1.000, blue: 0.421, alpha: 1.000)

            // ボタンの形状を定義.
            let path = makeNormalPath(width: width, height: height)
            color.setFill()
            path.fill()
            path.lineWidth = 0
            path.stroke()
        }

        super.draw(rect)
    }

    /*
     ボタンの形状を作成.
     */
    private func makeNormalPath(width: CGFloat, height: CGFloat) -> UIBezierPath{
        let bezierPath = UIBezierPath()
        bezierPath.move(to: CGPoint(x:46.33/120 * width, y:0.5/120 * height))
        bezierPath.addCurve(to: CGPoint(x:37.47/120 * width, y:30.41/120 * height),
                            controlPoint1: CGPoint(x:38.21/120 * width, y:0.5/120 * height),
                            controlPoint2: CGPoint(x:45.96/120 * width, y:18.21/120 * height))
        //
        bezierPath.addCurve(to: CGPoint(x:0.54/120 * width, y:30.41/120 * height),
                                   controlPoint1: CGPoint(x:28.97/120 * width, y:42.61/120 * height),
                                   controlPoint2: CGPoint(x:2.75/120 * width, y:21.75/120 * height))
        bezierPath.addCurve(to: CGPoint(x:28.61/120 * width, y:65.04/120 * height),
                                   controlPoint1: CGPoint(x:-1.68/120 * width, y:39.06/120 * height),
                                   controlPoint2: CGPoint(x:28.61/120 * width, y:53.23/120 * height))
        bezierPath.addCurve(to: CGPoint(x:12.36/120 * width, y:96.52/120 * height),
                                   controlPoint1: CGPoint(x:28.61/120 * width, y:76.84/120 * height),
                                   controlPoint2: CGPoint(x:4.23/120 * width, y:91.79/120 * height))
        bezierPath.addCurve(to: CGPoint(x:61.1/120 * width, y:83.92/120 * height),
                                   controlPoint1: CGPoint(x:20.48/120 * width, y:101.24/120 * height),
                                   controlPoint2: CGPoint(x:38.21/120 * width, y:83.92/120 * height))
        bezierPath.addCurve(to: CGPoint(x:100.99/120 * width, y:105.96/120 * height),
                                   controlPoint1: CGPoint(x:84/120 * width, y:83.92/120 * height),
                                   controlPoint2: CGPoint(x:95.82/120 * width, y:114.62/120 * height))
        bezierPath.addCurve(to: CGPoint(x:86.22/120 * width, y:65.04/120 * height),
                                   controlPoint1: CGPoint(x:106.16/120 * width, y:97.3/120 * height),
                                   controlPoint2: CGPoint(x:83.63/120 * width, y:81.56/120 * height))
        bezierPath.addCurve(to: CGPoint(x:114.29/120 * width, y:13.09/120 * height),
                                   controlPoint1: CGPoint(x:88.8/120 * width, y:48.51/120 * height),
                                   controlPoint2: CGPoint(x:117.24/120 * width, y:17.81/120 * height))
        bezierPath.addCurve(to: CGPoint(x:69.97/120 * width, y:30.41/120 * height),
                                   controlPoint1: CGPoint(x:111.33/120 * width, y:8.37/120 * height),
                                   controlPoint2: CGPoint(x:86.96/120 * width, y:37.88/120 * height))
        bezierPath.addCurve(to: CGPoint(x:46.33/120 * width, y:0.5/120 * height),
                                   controlPoint1: CGPoint(x:52.98/120 * width, y:22.93/120 * height),
                                   controlPoint2: CGPoint(x:54.46/120 * width, y:0.5/120 * height))
        bezierPath.close()

        return bezierPath
    }
}
```



## 一つのボタンから複数のボタンが飛び出す

ViewController.swift

```swift
import UIKit

class ViewController: UIViewController {

    var mainButton: UIButton = UIButton()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // 背景を黒色に設定.
        self.view.backgroundColor = UIColor.black

        // mainボタン生成.
        mainButton = UIButton(frame: CGRect(x: 0, y: 0, width: 100, height: 100))
        mainButton.center = self.view.center

        // myCustomButtonクラスのインスタンス生成.
        let myCusButton: MyCustomButton = MyCustomButton(frame: self.view.frame)
        myCusButton.mainButton = self.mainButton
        myCusButton.mainPosition = self.mainButton.layer.position

        // インスタンスをviewに追加.
        self.view.addSubview(myCusButton)

        // mainボタン各設定.
        mainButton.layer.masksToBounds = true
        mainButton.layer.cornerRadius = 50.0
        mainButton.backgroundColor = UIColor.red
        mainButton.setTitle("Fire!", for: .normal)
        mainButton.setTitleColor(UIColor.white, for: .normal)
        mainButton.addTarget(myCusButton, action: #selector(myCusButton.onDownMainButton(sender:)), for: .touchUpInside)
        mainButton.addTarget(myCusButton, action: #selector(myCusButton.onUpMainButton(sender:)), for: [.touchUpInside, .touchDragOutside])
        mainButton.tag = 0

        // mainボタンをviewに追加.
        self.view.addSubview(mainButton)
    }
    
    
    
    
}
```

MyCustomButton.swift

```swift
import Foundation
import UIKit

class MyCustomButton: UIView {

    // subボタン(飛び出すボタン)を生成
    var subButton_1: UIButton = UIButton()
    var subButton_2: UIButton = UIButton()
    var subButton_3: UIButton = UIButton()
    var subButton_4: UIButton = UIButton()
    var subButton_5: UIButton = UIButton()

    var mainButton: UIButton!

    var colors: NSMutableArray!

    var mainPosition: CGPoint!

    //var viewControll: UIViewController = ViewController()

    required init(coder aDecoder: NSCoder) {
        super.init(coder: aDecoder)!
    }

    override init(frame: CGRect) {
        super.init(frame: frame)
    }

    /* メインボタンイベント(Down) */
    @objc func onDownMainButton(sender: UIButton) {

        // 背景を黒色に設定.
        self.backgroundColor = UIColor.black

        UIView.animate(withDuration: 0.06,

                                   // アニメーション中の処理.
            animations: { () -> Void in

                // 縮小用アフィン行列を生成する.
                sender.transform = CGAffineTransform(scaleX: 0.9, y: 0.9)
            })
        { (Bool) -> Void in
        }
    }

    /* subボタンの座標を返すメソッド */
    func getPosition(angle: CGFloat, radius: CGFloat) -> CGPoint {

        // 度からラジアンに変換.
        let radian = angle * CGFloat(Double.pi) / 180.0

        // x座標を計算.
        let x_position:CGFloat = mainButton.layer.position.x + radius * cos(radian)

        // y座標を計算.
        let y_position = mainPosition.y + radius * sin(radian)
        let position = CGPoint(x: x_position, y: y_position)

        return position
    }

    /* メインボタンイベント(Up) */
    @objc func onUpMainButton(sender: UIButton) {

        // subボタンを配列に格納.
        let buttons = [subButton_1, subButton_2, subButton_3, subButton_4, subButton_5]

        // subボタン用の　UIColorを配列に格納.
        colors = [UIColor.yellow, UIColor.green, UIColor.cyan, UIColor.magenta, UIColor.purple] as NSMutableArray

        // mainボタンからの距離(半径).
        let radius: CGFloat = 150

        // subボタンに各種設定.
        for i in 0 ..< buttons.count {
            buttons[i].frame = CGRect(x: 0, y: 0, width: 60, height: 60)
            buttons[i].layer.cornerRadius = 30.0
            buttons[i].backgroundColor = colors[i] as? UIColor
            buttons[i].center = self.center
            buttons[i].addTarget(self, action: #selector(MyCustomButton.onClickSubButtons(sender:)), for: .touchUpInside)
            buttons[i].tag = i+1

            // subボタンをviewに追加.
            self.addSubview(buttons[i])
        }

        UIView.animate(withDuration: 0.06,

                                   // アニメーション中の処理.
            animations: { () -> Void in

                // 拡大用アフィン行列を作成する.
                sender.transform = CGAffineTransform(scaleX: 0.4, y: 0.4)

                // 縮小用アフィン行列を作成する.
                sender.transform = CGAffineTransform(scaleX: 1.0, y: 1.0)
            })
        { (Bool) -> Void in
        }

        UIView.animate(withDuration: 0.7,
                                   delay: 0.0,

                                   // バネを設定.
            usingSpringWithDamping: 0.5,

            // バネの弾性力.
            initialSpringVelocity: 1.5,
            options: .curveEaseIn,

            // アニメーション中の処理.
            animations: { () -> Void in

                // subボタンに座標を設定.
                self.subButton_1.layer.position = self.getPosition(angle: -90, radius: radius)
                self.subButton_2.layer.position = self.getPosition(angle: -30, radius: radius)
                self.subButton_3.layer.position = self.getPosition(angle: -60, radius: radius)
                self.subButton_4.layer.position = self.getPosition(angle: -120, radius: radius)
                self.subButton_5.layer.position = self.getPosition(angle: -150, radius: radius)
        }) { (Bool) -> Void in
        }
    }


    /* subボタンイベント   背景の色を設定. */
    @objc func onClickSubButtons(sender: UIButton) {

        // 背景色をsubボタンの色に設定.
        switch(sender.tag) {
        case 1:
            self.backgroundColor = colors[0] as? UIColor
        case 2:
            self.backgroundColor = colors[1] as? UIColor
        case 3:
            self.backgroundColor = colors[2] as? UIColor
        case 4:
            self.backgroundColor = colors[3] as? UIColor
        case 5:
            self.backgroundColor = colors[4] as? UIColor
        default:
            self.backgroundColor = UIColor.black
        }
    }

}
```

